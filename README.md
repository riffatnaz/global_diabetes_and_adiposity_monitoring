# global_diabetes_and_adiposity_monitoring
Global Diabetes & Adiposity Monitoring Dashboard
An interactive Power BI dashboard for global non-communicable disease (NCD) surveillance, tracking diabetes prevalence, treatment coverage, and body-mass-index (BMI) distribution across 200 countries and territories from 1980–2024, by sex.
Built on two NCD Risk Factor Collaboration (NCD-RisC) datasets, the dashboard surfaces cross-country and cross-time relationships between adiposity and diabetes burden, gender gaps in disease and treatment access, and regional disparities. It is designed as a reproducible analytical visual for population-health monitoring.
## Data Sources
•	NCD-RisC, The Lancet (2024)-Diabetes prevalence & treatment coverage
•	NCD-RisC, Nature (2026)-BMI category distribution
Both datasets are age-standardised. Diabetes and BMI data only fully overlap for 1990–2022; outside that range, single-dataset visuals still use each dataset's full native range.
## Data Model
The dashboard uses a star-schema model: two fact tables connected through three shared dimension tables. The two fact tables are never related to each other directly — all cross-dataset comparisons (e.g., obesity vs. diabetes scatter plots) work through the shared dimension tables, which is what lets Power BI resolve filter context correctly without double-counting.
## Key DAX Measures
20+ measures grouped by purpose, including:
•	Core KPIs — Avg Diabetes Prevalence, Avg Treatment Coverage, Avg Obesity %, Avg Underweight %
•	Trend measures — Diabetes YoY Change (pp), Diabetes Change Since 1990 (pp), Obesity YoY Change (pp), Obesity Change Since 1980 (pp)
•	Equity measures — Gender Gap — Diabetes (pp), Gender Gap — Obesity (pp), Untreated Population Share
•	Comparative measures — Diabetes-to-Obesity Ratio, Country Rank — Diabetes, Country Rank — Obesity
•	Supporting measures — Selected Year (Label), Countries in Selection, conditional-formatting helpers
## Dashboard Pages
1.	Global Overview — KPI cards with trend sparklines, filled world map (diabetes prevalence by country), dual-line global trend chart (diabetes vs. obesity over time)
2.	Country Deep Dive — country-level KPI cards, sex-split prevalence trend line, stacked BMI-band distribution over time, treatment-coverage gender comparison
3.	Risk Relationships — animated scatterplot (obesity % vs. diabetes prevalence, play axis by year, coloured by continent) with trend line; diabetes-to-obesity ratio by continent
4.	Gender & Treatment Equity — gender-gap KPIs, region × sex prevalence comparison, gender-gap trend over time, top-burden countries ranked by treatment coverage
## Reproducibility
All data transformations and the cleaned country/continent mapping are derived directly from the two NCD-RisC source files with no manual edits to the underlying figures. The data model can be refreshed by replacing the embedded tables with an updated NCD-RisC extract in the same column layout — no DAX changes required, since measures reference column names rather than hardcoded values.
