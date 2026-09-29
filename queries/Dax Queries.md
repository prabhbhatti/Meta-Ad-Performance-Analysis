You're absolutely right — those sections belong in your **README**, not a DAX reference file. Keep this file focused purely on the DAX. Here's the trimmed version:

```markdown
# 📊 DAX Documentation — Meta Ad Performance Dashboard

> **Tool:** Microsoft Power BI (DAX)  
> **Last Updated:** 2026-09-29

---

## 📑 Table of Contents

1. [Base Event Measures](#1--base-event-measures)
2. [Rate Measures](#2--rate-measures)
3. [Budget Measures](#3--budget-measures)
4. [Dynamic Measure Selection](#4--dynamic-measure-selection-field-parameter)
5. [Calendar Table](#5--calendar-table)

---

## 1. 🎯 Base Event Measures

> **Home Table:** `ad_events` &nbsp;•&nbsp; **Format:** Decimal Number

These measures count individual event types from the fact table.

| Measure | Description |
|---------|-------------|
| **Impressions** | Total ad impressions |
| **Clicks** | Total clicks |
| **Shares** | Total shares |
| **Comments** | Total comments |
| **Purchases** | Total purchases |
| **Engagements** | Combined Shares + Clicks + Comments |

```dax
Impressions =
COUNTROWS ( FILTER ( ad_events, ad_events[event_type] = "Impression" ) )
```

```dax
Clicks =
COUNTROWS ( FILTER ( ad_events, ad_events[event_type] = "Click" ) )
```

```dax
Shares =
COUNTROWS ( FILTER ( ad_events, ad_events[event_type] = "Share" ) )
```

```dax
Comments =
COUNTROWS ( FILTER ( ad_events, ad_events[event_type] = "Comment" ) )
```

```dax
Purchases =
COUNTROWS ( FILTER ( ad_events, ad_events[event_type] = "Purchase" ) )
```

```dax
Engagements =
[Shares] + [Clicks] + [Comments]
```

---

## 2. 📈 Rate Measures

> **Home Table:** `ad_events`

Performance ratios built on top of the base measures.

| Measure | Formula Logic | Format |
|---------|---------------|--------|
| **Click Through Rate** | Clicks ÷ Impressions | Percentage |
| **Engagement Rate** | Engagements ÷ Impressions | Decimal Number |
| **Conversion Rate** | Purchases ÷ Clicks | Percentage (2 dp) |
| **Purchase Rate** | Purchases ÷ Impressions | Percentage (2 dp) |

```dax
Click Through Rate =
DIVIDE ( [Clicks], [Impressions], 0 )
```

```dax
Engagement Rate =
DIVIDE ( [Engagements], [Impressions], 0 )
```

```dax
Conversion Rate =
DIVIDE ( [Purchases], [Clicks], 0 )
```

```dax
Purchase Rate =
DIVIDE ( [Purchases], [Impressions], 0 )
```

---

## 3. 💰 Budget Measures

> **Home Table:** `ad_events` &nbsp;•&nbsp; **Format:** Currency (1 decimal place)

| Measure | Description |
|---------|-------------|
| **Total Budget** | Sum of all campaign budgets |
| **Avg. Budget per Campaign** | Average budget across campaigns |

```dax
Total Budget =
SUM ( campaigns[total_budget] )
```

```dax
Avg. Budget per Campaign =
AVERAGE ( campaigns[total_budget] )
```

---

## 4. ⚙️ Dynamic Measure Selection (Field Parameter)

> **Created via:** Modeling → New Parameter → Fields &nbsp;•&nbsp; **Storage Mode:** Import

This field parameter lets users **switch the visualized metric** interactively via a slicer.

### 🔹 Parameter Definition

```dax
Select Dynamic Measure = {
    ( "Impressions", NAMEOF ( 'ad_events'[Impressions] ), 0 ),
    ( "Engagements", NAMEOF ( 'ad_events'[Engagements] ), 1 ),
    ( "Clicks",      NAMEOF ( 'ad_events'[Clicks] ),      2 ),
    ( "Shares",      NAMEOF ( 'ad_events'[Shares] ),      3 ),
    ( "Comments",    NAMEOF ( 'ad_events'[Comments] ),    4 ),
    ( "Purchases",   NAMEOF ( 'ad_events'[Purchases] ),   5 )
}
```

**Auto-generated columns:**

| Column | Purpose |
|--------|---------|
| `Select Dynamic Measure` | Display name (Text) |
| `Select Dynamic Measure Fields` | `NAMEOF` reference to the measure |
| `Select Dynamic Measure Order` | Sort order (0–5) |

### 🔹 Dynamic Title

> **Calculated column** in `Select Dynamic Measure` &nbsp;•&nbsp; **Data type:** Text  
> Returns a friendly title that updates with the selected measure.

```dax
Dynamic Title =
IF ( 'Select Dynamic Measure'[Select Dynamic Measure Order] = 0, "Impressions",
IF ( 'Select Dynamic Measure'[Select Dynamic Measure Order] = 1, "Engagements",
IF ( 'Select Dynamic Measure'[Select Dynamic Measure Order] = 2, "Clicks",
IF ( 'Select Dynamic Measure'[Select Dynamic Measure Order] = 3, "Shares",
IF ( 'Select Dynamic Measure'[Select Dynamic Measure Order] = 4, "Comments",
IF ( 'Select Dynamic Measure'[Select Dynamic Measure Order] = 5, "Purchases",
"Other" ) ) ) ) ) )
```

---

## 5. 📅 Calendar Table

> **Type:** Date Table (marked via *Mark as Date Table*)  
> **Relationship:** `Calender Table[Date]` → `ad_events[Event Date]`

### 🔹 Table Definition

```dax
Calender Table =
CALENDAR ( MIN ( ad_events[Event Date] ), MAX ( ad_events[Event Date] ) )
```

### 🔹 Calculated Columns

| Column | Data Type | Output Example |
|--------|-----------|----------------|
| **Date** | Date | `14 Mar 2001` |
| **Day** | Text | Mon, Tue, Wed |
| **day_num** | Text | Day of month (1, 2, 3…) |
| **month** | Text | Jan, Feb, Mar |
| **Week Day** | Whole Number | 1 = Monday … 7 = Sunday |
| **Week Number** | Whole Number | Week of year (starts Monday) |

```dax
-- Base column from CALENDAR()
Date
```

```dax
Day =
FORMAT ( 'Calender Table'[Date], "ddd" )
```

```dax
day_num =
FORMAT ( 'Calender Table'[Date], "d" )
```

```dax
month =
FORMAT ( 'Calender Table'[Date], "mmm" )
```

```dax
Week Day =
WEEKDAY ( 'Calender Table'[Date], 2 )
```

```dax
Week Number =
WEEKNUM ( 'Calender Table'[Date], 2 )
```

---

<div align="center">

**End of DAX Documentation**

</div>
```

Yes — put the **project overview, how-to-use, data model, and relationships diagram** in your `README.md`. That way the README tells the story of the whole project, and this file stays a clean, focused DAX reference. Good instinct. 👍