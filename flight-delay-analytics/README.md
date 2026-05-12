# Flight Delay Analytics Project

## Step 1 – Domain and Problem Definition

**Domain:** Transportation & Commercial Aviation

**Problem Statement:**  
Flight delays cause significant financial losses for airlines and severely impact passenger satisfaction. Currently, a substantial percentage of flights experience delays, but the primary drivers—whether they are rooted in carrier operations, weather, or scheduling—and when they are most likely to occur (e.g., specific months or days of the week) are not fully quantified. **The problem is that the average flight arrival delay and the frequency of severe delays exceed acceptable operational thresholds, making it difficult for airlines to optimize scheduling and resource allocation.**

**Why this is a strong problem definition:**
- **Specific:** It focuses on identifying the specific root causes (weather, carrier, NAS) and temporal patterns (seasonality, day of week) of flight delays.
- **Measurable:** Delays are quantified strictly in minutes, allowing us to track average delay times, delay frequencies, and correlate them with operational features.
- **Important:** Reducing delays directly improves airline profitability, reduces operational bottlenecks, and boosts customer satisfaction.

## Step 2 – Dataset Selection

To investigate this problem, we selected a comprehensive dataset containing approximately 3 million records of US domestic flights (`flights_sample_3m.csv`). 

**Why this dataset is appropriate:**
- It contains direct measurements of our problem: `ARR_DELAY` (Arrival Delay in minutes).
- It provides a detailed breakdown of delay root causes, including `DELAY_DUE_CARRIER`, `DELAY_DUE_WEATHER`, `DELAY_DUE_NAS`, `DELAY_DUE_SECURITY`, and `DELAY_DUE_LATE_AIRCRAFT`.
- It includes temporal data (`FL_DATE`) to allow for trend analysis and seasonality checks.
- The dataset is sufficiently rich, allowing for extensive Exploratory Data Analysis (EDA) and hypothesis testing to uncover the exact root causes of flight delays.

## Step 3 – Understanding and Preparing the Data
We performed cleaning by:
- Handling missing values in delay cause columns (imputed as 0).
- Removing records with missing arrival delays.
- Engineering new features like `MONTH`, `DAY_NAME`, and `DEP_HOUR`.

## Step 4 – Defining KPIs
1. **Average Arrival Delay (AAD):** Mean delay for all flights.
2. **Delay Rate (DR):** % of flights with any arrival delay.
3. **Severe Delay Rate (SDR):** % of flights with delay > 15 minutes.
4. **Average Departure Delay (ADD):** Mean delay at takeoff.

## Step 5 – Hypothesis-Driven Analysis
- **H1:** Winter weather significantly impacts delays (Confirmed: Weather delays spike in Dec/Jan).
- **H2:** Legacy vs. Low-Cost performance (Insights show legacy carriers often have better recovery mechanisms).
- **H3:** Evening "Ripple Effect" (Confirmed: Delays increase steadily throughout the day).

## Step 6 & 7 – EDA & Root Cause Analysis
Analysis shows that **'Late Aircraft'** and **'Carrier'** delays are the most significant contributors. This indicates that operational turnaround and fleet scheduling are bigger bottlenecks than weather.

## Step 8 – Insights and Recommendations
- **Insight:** Peak delays occur between 4 PM and 8 PM.
- **Recommendation:** Increase turnaround buffer times in evening schedules to prevent the cumulative ripple effect of morning delays.
