# 📊 Meta Ad Performance Analysis — Summary Report

**Name:** Bhatti Prabhpreet Singh
**Tools:** Power BI (data modeling & dashboards), DAX (KPIs & field parameters)
**Dataset:** `ad_events`, `ads`, `campaigns`, `users` — ad event records across Facebook & Instagram

---

## 1. Executive Summary

This project analyzes and compares ad performance across **Facebook and Instagram** to understand which platform delivers stronger reach, engagement, and conversions. Two dedicated dashboards were built in Power BI, each powered by a **dynamic measure selector** that lets users view every chart through six different metrics — Impressions, Engagements, Clicks, Shares, Comments, and Purchases.

The headline story is clear: **Facebook is the stronger performer on both volume and efficiency.** It delivers roughly 1.7x the impressions of Instagram *and* converts them at a higher rate (5.21% vs 4.82%). This challenges the common assumption that one platform is purely for awareness and the other for conversion — here, Facebook leads across the funnel.

**Headline results:**

| KPI | Facebook | Instagram |
|-----|----------|-----------|
| Impressions | 216.0K | 123.8K |
| Engagements | 29.3K | 16.8K |
| Clicks | 25.4K | 14.7K |
| Shares | 1.3K | 682 |
| Comments | 2.6K | 1.5K |
| Purchases | 1.3K | 708 |
| Click-Through Rate | 11.76% | 11.86% |
| Engagement Rate | 14% | 14% |
| Conversion Rate | 5.21% | 4.82% |
| Purchase Rate | 0.61% | 0.57% |

---

## 2. Objectives

1. Which platform — Facebook or Instagram — performs better overall?
2. How do the two platforms compare across each metric (reach vs engagement vs conversions)?
3. Which ad types (Carousel, Image, Stories, Video) drive the best results on each platform?
4. How efficiently does each platform convert impressions into purchases?
5. Which audiences (gender & age) should the budget target?

---

## 3. Methodology

- **Data modeling:** Built a star schema in Power BI linking `ad_events` (fact) to `ads`, `campaigns`, and `users` dimension tables, with a calendar table for time intelligence.
- **KPI calculation:** Wrote DAX measures for all six base metrics plus derived rates (CTR, Engagement Rate, Conversion Rate, Purchase Rate).
- **Dynamic measure:** Created a **field parameter** so every chart (Gender, Age, Country, Weekly & Hourly trends) can be re-pivoted to any of the six metrics without rebuilding the visual — enabling flexible, self-serve exploration.
- **Platform split:** Built two parallel dashboards (Facebook & Instagram) with identical layouts for clean side-by-side comparison.

---

## 4. Key Findings & Insights

### 4.1 Platform Comparison — Overall

| Metric | Facebook | Instagram | Winner |
|--------|----------|-----------|--------|
| Impressions | 216.0K | 123.8K | Facebook |
| Engagements | 29.3K | 16.8K | Facebook |
| Engagement Rate | 14% | 14% | Tie |
| Click-Through Rate | 11.76% | 11.86% | Instagram (marginal) |
| Conversion Rate | 5.21% | 4.82% | Facebook |
| Purchases | 1.3K | 708 | Facebook |

> **Insight:** Facebook dominates on raw volume, generating **~74% more impressions** and nearly **double the purchases** of Instagram. Crucially, it also converts *more efficiently* — a 5.21% conversion rate vs Instagram's 4.82%. The two platforms are near-identical on the middle-funnel rates (CTR ~11.8%, Engagement Rate 14% on both), meaning users interact at the same rate once reached — but Facebook simply reaches more people and turns them into buyers more effectively. Instagram edges CTR by a hair (11.86% vs 11.76%), its only win.

### 4.2 Facebook — Performance by Ad Type

| Ad Type | Impressions | Clicks | CTR | ER | Conv. Rate | Purchase Rate |
|---------|-------------|--------|------|-----|-----------|---------------|
| **Stories** | 19.1K | 2.3K | 11.77% | 14% | **5.91%** | **0.70%** |
| **Video** | 12.3K | 1.4K | 11.56% | 13% | 5.12% | 0.59% |
| Carousel | 12.8K | 1.6K | 12.33% | 14% | 4.70% | 0.58% |
| Image | 13.7K | 1.6K | 11.88% | 14% | **3.74%** | **0.44%** |

> **Insight:** **Stories is Facebook's standout format** — it earns the most impressions (19.1K), the most clicks (2.3K), *and* the highest conversion rate (5.91%) and purchase rate (0.70%). It's the rare format that wins on both volume and efficiency. **Image is the clear weak link**: despite the second-highest impressions (13.7K), it converts at just 3.74% — the lowest of any format — and has the lowest purchase rate (0.44%). Interestingly, Carousel earns the best CTR (12.33%) but a below-average conversion rate, showing it attracts clicks that don't translate into sales.

### 4.3 Instagram — Performance by Ad Type

| Ad Type | Impressions | Clicks | CTR | ER | Conv. Rate | Purchase Rate |
|---------|-------------|--------|------|-----|-----------|---------------|
| **Carousel** | 10.5K | 1.2K | 11.59% | 13% | **5.35%** | 0.62% |
| **Stories** | 10.1K | 1.2K | 12.05% | 14% | 5.28% | **0.64%** |
| Image | 10.0K | 1.3K | 12.49% | 14% | 4.23% | 0.53% |
| Video | 2.7K | 0.3K | **12.63%** | 14% | 4.34% | 0.55% |

