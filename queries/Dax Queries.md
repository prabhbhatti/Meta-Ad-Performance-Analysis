# Meta Ad Performance Dashboard — DAX Documentation

**Report:** Meta Ad Performance Dashboard  
**Last documented:** 2026-09-29  

---

## Data Model Overview

| Table | Type | Key Columns |
|-------|------|-------------|
| `ad_events` | Fact | ad_id, event_id, event_type, timestamp, user_id, Event Date, Event Hour, day_of_week, time_of_day |
| `ads` | Dimension | ad_id, ad_type, campaign_id, target_age_group, target_gender, target_interests |
| `campaigns` | Dimension | campaign_id, name, start_date, end_date, duration_days, total_budget |
| `users` | Dimension | (user attributes) |
| `Calender Table` | Date | Date, Day, day_num, month, Week Day, Week Number |
| `Select Dynamic Measure` | Field Parameter (Import) | Select Dynamic Measure, ...Fields, ...Order, Dynamic Title |

---

## 1. Base Event Measures
*Home table: `ad_events` — Format: Decimal number*

```dax
Impressions = COUNTROWS(FILTER(ad_events, ad_events[event_type] = "Impression"))
Clicks = COUNTROWS(FILTER(ad_events, ad_events[event_type] = "Click"))
Shares = COUNTROWS(FILTER(ad_events, ad_events[event_type] = "Share"))
Comments = COUNTROWS(FILTER(ad_events, ad_events[event_type] = "Comment"))
Purchases = COUNTROWS(FILTER(ad_events, ad_events[event_type] = "Purchase"))
Engagements = [Shares] + [Clicks] + [Comments]


## 2. Rate Measures
*Home table: `ad_events` — Format: Percentage*
Click Through Rate = DIVIDE([Clicks], [Impressions], 0)
Engagement Rate = DIVIDE([Engagements], [Impressions], 0) — Format: Decimal number*
Conversion Rate = DIVIDE([Purchases], [Clicks], 0)
Purchase Rate = DIVIDE([Purchases], [Impressions], 0)


## 3. Budget Measures
*Home table: `ad_events` — Format: Currency (1 decimal place)*
Total Budget = SUM(campaigns[total_budget])
Avg. Budget per Campaign = AVERAGE(campaigns[total_budget])


## 4. Dynamic Measure Selection(Field Parameter)
Created via Modeling → New parameter → Fields. Storage mode: Import
Select Dynamic Measure = {
    ("Impressions", NAMEOF('ad_events'[Impressions]), 0),
    ("Engagements", NAMEOF('ad_events'[Engagements]), 1),
    ("Clicks",      NAMEOF('ad_events'[Clicks]),      2),
    ("Shares",      NAMEOF('ad_events'[Shares]),      3),
    ("Comments",    NAMEOF('ad_events'[Comments]),    4),
    ("Purchases",   NAMEOF('ad_events'[Purchases]),   5)
}

Dynamic Title
Calculated column in Select Dynamic Measure table — Data type: Text
Dynamic Title = 
IF('Select Dynamic Measure'[Select Dynamic Measure Order] = 0, "Impressions",
IF('Select Dynamic Measure'[Select Dynamic Measure Order] = 1, "Engagements",
IF('Select Dynamic Measure'[Select Dynamic Measure Order] = 2, "Clicks",
IF('Select Dynamic Measure'[Select Dynamic Measure Order] = 3, "Shares",
IF('Select Dynamic Measure'[Select Dynamic Measure Order] = 4, "Comments",
IF('Select Dynamic Measure'[Select Dynamic Measure Order] = 5, "Purchases",
"Other"))))))

## 5. Calendar Table
Calender Table = CALENDAR(MIN(ad_events[Event Date]), MAX(ad_events[Event Date]))
Date = -- base column from CALENDAR()
Day = FORMAT('Calender Table'[Date], "ddd") Data type: Text — e.g. Mon, Tue, Wed
day_num = FORMAT('Calender Table'[Date], "d") Data type: Text — day of month (1, 2, 3…)
month = FORMAT('Calender Table'[Date], "mmm") Data type: Text — e.g. Jan, Feb, Mar
Week Day = WEEKDAY('Calender Table'[Date], 2) Data type: Whole number — 1 = Monday … 7 = Sunday
Week Number = WEEKNUM('Calender Table'[Date], 2) Data type: Whole number — week starts Monday


