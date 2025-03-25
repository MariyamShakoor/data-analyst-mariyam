# 📘 README: Diagnostic Analysis of City of Vancouver Capital Budget Dataset

---

### ✅ **Project Title**
**Diagnostic Analysis of the 2024 Multi-Year Capital Project Budget Dataset**

---

### ✅ **Project Description**
This project represents the second phase of the Data Analytics Platform (DAP) designed for the City of Vancouver. After completing foundational data wrangling tasks, this stage focuses on performing diagnostic analysis on the city's capital budget dataset to uncover insights on expenditure trends, funding distributions, and strategic budget allocations.

---

### ✅ **Objective**
To analyze the cleaned and cataloged budget data using SQL queries in Amazon Athena in order to identify key projects, assess funding patterns, and support strategic financial planning for the 2024–2026 period.

---

### ✅ **Dataset**
- **Title**: 2024 Multi-Year Capital Project Budget Requests and Capital Expenditure Budget  
- **Source**: City of Vancouver Open Data Portal  
- **Content**: Project names, budget requests (2024), forecasted expenditures (2025–2026), funding sources (debt, reserves, partner contributions), and approvals

---

### ✅ **Methodology**

#### 1. **Environment Setup**
- Two AWS Glue Crawlers were configured: `budgetrequest-crawler-my` to scan S3 buckets and populate the AWS Glue Data Catalog.
- The crawler created two tables: `budgetrequest-trf_system` and `budgetrequest-metrics`, holding the transformed and summarized financial data.
- Amazon Athena was used for querying the dataset. The data source was `AwsDataCatalog` and the database selected was `budgetrequest-catalog-my`.
- Query results were stored in the Amazon S3 location `s3://budgetrequest-cur-my`.

#### 2. **Analysis Overview**
Each analysis step was conducted using SQL queries within Amazon Athena and focused on deriving specific financial insights from the dataset.

##### a. **Most Expensive Capital Projects (2024 & 2025)**
- Queried projects by descending order of budget for 2024 and forecast for 2025.
- Identified the top-funded projects:
  - **2024**: "2023–2026 Housing Land Acquisition" with $39.82 million.
  - **2025**: "Pacific National Exhibition (PNE) Amphitheatre" with $74.98 million.
- Insights show significant resource dedication toward housing in the earlier year and a shift to infrastructure in the following year.

##### b. **Forecasted Expenditure Trends (2024–2026)**
- Analyzed capital project budgets forecasted over three years (2024, 2025, 2026).
- Sorted by 2024 budget and included forecast values for 2025 and 2026.
- The top three projects with rising financial impact were:
  - "2023–2026 Housing Land Acquisition"
  - "Coal Harbour – Housing"
  - "PNE Amphitheatre"
- This analysis revealed a forward-looking expansion of investment into large-scale community development projects.

##### c. **Comparative Analysis of Approved vs. Requested Budgets**
- Calculated the difference between new 2024 budget requests and previously approved amounts.
- Highlighted:
  - "2023–2026 New Land for Parks" and "2024 Distribution Main Replacement" as having major increases.
  - Projects like "Permanent Public Plazas" had no previous approvals, signaling newly emerging priorities.
- This comparison supported understanding of evolving funding priorities and areas requiring strategic adjustment.

##### d. **Funding Source Analysis**
- Evaluated the distribution of total project budgets across four funding types:
  - Pay-as-you-go
  - Borrowing authority (debt)
  - Reserve funds
  - Partner contributions
- Showed how certain projects are entirely city-funded while others rely on external debt, providing a nuanced view of fiscal strategies.

##### e. **Partner Contribution Evaluation**
- Identified projects with more than 10% of their funding from external partners.
- Sample projects:
  - Archive Facility Renovations
  - Underground Lighting Conduit Installations
- Illustrated how public-private collaborations strengthen municipal investment capabilities and reduce risk.

### ✅ **Tools and Technologies**
- **Data Querying**: Amazon Athena (SQL)
- **Metadata & Tables**: AWS Glue Data Catalog
- **Data Storage**: Amazon S3
- **ETL & Crawling**: AWS Glue Crawlers
- **Documentation**: AWS Console Screenshots, SQL scripts

---

### ✅ **Deliverables**
- SQL queries used in Athena for budget analysis
- Athena query logs and screenshots
- Visuals of the most expensive, forecasted, and partner-supported projects
- Analytical report summarizing key budgetary insights

---

### ✅ **Conclusion**
The diagnostic analysis phase provided actionable financial insights from the cleaned and cataloged dataset. Key patterns in capital expenditure reveal Vancouver’s evolving priorities—shifting from housing in 2024 to infrastructure in 2025. The analysis also illustrates how funding sources are balanced between internal city finances and external contributions, supporting more resilient and collaborative public project management.

This diagnostic work reinforces the role of AWS cloud tools in enabling transparent, data-driven planning for urban infrastructure and public investment strategy.

> 📌 _Tip: Link Athena query screenshots and SQL scripts directly in your GitHub repo for reference._

