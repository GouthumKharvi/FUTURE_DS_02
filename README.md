# FUTURE_DS_02
SOCIAL MEDIA CAMPAIGN PERFORMANCE TRACKER(PowerBI)

# 📊 Social Media Campaign Performance Tracker

A detailed Power BI dashboard project analyzing the effectiveness and performance of **Facebook and Instagram ad campaigns**. This report uses **DAX measures**, **KPI cards**, and **interactive visuals** to uncover key trends, user behavior, and ROI performance over a specific timeframe.

---

## 🧪 Objective

The primary goal of this project is to **analyze social media campaign performance** between **August 17–30, 2017**, based on **audience age, gender, ad ID, campaign ID**, and more. 

The insights will help the marketing team:
- Optimize ad spend
- Improve conversion rates
- Increase ROI
- Target the most engaged demographics

---

## 📂 Dataset Overview

This dataset was provided as part of an internship task and includes the following fields:

| Column Name            | Description                                        |
|------------------------|----------------------------------------------------|
| `ad_id`                | Unique ID of the advertisement                    |
| `reporting_start`      | Start date of campaign report                     |
| `reporting_end`        | End date of campaign report                       |
| `campaign_id`          | Unique ID assigned to the campaign                |
| `fb_campaign_id`       | Facebook’s internal campaign ID                   |
| `age`                  | Age group targeted (e.g., 30–34, 35–39, etc.)     |
| `gender`               | Targeted gender (`M` or `F`)                      |
| `impressions`          | How many times the ad was shown                   |
| `clicks`               | Number of times users clicked the ad              |
| `spent`                | Amount of money spent on that ad (₹ removed)      |
| `total_conversion`     | Total number of conversions tracked               |
| `approved_conversion`  | Approved conversions after quality validation     |

> ⚠️ Columns `interest1`, `interest2`, and `interest3` were removed due to missing/irrelevant values.

---

## 🚀 Step-by-Step Project Workflow

### 1️⃣ Data Loading & Cleaning

- Imported CSV into **Power BI**
- Renamed the table to `CampaignData`
- Checked and converted data types (Date, Whole Number, Currency)
- Removed null columns (interest-based)
- Validated the dataset for missing values

---

### 2️⃣ Data Modeling

- Flat data model — single table (`CampaignData`)
- Ensured currency and date formatting consistency
- Added visual-level and page-level slicers
- Optimized table columns by removing unused fields

---

## 🧠 DAX Measures (Full List)

### 📌 Basic Metrics

```DAX
Total Impressions = SUM('CampaignData'[impressions])
Total Clicks = SUM('CampaignData'[clicks])
Total Spent = SUM('CampaignData'[spent])
Total Conversions = SUM('CampaignData'[total_conversion])
Approved Conversions = SUM('CampaignData'[approved_conversion])
```

###  📌 Performance Ratios
```DAX

CTR (%) = DIVIDE(SUM('CampaignData'[clicks]), SUM('CampaignData'[impressions])) * 100

ROI (%) = DIVIDE(SUM('CampaignData'[approved_conversion]), SUM('CampaignData'[spent])) * 100

CPC = DIVIDE(SUM('CampaignData'[spent]), SUM('CampaignData'[clicks]))

CPA = DIVIDE(SUM('CampaignData'[spent]), SUM('CampaignData'[approved_conversion]))
```

### 📌 Advanced Calculations
```DAX
CTR by Age = CALCULATE(
    DIVIDE(SUM('CampaignData'[clicks]), SUM('CampaignData'[impressions])) * 100,
    ALLEXCEPT('CampaignData', 'CampaignData'[age])
)
```

```DAX

CTR by Campaign = CALCULATE(
    DIVIDE(SUM('CampaignData'[clicks]), SUM('CampaignData'[impressions])) * 100,
    ALLEXCEPT('CampaignData', 'CampaignData'[campaign_id])
)
```


📌 Funnel Metrics
```DAX
Clicks Funnel = SUM('CampaignData'[clicks])
Conversion Funnel = SUM('CampaignData'[total_conversion])
Approved Funnel = SUM('CampaignData'[approved_conversion])
```

📊 KPI Cards (Top Section of Dashboard)
Each KPI is calculated using DAX and visualized using Power BI card visuals:

| KPI                  | Formula                              | Insight                         |
| -------------------- | ------------------------------------ | ------------------------------- |
| Total Spent          | `SUM(spent)`                         | 20,000 budget used             |
| ROI (%)              | `Approved Conversions / Spent * 100` | 49.08% return on investment     |
| CTR (%)              | `Clicks / Impressions * 100`         | 0.01% — low user engagement     |
| Total Clicks         | `SUM(clicks)`                        | 12,000 users clicked ads        |
| Total Impressions    | `SUM(impressions)`                   | 78.51 million total views       |
| Total Conversions    | `SUM(total_conversion)`              | 1645 conversions tracked        |
| Approved Conversions | `SUM(approved_conversion)`           | 585 final validated conversions |


### 📈 Visualizations & Charts
🎯 CTR (%) by Age Group
Type: Clustered Bar Chart

Shows engagement levels per age range

Insight:

Age 45–49 → Highest CTR (0.023%)

Age 40–44 → Second Highest CTR (0.017%)


###🧍‍♂️ Total Spent by Gender
Type: Pie Chart

Male: 87.51%

Female: 12.49%

Suggests budget skewed heavily toward male audience

### 📉 Impressions vs Clicks
Type: Line Chart

Compares views (impressions) and engagements (clicks)

### Peak Campaign:

12.8M impressions, 1831 clicks, 97 approved conversions

### Low Campaign:

730K impressions, 104 clicks, only 3 approved conversions

### 📊 Campaign Performance vs CTR
Type: Combo Chart (Column + Line)

Metrics per campaign_id:

CPC, CPA, CTR, conversions

Example (campaign 1178):

Spent: 16,577, CTR: 0.01%, Approved: 378

### 🔁 Funnel Chart
Clicks → Conversions → Approved Conversions

Values:

Clicks: 12K

Total Conversions: 2K

Approved Conversions: 1K

Shows performance drop-off across funnel

### 📦 Top Ads by Engagement
Type: Tree Map

Highlights top ad_id values by total clicks

ad_id 952031: 8 clicks

ad_id 952001: 2 clicks


### 🔎 Filters & Slicers Used
Filter Type	Values Used
Date Range	17–08–2017 to 30–08–2017
Campaign ID	916, 936, 1178
Age Groups	30–34, 35–39, 40–44, 45–49
Gender	M, F
Total Conversion Slider	0 to 60
Spent Slider	0 to 639.94

### 📌 Final Campaign Insights
Metric	Value
Total Spent	20,000
CTR	0.01%
ROI	49.08%
Approved Conversions 585


### 📍 Best Campaign
Impressions: 12.8M

Clicks: 1831

Approved Conversions: 97

### 📍 Low Campaign
Impressions: 730K

Clicks: 104

Approved Conversions: 3


### 🧠 Recommendations for Next Campaign
Focus on age groups 45–49 and 40–44 (highest CTR).

Reduce ad spend on age groups with low engagement.

Rebalance gender-based budget (female audience underutilized).

Improve ad creatives based on top-performing ad IDs.

Run A/B tests for better click-through experimentation.

Monitor CTR, CPC, CPA metrics in real-time for optimization.



### 👨‍💻 Tools & Skills Used
Power BI Desktop

DAX (Data Analysis Expressions)

Power Query Editor

Data Modeling & Cleansing

KPI Cards & Funnel Charts

Interactive Dashboard Design

Data Interpretation for Business Insights















