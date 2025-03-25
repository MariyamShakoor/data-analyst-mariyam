# Automated Data Ingestion As a Part of Migration of UCW to AWS Cloud
# Project 1: Automated Data Ingestion for Academic Accommodation for Students with Accessibility Needs at UCW (5051 p) (#)


---

## Objective
To automate and standardize the ingestion, profiling, and management of academic accommodation datasets for students with accessibility needs, aligned with UCW Procedure 5051p. The project enhances data quality, governance, and accessibility for administrative decision-making and compliance tracking.

---

## Datasets Used
- **Student_Information_List.csv** – Contains basic student information.
- **Academic_Accommodation_Letter_Dataset.csv** – Holds accommodation implementation status by student.
- **Appeals_Information_Dataset.csv** – Records accommodation-related appeal types.

---

## Methodology
### 1. Data Upload & Organization
- Used PowerShell with `Write-S3Object` to upload datasets into structured Amazon S3 buckets.
- Followed naming convention:
  ```
  accomodation/<list-type>/year=2025/quarter=01/month=1/server=AGVS-My/
  ```

### 2. Cloud Storage & Access Control
- Stored all datasets in Amazon S3.
- Ensured data traceability and security using key naming standards.

### 3. Schema Mapping
- Established relationships:
  - `StudentID` as primary key across all datasets
  - Accommodation and appeals linked with one-to-one or one-to-many references

### 4. Data Architecture
- Centralized infrastructure in EC2 + VPC environment (AGVS-My)
- Access given to:
  - Academic Operations Team
  - Data Analytics Team

---

## Tools & Technologies
- **AWS S3** – Cloud storage
- **PowerShell / AWS CLI** – Data automation
- **Amazon EC2 + VPC** – Secure compute
- **CSV** – Data format

---

## Deliverables
- Amazon S3 structured folders with data
- System architecture diagram
- Entity-relationship mapping (ERD logic)
- Screenshots of all key steps

---

## Screenshots to Include
- PowerShell commands (Write-S3Object)
- S3 bucket folder structures
- Architecture diagram showing EC2, S3, users, datasets

---

## Key Learning Outcomes
- Designed and implemented a cloud-native data ingestion pipeline
- Applied institutional policy (UCW Procedure 5051p) to technical workflows
- Practiced automation and secure AWS storage
- Demonstrated the ability to manage education-related data responsibly

---

## Repository Structure (Suggested)
```
├── data-samples/
│   ├── Student_Information_List.csv
│   ├── Academic_Accommodation_Letter_Dataset.csv
│   └── Appeals_Information_Dataset.csv
├── scripts/
│   └── upload-to-s3.ps1
├── screenshots/
│   ├── powershell-upload.png
│   ├── s3-folder-structure.png
│   └── system-architecture.png
├── architecture/
│   └── academic-data-ingestion-diagram.png
├── README.md
```

---

# Project 2:  Data Wrangling for Academic Accommodations (Procedure 5051p)

## Project Title  
**Data Wrangling for Academic Accommodation and Appeal Records Using AWS (Procedure 5051p Compliance)**

## Project Description  
This project focuses on comprehensive data wrangling to clean, transform, and unify academic accommodation and appeal records for students with accessibility needs, in compliance with **Procedure 5051p**. Leveraging AWS services such as S3, Glue DataBrew, Athena, and Glue Catalog, the objective is to create a reliable, analysis-ready dataset that supports institutional decision-making, compliance reporting, and student service optimization.

---

## Objective  
The primary goal of this project is to perform data profiling, cleaning, and transformation across multiple CSV and TXT datasets related to student accommodations, appeals, and system logs. The final output is a consolidated, high-quality dataset that reflects accurate records for accessibility services and supports downstream analytics, including equity audits and policy planning.

---

## Background  
Academic institutions are expected to maintain precise, transparent records for students requiring academic accommodations. However, this data often resides in fragmented files or databases, leading to inconsistencies and data quality issues. This project directly supports **Procedure 5051p: Academic Accommodation for Students with Accessibility Needs**, ensuring that accommodation and appeal data is reliable, accessible, and actionable through cloud-based wrangling practices.

---

## Dataset Description  

| Dataset Name                     | Description                                                  |
|----------------------------------|--------------------------------------------------------------|
| `StudentInformationList.csv`     | Basic student records with IDs and names                     |
| `AcademicAccommodationsList.csv` | Accommodation types and implementation status               |
| `AppealsInformationList.csv`     | Appeal IDs, types, and linked student IDs                    |
| `AccommodationUserLog.txt`       | Raw log of user access to the accommodation platform         |

