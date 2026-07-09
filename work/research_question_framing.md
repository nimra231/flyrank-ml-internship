# Research Question Framing

## Lane
**Lane 2: Refresh / Content Opportunity Scoring** (Core lane)

## Research Question
Which content pages show enough evidence of decline or missed opportunity — combined with 
enough search visibility to matter — that they should be prioritized for human review first?

## Unit of Analysis
One row = one content page (`content_id`), evaluated using its trailing performance signals 
(impressions, clicks, position, freshness, engagement) over a defined window.

## Output
A ranked queue of pages, each with:
- an opportunity/risk score
- a suggested action (e.g., refresh, monitor, protect)
- reason codes explaining why the page was flagged (e.g., "stale_visible_page", 
  "declining_with_demand")

## The Action Someone Could Take
A content reviewer or SEO strategist uses the ranked queue to decide which pages to manually 
review and refresh first, given limited review capacity (e.g., "review the top 50 pages this 
week").

## Cost of a Wrong Recommendation
- **False positive** (flagging a page that didn't actually need review): wastes reviewer time, 
  lowers trust in the system's recommendations over time.
- **False negative** (missing a page that was genuinely declining): a real opportunity to 
  recover traffic/visibility is missed, and the problem may worsen before it's caught.
Since review capacity is limited, precision at the top of the ranking (Precision@K) matters 
more than perfect recall across the whole dataset.

## Why Data/ML Helps (Not Just "Train a Model")
Manually reviewing all pages isn't feasible at scale, and a simple fixed rule (e.g., "flag 
anything older than 6 months") misses nuance — a page can be old but still performing well, or 
recently updated but already declining. The starter pipeline's own baseline rule only reached 
Precision@50 = 0.240, while a learned model reached 0.740 on the same data — showing that the 
*relationships between signals* (freshness, visibility, position, engagement) matter more than 
any single rule can capture. This isn't "just train a model" because the real work is in: 
defining what "worth reviewing" honestly means, avoiding leakage (e.g., never using the 
product's own decision flags as a feature), and validating that the ranking is genuinely useful 
for a reviewer with limited capacity — not just statistically accurate.

## Cautious Language Note
This work identifies *pages worth reviewing first*, based on observed historical signals. It 
does not predict that a refresh will cause recovery, and it makes no claims about how Google's 
ranking algorithm works. All findings will be described as observed, directional, and 
decision-support only.

## Lane Confirmation
This is a provisional lane choice and may be confirmed or changed by the end of Week 4, per 
program guidelines.
