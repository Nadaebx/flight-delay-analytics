# ✈️ Flight Delay & Cancellation Analysis (2019–2023)

> **CET242 – Data Analytics and Visualization | Spring 2026**
> Faculty of Engineering Technology — Elsewedy University of Technology

---

## 📌 Project Problem

> *"Which airlines, routes, and time periods experience the highest flight delays between 2019–2023, and what are the root causes driving these delays?"*

Flight delays cost the US economy over **$28 billion annually**. This project uses real flight data to find exactly where, when, and why delays happen — and what can be done about it.

---

## 📂 Project Structure

```
📁 Flight-Delay-Analysis/
│
├── 📓 Python_Analysis.ipynb        ← Data cleaning, EDA, hypothesis testing, charts
├── 📊 Flight_Delay_Dashboard.pbix  ← Power BI interactive dashboard (4 pages)
├── 📄 Member4_Report.docx          ← Final report with insights & recommendations
├── 📁 dataset/
│   └── flights_sample_3m.csv       ← Cleaned dataset (100K rows)
└── 📄 README.md                    ← You are here
```

---

## 👥 Team Division

| Member | Responsibility |
|--------|---------------|
| Member 1 | Problem definition, dataset selection, data cleaning |
| Member 2 | KPI definition, hypothesis writing & testing in Python |
| Member 3 | Exploratory Data Analysis (EDA) & root cause analysis |
| **Member 4** | **Power BI dashboard, insights, recommendations, final report** |

---

## 📊 Dataset

- **Source:** [Kaggle — Flight Delay and Cancellation Dataset (2019–2023)](https://www.kaggle.com/datasets/patrickzel/flight-delay-and-cancellation-dataset-2019-2023)
- **File used:** `flights_sample_3m.csv`
- **Rows:** 100,000 flights
- **Time period:** 2019 to 2023

### Key Columns Used
| Column | Description |
|--------|-------------|
| `FL_DATE` | Flight date |
| `AIRLINE` | Airline name |
| `ORIGIN_CITY` / `DEST_CITY` | Departure and arrival cities |
| `DEP_DELAY` / `ARR_DELAY` | Delay in minutes |
| `CANCELLED` | 1 = cancelled, 0 = not |
| `CANCELLATION_CODE` | A=Carrier, B=Weather, C=NAS, D=Security |
| `DELAY_DUE_CARRIER/WEATHER/NAS/LATE_AIRCRAFT` | Root cause minutes |

---

## 📈 KPIs (Key Performance Indicators)

| KPI | Value | What it tells us |
|-----|-------|-----------------|
| Total Flights | 3,000,000 | Scale of the analysis |
| Avg Departure Delay | **10 min** | Core problem metric |
| Avg Arrival Delay | 4 min | Airlines partially recover in-air |
| On-Time Rate | **67%** | Only 2 in 3 flights depart on time |
| Cancellation Rate | 3% | ~90K flights fully cancelled |
| Total Delays | **993K** | Nearly 1 million delayed flights |
| Severe Delay Rate | 6% | 1 in 16 flights delayed 60+ minutes |

---

## 🔬 Hypotheses Tested

| # | Hypothesis | Result |
|---|-----------|--------|
| 1 | Delays are worse on Fridays and Sundays | ✅ ACCEPTED |
| 2 | Late aircraft is the biggest cause of delays | ✅ ACCEPTED |
| 3 | Weather is the main reason for cancellations | ✅ ACCEPTED |

---

## 🗺️ Power BI Dashboard (4 Pages)

### Page 1 — Overview
> *How bad is the delay problem overall?*
- 5 KPI cards: Total Flights, Avg Departure Delay, Avg Arrival Delay, Cancellation Rate, On-Time Rate
- Bar chart: Avg departure delay by airline → **JetBlue has the worst delays**
- Line chart: Delay trend by month → **Summer months peak**
- Line chart: Cancellations by month
- Pie chart: Flight distribution by delay category

### Page 2 — Root Causes
> *Why are flights delayed?*
- Cards: Total Delays (993K) and Severe Delay Rate (6%)
- Clustered bar: Carrier vs Weather vs NAS vs Late Aircraft delay by airline → **Late Aircraft dominates**
- Donut chart: Cancellation reasons → **Weather (36.47%) is #1**
- Bar chart: Delays by day of week → **Friday is worst**

### Page 3 — Where & When
> *Where are delays concentrated?*
- Bar chart: Top 10 worst departure cities → **Pago Pago, TT leads**
- Bar chart: Top 10 worst arrival cities → **Williamsport, PA leads**
- Line chart: Delay trend 2019–2023 → **Dropped in 2020 (COVID), spiked in 2021–2022**
- Stacked bar: Cancellations by airline → **Southwest Airlines leads with 6,000+**

### Page 4 — Interactive Explorer
> *Live filtering for discussion*
- Slicers: Year, Airline, Delay Category, Cancellation Code
- All charts update live when filters are changed

---

## 💡 Key Insights

1. **JetBlue Airways** has the highest average departure delay of any major airline
2. **Late Aircraft** is the #1 delay cause — one late plane creates a chain reaction
3. **Friday and Sunday** are consistently the worst days for delays
4. **Weather** causes 36% of cancellations but airlines can reduce impact with proactive rebooking
5. **Southwest Airlines** has 6,000+ cancellations — highest of any carrier
6. Delays **dropped in 2020** (COVID reduced flights) then spiked back in 2021–2022

---

## ✅ Recommendations

| # | Insight | Recommendation | Expected Impact |
|---|---------|---------------|-----------------|
| 1 | Friday/Sunday worst days | Add staff and buffer time on peak days | Reduce peak-day delays by ~3 min |
| 2 | Late aircraft is #1 cause | Stricter turnaround policies, spare aircraft at hubs | Reduce overall delays 20–30% |
| 3 | JetBlue worst airline | Operational audit + benchmark against leaders | Improve on-time rate significantly |
| 4 | Weather causes 36% of cancellations | Better weather prediction + proactive rebooking | Reduce complaints by 40% |
| 5 | Southwest highest cancellations | Add recovery buffers in network planning | Prevent 1,200+ cancellations/year |
| 6 | 2021–2022 spike after COVID | Better capacity planning for demand surges | Prevent repeat of post-COVID chaos |

---

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| Python (Pandas, NumPy) | Data cleaning, EDA, hypothesis testing |
| Matplotlib / Seaborn | Python visualizations |
| Power BI Desktop | Interactive dashboard |
| Microsoft Word | Final report |
| GitHub | Version control and submission |

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
3. If data doesn't load, go to Transform Data → update the CSV file path

### Dataset
Download from Kaggle:
👉 https://www.kaggle.com/datasets/patrickzel/flight-delay-and-cancellation-dataset-2019-2023

---

## 📝 Final Report

The final report (`Member4_Report.docx`) covers:
- Problem statement and why it matters
- Dataset description and cleaning steps
- KPI definitions and values
- Hypothesis testing results
- Analysis summary from all 4 dashboard pages
- 6 data-driven recommendations with expected impact
- Conclusions

---



*This project was completed as part of the CET242 final project requirement — applying real-world data analytics thinking to solve a meaningful industry problem.*
