# Google_Ads_Api Create campaign
End-to-end flow (step-by-step) for create campaigns 

### 1- Entry: choose goal + campaign type (UI wizard first screen)

UI fields: Goal (Sales/Leads/Traffic — used to prefill settings), Campaign Type (Search, Display, Performance Max, Demand Gen, App, Video).

Implementation: map chosen goal → suggested AdvertisingChannelType, bidding strategy, and UI preset. (Note: some video types can only be read via API; consider recommending Performance Max/Demand Gen for full API manageability).

### 2- Campaign basics (name, status, start/end dates, ad scheduling, networks)

Create local draft record (DB) with these fields, status = draft. UI shows advanced toggle for network settings.

API mapping: Campaign resource (advertisingChannelType, name, status, startDate, endDate, networkSettings). Recommendation: create campaigns initially PAUSED then enable after ads/targeting ready. 
Google for Developers

### 3- Budget & bidding (shared vs campaign budget, bidding strategy)

UI: per-campaign budget or shared budget (dropdown for existing shared budgets). Bidding type (Manual CPC, Target CPA, Maximize Conversions, Target ROAS, Portfolio strategies).

API resources: CampaignBudget (create via CampaignBudgetService) and campaign’s bidding fields. If using shared, create or reuse CampaignBudget resource and attach its resourceName to Campaign. 

### 4- Targeting (locations, languages, audiences, demographics, devices)

UI: location picker, languages, audience segments, custom intent, device type, negative locations.

API mapping: CampaignCriterion and AdGroupCriterion (for keywords), use CampaignCriterionService / AdGroupCriterionService. Apply geotargeting & languages at campaign level. 

### 5- Ad groups, keywords & bids (container + targeting)

UI: create one or more ad groups, set ad group bid defaults, add keywords (match types), negative keyword lists.

API mapping: AdGroup (AdGroupService), AdGroupCriterion for keywords, and bids via cpcBidMicros on AdGroup or AdGroupCriterion. 

### 6- Ads & assets (Responsive Search Ads, Image, Video, Asset groups for PMax)

UI: upload images, enter headlines/descriptions, final URLs, path fields, preview. For Performance Max use Asset Groups and asset signals.

API mapping: AdGroupAd with Ad (e.g., ResponsiveSearchAdInfo), AssetService for images/assets, AssetGroup for Performance Max. 

### 7- Extensions & extras (sitelinks, callouts, structured snippets, location extensions)

UI: extension editor and preview. Support shared vs campaign-level extensions.

API mapping: Assets and extension resources (specific services; treat as separate mutate ops).

### 8- Review & validation (client-side + server-side)

Server side runs validation rules that mirror Google Ads constraints (asset count limits, headline lengths, required fields for selected campaign type). If everything valid, prepare bulk mutate payload. (Use client libs to validate or call Google Ads test token endpoints in test accounts.)

### 9- Create (send to Google Ads API)

Best practice: bundle required resources into a single bulk mutate (campaignBudget, campaign, ad groups, adGroupAds, adGroupCriteria, campaignCriteria) so the account ends up in a valid serving state in one request. This lowers partial-create risk. 

API endpoints: CampaignBudgetService.mutateCampaignBudgets, CampaignService.mutateCampaigns, AdGroupService.mutateAdGroups, AdGroupAdService.mutateAdGroupAds, AdGroupCriterionService.mutateAdGroupCriteria. Example curl samples show Developer-Token + login headers. 

### 10- Handle response & store resource names

Save returned resourceName(s) into your DB records (campaign_resource_name, ad_group_resource_name, asset resource names). Update local status from draft → created (and keep enabled/paused state as returned).

### 11- Post-create tasks

(a) Create conversion goals / conversion tracking linking if user requested.

(b) Add ad extensions or shared negative lists.

(c) If campaign was created PAUSED, run an automated final validation checklist and flip to ENABLED when safe.

### 12- Monitoring / sync / retry

Queue a job to fetch campaign status and diagnostics (GoogleAdsService.search or SearchStream) and show warnings in the UI (policy rejections, insufficient billing, missing assets). Implement retry/backoff for transient errors. 


### 14- Edge cases

Some campaign types (certain video campaign edits) cannot be written via API — show UI warning and link to Google Ads UI or recommend alternatives like Performance Max/Demand Gen that are fully manageable. 
