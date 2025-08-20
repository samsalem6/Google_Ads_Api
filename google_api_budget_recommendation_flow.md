# Updated Search Campaign Flow with Budget Logic
## Step 1: Campaign Settings

Campaign name

Campaign type: Search

Goal selection (Sales, Leads, Website Traffic, etc.)

Bidding strategy (Manual CPC, Maximize Conversions, Target CPA, etc.)

Networks (Google Search, Search Partners, Display opt-in)

Locations (include / exclude — from geo_target_constant API)

Languages

Ad schedule

Conversion goals (fetched from customer_conversion_goal + conversion_action)

## Step 2: Audience & Keywords

Add audience targeting (from GA4, in-market, remarketing, custom segments)

Add keyword targeting:

Keyword suggestions (via KeywordPlanIdeaService)

Match types (Broad, Phrase, Exact)

## Step 3: Ad Groups

Ad group name

Default max CPC bid

Add keywords

## Step 4: Responsive Search Ads

Final URL

Display path

Headlines (up to 15)

Descriptions (up to 4)

Ad extensions:

Sitelink, Callout, Structured Snippets, Call, Location, Lead Form, etc.

## Step 5: Budget Recommendation (AI-Driven)

System gathers all prior inputs:

Goals + Conversion actions

Keywords (from Ad Groups)

Bidding strategy

Locations & Languages

System creates a temporary Keyword Plan:

KeywordPlanCampaign (with campaign-level settings)

KeywordPlanAdGroup (per ad group)

KeywordPlanKeyword (keywords added)

System calls Forecast API:

KeywordPlanService.GenerateForecastMetrics

Gets predicted clicks, impressions, conversions, and cost.

System calls RecommendationService (CAMPAIGN_BUDGET):

Returns suggested Low / Recommended / High budgets with estimated outcomes.

UI shows budget options like Google Ads:

Low: $10/day → ~150 clicks/week

Recommended: $25/day → ~400 clicks/week

High: $50/day → ~800 clicks/week

Custom option: user can override

# Step 6: Review & Publish

Review campaign summary (settings, ads, audiences, budget).

Save & Publish → calls:

CampaignBudgetService (create budget)

CampaignService (create campaign)

AdGroupService (create ad groups)

AdGroupAdService (create ads)

CampaignExtensionSettingService (attach extensions)

✅ Now the flow matches real Google Ads UI:

Budget step comes after ads & targeting,

Recommendations are data-driven, not random,

Final step is clean Review & Publish.
