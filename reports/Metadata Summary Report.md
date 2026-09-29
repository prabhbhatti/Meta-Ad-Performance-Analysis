# 📊 Meta Ad Performance Analysis — Summary Report

**Name:** Bhatti Prabhpreet Singh
**Tools:** Power BI (data modeling & dashboard), DAX (KPIs & measures)
**Dataset:** `ad_events`, `ads`, `campaigns`, `users` — [XX,XXX]+ ad event records across multiple campaigns

---

## 1. Executive Summary

This project analyzes Meta ad campaign performance to understand how effectively ads convert impressions into engagement and purchases. Using Power BI to model the data and DAX to calculate key metrics, the analysis surfaces clear opportunities to improve return on ad spend through budget reallocation, audience targeting, and creative optimization.

**Headline results:**

| KPI | Value |
|-----|-------|
| Total Impressions | [X,XXX,XXX] |
| Total Clicks | [XXX,XXX] |
| Total Engagements | [XXX,XXX] |
| Total Purchases | [XX,XXX] |
| Click-Through Rate (CTR) | [X.X%] |
| Conversion Rate | [X.X%] |
| Total Budget | [$XXX,XXX] |

---

## 2. Objectives

The analysis set out to answer five core business questions:

1. How are campaigns performing overall (reach, engagement, conversions)?
2. Which campaigns and ads deliver the best return on budget?
3. How efficiently do impressions convert into clicks and purchases?
4. What audience segments engage and convert the most?
5. Where are the biggest opportunities to improve ad spend efficiency?

---

## 3. Methodology

- **Data modeling:** Built a star schema in Power BI linking `ad_events` (fact) to `ads`, `campaigns`, and `users` dimension tables, with a dedicated calendar table for time intelligence.
- **KPI calculation:** Wrote DAX measures for base event counts (impressions, clicks, engagements, purchases) and derived rate metrics (CTR, engagement rate, conversion rate, purchase rate).
- **Visualization:** Built an interactive dashboard with a dynamic field parameter allowing users to switch the visualized metric on the fly.

---

## 4. Key Findings & Insights

### 4.1 Performance by Campaign

| Campaign | Impressions | Conversions | Conv. Rate |
|----------|-------------|-------------|------------|
| **[Top Campaign]** | [XXX,XXX] | [X,XXX] | [X.X%] |
| [Campaign 2] | [XXX,XXX] | [X,XXX] | [X.X%] |
| [Campaign 3] | [XXX,XXX] | [X,XXX] | [X.X%] |
| **[Lowest Campaign]** | [XXX,XXX] | [XXX] | [X.X%] |

![Performance by Campaign](../visuals/02_Campaign%20Performance/Campaign%20Performance.png)

> **Insight:** [Campaign X] drove the highest conversion rate at [X.X%], significantly outperforming the campaign average. Meanwhile, [Campaign Y] generated high impressions but low conversions, indicating strong reach but weak conversion efficiency — a clear candidate for creative or targeting review.

### 4.2 Engagement Funnel

| Stage | Volume | Rate |
|-------|--------|------|
| Impressions | [X,XXX,XXX] | — |
| Clicks | [XXX,XXX] | [CTR X.X%] |
| Engagements | [XXX,XXX] | [Eng. Rate X.X%] |
| Purchases | [XX,XXX] | [Conv. Rate X.X%] |

![Engagement Funnel](../visuals/03_Funnel/Engagement%20Funnel.png)

> **Insight:** The funnel reveals the biggest drop-off occurs between [stage] and [stage], where only [X.X%] of [users] progress. This suggests [interpretation — e.g. the landing experience or offer isn't converting clicks into purchases], representing the clearest opportunity to lift overall ROI.

### 4.3 Performance by Day / Time

| Period | Engagements |
|--------|-------------|
| **[Best day/time]** | [XX,XXX] |
| [Period 2] | [XX,XXX] |
| [Period 3] | [XX,XXX] |
| **[Worst day/time]** | [X,XXX] |

![Engagement Over Time](../visuals/04_Trends/Engagement%20Over%20Time.png)

> **Insight:** Engagement peaks on [day/time], while [period] shows the weakest activity. Aligning ad scheduling and budget pacing toward these high-engagement windows could improve efficiency without increasing total spend.

### 4.4 Budget Efficiency

| Metric | Value |
|--------|-------|
| Total Budget | [$XXX,XXX] |
| Avg. Budget per Campaign | [$XX,XXX] |
| Cost per Conversion (best campaign) | [$XX] |
| Cost per Conversion (worst campaign) | [$XXX] |

![Budget by Campaign](../visuals/05_Budget/Budget%20by%20Campaign.png)

> **Insight:** Budget is [evenly / unevenly] distributed across campaigns. [Campaign X] delivers conversions at [$XX] each — far more efficient than [Campaign Y] at [$XXX] each. Reallocating spend from underperforming to high-efficiency campaigns could increase total conversions at the same budget.

### 4.5 Audience Insights

| Segment | Conv. Rate |
|---------|------------|
| **[Top segment]** | [X.X%] |
| [Segment 2] | [X.X%] |
| [Segment 3] | [X.X%] |
| **[Lowest segment]** | [X.X%] |

![Conversion by Audience](../visuals/06_Audience/Conversion%20by%20Audience.png)

> **Insight:** [Segment] converts at [X.X%], well above other groups, while [segment] shows strong reach but low conversion. This points to an opportunity to shift targeting and budget toward the highest-converting audiences.

---

## 5. Recommendations

1. **Reallocate budget toward high-efficiency campaigns.** Shift spend from [low-ROI campaign] to [high-ROI campaign], which converts at a fraction of the cost per acquisition.
2. **Fix the biggest funnel drop-off.** With the largest fall-off between [stage] and [stage], review [landing pages / offers / creative] to convert more clicks into purchases.
3. **Optimize ad scheduling.** Concentrate delivery around [peak day/time], where engagement is strongest, and reduce spend during consistently low-performing windows.
4. **Double down on top audiences.** Increase targeting toward [top-converting segment] and reduce spend on low-converting segments.
5. **Refresh underperforming creative.** [Campaign/ad] generates impressions but few conversions — test new creative or messaging before continuing to fund it.

---

## 6. Conclusion

The Meta ad campaigns generated **[X,XXX,XXX] impressions** and **[XX,XXX] conversions** on a total budget of **[$XXX,XXX]**, achieving a **[X.X%] click-through rate** and **[X.X%] conversion rate**. Performance is driven by [top campaign/audience], with the clearest growth levers being budget reallocation toward efficient campaigns, fixing the [stage] funnel drop-off, and aligning delivery to peak engagement windows.

These optimizations offer a path to increasing conversions and improving return on ad spend without raising the total budget.