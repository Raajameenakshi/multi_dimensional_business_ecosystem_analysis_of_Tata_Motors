# Multi-Dimensional Business Ecosystem Analysis of Tata Motors

A data-driven analysis of Tata Motors' performance over ten fiscal years (2015-16 to 2024-25), built around a custom **Ecosystem Resilience Index (ERI)**. Capstone project for the **Business Data Management (BDM)** course.

## Dataset

- **Name:** Tata Motors Multi-Dimensional Performance Data
- **Period:** FY 2015-16 to FY 2024-25
- **Size:** 46 indicators across 10 fiscal years
- **Source:** Publicly available documents published by Tata Motors: annual reports, Business Responsibility and Sustainability Reports (BRSR), and quarterly financial statements

The indicators cover financial results (Revenue, EBITDA, PBT, PAT, Free Cash Flow, Net Debt/Equity), operations (vehicle sales, market share, inventory turnover), geographic revenue split, R&D and capital spending, and sustainability data (emissions, energy use, safety, workforce).

- [Dataset and indicator descriptions](https://docs.google.com/spreadsheets/d/1PZMPE3osAxjHKZAHPOkZ9QVb_fAPfx26npTHxGZnC9Y/edit?usp=sharing)
- [Source documents](https://drive.google.com/drive/folders/1EKZHZqm7em33oN68GIaa0E2U5kupmDWD?usp=sharing)

## Ecosystem Resilience Index

The ERI combines 21 metrics grouped into five dimensions:

| Dimension | Metrics |
|---|---|
| Financial Stability | Revenue, EBITDA, PAT, Free Cash Flow, Net Debt/Equity Ratio |
| Operational Health | Total vehicle sales, Market Share (CV and PV), Inventory Turnover, Employee Turnover |
| Market and Geographic Diversity | Exports, JLR units sold, Geographic Diversification Index |
| Strategic Investments and Innovation | Capital Expenditure, R&D spend (TML and JLR), Training Hours |
| Sustainability and Future Readiness | GHG Emissions (Scope 1 and 2), Direct Energy Consumption, Lost Time Injury Frequency Rate, Total Employees |

### How it is calculated

1. **Normalize each metric to a 0-1 scale** using min-max scaling. For metrics where lower is better (Net Debt/Equity, Employee Turnover, emissions, energy use, injury rate), the scale is inverted.
2. **Compute geographic diversification** with a weighted Berry-Herfindahl Index. Each region's revenue share is multiplied by a market-size weight, the shares are re-normalized, and the score is `1 - sum(share²)`. A higher score means revenue is spread across more regions. The market-size weights (India 1.0, China 0.8, UK 0.6, USA 1.2, Rest of Europe 0.7, Rest of World 0.5) are assumptions chosen for this project.
3. **Average the normalized metrics** within each dimension to get five dimension scores.
4. **Combine the dimensions** with equal weights (0.2 each) into the final ERI.

## Key Findings

- **ERI trend:** The ERI fell sharply to 0.341 in 2019-20, recovered gradually, and reached 0.572 in 2023-24 and 0.633 in 2024-25.
- **Revenue and margins:** Revenue grew strongly in recent years, but the EBITDA margin fluctuated.
- **Profitability:** PBT and PAT are often well below EBITDA, which points to interest, depreciation, and tax costs.
- **Sales mix:** Growth is driven by passenger vehicles. PV market share has risen, while CV market share has declined.
- **Geography:** India's share of revenue has grown substantially, while revenue from markets such as China and the UK has been more volatile.

## Project Structure

    ├── BDM_Project.ipynb                              # Analysis, ERI calculation, and charts
    ├── BDM_Data.csv                                   # Input dataset
    ├── reports/
    │   ├── Raajameenakshi_BDM_Proposal.pdf            # Project proposal
    │   ├── Raajameenakshi_-_Mid_Term.pdf              # Mid-term report
    │   └── Raajameenakshi_BDM_Final_Report_.pdf       # Final report
    └── README.md


## Notebook Contents

1. Load and inspect the dataset (shape, data types, summary statistics)
2. Revenue and EBITDA margin (dual-axis chart)
3. EBITDA, PBT, and PAT comparison (grouped bar chart)
4. Geographic revenue distribution (stacked bar chart)
5. Vehicle sales and market share (dual-axis chart with stacked bars)
6. ERI calculation and export to `tata_motors_eri_output.csv`
7. ERI and dimension trends (stacked bar chart with ERI line)

## Tech Stack

Python, Pandas, NumPy, Matplotlib, Seaborn
