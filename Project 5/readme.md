# Data Wrangling

## Project Title:  
**Data Wrangling and Transformation Using AWS Glue DataBrew for **

---

## Objective:  
To transform and standardize a capital budget request dataset by addressing data quality issues, ensuring consistent formatting, and preparing it for downstream analysis and reporting.

---

## Background:  
Following data profiling, key quality issues were identified such as inconsistent column naming and special characters in textual fields. Data wrangling was implemented to clean, format, and partition the dataset to meet the analytical and reporting requirements of stakeholders.

---

## Dataset:  
- **Source**: AWS S3 bucket (`budgetrequest-raw-my`)  
- **File Type**: CSV  
- **Size**: 592 records, 20 columns  
- **Key Fields**:  
  - `ProjectId`: Unique project identifier  
  - `ProjectProgramName`: Name of the capital project  
  - `ServiceCategory1`: Main public service area  
  - `TotalOpenProjectBudgetIn2024`: Budget allocated for 2024  
  - `MultiYearCapitalProjectBudgetsPreviouslyApproved`: Budget from previous fiscal years  
  - `DeliveryDepartment`: Executing department  
  - `CommunityPriority`: Community relevance flag

---

## Methodology:

### Common Issues Addressed:
- Missing values  
- Duplicates  
- Inconsistent formats (e.g., date or currency formats)  
- Unnecessary whitespace or special characters  
- Irrelevant columns  
- Inconsistent or redundant category names  

### Steps:

1. **Data Preparation in AWS S3**  
   - Created a transformed S3 bucket named `budgetrequest-trf-my` with `/system` and `/user` directories.

2. **Cleaning and Formatting with AWS Glue DataBrew**  
   - Initiated a cleaning project: `budgetrequest-cln-my`  
   - Removed special characters from `ProjectProgramName`.  
   - Converted all column names to **camelCase** for standardization.

3. **Output Configuration**  
   - **CSV Output**:  
     - Overwrites file for each job run  
     - Stores single consolidated output in `/user` folder  
   - **Parquet Output**:  
     - Enables columnar storage format  
     - Configured partitioning by `ServiceCategory1`, `ServiceCategory2`, and `ServiceCategory3`  
     - Allows efficient querying for large-scale analytics

4. **Storage and Validation**  
   - Final outputs stored in the transformed S3 bucket  
   - Verified structure via AWS Glue and S3 object browser

---

## Tools and Technologies:  
- **AWS Glue DataBrew** – Visual tool for data transformation and profiling  
- **AWS S3** – Storage for raw and processed datasets  
- **IAM (LabRole)** – Permissions for Glue access  
- **Parquet & CSV** – Chosen output formats for flexibility and performance  
- **Draw.io** – Used for architecture and workflow diagrams

---

## Deliverables:  
- Cleaned dataset in **CSV** and **Parquet** formats  
- Partitioned Parquet output for scalable analysis  
- Project configuration in AWS Glue DataBrew  
- Architecture and flow diagrams  
- Standardized, camelCase column headers  
- Outputs accessible in `budgetrequest-trf-my` S3 bucket

---

## Timeline:  
- **Week 1** – Data profiling and quality assessment  
- **Week 2** – Design of transformed S3 structure and configuration in Glue DataBrew  
- **Week 3** – Execution of cleaning jobs and generation of CSV output  
- **Week 4** – Configuration of Parquet outputs and validation of partitions  
- **Week 5** – Compilation of deliverables and documentation
