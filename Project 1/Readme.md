#Project 1
![System Diagram](Project%201/images/Screenshot%202025-02-02%20135035.png)

# 📘 README: Data Wrangling & Analysis on Vancouver Capital Budget Dataset

---

### ✅ **Project Title**  
**Data Analytics Platform (DAP) Design and Implementation for the City of Vancouver Capital Budget Dataset**

---

### ✅ **Project Description**  
This project showcases a cloud-based data wrangling and analytics workflow applied to the *2024 Multi-Year Capital Project Budget Requests and Capital Expenditure Budget* dataset. The solution ensures structured data transformation using AWS services, enabling financial transparency and strategic planning for the City of Vancouver. This project involves the preparation, organization, and analysis of the 2024 Multi-Year Capital Project Budget Requests and Capital Expenditure Budget dataset released by the City of Vancouver. The dataset includes vital information about proposed capital projects, funding sources, previously approved budgets, and forecasted spending from 2024 to 2028. The main objective is to clean, structure, and examine the data to uncover patterns in funding requests, identify priority service areas, and assess the city’s financial planning strategies. By transforming the raw dataset into a clear and analyzable format, this project supports better decision-making and transparency in municipal budgeting and long-term capital investment planning.

---

### ✅ **Objective**  
To design and implement a robust Data Analytics Platform (DAP) using AWS that transforms raw municipal budget data into structured, high-quality datasets for analysis, forecasting, and visualization.

---

### ✅ **Dataset**  
- **Source**: City of Vancouver Open Data Portal  
- **Title**: 2024 Multi-Year Capital Project Budget Requests and Capital Expenditure Budget  
- **Records**: 592 rows across 20 columns  
- **Key Fields**:
 1. **Project/Program Name** – Name or description of the capital project or program.  
2. **Service Category 1, 2, 3** – Hierarchical classification of the project’s service area.  
3. **Previously Approved Budget** – Funds approved in prior capital plans.  
4. **2024 Budget Request** – New funding requested for the project in 2024.  
5. **Total Open Budget in 2024** – Total available funds for the project in 2024.  
6. **Spending Forecast till 2023** – Expected project spending by the end of 2023.  
7. **Available Budget in 2024** – Remaining funds available to spend in 2024.

---

### ✅ **Methodology (Detailed)**

#### 1. **Data Ingestion**
- Raw CSV dataset uploaded to **Amazon S3 bucket** `budgetrequest-raw-my`.
- Centralized storage in the `us-east-1` region enabled seamless downstream processing.

#### 2. **Data Profiling**
- Conducted using **AWS Glue DataBrew**:
  - 99% of data was valid with minimal missing values
  - Profiling displayed data types, distributions, and variable correlations
  - Insights into budget distribution across 13 major service categories

#### 3. **Data Cleaning**
- Executed via **Glue DataBrew cleaning job** `budgetrequest-cln-my`:
  - Missing values were addressed through removal or imputation
  - Standardized formats and corrected data types
  - Exported cleaned datasets in `.csv` and `.parquet` formats to the `budgetrequest-trf-my` S3 bucket

#### 4. **Data Cataloging**
- **AWS Glue Crawler** scanned cleaned datasets to generate metadata
- Tables registered in **Glue Data Catalog**:
  - `budgetrequest-trf_system`
  - `budgetrequest-metrics`
- Enabled integration with **Amazon Athena** and **Redshift**

#### 5. **Data Summarization**
- Used **AWS Glue Studio Visual ETL** job (`budgetrequest-summarization`) to:
  - Filter projects with approved budgets only
  - Aggregate data by service category
  - Produce user/system-level summaries
  - Outputs saved in `budgetrequest-cur-my` bucket for analysis

#### 6. **Storage Lifecycle Configuration**
- Implemented S3 lifecycle rules:
  - First 45 days in **S3 Standard**
  - Then moved to **S3 Glacier Instant Retrieval**
- Enabled cost-optimized, long-term data storage while maintaining accessibility

---

### ✅ **Tools and Technologies**
- **Cloud Storage & Compute**: Amazon S3, AWS Glue, AWS Glue Studio
- **Data Wrangling**: AWS Glue DataBrew
- **Metadata Management**: AWS Glue Data Catalog, Glue Crawlers
- **Querying & Reporting**: Amazon Athena
- **ETL Visualization**: Glue Studio (Visual Flow)
- **Documentation & Design**: Draw.io, AWS Console Screenshots

---

### ✅ **Deliverables**
- 📁 Cleaned, profiled, and summarized datasets (CSV & Parquet)
- 📊 AWS Glue Data Catalog with metadata tables
- 🔄 Visual ETL jobs for summarization and cleaning
- 🗃️ Lifecycle-managed storage using S3 Glacier
- 📄 Comprehensive documentation with architecture diagrams and AWS interface screenshots

---

### ✅ **Key Insights**
- Budget distribution was right-skewed with a few high-cost projects
- Pay-as-you-go funding is prevalent for smaller budgets, while debt funding dominates larger ones
- Highest number of projects were proposed under "Parks & Public Spaces" and "Housing"

---

### ✅ **Conclusion**
This project demonstrates a fully functional cloud-native data analytics pipeline tailored for municipal budget data. It highlights real-world applications of AWS services in data ingestion, preparation, profiling, storage, and summarization — positioning it as a model for scalable and transparent data governance in public sector analytics.

The implementation> 📌 _Note: Replace placeholder image links in GitHub with your actual AWS screenshots for production-ready documentation._