---

## ⚙️ Methodology

### 1. **Data Collection**  
- Upload CSV and TXT files to Amazon S3 (`academics-raw-my` bucket)  
- Define folder structure by file type, server, and timestamp  
- Enable lifecycle rules for archival in Glacier Instant Retrieval  

### 2. **Data Assessment**  
- Use AWS Glue DataBrew for initial profiling  
- Review for missing values, duplicate rows, incorrect formats, and type mismatches  
- Document column types, key fields, and invalid entries  

### 3. **Data Cleaning**  
- Remove duplicate entries  
- Impute or handle missing values appropriately  
- Standardize column formats (dates, text casing, etc.)  
- Normalize categorical values (e.g., appeal status = Active/Closed)  

### 4. **Data Transformation**  
- Convert date strings to datetime objects  
- Derive new fields such as:
  - `AccommodationDuration`
  - `AppealStatusFlag`  
- Aggregate logs for access count per student  

### 5. **Data Consolidation**  
- Join datasets using `StudentID`, `AppealID`, and `RecordDate` as keys  
- Create a unified master dataset for institutional reporting and analysis  

### 6. **Documentation and Validation**  
- Record all transformation steps via Glue DataBrew recipes  
- Validate final dataset using exploratory analysis in Athena  
- Create data quality summary matrix (Invalid, Outdated, Outliers, Missing, Type Issues)  

---

## Tools and Technologies  

| Tool                | Use Case                                |
|---------------------|------------------------------------------|
| **Amazon S3**        | Raw and cleaned dataset storage         |
| **AWS Glue DataBrew**| Profiling, transformation, cleaning     |
| **Amazon Athena**    | SQL-based querying and validation       |
| **AWS Glue Catalog** | Schema definitions and data cataloging  |
| **Amazon EC2**       | Host platform for visual architecture   |


---

## Deliverables  

- A fully cleaned and consolidated academic accommodations dataset (CSV format)  
- Glue DataBrew recipes for cleaning, profiling, and transformation  
- ERD and AWS architecture diagrams  
- Data quality reports and heatmaps   

---

## Timeline  

| Week | Milestone                                      |
|------|-----------------------------------------------|
| 1    | Dataset ingestion into S3 & folder setup       |
| 2    | Data profiling using Glue DataBrew             |
| 3    | Data cleaning and normalization                |
| 4    | Transformation and feature engineering         |
| 5    | Data merging and validation using Athena       |
| 6    | Documentation, reporting, and project delivery |

---

## Insights & Impact  

- Supported data governance aligned with Procedure 5051p  
- Enabled accurate tracking of accommodation implementation status  
- Improved data reliability for accessibility services, audits, and reporting  
- Identified duplicate, outdated, and incomplete entries using Glue profiling  

---

# Data Enrichment
# Project 3: Automated Academic Accommodation Data Enrichment (Procedure 5051p)



## 🎯 Objective
This project focuses on enrichment and managing datasets related to academic accommodations for students with accessibility needs at a university, based on **Procedure 5051p**. The aim is to provide a clean, accessible, and queryable metadata layer using AWS Data Catalog, enhancing the usability of accommodation, appeals, and student records data across AWS S3 storage.

## 🗃️ Background
Universities store data on student accommodations, appeals, and services across various logs and systems. Manual management of this data is error-prone, lacks consistency, and limits accessibility for analytics or compliance. AWS Glue and S3 provide a scalable solution to automate metadata extraction, manage schema changes, and support downstream applications through cataloged datasets.

## Datasets Involved
- **Student Information List**
- **Academic Accommodations List**
- **Appeals Information List**
- **Accommodation Letter List**
- **Student Log Files (ASVS & AWA servers)**

## Tools and Technologies
- **AWS Glue** (Data Catalog, Crawler, and ETL Visual Editor)
- **Amazon S3** (Raw and curated storage layers)
- **AWS Glue DataBrew** (Data Profiling and Cleaning)
- **Parquet Format** (Optimized storage)
- **IAM** (for access control)
- **Python (optional)** for custom transformation scripts

## Implementation Steps

### 1. Data Ingestion
- Upload raw data from various sources (CSV, logs, form submissions) into Amazon S3 under designated buckets: `academics-raw-my` and `academics-cur-my`.

### 2. Data Profiling & Cleaning
- Used **AWS Glue DataBrew** to:
  - Profile datasets (check for missing, invalid, duplicate values)
  - Clean datasets (remove inconsistencies, format columns)
  - Run recipe jobs for each dataset (e.g., `acad-stud-info-cln-my`, `acad-acomm-lst-cln-my`)

