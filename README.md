# MBA Graduate-mariyam
# Project 1:Automated Data Ingestion for Academic Accommodation for Students with Accessibility Needs at UCW


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
- ✅ Amazon S3 structured folders with data
- ✅ System architecture diagram
- ✅ Entity-relationship mapping (ERD logic)
- ✅ Screenshots of all key steps

---

## 🖼️ Screenshots to Include
- PowerShell commands (Write-S3Object)
- S3 bucket folder structures
- Architecture diagram showing EC2, S3, users, datasets

---

## 🧠 Key Learning Outcomes
- Designed and implemented a cloud-native data ingestion pipeline
- Applied institutional policy (UCW Procedure 5051p) to technical workflows
- Practiced automation and secure AWS storage
- Demonstrated the ability to manage education-related data responsibly

---

## 📁 Repository Structure (Suggested)
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

## 🚀 Next Steps
- Add dataset samples (anonymized)
- Upload PowerShell script and architecture diagram
- Push project to GitHub and update repository URL here

Let me know if you'd like help generating the PowerShell upload script or drawing the architecture image!
