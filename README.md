## Deflating Economic Data — Nominal vs. Real
**Abigail Ray ECON3916**

**Objective:** This project separates genuine changes in purchasing power from the effects of inflation by deflating nominal U.S. economic time series — wages and Big Mac prices — into constant dollars using CPI data pulled directly from FRED.

**Methodology:**
- Retrieved CPI (CPIAUCSL) and average hourly earnings (AHETPI) from FRED's public CSV endpoint, requiring no API credential
- Built a reusable `deflate_series()` function implementing the standard deflation formula: Real Value = (Nominal Value / CPI) × Base-Year CPI
- Applied the function to convert 1964–present nominal wage data into constant 2020 dollars
- Extended the analysis to The Economist's Big Mac Index, aligning semi-annual price observations with monthly CPI readings via `.asof()` matching
- Verified results against the growth identity (1 + nominal) = (1 + real) × (1 + CPI) to confirm internal consistency
- Built an interactive ipywidgets-based explorer allowing users to toggle between series, adjust the base year, and switch between nominal/real views in real time

**Key Findings:**
- Nominal average hourly earnings rose from $2.50 to $32.53, but real earnings (in 2020 dollars) moved only from $20.92 to $25.20 — most of the nominal gain reflects inflation, not increased purchasing power
- The US Big Mac price rose 178% in nominal terms since 2000, but only 43% in real terms once the 95% rise in CPI over the same period is stripped out
- These results reinforce a central lesson of price-index analysis: nominal figures alone systematically overstate economic progress, and any comparison of monetary values across time requires deflation to be meaningful