### 3. Data Cataloging
- Created **AWS Glue Crawlers** for each dataset to:
  - Automatically infer schema
  - Create tables in the `academics-data` and `academics-cur-my` databases
- Table examples:
  - `stud-list-metrics`
  - `accomod-letter-list-metrics`
  - `appeal-info-list-metrics`
  - `acad_accomm_trfsystem`

### 4. Data Transformation (Optional)
- Designed **Visual ETL Jobs** using AWS Glue Studio for:
  - Summarizing metrics (e.g., Follow-up needed in Appeals)
  - Merging datasets
  - Creating clean outputs in S3 as Parquet files

### 5. Data Storage and Lifecycle Management
- Applied **S3 Lifecycle Rules** to archive old raw data (Glacier Instant Retrieval)
- Maintained versioned folders for job outputs (e.g., `Report_Date=2025-02-09`)

## Outputs
- Cleaned and cataloged Parquet datasets, queryable via Athena or Redshift Spectrum
- Metrics dashboards derived from summarized ETL outputs
- Traceable S3 logs from `ASVS` and `AWA` servers

## Example Use Cases
- Faculty can quickly access accommodations data for course planning
- Accessibility officers can generate compliance reports
- Analysts can visualize accommodation trends and appeal outcomes

## Status
✔️ Data cataloging and profiling complete  
✔️ Recipe jobs executed for all datasets  
✔️ Crawlers and ETL jobs deployed  
✔️ Visual workflows created and outputs stored in `academics-cur-my`  

## Folder Structure
academics-raw-my/ ├── accomodation/ │ ├── user-log/ │ └── accommodation-user-log.txt ├── appeals/ │ └── raw.csv

academics-cur-my/ ├── appeal-information-list/ │ └── Report_Date=2025-02-09/ ├── accommodation-letter-list/ │ └── metrics/ │ └── system/ │ └── approvedaccommodations-*.csv

## Screenshots
Included:
- Glue ETL visual jobs
- DataBrew profiles
- Crawler outputs
- S3 output reports
---
# Diagnostic Analysis for Capital Budget Forecasting – City of Vancouver
## Project 4: Capital Budget Forecast Analysis for the City of Vancouver Using AWS Athena

## Objective:  
The primary objective is to analyze the City of Vancouver’s multi-year capital budget data to extract actionable insights that support strategic financial planning. Using Amazon Athena, the project delivers comprehensive evaluations of spending priorities, funding distributions, and partner contributions for capital projects planned between 2024 and 2026.

## Background:  
The City of Vancouver allocates substantial resources to long-term capital projects, including infrastructure, housing, and public amenities. Understanding where and how these funds are distributed is critical for effective governance and transparency. This project enables high-level analysis using serverless SQL querying via Amazon Athena, offering fast, flexible access to clean budget datasets stored on AWS. This project focuses on implementing an automated data governance mechanism by conducting data quality checks on datasets stored in Amazon S3. Leveraging AWS Glue Studio, a visual ETL pipeline named budgetrequest-QC-My was developed to assess data completeness and uniqueness. The pipeline routes quality-passed and failed data to designated folders, ensuring efficient data organization and optimizing storage for scalable analytics.


## Dataset:  
The analysis uses the following dataset:

- **2024 Multi-Year Capital Project Budget Requests and Capital Expenditure Budget**  
  Key fields include:  
  • `projectprogramname`  
  • `annualcapitalexpenditure2024capitalexpenditurebudget`  
  • `annualcapitalexpenditure2025forecast`  
  • `forecast_2026`  
  • `funding_source`  
  • `partner_contribution`  
  • `approved_budget` vs `requested_budget`

## Methodology:

### 1– Data Collection:  
- The dataset was accessed through AWS Athena after being cataloged in AWS Glue.  
- Database: `budgetrequest-catalog-my`  
- Tables: `budgetrequest-trf_system`, `budgetrequest-metrics`  
- Query results were stored in `s3://budgetrequest-cur-my`.

### 2– Data Analysis Strategy:  
The following queries were performed using SQL in Athena:

- **Most Expensive Capital Projects (2024 & 2025):**  
  Identified top-budgeted projects by sorting 2024 actuals and 2025 forecasts in descending order.  
  📍 *Results:*  
  - 2024: *2023–2026 Housing Land Acquisition* – ~$39.82M  
  - 2025: *PNE Amphitheatre* – ~$74.98M  

