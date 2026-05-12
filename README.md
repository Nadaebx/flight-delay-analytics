# ✈️ Flight Delay & Cancellation Analysis (2019–2023)

> **CET242 – Data Analytics and Visualization | Spring 2026**
> Faculty of Engineering Technology — Elsewedy University of Technology

---

## 📌 Project Problem

> *"Which airlines, routes, and time periods experience the highest flight delays between 2019–2023, and what are the root causes driving these delays?"*

Flight delays cost the US economy over **$28 billion annually**. This project uses real flight data to pinpoint exactly where, when, and why delays happen — and what operational changes can reduce them.

---

## 📂 Project Structure

```
📁 Flight-Delay-Analysis/
│
├── 📓 Python_Analysis.ipynb          ← Data cleaning, EDA, hypothesis testing, charts
├── 📊 Flight_Delay_Dashboard.pbix    ← Power BI interactive dashboard (4 pages)
├── 📄 Member4_Report.docx            ← Final report with insights & recommendations
├── 📁 data/
│   ├── raw/
│   │   └── flights_sample_3m.csv     ← Original dataset (300K rows loaded)
│   └── cleaned/
│       └── cleaned_flights_dataset.csv ← Cleaned dataset (291,357 rows, 34 columns)
└── 📄 README.md                      ← You are here
```

---

## 👥 Team Division

| Member | Responsibility |
|--------|----------------|
| Member 1 | Problem definition, dataset selection, data cleaning |
| Member 2 | KPI definition, hypothesis writing & testing in Python |
| Member 3 | Exploratory Data Analysis (EDA) & root cause analysis |
| **Member 4** | **Power BI dashboard, insights, recommendations, final report** |

---

## 📊 Dataset

