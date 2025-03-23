# Migration of UCW to AWS Cloud
# Project 1: Automated Data Ingestion for Academic Accommodation for Students with Accessibility Needs at UCW (5051 p)


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


# Project 3: Automated Academic Accommodation Data Cataloging (Procedure 5051p)



## 🎯 Objective
This project focuses on cataloging and managing datasets related to academic accommodations for students with accessibility needs at a university, based on **Procedure 5051p**. The aim is to provide a clean, accessible, and queryable metadata layer using AWS Glue Data Catalog, enhancing the usability of accommodation, appeals, and student records data across AWS S3 storage.

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
