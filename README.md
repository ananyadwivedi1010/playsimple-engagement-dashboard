# 🎮 PlaySimple Word Games — Player Engagement & Retention Dashboard

> **Business Analyst Portfolio Project** | Power BI | CRM & Player Analytics  
> Inspired by PlaySimple Games' portfolio: *Daily Themed Crossword, WordTrip, WordTrek, WordJam, GuessUp*

---

## 📌 Project Overview

This project simulates the work of a **Business Analyst at a mobile word gaming company**, building a Power BI dashboard to track player engagement, retention, and monetization — the core KPIs PlaySimple's BA team monitors daily.

**Business Problem:**  
A mobile word game company is experiencing high early churn (players leaving within the first 3 days). Leadership needs a data-driven view of where players drop off, which games retain the best, and how to improve conversion from free to paying users.

**Solution:**  
An end-to-end Power BI dashboard covering the full player lifecycle — from install to churn to revenue — with actionable business recommendations.

---

## 🗂️ Repository Structure

```
playsimple-engagement-dashboard/
│
├── data/
│   └── player_data.csv          ← Simulated dataset (500 players)
│
├── powerbi/
│   └── DAX_Measures.txt         ← All DAX formulas used in the dashboard
│
├── docs/
│   └── Business_Recommendations.md  ← Key insights & recommendations
│
└── README.md
```

---

## 📊 Dashboard Pages & Visuals

### Page 1 — Executive Summary
| Visual | Type | Insight |
|--------|------|---------|
| Total Players, Day1/7/30 Retention % | KPI Cards | At-a-glance health metrics |
| Paying Conversion Rate | KPI Card | Monetization pulse |
| Total Revenue (USD) | KPI Card | Revenue snapshot |
| Avg Session Duration | KPI Card | Engagement depth |

### Page 2 — Retention Analysis
| Visual | Type | Insight |
|--------|------|---------|
| Retention curve (Day 1 → 7 → 30) | Line Chart | Where players drop off |
| Churn by game title | Clustered Bar | Which games retain best |
| Days active distribution | Histogram | Player lifecycle spread |
| Day 3 churn highlight | Card + Conditional Format | Critical drop-off alert |

### Page 3 — Player Segmentation
| Visual | Type | Insight |
|--------|------|---------|
| Free vs. Paying users | Donut Chart | Monetization funnel |
| Churn by country | Filled Map | Geography of engagement |
| Platform split (Android vs iOS) | Pie Chart | Platform performance |
| Power Users (30+ days) vs Casual | Stacked Bar | Segment breakdown |

### Page 4 — Monetization & Engagement
| Visual | Type | Insight |
|--------|------|---------|
| Avg session duration by game | Bar Chart | Which game drives depth |
| Puzzles per session trend | Line Chart | Engagement over time |
| Revenue by country | Treemap | Top revenue markets |
| ARPU by platform | Bar Chart | Android vs iOS revenue |

---

## 🧮 DAX Measures Used

```dax
// Day 7 Retention Rate
Day7 Retention % = 
DIVIDE(
    CALCULATE(COUNTROWS(player_data), player_data[day7_retention] = 1),
    COUNTROWS(player_data)
) * 100

// Paying Conversion Rate
Paying Conversion % = 
DIVIDE(
    CALCULATE(COUNTROWS(player_data), player_data[is_paying_user] = 1),
    COUNTROWS(player_data)
) * 100

// Day 3 Churn %
Day3 Churn % = 
DIVIDE(
    CALCULATE(COUNTROWS(player_data), player_data[days_active] <= 3),
    COUNTROWS(player_data)
) * 100
```
*See `powerbi/DAX_Measures.txt` for all 12 measures.*

---

## 📁 Dataset Description

**File:** `data/player_data.csv`  
**Records:** 500 simulated players  
**Time Period:** Jan 2024 – Oct 2024

| Column | Description |
|--------|-------------|
| `player_id` | Unique player ID (PSG1000–PSG1499) |
| `install_date` | Date the game was installed |
| `country` | Player's country (India, USA, UK, Canada, Australia, Germany, Brazil, France) |
| `game_title` | Which PlaySimple game they play |
| `platform` | Android or iOS |
| `days_active` | Total days the player was active |
| `last_active_date` | Last date of session |
| `avg_session_min` | Average session length in minutes |
| `puzzles_per_session` | Avg puzzles completed per session |
| `total_sessions` | Total sessions since install |
| `level_reached` | Highest level/puzzle reached |
| `is_paying_user` | 1 = paying, 0 = free |
| `revenue_usd` | Revenue generated (0 for free users) |
| `day1_retention` | 1 if returned on Day 1 |
| `day7_retention` | 1 if active by Day 7 |
| `day30_retention` | 1 if active by Day 30 |

---

## 💡 Key Findings

1. **34% of players churn within the first 3 days** — the most critical drop-off window
2. **Daily Themed Crossword** has the highest Day 30 retention among all titles
3. **India and USA** are the top markets but churn fastest after Day 7
4. **Paying users average 3x more sessions** than free users before converting
5. **iOS users show 22% higher ARPU** than Android despite lower install share

---

## ✅ Business Recommendations

1. **Re-engagement push notification at Day 2** to catch users before the Day 3 churn spike
2. **Localized content** for India market to improve Day 7 retention
3. **Soft paywall at Level 15** (avg conversion point) with a free trial offer
4. **Cross-promote Daily Themed Crossword** to WordTrip/WordJam players (higher retention)
5. **iOS-exclusive bundle pricing** to capitalize on higher willingness to pay

---

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| Microsoft Power BI Desktop | Dashboard creation, DAX measures |
| Power Query | Data transformation & cleaning |
| Python (pandas, numpy) | Dataset generation |
| Excel | Data validation |
| GitHub | Version control & portfolio hosting |

---

## 🚀 How to Use

1. Clone this repository
2. Open Power BI Desktop
3. Click `Get Data` → `Text/CSV` → select `data/player_data.csv`
4. Go to `Transform Data` → set correct data types (dates as Date, flags as Whole Number)
5. Create a new measure and paste from `powerbi/DAX_Measures.txt`
6. Build visuals using the dashboard structure above

---

## 👤 About This Project

Built as a **portfolio project** to demonstrate Business Analyst skills in:
- Player lifecycle analysis
- KPI definition and tracking
- Data storytelling with Power BI
- Actionable insight generation for a gaming product team

*Dataset is simulated for portfolio purposes, inspired by the product analytics work done at mobile gaming studios.*

---

⭐ *If you found this useful, feel free to star the repo!*
