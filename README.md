# 📊 Meta Ad Performance Analysis (Facebook vs Instagram)

Hi, and welcome to my project! 👋

This is an end to end data analytics project where I looked at how ad campaigns performed on **Facebook** compared to **Instagram**. The goal was to figure out which platform gives better results and where the marketing budget should actually go. I built the whole thing in **Power BI** using **DAX**, and I put together two interactive dashboards that make it easy to compare both platforms side by side.

![Facebook Dashboard](visuals/01_Facebook/Overall%20Dashboard/Facebook%20Dashboard.png)

---

## 📌 Project Overview

The idea behind this project was to take raw ad event data and turn it into something a marketing team could actually use. I wanted to see which platform reaches more people, which one turns those people into buyers, and which ad types are worth spending more on. Everything is broken down by platform so the comparison is clear and easy to follow.

---

## 🎯 What This Project Answers

I set out to answer a few simple but important business questions:

1. Which platform performs better overall, Facebook or Instagram?
2. How do the two compare on reach, engagement, and actual sales?
3. Which ad types (Carousel, Image, Stories, Video) work best on each platform?
4. How good is each platform at turning views into purchases?
5. Which age groups and genders should the budget focus on?

---

## 🧠 The Short Version (Key Findings)

If you only read one thing, read this:

**Facebook is the stronger platform.** It reached almost twice as many people as Instagram and made nearly double the sales. Both platforms get people to react in a similar way once they see an ad, but Facebook simply reaches more people and is a bit better at closing the sale.

A few other things I found:

* 🥇 **Stories** was the best ad format on both platforms, so it is a safe bet.
* 📉 **Image ads** were the weakest for sales on both platforms and need fresh ideas.
* 🎥 **Instagram Video** barely gets shown but has the best click rate anywhere, so it is being wasted.
* 👥 The audience skews young on both platforms, mostly people between **18 and 30**.

You can find the full write up in the reports folder.

---

## 🛠️ Tools & Technologies

* **Power BI** for building the data model and dashboards
* **DAX** for all the KPIs and calculations (CTR, Engagement Rate, Conversion Rate, Purchase Rate)
* **Data modeling** using a star schema to connect the tables
* **Field parameters** so every chart can switch between six metrics without extra visuals
* **Dataset** made up of four tables: ad_events, ads, campaigns, and users

---

## 📁 Repository Structure

```
├── data/
│   ├── ad_events.csv                  # Every ad interaction record
│   ├── ads.csv                        # Ad level details
│   ├── campaigns.csv                  # Campaign level details
│   └── users.csv                      # User info for audience analysis
│
├── docs/
│   └── README.md                      # Extra project documentation
│
├── queries/
│   └── Dax Queries.md                 # All DAX measures with explanations
│
├── reports/
│   ├── Metadata Summary Report.md     # Full analysis, insights & recommendations
│   └── README.md
│
├── visuals/
│   ├── 01_Facebook/                   # Facebook charts + dashboard
│   ├── 02_Instagram/                  # Instagram charts + dashboard
│   └── 03_Data Model View/            # The star schema data model
│
└── README.md                          # You are here
```
---

## 📊 Sample Visuals

| Analysis | Preview |
|----------|---------|
| Facebook Dashboard | ![Facebook Dashboard](visuals/01_Facebook/Overall%20Dashboard/Facebook%20Dashboard.png) |
| Instagram Dashboard | ![Instagram Dashboard](visuals/02_Instagram/Overall%20Dashboard/Instagram%20Dashboard.png) |
| Data Model View | ![Data Model View](visuals/03_Data%20Model%20View/Data%20Model%20View.png) |

---

## 🚀 How to Explore This Project

1. Start here with this README to get the big picture.
2. Open the **reports** folder to read the full analysis and recommendations.
3. Check the **visuals** folder to see the dashboards and charts for each metric.
4. Look at the **queries** folder if you want to see the DAX behind the numbers.

---

## 🧠 What I Took Away From This

This project gave me a chance to work through a real business problem from start to finish, from raw data all the way to a clear set of recommendations someone could actually act on. It pushed my skills in data modeling, DAX, and turning numbers into a story that makes sense.

---

## 📬 Contact

Thanks for taking the time to look through my project. Feel free to reach out if you have any questions!

**Bhatti Prabhpreet Singh**
* LinkedIn: https://www.linkedin.com/in/bhatti-prabhpreet-singh/
* Email: prabhbhatti.psb@gmail.com