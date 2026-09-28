# 📄 Documentation — Meta Ad Performance Analysis

This folder contains reference materials for the Meta Ad Performance Analysis
Power BI project: the data dictionary, data model overview, KPI definitions,
and project notes.

---

## 📚 Table of Contents
1. [Project Overview](#-project-overview)
2. [Data Model](#-data-model)
3. [Data Dictionary](#-data-dictionary)
4. [KPI & Measure Definitions](#-kpi--measure-definitions)
5. [Report Pages](#-report-pages)
6. [Assumptions & Scope](#-assumptions--scope)

---

## 🎯 Project Overview

An interactive Power BI report analyzing **Meta (Facebook & Instagram) advertising
campaign performance**. The dashboard tracks the full marketing funnel —
**impressions → clicks → engagement → purchases** — and breaks performance down
by audience demographics and campaign budget.

**Tools:** Power BI Desktop · DAX · Star-schema data model

---

## 🗂️ Data Model

The report uses a **star schema** with a central events fact table surrounded by
descriptive dimension tables.

| Table        | Type       | Grain / Description                                   |
|--------------|------------|-------------------------------------------------------|
| `ad_events`  | Fact       | One row per ad event (impression, click, engagement, purchase) |
| `ads`        | Dimension  | One row per ad (creative, targeting attributes)       |
| `campaigns`  | Dimension  | One row per campaign (budget, campaign metadata)      |
| `users`      | Dimension  | One row per user (demographic attributes)             |

**Relationships:** `campaigns` → `ads` → `ad_events` ← `users`
(one-to-many, single-direction filtering from dimensions to fact).

---

## 📖 Data Dictionary

### `ad_events` (Fact)
| Column        | Type     | Description                                        |
|---------------|----------|----------------------------------------------------|
| `event_id`    | Text/ID  | Unique identifier for each event                   |
| `ad_id`       | ID (FK)  | Links to `ads[ad_id]`                              |
| `user_id`     | ID (FK)  | Links to `users[user_id]`                         |
| `event_type`  | Text     | Type of event: Impression, Click, Share, Comment, Purchase |
| `event_date`  | Date     | Date the event occurred                            |

### `ads` (Dimension)
| Column          | Type   | Description                                          |
|-----------------|--------|------------------------------------------------------|
| `ad_id`         | ID (PK)| Unique ad identifier                                 |
| `campaign_id`   | ID (FK)| Links to `campaigns[campaign_id]`                   |
| `target_gender` | Text   | Gender the ad was **targeted** at: Male, Female, All |

> ⚠️ **Note:** `target_gender` describes *targeting intent* (how the ad was aimed),
> **not** the actual gender of the user who saw it. See the `users` table for that.

### `campaigns` (Dimension)
| Column         | Type    | Description                              |
|----------------|---------|------------------------------------------|
| `campaign_id`  | ID (PK) | Unique campaign identifier               |
| `total_budget` | Numeric | Lump-sum budget allocated to the campaign|

### `users` (Dimension)
| Column        | Type   | Description                                  |
|---------------|--------|----------------------------------------------|
| `user_id`     | ID (PK)| Unique user identifier                       |
| `user_gender` | Text   | The **actual** gender of the user            |

---

## 🧮 KPI & Measure Definitions

### Volume Metrics
| Measure       | Definition                                           |
|---------------|------------------------------------------------------|
| Impressions   | Count of events where `event_type = "Impression"`    |
| Clicks        | Count of events where `event_type = "Click"`         |
| Shares        | Count of events where `event_type = "Share"`         |
| Comments      | Count of events where `event_type = "Comment"`       |
| Purchases     | Count of events where `event_type = "Purchase"`      |
| Engagements   | Sum of Clicks + Shares + Comments                    |

### Rate Metrics
| Measure          | Formula                          | Meaning                              |
|------------------|----------------------------------|--------------------------------------|
| CTR              | Clicks ÷ Impressions             | Click-through rate                   |
| Engagement Rate  | Engagements ÷ Impressions        | Share of impressions that engaged    |
| Conversion Rate  | Purchases ÷ Clicks               | Clicks that led to a purchase        |
| Purchase Rate    | Purchases ÷ Impressions          | Impressions that led to a purchase   |

### Budget Metrics
| Measure                | Definition                              |
|------------------------|-----------------------------------------|
| Total Budget           | Sum of `campaigns[total_budget]`        |
| Avg. Budget / Campaign | Total Budget ÷ distinct count of campaigns |

---

## 📊 Report Pages

| Page                | Key Visuals                                                    |
|---------------------|----------------------------------------------------------------|
| Overview            | Funnel KPIs, headline cards, trend over time                   |
| Audience Demographics | Impressions by Gender (donut, uses `ads[target_gender]`), age/region breakdowns |
| Campaign / Budget   | Budget by campaign, spend vs. performance                      |

**Interactive features:** field parameters (dynamic metric/axis switching) and
report-page tooltips for richer hover context.

---

## ⚠️ Assumptions & Scope

- **Gender donut uses `target_gender`** (targeting intent). Slices: Female 44%,
  All 35%, Male 21%.

---