- **Forecasted Expenditure Trends (2024–2026):**  
  Analyzed budget allocations across the top 10 projects for three consecutive years to identify trend patterns.  
  📍 *Top Projects:*  
  - Housing Land Acquisition  
  - Coal Harbour – Housing  
  - PNE Amphitheatre

- **Comparative Budget Analysis (Requested vs Approved – 2024):**  
  Compared the difference between newly requested and previously approved budgets for each project.  
  📍 *Key Insights:*  
  - Significant increases seen in *New Land for Parks*, *Distribution Main Replacement*, and *Drinking Water Demand Management*.  
  - New projects like *Permanent Public Plazas* had no prior funding but received large new requests.

- **Funding Source Analysis:**  
  Broke down the top 10 projects by their funding sources:  
  - Pay-as-you-go  
  - Debt financing  
  - Reserve funds  
  - Partner contributions  
  📍 *Findings:*  
  - Infrastructure-heavy projects (e.g. *Sewer Main Renewal – Balaclava Catchment Area*) rely on debt.  
  - Others (e.g. *Distribution Main Replacement*) are fully internally funded.

- **Partner Contribution Evaluation:**  
  Selected projects where external partner funding exceeds 10% of the total budget.  
  📍 *Examples:*  
  - *Underground Lighting Conduit*  
  - *Archive Facility Renovation*

### 3– Documentation and Interpretation:  
- Insights were compiled into structured tables, figures, and summaries.  
- Strategic interpretations supported planning decisions around funding, scheduling, and community partnership initiatives.  
- Screenshots of SQL queries and results from Athena were included in the project report.

## Tools and Technologies:
- **Amazon Athena** – SQL querying  
- **AWS Glue Data Catalog** – Metadata registry  
- **Amazon S3** – Query result and data storage  
- **SQL** – Analytical queries  
- **AWS Console** – Service management and screenshots

## Deliverables:
- SQL scripts for all five analytical dimensions  
- Summary report of capital budgeting insights  
- Tables of top-funded projects, funding breakdowns, and year-wise projections  
- Athena console screenshots of query results  
- Final result dataset stored in Parquet format in Amazon S3

## Timeline:
- **Week 1** – Catalog setup and environment configuration  
- **Week 2** – Query development in Athena  
- **Week 3** – Insight extraction and result interpretation  
- **Week 4** – Documentation, reporting, and visualization

This project enables the City of Vancouver to make informed decisions about capital planning and funding strategy through robust, cloud-based budget analysis.
--

# Data Quality Management Pipeline in AWS  
#**Project 5: A Visual ETL Approach for Scalable Data Governance**

## Project Overview
This project implements an automated pipeline for ensuring data quality and governance using **AWS Glue Studio** and **Amazon S3**. The pipeline performs completeness and uniqueness checks on datasets stored in S3, then segregates and stores validated and invalidated data into separate locations to maintain quality standards and enable structured data governance.

---

## Objectives
- Automate data quality checks using AWS Glue visual workflows.
- Implement structured routing for quality-verified and rejected data.
- Maintain scalable data governance through organized S3 storage.

---

## Architecture Components

- **Raw Input Bucket**: `s3://budgetrequest-raw-my`
- **Transformed Output Bucket**: `s3://budgetrequest-trf-my/Quality_Check/`
  - Subfolders:
    - `Passed/`
    - `Failed/`
- **ETL Job Name**: `budgetrequest-QC-My` (AWS Glue Studio Visual Job)
- **Execution Role**: `LabRole` with permissions for S3 and Glue operations

---

## Data Quality Rules

| Rule Type     | Field                  | Condition                            |
|---------------|------------------------|--------------------------------------|
| Completeness  | Service_Category_3     | ≥ 95% non-null values                |
| Uniqueness    | Project/Program_Name   | ≥ 99% unique values                  |
| Freshness     | Not applied            | Dataset does not include timestamps  |

---

## Pipeline Workflow

1. **Data Ingestion**  
   Raw CSV data is loaded from `budgetrequest-raw-my` into AWS Glue Studio.

2. **Quality Evaluation**  
   The **Evaluate Data Quality** transform is used to apply defined rules. Quality outcomes are stored in additional columns.

3. **Conditional Routing**  
   Records are routed using the **ConditionalRouter**:
   - Records marked as “Passed” are grouped under `quality_passed`.
   - All other records are sent to the `default_group`.

4. **Schema Adjustment**  
   The **Change Schema** transform removes quality indicator columns from the passed dataset to maintain clean structure and reduce storage overhead.

