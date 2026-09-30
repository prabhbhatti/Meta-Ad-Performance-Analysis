# 📊 Meta Ad Performance Analysis — Summary Report

**Name:** Bhatti Prabhpreet Singh
**Tools:** Power BI (data modeling & dashboards), DAX (KPIs & field parameters)
**Dataset:** ad_events, ads, campaigns, users. Ad event records across Facebook & Instagram.

---

## 1. Executive Summary

This project looks at how ads performed on Facebook compared to Instagram, so we can see which platform gives better reach, engagement, and sales. I built two dashboards in Power BI, one for each platform, and both use a measure selector that lets you view any chart by six different metrics: Impressions, Engagements, Clicks, Shares, Comments, and Purchases.

The main takeaway is simple. Facebook is the better performer. It reaches almost twice as many people as Instagram and it also turns those people into buyers at a slightly higher rate. So it wins on both size and quality, which is not always what people expect.

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

1. Which platform performs better overall, Facebook or Instagram?
2. How do the two platforms compare on reach, engagement, and sales?
3. Which ad types (Carousel, Image, Stories, Video) work best on each platform?
4. How well does each platform turn views into actual purchases?
5. Which age groups and genders should we spend the budget on?

---

## 3. Methodology

I built a star schema in Power BI that connects the ad_events table to the ads, campaigns, and users tables, plus a calendar table for date based analysis. I wrote DAX measures for all six main metrics and for the rate calculations like CTR, Engagement Rate, Conversion Rate, and Purchase Rate.

I also created a field parameter so every chart can be switched to show any of the six metrics without building a new visual each time. Finally, I made two matching dashboards, one for Facebook and one for Instagram, so they are easy to compare side by side.

---

## 4. Key Findings & Insights

### 4.1 Platform Comparison — Overall

| Metric | Facebook | Instagram | Winner |
|--------|----------|-----------|--------|
| Impressions | 216.0K | 123.8K | Facebook |
| Engagements | 29.3K | 16.8K | Facebook |
| Engagement Rate | 14% | 14% | Tie |
| Click-Through Rate | 11.76% | 11.86% | Instagram (just barely) |
| Conversion Rate | 5.21% | 4.82% | Facebook |
| Purchases | 1.3K | 708 | Facebook |

**What this means:** Facebook is clearly ahead. It got about 74% more views than Instagram and made nearly double the purchases. The two platforms are basically tied on the in between steps, since both have a 14% engagement rate and almost the same click through rate. So people react the same way once they see an ad. The difference is that Facebook simply shows ads to more people and is a bit better at turning them into buyers. Instagram only wins on click through rate, and even then by a tiny amount.

### 4.2 Facebook — Performance by Ad Type

| Ad Type | Impressions | Clicks | CTR | ER | Conv. Rate | Purchase Rate |
|---------|-------------|--------|------|-----|-----------|---------------|
| **Stories** | 19.1K | 2.3K | 11.77% | 14% | **5.91%** | **0.70%** |
| **Video** | 12.3K | 1.4K | 11.56% | 13% | 5.12% | 0.59% |
| Carousel | 12.8K | 1.6K | 12.33% | 14% | 4.70% | 0.58% |
| Image | 13.7K | 1.6K | 11.88% | 14% | **3.74%** | **0.44%** |

**What this means:** Stories is the best format on Facebook by a clear margin. It gets the most views, the most clicks, and the highest conversion rate. That is rare, because usually a format is good at one thing but not both. Image ads are the weak spot. They get plenty of views but the fewest sales, so the money spent on them is not working very hard. One thing to watch is Carousel, which gets the most clicks but not many sales, meaning people click but do not buy.

### 4.3 Instagram — Performance by Ad Type

| Ad Type | Impressions | Clicks | CTR | ER | Conv. Rate | Purchase Rate |
|---------|-------------|--------|------|-----|-----------|---------------|
| **Carousel** | 10.5K | 1.2K | 11.59% | 13% | **5.35%** | 0.62% |
| **Stories** | 10.1K | 1.2K | 12.05% | 14% | 5.28% | **0.64%** |
| Image | 10.0K | 1.3K | 12.49% | 14% | 4.23% | 0.53% |
| Video | 2.7K | 0.3K | **12.63%** | 14% | 4.34% | 0.55% |