- **Source:** [Kaggle — Flight Delay and Cancellation Dataset (2019–2023)](https://www.kaggle.com/datasets/patrickzel/flight-delay-and-cancellation-dataset-2019-2023)
- **File used:** `flights_sample_3m.csv`
- **Rows loaded:** 300,000 → **291,357 after cleaning**
- **Columns:** 32 original → **34 after feature engineering**
- **Time period:** 2019 to 2023

### Key Columns Used

| Column | Description |
|--------|-------------|
| `FL_DATE` | Flight date |
| `AIRLINE` | Airline name |
| `ORIGIN_CITY` / `DEST_CITY` | Departure and arrival cities |
| `DEP_DELAY` / `ARR_DELAY` | Delay in minutes (negative = early) |
| `CANCELLED` | 1 = cancelled, 0 = not |
| `CANCELLATION_CODE` | A=Carrier, B=Weather, C=NAS, D=Security |
| `DELAY_DUE_CARRIER` | Carrier-caused delay minutes |
| `DELAY_DUE_WEATHER` | Weather-caused delay minutes |
| `DELAY_DUE_NAS` | National Air System delay minutes |
| `DELAY_DUE_LATE_AIRCRAFT` | Late aircraft delay minutes |
| `MONTH` *(engineered)* | Extracted from FL_DATE |
| `DAY_NAME` *(engineered)* | Day of week extracted from FL_DATE |

---

## 🧹 Data Cleaning Summary

| Step | Action | Rationale |
|------|--------|-----------|
| Missing delay causes | Filled with `0` | NaN = no delay occurred for that cause |
| Missing `ARR_DELAY` | Rows dropped | Cannot analyze delays without the target variable |
| Duplicates | Removed | 0 duplicates found |
| `FL_DATE` | Converted to `datetime64` | Enables time-based feature extraction |
| Feature engineering | Added `MONTH`, `DAY_NAME` | Enables temporal pattern analysis |

**Final shape: 291,357 rows × 34 columns**

---

## 📈 KPIs (Key Performance Indicators)

| KPI | Value | Interpretation |
|-----|-------|----------------|
| Total Flights Analyzed | 291,357 | Scale of analysis |
| Avg Departure Delay | **10.11 min** | Core operational problem metric |
| Avg Arrival Delay | **4.32 min** | Airlines partially recover in-air |
| Delay Rate (>0 min) | **33.64%** | 1 in 3 flights arrives late |
| Severe Delay Rate (>15 min) | **17.72%** | Nearly 1 in 5 flights seriously delayed |
| Cancellation Rate | ~3% | ~90K flights fully cancelled (full dataset) |
| Total Delayed Flights | ~993K | Nearly 1 million delayed (full dataset) |

---

## 🔬 Hypotheses Tested

### H1 — Winter months show significantly higher weather-related delays
**Result: ✅ ACCEPTED**
The bar chart of average weather delay by month confirms December, January, and February have higher weather-related delay minutes than summer months, consistent with Northern Hemisphere winter weather patterns.

### H2 — Legacy carriers have better performance than low-cost carriers
**Result: ⚠️ PARTIALLY ACCEPTED**
The severe delay rate (>15 min) chart by airline shows a mixed picture. While some legacy carriers perform better, certain low-cost carriers outperform legacy peers. JetBlue and Southwest show notably higher severe delay rates regardless of classification.

### H3 — Evening flights experience more delays due to the ripple effect
**Result: ✅ ACCEPTED**
The hourly delay chart clearly shows average arrival delays climbing through the day, peaking between 16:00–20:00 (4 PM–8 PM). This confirms the ripple/cascade effect where morning delays compound throughout the day.

---

## 🗺️ Power BI Dashboard (4 Pages)

### Page 1 — Overview
*How bad is the delay problem overall?*
- 5 KPI cards: Total Flights, Avg Departure Delay, Avg Arrival Delay, Cancellation Rate, On-Time Rate
- Bar chart: Avg departure delay by airline → **JetBlue has the worst delays**
- Line chart: Delay trend by month → **Summer months peak**
- Line chart: Cancellations by month
- Pie chart: Flight distribution by delay category

### Page 2 — Root Causes
*Why are flights delayed?*
- Cards: Total Delays (993K) and Severe Delay Rate (6%)
- Clustered bar: Carrier vs Weather vs NAS vs Late Aircraft by airline → **Late Aircraft dominates**
- Donut chart: Cancellation reasons → **Weather (36.47%) is #1**
- Bar chart: Delays by day of week → **Friday is worst**

### Page 3 — Where & When
*Where are delays concentrated?*
- Bar chart: Top 10 worst departure cities → **Pago Pago, TT leads**
- Bar chart: Top 10 worst arrival cities → **Williamsport, PA leads**
- Line chart: Delay trend 2019–2023 → **Dropped in 2020 (COVID), spiked in 2021–2022**
- Stacked bar: Cancellations by airline → **Southwest Airlines leads with 6,000+**

### Page 4 — Interactive Explorer
*Live filtering for discussion*
- Slicers: Year, Airline, Delay Category, Cancellation Code
- All charts update live when filters are applied

---

## 💡 Key Insights

1. **JetBlue Airways** has the highest average departure delay of any major airline
2. **Late Aircraft** is the #1 delay cause — one late plane triggers a chain reaction across the network
3. **Evening flights (4–8 PM)** are twice as likely to be delayed due to cumulative ripple effects
4. **Friday and Sunday** are consistently the worst days for delays
5. **Weather** causes 36% of cancellations but airlines can reduce impact via proactive rebooking
6. **Southwest Airlines** has 6,000+ cancellations — highest of any carrier
7. Delays **dropped sharply in 2020** (COVID reduced operations) then spiked in 2021–2022
8. **Late Aircraft + Carrier issues** together account for over 60% of all delay minutes

---

## ✅ Recommendations

| # | Insight | Recommendation | Expected Impact |
|---|---------|----------------|-----------------|
| 1 | Friday/Sunday worst days | Add staff and buffer time on peak days | Reduce peak-day delays by ~3 min |
| 2 | Late aircraft is #1 cause | Stricter turnaround policies, spare aircraft at hubs | Reduce overall delays 20–30% |
| 3 | JetBlue worst airline | Operational audit + benchmark against top performers | Improve on-time rate significantly |
| 4 | Weather causes 36% cancellations | Better weather prediction + proactive rebooking | Reduce complaints by 40% |
| 5 | Southwest highest cancellations | Add recovery buffers in network planning | Prevent 1,200+ cancellations/year |
| 6 | 2021–2022 spike after COVID | Better capacity planning for demand surges | Prevent repeat of post-COVID chaos |
| 7 | Evening ripple effect | Increase scheduled turnaround times for evening slots | Reduce evening delays 15–20% |
| 8 | Crew/carrier delays | Optimize crew scheduling and ground handling efficiency | Cut carrier delays significantly |

---

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| Python (Pandas, NumPy) | Data loading, cleaning, feature engineering |
| Matplotlib / Seaborn | Python visualizations and EDA charts |
| Power BI Desktop | Interactive 4-page dashboard |
| Microsoft Word | Final report writing |
| GitHub | Version control and project submission |

---

## 📋 How to Run

### Python Notebook
```bash
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook Python_Analysis.ipynb
```

### Power BI Dashboard
1. Download and install [Power BI Desktop](https://powerbi.microsoft.com/desktop/)
2. Open `Flight_Delay_Dashboard.pbix`
3. If data doesn't load → Transform Data → update the CSV path to your local file

### Dataset
Download from Kaggle:
👉 https://www.kaggle.com/datasets/patrickzel/flight-delay-and-cancellation-dataset-2019-2023

---

## 📝 Final Report

`Member4_Report.docx` covers:
- Problem statement and economic context
- Dataset description and full cleaning methodology
- KPI definitions and computed values
- Hypothesis testing results with charts
- Dashboard walkthrough (all 4 pages)
- 8 data-driven recommendations with expected impact
- Conclusions

---

*This project was completed as part of the CET242 final project requirement at Elsewedy University of Technology — applying real-world data analytics to solve a meaningful industry problem.*
