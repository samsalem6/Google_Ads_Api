# AI-Enhanced Search Campaign Flow

## Step 1: Campaign Settings

Campaign name, type = Search, bidding, budget, dates, networks, locations, languages, schedule.

AI enhancement:

Use GenerateRecommendations → get budget + bidding recommendations before user sets them.

Use RecommendationService → suggest networks (e.g., opt-in to Display partners).

## Step 2: Conversion Tracking (optional)

Choose or create conversion actions.

AI enhancement:

Use RecommendationService to suggest which conversion actions should be linked based on account activity.

## Step 3: Audience & Keywords

Add audiences, add keywords.

AI enhancement:

KeywordPlanIdeaService → generate keyword ideas from website URL + seed terms.

Show AI-suggested match types (Broad/Phrase/Exact split).

RecommendationService → suggest audience segments (in-market, remarketing, custom).

## Step 4: Ad Groups

Ad group name, CPC, keywords.

AI enhancement:

Pre-fill keyword clusters with KeywordPlanIdeaService results.

Use Recommendations to adjust default bids per ad group.

## Step 5: Responsive Search Ads (RSA)

Final URL, display path, up to 15 headlines + 4 descriptions, extensions.

AI enhancement:

SmartCampaignSuggestService.SuggestSmartCampaignAd → get AI-generated headlines + descriptions.

Auto-generate sitelinks, callouts, snippets from RecommendationService.

Optionally enable Automatically Created Assets (ACA) in UI (not API-controlled, but you can manage the outputs via API).

## Step 6: Review & Publish

Campaign summary.

AI enhancement:

Run RecommendationService again → show “fixes” (raise budget, add extensions, new keywords).

# AI-Enhanced Performance Max Campaign Flow

## Step 1: Campaign Settings

Name, type = Performance Max, goal selection, bidding strategy, budget, dates, locations, languages, URL expansion.

AI enhancement:

GenerateRecommendations → budget + bidding recs.

RecommendationService → suggest goal settings & URL expansion toggle.

## Step 2: Asset Groups

Asset group name, final URLs, headlines, descriptions, business name, logos, images, videos, CTA text.

AI enhancement:

SmartCampaignSuggestService.SuggestSmartCampaignAd → auto-generate headlines + descriptions from business info.

KeywordPlanIdeaService → scan site for product/service categories → use to structure asset groups.

AI can also pull images/videos from website & YouTube (or Google auto-generate videos if none provided).

## Step 3: Audience Signals

Add custom segments, lists, interests, demographics.

AI enhancement:

RecommendationService → suggest audience signals based on similar advertisers.

KeywordPlanIdeaService → feed into custom audience segments.

## Step 4: Extensions

Sitelinks, callouts, snippets, call, lead forms.

AI enhancement:

RecommendationService → suggest which extensions to add (callouts, sitelinks, structured snippets).

Auto-generate sitelinks from site navigation (About, Contact, Offers).

## Step 5: Review & Publish

Settings summary.

AI enhancement:

Run RecommendationService → check coverage (budget too low? missing assets? no call extensions?).

✅ Key Enhancements Summary
Step	Search AI Plug	PMax AI Plug
Budget/Bidding	GenerateRecommendations, RecommendationService	GenerateRecommendations, RecommendationService
Keywords	KeywordPlanIdeaService, SmartCampaignSuggestService	KeywordPlanIdeaService for asset groups
Ad Text	SmartCampaignSuggestService.SuggestSmartCampaignAd	Same (for text assets)
Extensions	RecommendationService	RecommendationService
Audiences	RecommendationService, KeywordPlanIdeaService	RecommendationService
Review	RecommendationService (final fixes)	RecommendationService (final fixes)

⚡ With this, your flow behaves like Google Ads UI:

Every step is prefilled with Google’s own AI recommendations, but still editable before final publish.