**What this means:** On Instagram the winner is different. Carousel brings the most sales, with Stories close behind. The most interesting point is Video. It barely gets shown (only 2.7K views), but it has the highest click through rate on either platform. That tells me Instagram Video is being ignored even though it clearly gets people to click, so it deserves more budget. Just like on Facebook, Image is the weakest format for sales.

**Quick tip across both platforms:** Stories does well on both, so it is a safe bet everywhere. Image is the worst for sales on both, so it needs new creative or less spending.

### 4.4 Engagement Breakdown (Clicks vs Shares vs Comments)

| Engagement Type | Facebook | Instagram | Facebook is higher by |
|-----------------|----------|-----------|-----------------------|
| Clicks | 25.4K | 14.7K | 73% |
| Comments | 2.6K | 1.5K | 73% |
| Shares | 1.3K | 682 | 91% |

**What this means:** Facebook beats Instagram on every type of engagement. The biggest gap is in shares, where Facebook is 91% higher. That means Facebook content gets passed around more. Clicks and comments are both about 73% higher, which matches the gap in views, so those are just following the reach. Shares are the standout, which shows Facebook users are more likely to spread content to others.

### 4.5 Conversion Funnel by Platform

| Stage | Facebook | Instagram |
|-------|----------|-----------|
| Impressions | 216.0K | 123.8K |
| Clicks | 25.4K | 14.7K |
| Purchases | 1.3K | 708 |
| View to Click (CTR) | 11.76% | 11.86% |
| Click to Purchase (Conv. Rate) | 5.21% | 4.82% |
| View to Purchase (Purchase Rate) | 0.61% | 0.57% |

**What this means:** On both platforms, most people drop off right after seeing the ad. Only about 12% actually click, so that first step is where we lose the most people. After the click, Facebook does a better job of getting the sale (5.21% vs 4.82%). So the real reason Facebook ends up with more purchases is that it is better at closing the deal once someone clicks.

### 4.6 Audience Insights — Gender & Age

**Gender split (stays about the same across all metrics):**

| Segment | Facebook | Instagram |
|---------|----------|-----------|
| Female | about 43% | about 35 to 37% |
| Untargeted (All) | about 35% | about 36 to 38% |
| Male | about 21% | about 26 to 28% |

**Age:** On both platforms the best results come from people in their early to mid twenties, and it drops off after age 30. So the audience is young. Facebook peaks a little later (mid twenties) and Instagram a little earlier (early twenties).

**What this means:** Facebook's audience is more female, and most of its purchases come from women. Instagram is more balanced between men and women, with a bigger male share. So for Facebook it makes sense to lead with content aimed at women, while Instagram can go broader. Either way, both platforms should focus the budget on the 18 to 30 age group, since that is where almost all the activity happens.

---

## 5. Recommendations

1. **Put more budget on Facebook.** It reaches more people and sells better, so it should get the bigger share of spend.
2. **Lean into Stories.** It is a top performer on both platforms and the single best format on Facebook, so shift more spend toward it.
3. **Fix or drop Image ads.** They are the worst for sales on both platforms. Either give them fresh creative or move that money to Stories and Carousel.
4. **Give Instagram Video a real chance.** It gets the best click rate anywhere but is barely being used, so it is worth testing with more budget.
5. **Work on the first step of the funnel.** Only about 12% of people click after seeing an ad, so better hooks and targeting here would lift everything else.
6. **Match the audience to the platform.** Lead with female focused content on Facebook, keep it balanced on Instagram, and focus on the 18 to 30 age group on both.

---

## 6. Conclusion

Overall, the campaigns brought in 216.0K views on Facebook and 123.8K on Instagram, leading to 1.3K and 708 purchases. Facebook came out ahead on almost everything: more reach, more engagement, more sales, and a better conversion rate. Instagram's only wins were a slightly better click rate and a Video format that performs well but is hardly being used.

The clearest ways to grow are to spend more on Facebook and on Stories, fix the weak Image ads, test Instagram Video properly, and improve the first step of the funnel where most people drop off. The dashboards with the measure selector make it easy to keep an eye on all six metrics in one place.