5. **Partitioning & Output**  
   The **Autobalance Processing** node is configured to write each dataset as a single CSV file. Outputs are directed to:
   - `s3://budgetrequest-trf-my/Quality_Check/Passed/`
   - `s3://budgetrequest-trf-my/Quality_Check/Failed/`

---

## Result Summary

- **Total Records Evaluated**: 200  
- **Records Passed**: 195  
- **Records Failed**: 5

---

## Folder Structure

--
# Data Lake Security Implementation for the City of Vancouver  
**Ensuring Confidentiality, Integrity, and Availability for 2024 Capital Project Budget Data**

## 📘 Overview
This project implements a comprehensive data security architecture for the **City of Vancouver’s 2024 Multi-Year Capital Project Budget Requests and Capital Expenditure Budget**. The solution uses AWS-native services to protect data at rest and in transit within a multi-zone **data lake** environment, ensuring compliance with the **CIA triad**: Confidentiality, Integrity, and Availability.

---

## 🎯 Objective
To secure and govern sensitive financial datasets related to the City of Vancouver’s capital planning by leveraging:
- AWS Key Management Service (KMS)
- Amazon S3 bucket encryption
- S3 bucket versioning
- Cross-region replication

---

## 🛠️ Architecture Components

### 🔐 Key Management – AWS KMS
- **Key Type**: Symmetric
- **Key Name**: `budgetrequest-key-my`
- **Role Permissions**: 
  - `LabRole` assigned permissions to create, rotate, and use the key
- **Usage**: Encrypts and decrypts all data within the following S3 buckets:
  - `budgetrequest-raw-my`
  - `budgetrequest-cur-my`
  - `budgetrequest-trf-my`

---

### 🪣 S3 Bucket Encryption (Confidentiality)
All relevant buckets are configured to use server-side encryption with the KMS-managed key:

| Bucket Name              | Zone         | Encryption Type                |
|--------------------------|--------------|--------------------------------|
| budgetrequest-raw-my     | Raw          | SSE-KMS (`budgetrequest-key-my`) |
| budgetrequest-cur-my     | Curated      | SSE-KMS (`budgetrequest-key-my`) |
| budgetrequest-trf-my     | Transformed  | SSE-KMS (`budgetrequest-key-my`) |

---

### 📄 S3 Bucket Versioning (Integrity)
Versioning is enabled to protect against accidental deletion or overwrites, allowing data rollback when needed.

| Bucket Name              | Versioning Status |
|--------------------------|-------------------|
| budgetrequest-raw-my     | Enabled           |
| budgetrequest-cur-my     | Enabled           |
| budgetrequest-trf-my     | Enabled           |

---

### 🌐 S3 Replication (Availability)
Data is automatically replicated to backup buckets to ensure high availability and disaster recovery capability.

| Source Bucket            | Destination Bucket       | Encryption | Versioning | Replication Rule |
|--------------------------|--------------------------|------------|------------|------------------|
| budgetrequest-raw-my     | budgetrequest-raw-bac-my | KMS-Enabled| Enabled    | budgetrequest-rep-rul-my |
| budgetrequest-cur-my     | budgetrequest-cur-bac-my | KMS-Enabled| Enabled    | budgetrequest-rep-rul-my |
| budgetrequest-trf-my     | budgetrequest-trf-bac-my | KMS-Enabled| Enabled    | budgetrequest-rep-rul-my |

- Scope: Applies to all new objects (existing objects not replicated)
- Secure replication of encrypted files with KMS key support

---

## 🗂️ Folder and Bucket Layout

|-- budgetrequest-raw-my/ |-- budgetrequest-cur-my/ |-- budgetrequest-trf-my/ |-- budgetrequest-raw-bac-my/ |-- budgetrequest-cur-bac-my/ |-- budgetrequest-trf-bac-my/ |-- kms/ (AWS Key: budgetrequest-key-my)

---

## 🛡️ Security Outcomes

- **Confidentiality**: All data encrypted using a customer-managed KMS key
- **Integrity**: Versioning ensures historical data retention and change tracking
- **Availability**: Cross-region replication ensures data redundancy and resilience

---

## 📁 Dataset Secured
- **2024 Multi-Year Capital Project Budget Requests**
- **Capital Expenditure Budget**  
These datasets contain sensitive financial planning data critical to city infrastructure and investment initiatives.

---

## 👨‍💼 Developed By
[Your Name or Team Name]  
[Institution or Organization Name]  
March 2025

