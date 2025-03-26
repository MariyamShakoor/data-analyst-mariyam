
# Project 3: Automated Data Ingestion for UCW Academic Accommodation under Procedure 5051p

---

### **Project Title**
**Automated Data Ingestion for Academic Accommodation Requests at UCW using AWS S3**

---

### **Project Description**
This project is part of a university-wide initiative to modernize UCW’s data infrastructure supporting **academic accommodations** for students with accessibility needs. Aligned with **UCW Procedure 5051p**, this initiative introduces a fully automated and auditable system for ingesting academic accommodation records into AWS S3 using PowerShell and structured folder hierarchy.

The system is built to ensure secure, version-controlled delivery of critical datasets like **Student Information**, **Academic Accommodation Letters**, and **Appeals Information** from the operational EC2 server to a central S3-based data lake. These datasets serve multiple stakeholders including Academic Operations, Accessibility Services, and the Registrar’s Office. This process forms the first step in a broader academic data pipeline supporting compliance, analytics, and service improvement.

---

### **Objective**
The core objective is to establish a secure, consistent, and metadata-tagged ingestion mechanism to automate the transfer of CSV datasets to the AWS S3 data lake. The pipeline supports traceability, temporal classification (by year/quarter/month), and reliable correlation across academic records via shared identifiers (e.g., `StudentID`).

---

### **Datasets**

#### 📄 Student-Information-List.csv
- **Description**: Core student registry file
- **Fields**: 
  - `StudentID`: Unique identifier (Primary Key)
  - `FullName`: Student's full name
  - `LevelID`: Educational program level

#### Academic_Accommodation_Letter_Dataset.csv
- **Description**: Details of approved academic accommodations
- **Fields**:
  - `StudentID`: Links to the student registry
  - `LetterID`: Unique accommodation letter identifier
  - `ImplementationDetails`: Notes about the implementation process

#### Appeals_Information_Dataset.csv
- **Description**: Student-initiated appeals related to accommodation
- **Fields**:
  - `StudentID`: Foreign Key from student registry
  - `AppealID`: Unique appeal entry
  - `AppealType`: Nature of appeal (e.g., review request, modification)

---

### **Design**


---

### **Data Storgae in S3**

Each dataset is ingested using precise versioned folder keys that track origin, year, quarter, and upload server. This structure supports auditing, retention management, and future pipeline extensibility.

```plaintext
academics-raw-my/
├── accomodation/
│   ├── student-information-list/
│   │   └── year=2025/quarter=01/month=1/server=AGVS-My/
│   │       └── Student-Information-List.csv
│   ├── academic-accomodation-letter-list/
│   │   └── year=2025/quarter=1/server=AGVS-My/
│   │       └── Academic_Accommodation_Letter_Dataset.csv
│   └── appeal-information-list/
│       └── year=2025/quarter=01/month=1/server=AGVS-My/
│           └── Appeals_Information_Dataset.csv
```

---

### **Ingestion Process**
The ingestion process is implemented through PowerShell scripts run on an EC2 instance, utilizing the `Write-S3Object` command to upload CSV files directly to S3 with custom key naming.

```powershell
Write-S3Object -Bucket academics-raw-my -File "C:\path\Student-Information-List.csv" -Key "accomodation/student-information-list/year=2025/quarter=01/month=1/server=AGVS-My/Student-Information-List.csv"

Write-S3Object -Bucket academics-raw-my -File "C:\path\Academic_Accommodation_Letter_Dataset.csv" -Key "accomodation/academic-accomodation-letter-list/year=2025/quarter=1/server=AGVS-My/Academic_Accommodation_Letter_Dataset.csv"

Write-S3Object -Bucket academics-raw-my -File "C:\path\Appeals_Information_Dataset.csv" -Key "accomodation/appeal-information-list/year=2025/quarter=01/month=1/server=AGVS-My/Appeals_Information_Dataset.csv"
```

---

### **Data Schema Relationships**
The ingestion system ensures the following relationships:
- `StudentID` links across all three datasets
- Referential integrity maintained by enforcing primary/foreign keys
- Future extensions will include relationship with `AccommodationStatusLogs.csv`

Entity Relationship View:
- Student (1) → (M) Accommodation Letters
- Student (1) → (M) Appeals

---

### **Data Profiling with AWS Glue DataBrew**
Each dataset was profiled using **AWS Glue DataBrew** to assess quality:
- **Total Rows**: 50
- **Missing Cells**: 0 (100% valid data)
- **Duplicates**: None detected
- **Data Types**: 8 string fields per dataset

**Profile Jobs**:
- `acad-stud-info-ds-prf-my`
- `acad-acomm-lst-prf-my`
- `acad-app-info-list-prf-my`

**Profiling Outputs**:
- Column-level statistics
- Summary of correlations
- Data quality metrics (e.g., invalid, outliers)

---

### **Architecture Overview**
![Architecture Diagram](./images/academic-data-ingestion-diagram.png)

**Highlights**:
- Ingestion from general and web servers (EC2)
- Two separate availability zones for redundancy
- Ingested into academic data lake S3 bucket
- Profiled and prepared through AWS Glue

---

### **Compliance with UCW Procedure 5051p**
This system helps meet regulatory and internal policy requirements:
- Supports transparency of accommodation workflows
- Ensures appeals and accommodations are traceable
- Enables historical reconstruction and audit readiness

UCW’s Accessibility Office, Registrar, and Academic Services benefit from:
- Centralized data access
- Snapshot-style historical versions
- Streamlined service improvement workflows

---

### **Conclusion**
This automated data ingestion system for UCW’s academic accommodation datasets is a scalable, cloud-native solution. By leveraging EC2 for operational connectivity and S3 for lifecycle-enabled storage, combined with Glue DataBrew for validation, it creates a foundation for secure academic governance, accessibility monitoring, and data analytics.


