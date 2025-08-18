# AI-Enhanced Search Campaign Flow (Full Fields)

## Step 1: Campaign Settings

- Campaign name

- Campaign type = Search

### Note: 
After choosing a campaign goal (e.g. Sales, Leads, Website Traffic), Google Ads asks:

- “Select the ways you’d like to reach your goal”
👉 This is basically where you choose the conversion sources / actions relevant to the goal.

Available options in the UI:

🌐 Website visits → Enter website URL(s) (usually GA4 linked, tracks conversions like purchases, sign-ups, etc.)

📞 Phone calls → Add call extensions or call tracking numbers

📍 Store visits → If linked with Business Profile

🛒 App downloads → From Google Play / App Store (if app campaign)

- Networks: Search Network, Display Network (toggle)

- Start / End dates

- Ad schedule: days, hours

- Locations: country, region, radius targeting

- Languages

- Bidding strategy: Manual CPC, Maximize Clicks, Maximize Conversions, Target CPA, Target ROAS

- Final URL expansion (on/off)

- Tracking template (optional)

### ### AI enhancement:

- RecommendationService → suggest networks, bidding strategies, schedules based on industry benchmarks.

## Step 2: Conversion Tracking (optional)

- Conversion actions: import from GA4 or create new (website, call, app, offline)

- Include in Conversions toggle

- Attribution model: Last Click, Data-Driven, Position-Based, Linear, etc.

### ### AI enhancement:

- RecommendationService → suggest optimal conversion goals based on account data.

## Step 3: Audience & Keywords

- Audiences:

- In-market segments

- Remarketing lists

- Custom segments

- Import from GA4 (user lists, predictive audiences)

- Keywords:

- Manual entry

- Upload file

- KeywordPlanIdeaService → suggestions from website or seed term

- Match types: Broad, Phrase, Exact

### ### AI enhancement:

- RecommendationService → suggest relevant in-market/custom segments.

## Step 4: Ad Groups

- Ad group name

- Default max CPC bid

- Keywords (clustered by theme)

### ### AI enhancement:

- Keyword clustering + bid adjustments auto-suggested via KeywordPlanIdeaService + Recommendations.

## Step 5: Responsive Search Ads (RSA)

- Final URL

- Display path (2 optional fields)

- Headlines (up to 15)

- Descriptions (up to 4)

- Business name

- Ad strength meter

- Extensions: Sitelinks, Callouts, Snippets, Calls, Lead Forms, Price, Promotion

### AI enhancement:

- SmartCampaignSuggestService.SuggestSmartCampaignAd → generate headlines + descriptions

- RecommendationService → generate sitelinks, callouts, snippets.

## Step 6: Budget Recommendations

- Daily budget (micros)

- Show range: Low, Recommended, High

### AI enhancement:

- GenerateRecommendations → recommend budget & bid strategy after keywords/audience/ad setup.

## Step 7: Review & Publish

- Review summary (settings, ads, keywords, budget)

- Fix alerts (missing conversions, low budget, too few assets)

- Publish

### AI enhancement:

- RecommendationService final scan: “Add more headlines”, “Increase budget”, “Add sitelinks”.

# AI-Enhanced Performance Max Campaign Flow (Full Fields)

## Step 1: Campaign Settings

- Campaign name

- Type = Performance Max

- Goal selection: Sales, Leads, Website Traffic, etc.

### Note:
After choosing a campaign goal (e.g. Sales, Leads, Website Traffic), Google Ads asks:

- “Select the ways you’d like to reach your goal”
👉 This is basically where you choose the conversion sources / actions relevant to the goal.

Available options in the UI:

🌐 Website visits → Enter website URL(s) (usually GA4 linked, tracks conversions like purchases, sign-ups, etc.)

📞 Phone calls → Add call extensions or call tracking numbers

📍 Store visits → If linked with Business Profile

🛒 App downloads → From Google Play / App Store (if app campaign)

- Bidding strategy: Maximize Conversions, Maximize Conversion Value, Target CPA, Target ROAS

- Start / End dates

- Ad schedule

- Locations (geo targeting)

- Languages

- URL expansion (on/off)

- Tracking template (optional)

### AI enhancement:

- RecommendationService → suggest goal/bid combos.

## Step 2: Asset Groups

- Asset group name

- Final URLs (multiple allowed)

- Headlines (up to 15)

- Descriptions (up to 5)

- Long headline

- Business name

- Logos

- Images

- Videos (upload or let Google auto-generate)

- Call-to-action text

- Ad strength meter

### AI enhancement:

- SmartCampaignSuggestService → generate ad text

- AI auto-pull images/videos from website/YouTube

- KeywordPlanIdeaService → recommend asset group structure.

## Step 3: Audience Signals

- Custom segments

- Custom intent (keywords)

- Demographics: age, gender, parental status, income

- Customer lists

- GA4 imports: predictive audiences, custom GA4 segments

### AI enhancement:

- RecommendationService → suggest audience signals based on vertical.

## Step 4: Extensions

- Sitelinks

- Callouts

- Snippets

- Call extension

- Lead form

- Price extension

- Promotion extension

### AI enhancement:

- RecommendationService → suggest which extensions to add

- Auto-generate sitelinks from navigation structure.

## Step 5: Budget Recommendations

- Daily budget

- Recommended range: Low, Recommended, High

### AI enhancement:

- GenerateRecommendations after assets + audiences are defined.

## Step 6: Review & Publish

- Campaign summary (settings, budget, ads, assets, targeting)

- Fix alerts (missing extensions, low budget, weak ad strength)

- Publish campaign

### AI enhancement:

- RecommendationService → flag issues before launch.

## Step 7: Post-Launch Optimization

- Realtime reporting

- GA4 linking → conversion data + audience expansion

- RecommendationService → continuous optimizations (budget adjustments, add assets, broaden targeting)

- Experimentation: run A/B or geo experiments.

## ✅ Key Enhancements Summary

| Step                | Search AI Plug                               | PMax AI Plug                                |
|----------------------|----------------------------------------------|--------------------------------------------|
| Campaign Settings    | RecommendationService                        | RecommendationService                      |
| Conversion Tracking  | RecommendationService                        | —                                          |
| Audience & Keywords  | KeywordPlanIdeaService, RecommendationService | RecommendationService, GA4 import         |
| Ad Text / Assets     | SmartCampaignSuggestService                  | SmartCampaignSuggestService                |
| Audiences            | RecommendationService, GA4 import            | RecommendationService, GA4 import          |
| Extensions           | RecommendationService                        | RecommendationService                      |
| Budget               | GenerateRecommendations                      | GenerateRecommendations                    |
| Review               | RecommendationService                        | RecommendationService                      |
| Post-Launch          | —                                            | RecommendationService, Experiments         |



## ⚡ With this, your flow mirrors the Google Ads UI step for step, including all fields + AI injections + GA4 audience integration.

## ✅ With this enhanced flow:

- Search Campaigns → More manual but AI assists in keywords, ads, and budgets.

- Performance Max Campaigns → Heavily automated with AI for creative, targeting, and budgets.

- GA4 Integration → Brings in remarketing and predictive audiences just like real Google Ads.

