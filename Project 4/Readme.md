#Project 4 (DATA BREW)
# 📘 README: Data Wrangling for Academic Accommodation Dataset (UCW - Procedure 5051p)

---

### ✅ **Project Title**  
**Data Wrangling and Transformation of Academic Accommodation Data under UCW Procedure 5051p**

---

### ✅ **Project Description**  
This project is a key component of the broader cloud-based academic data infrastructure established by University Canada West (UCW) to ensure compliance with **Procedure 5051p: Academic Accommodations for Students with Accessibility Needs**. The wrangling process supports reliable academic data analytics by transforming and validating raw CSV files into structured, high-quality datasets for use in reporting, compliance audits, student accessibility tracking, and internal decision-making.

Raw data is collected through PowerShell-enabled ingestion pipelines and stored in an Amazon S3 bucket (`academics-raw-my`) in a structured path format. These raw datasets are then profiled, cleaned, and standardized using AWS Glue DataBrew recipe jobs. Once validated, the cleaned versions are stored in `academics-trf-my` under appropriate Cleaned and Errors subfolders. This pipeline enables UCW to ensure data quality and readiness for governance, visualization, and research workflows.

---

### ✅ **Objective**  
The objective of this phase is to ensure that all datasets ingested from the academic operations environment—namely student information, accommodation letters, and appeal records—are transformed into clean, consistent, and validated formats. These cleaned datasets support downstream use in analytical platforms (Athena, Redshift) and ensure that UCW maintains data integrity and traceability across all records related to academic accommodations.

---

### ✅ **Dataset**
The following datasets were ingested into Amazon S3 and wrangled:

- **Student-Information-List.csv**  
  Contains unique identifiers (`StudentID`), student names, and education level.

- **Academic_Accommodation_Letter_Dataset.csv**  
  Contains `StudentID`, `LetterID`, and details about the implementation or type of academic accommodations offered to students.

- **Appeals_Information_Dataset.csv**  
  Contains `StudentID`, `AppealID`, and `AppealType`, used to track formal requests for reconsideration of accommodation decisions.

These datasets are versioned using metadata folders: `year=2025/quarter=01/month=01/server=AGVS-My`. All three share `StudentID` as a common key for cross-referencing.

---

### ✅ **Methodology**

#### 🔍 1. Data Profiling
Data profiling jobs were created using **AWS Glue DataBrew** to analyze and audit the structure and quality of each dataset before cleaning:

- No missing values were detected in any of the datasets
- All fields were correctly typed (primarily STRING format)
- Uniqueness of primary keys (`StudentID`, `LetterID`, `AppealID`) was verified
- Distribution of categorical and string values was within expected ranges

**Profile Job IDs:**
- `acad-stud-info-ds-prf-my`
- `acad-acomm-lst-ds-prf-my`
- `acad-app-info-list-ds-prf-my`

#### 🧽 2. Data Cleaning and Recipe Execution
Three recipe jobs were created and run successfully. These recipes executed transformations including:
- Renaming of fields (e.g., StudentID → student_id)
- Trimming whitespaces from string values
- Lowercasing of all string columns for consistency
- Removal of any accidental metadata headers or footers
- Null value handling (none found in this case)
- Validation of `StudentID` consistency across all three datasets

**Recipe Job IDs:**
- `acad-stud-info-cln-my`
- `acad-acomm-lst-cln-my`
- `acad-app-info-list-cln-my`

Each dataset’s cleaned output was saved to a **Cleaned** folder in S3, while records failing validation or requiring audit were directed to the **Errors** folder (currently no errors reported).

#### 📁 3. Output Folder Structure in Amazon S3
Organized under the `academics-trf-my` bucket:

```
s3://academics-trf-my/
├── student-information-list/
│   ├── Cleaned/    # Profiled and cleaned dataset
│   └── Errors/     # Error-handled or rejected entries (currently empty)
├── academic-accomodation-letter-list/
│   ├── Cleaned/
│   └── Errors/
├── appeal-information-list/
│   ├── Cleaned/
│   └── Errors/
```

#### 🧾 4. Schema Validation and Consistency Checks
- All three datasets were validated to share the `StudentID` field, enabling joins
- Additional checks for duplicate rows and schema mismatches were performed and passed
- Custom formats were enforced (e.g., lower_case_snake_format for column names)
- A comprehensive diagram was created to map entity relationships

---

### ✅ **Tools and Technologies**
- **AWS Glue DataBrew**: For data profiling, recipe creation, and job orchestration
- **Amazon S3**: Raw and cleaned data storage (academics-raw-my / academics-trf-my)
- **PowerShell & AWS CLI**: For dataset ingestion and folder structuring
- **IAM Roles (LabRole)**: To manage job permissions and access policies
- **EC2 Server Environment**: Operational virtual machines for ingestion and logging

---

### ✅ **Deliverables**
- 📁 Three profiled and cleaned datasets in the S3 `academics-trf-my` bucket
- 📄 Profiling reports and logs from Glue DataBrew for each dataset
- 📂 Structured folder hierarchy for Cleaned and Error records
- 🧾 Validated schema map and data dictionary
- 📊 Ready-to-query datasets compatible with Athena and Redshift

---

> 📌 _Note: All raw datasets remain preserved in the S3 bucket `academics-raw-my`, in compliance with UCW data retention policy._

