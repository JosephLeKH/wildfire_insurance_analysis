# Burning Coverage: How Wildfires Reshape Home Insurance in California

**Authors:** Joseph Le, Ganesh Venu, Mason Mckhann  
**Course:** DataSci 112 (Spring 2025)  

---

## Overview

Wildfire activity in California has surged over the past decade, leaving homeowners increasingly exposed and destabilizing the insurance market. As private insurers retreat from high-risk areas, more Californians are pushed into costly last-resort coverage such as the **FAIR Plan**.  

This project quantifies those dynamics by combining **county-level wildfire data (2016–2023)** with **insurance policy data** (new, renewed, non-renewed counts) across three coverage types:  
- **Voluntary Market** — private insurers  
- **FAIR Plan** — state-mandated “insurer of last resort”  
- **Difference-in-Conditions (DIC)** — wrap-around policies paired with FAIR  

**Key Question:**  
How do spikes in wildfire activity drive shifts in insurance markets across California counties?

---

## Repository Structure

- **`Wildfire_Data_Collection.ipynb`**  
  Web-scrapes wildfire incident data from [fire.ca.gov](https://www.fire.ca.gov/) and insurance policy PDFs from [insurance.ca.gov](https://www.insurance.ca.gov/). Cleans and merges them into a unified **County × Year** dataset (2016–2023).  

- **`Wildfire_Analysis.ipynb`**  
  Performs descriptive and statistical analysis:  
  - Yearly correlations between wildfire exposure and lagged non-renewals  
  - FAIR Plan share of total policies by county and year  
  - Voluntary renewal rate trends  
  - County-level case studies and heatmaps  

- **`aggregated_fires_insurance_dataset.csv`** *(generated)*  
  Unified dataset with wildfire and insurance metrics, used in analysis.

- **`figures/`**  
  Contains exported visuals (A–F) used in the results section.

---

## Methodology

1. **Data Collection**  
   - Wildfire records scraped by incident, converted to **county–year acres burned**.  
   - Insurance PDFs parsed into policy counts (new, renewed, non-renewed) for Voluntary, FAIR, and DIC.  
   - Joined datasets on County and Year; cleaned county name variants.  

2. **Lagged Insurance Response**  
   - Constructed **1-year lag** of non-renewed voluntary policies to test whether major fires trigger insurer withdrawals the following year.  

3. **Derived Metrics**  
   - **FAIR Share (%)** = FAIR policies ÷ total policies  
   - **% Renewed** = Renewed ÷ (Renewed + Non-Renewed)  
   - **Fire Exposure Normalization** = Acres ÷ Population (county-level)  

4. **Visualization & Analysis**  
   - Heatmaps, line charts, and correlations built with `plotly`.  
   - Top fire-exposed counties identified by acres ÷ population.  
   - Case study: Alameda County.  

---

## Results

### A. Lagged Wildfire Effect → Non-Renewals  
Spikes in wildfire activity are followed by **sharp increases in non-renewals** the next year.  
Example: 2018 fires → 2019–2020 non-renewal surge.  
![Lagged Effect](figures/A_lagged_effect.png)

---

### B. Correlation Supports Time-Lag Theory  
Correlation analysis (r ≈ **0.68**) confirms a strong link between acres burned and next-year non-renewals.  
![Correlation Matrix](figures/B_correlation.png)

---

### C. Rising Dependence on FAIR Plan  
FAIR share of policies climbs year-over-year in the **10 most fire-exposed counties**.  
![FAIR Plan Growth](figures/C_fair_plan_growth.png)

---

### D. Declining Voluntary Renewals  
Voluntary renewal % has **fallen steadily since 2016**. Sharp declines follow major fire seasons (Camp, Tubbs, Dixie), with no recovery.  
![Voluntary Renewal Decline](figures/D_voluntary_renewals.png)

---

### E. Structural Shift in High-Risk Counties  
In counties >300k population with high fire exposure, **FAIR + DIC policy counts** rose sharply post-2019.  
![High-Risk County Shift](figures/E_highrisk_shift.png)

---

### F. Alameda County Case Study  
FAIR + DIC policies tripled from 2020 to 2023 after a local wildfire, showing how even urban-adjacent counties face insurer withdrawal.  
![Alameda County Case Study](figures/F_alameda_case.png)

---

## Significance

Our findings reveal an **insurance system that is reactive, fragile, and increasingly reliant on last-resort coverage**. As wildfires intensify:  
- Homeowners are forced out of the voluntary market.  
- FAIR Plan dependence grows, raising costs and reducing coverage quality.  
- Families in both rural and urban-adjacent counties are left vulnerable.  

Beyond California, this framework shows how **environmental shocks reshape financial systems** and can inform policy on climate resilience, insurance regulation, and equitable coverage.

---

## Limitations & Future Work

- **Lag structures**: Focused on 1-year lag; multi-year impacts remain unexplored.  
- **Policy costs**: Data covers counts, not premiums; affordability effects need further study.  
- **Regulatory responses**: Moratoriums and policy interventions were not explicitly modeled.  

Future research could apply **panel regressions, event studies, or predictive models** using broader environmental and socioeconomic risk factors.

---

## Getting Started

1. Clone the repository:  
   ```bash
   git clone https://github.com/<your-username>/<repo-name>.git
   cd <repo-name>
   ```
2. Install dependencies:  
   ```bash
   pip install -r requirements.txt
   ```
3. Run notebooks in order:  
   1. `Wildfire_Data_Collection.ipynb`  
   2. `Wildfire_Analysis.ipynb`

---

## Acknowledgments

- [fire.ca.gov](https://www.fire.ca.gov/) – wildfire incident data  
- [insurance.ca.gov](https://www.insurance.ca.gov/) – insurance policy reports  
- Stanford DataSci 112 faculty and peers  

---