> **Insight:** On Instagram the picture flips — **Carousel is the top converter (5.35%)**, narrowly ahead of Stories (5.28%). **Video is dramatically underused**: at just 2.7K impressions it has by far the smallest reach, yet it posts the **highest CTR of any format on either platform (12.63%)**. That's a strong signal that Instagram Video is being under-invested — it earns clicks efficiently but simply isn't being served enough. Image, as on Facebook, is a laggard for conversions (4.23%).

> **Cross-platform takeaway:** Stories converts well on *both* platforms (5.91% FB / 5.28% IG), making it the safest high-performing format across the board. Image consistently underperforms on both and is the prime candidate for creative overhaul or reduced spend.

### 4.4 Engagement Breakdown (Clicks vs Shares vs Comments)

| Engagement Type | Facebook | Instagram | FB Advantage |
|-----------------|----------|-----------|--------------|
| Clicks | 25.4K | 14.7K | +73% |
| Comments | 2.6K | 1.5K | +73% |
| Shares | 1.3K | 682 | +91% |

> **Insight:** Facebook leads every engagement type, but the gap is widest on **Shares (+91%)** — content on Facebook gets amplified far more relative to its reach than on Instagram. Comments and Clicks both scale at ~+73%, closely mirroring the impression gap, which means those interactions are proportional to reach. Shares are the exception, pointing to Facebook's stronger viral/sharing behaviour among its audience.

### 4.5 Conversion Funnel by Platform

| Stage | Facebook | Instagram |
|-------|----------|-----------|
| Impressions | 216.0K | 123.8K |
| Clicks | 25.4K | 14.7K |
| Purchases | 1.3K | 708 |
| Impression → Click (CTR) | 11.76% | 11.86% |
| Click → Purchase (Conv. Rate) | 5.21% | 4.82% |
| Impression → Purchase (Purchase Rate) | 0.61% | 0.57% |

> **Insight:** Both platforms lose the vast majority of users at the **impression → click** stage (only ~11.8% click through on each), so this is the universal bottleneck. The platforms *separate* at the **click → purchase** step, where Facebook retains 5.21% vs Instagram's 4.82%. In other words, both attract clicks at the same rate, but Facebook is better at turning those clicks into buyers — the single biggest reason its end-to-end purchase rate (0.61%) beats Instagram's (0.57%).

### 4.6 Audience Insights — Gender & Age

**Gender split (consistent across all six metrics):**

| Segment | Facebook | Instagram |
|---------|----------|-----------|
| Female | ~43% | ~35–37% |
| All / Untargeted | ~35% | ~36–38% |
| Male | ~21% | ~26–28% |

**Age:** On both platforms, performance peaks in the **early-to-mid 20s** and declines steadily after age 30 — a distinctly young-skewed audience. Facebook's peak sits slightly later (~mid-20s) while Instagram skews a touch younger (~early 20s).

> **Insight:** Facebook's audience is **notably more female (43%)** and its purchases skew female-heavy (572 female vs 279 male). Instagram is **more gender-balanced**, with a larger male share (26–28%) across every metric. This is a real targeting lever: female-focused creative will resonate more on Facebook, while Instagram supports a broader, more balanced gender strategy. Both platforms should concentrate spend on the **18–30 age band**, which drives the clear majority of every metric.

---

## 5. Recommendations

1. **Prioritize Facebook for scale and conversion.** It out-delivers Instagram on both reach (+74% impressions) and efficiency (5.21% vs 4.82% conversion) — it should carry the larger share of budget.
2. **Double down on Stories.** It's a top-3 converter on both platforms and Facebook's single best format (5.91% conversion). Shift budget toward Stories placements.
3. **Fix or cut Image ads.** Image is the weakest converter on both platforms (3.74% FB / 4.23% IG). Refresh the creative/CTA or reallocate that spend to Stories and Carousel.
4. **Scale up Instagram Video.** It has the highest CTR anywhere (12.63%) but the lowest reach (2.7K) — it's being starved. Increase Video investment on Instagram to capture that efficient click behaviour.
5. **Attack the top-funnel bottleneck.** Only ~11.8% of impressions convert to clicks on both platforms. Stronger hooks, creative, and targeting at this stage would lift the entire funnel.
6. **Target by platform demographics.** Lead with female-focused creative and the 18–30 age band on Facebook; use a more gender-balanced approach on Instagram where the male share is meaningfully higher.

---

## 6. Conclusion

Across the two platforms, the campaigns generated **216.0K Facebook impressions** and **123.8K Instagram impressions**, driving **1.3K and 708 purchases** respectively. Facebook is the stronger performer on nearly every dimension — more reach, more engagement, more purchases, and a higher conversion rate — while Instagram's only edge is a marginally better click-through rate and a Video format that punches above its weight.

The clearest growth levers are: shifting budget toward Facebook and toward Stories placements, fixing underperforming Image creative, scaling Instagram's efficient-but-underused Video, and tightening top-of-funnel targeting around the young, Facebook-female-leaning audience that drives the results. The dynamic measure dashboards make it easy to monitor all six metrics through a single, flexible view.