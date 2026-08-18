# Support Ticket Analytics Dashboard

A Power BI business intelligence dashboard designed to analyze and monitor support-ticket operations across **Redmine** and **Freshdesk**.

The project combines ticket data from both platforms into an analytics-ready dataset and provides interactive views for monitoring ticket volume, status, priority, client activity, consultant workload, aging, overdue tickets, resolution performance, and support levels.

> **Note:** This repository uses **masked/anonymized data** for portfolio and demonstration purposes. Original client names, consultant information, ticket identifiers, contact information, and other potentially confidential information have been replaced or transformed.

---

## Project Overview

This project was developed as an end-to-end data analytics and business intelligence workflow.

The process begins with raw support-ticket data from Redmine and Freshdesk. The data is cleaned, standardized, anonymized, transformed into reporting-ready datasets, and then visualized in Power BI.

The final dashboard contains **5,011 support tickets**, consisting of:

* **3,204 Redmine tickets**
* **1,807 Freshdesk tickets**

The dashboard is designed to help users understand:

* Overall ticket volume
* Ticket status distribution
* Ticket priority
* Ticket trends over time
* Client ticket activity
* Consultant workload
* Ticket aging
* Resolution duration
* Overdue tickets
* Critical open tickets
* Client environment
* Support level distribution
* Individual ticket details

---

## Dashboard Pages

### 1. Homepage

The homepage provides a high-level overview of the support-ticket dataset.

Key elements include:

* Total Tickets
* Tickets by Platform
* Ticket Volume Trend
* Ticket Status KPIs
* Navigation to detailed dashboard pages

The dashboard shows **5,011 total tickets** and provides a breakdown between Redmine and Freshdesk.

---

### 2. Executive Dashboard

The Executive Dashboard provides an operational overview of ticket activity.

### Key Metrics

* Total Tickets
* Average Aging
* Average Resolution Duration
* Average Tickets Created
* Average Tickets Closed
* Overdue Tickets
* Critical Open Tickets

### Visualizations

* Tickets by Priority
* Ticket Volume by Consultant
* Ticket Volume by Status
* Ticket Volume by Client
* Client Environment
* Ticket Volume Trend

The dashboard also includes interactive filters for date, client, consultant, status, priority, and source system.

---

### 3. Client Details

The Client Details page provides a focused view of an individual client's support activity.

It includes:

* Client Details
  * Client Environment
  * Client Status
  * Project Phase
  * Product
* Total Tickets
* Overdue Tickets
* Critical Open Tickets
* Average Metrics
* Ticket Volume by Consultant
* Tickets by Priority
* Tickets by Status
* Ticket Volume Trend
* Support Level
* Detailed ticket records

For example, the dashboard can display an anonymized client profile together with its operational and ticket metrics.

---

### 4. Consultant Details

The Consultant Details page focuses on the workload and ticket activity associated with an individual consultant.

It provides:

* Ticket Volume Trend
* Ticket Volume by Client
* Tickets by Priority
* Tickets by Status
* Average Ticket Metrics
* Overdue Tickets
* Critical Open Tickets
* Number of Clients Handled
* Client Environment
* Support Level

The consultant trend can also be viewed at a different levels such as yearly, monthly, weekly, and daily.

---

### 5. Ticket Explorer

The Ticket Explorer provides a detailed table for searching and examining individual support tickets.

Available fields include:

* Date
* Ticket ID
* Ticket Concern
* Client Name
* In-charge
* Status
* Priority
* Due Date
* Module

The page also provides filters for date, client, consultant, status, priority, and source system, as well as a search capability for ticket ID, concern, client, or consultant.

---

# Data Preparation & Anonymization

Before the data was used in Power BI, a Python/Pandas preprocessing workflow was developed to clean, transform, and anonymize the source data.

The Jupyter Notebook documents the complete masking process.

## Data Sources

The original workflow uses data from:

* Redmine
* Freshdesk
* Client environment/reference data

The raw Redmine dataset contains **3,204 ticket records across 22 columns**, while the Freshdesk dataset contains **1,807 ticket records across 29 columns**.

The notebook then creates processed datasets specifically structured for analytics and Power BI reporting.

---

## Anonymization Techniques

Several masking techniques were implemented to prevent disclosure of confidential information.

### Client Names

Original client identifiers are replaced with sequential aliases:

```text
Client 001
Client 002
Client 003
...
```

### Ticket IDs

Ticket identifiers are replaced with platform-specific aliases.

Examples:

```text
RM-TKT-0001
RM-TKT-0002
RM-TKT-0003
```

and

```text
FD-TKT-0001
FD-TKT-0002
FD-TKT-0003
```

### Bug IDs

Bug identifiers are anonymized using SHA-256 hashing and represented using a platform-specific identifier such as:

```text
RM-BG-XXXXXXXX
```

### Contact Information

Freshdesk contact information is masked while maintaining relationships between clients and their contacts.

Contact aliases follow a structure similar to:

```text
Client 001 Rep 001
Client 001 Rep 002
```

### Consultant / Agent Information

Consultant and agent identifiers are anonymized to prevent exposure of the original personnel information.

### Text Cleaning

Text fields such as root causes are cleaned and standardized by:

* Removing parenthetical text
* Normalizing whitespace
* Removing unnecessary leading/trailing spaces

---

# Data Transformation

After anonymization, separate processed datasets are generated for Redmine and Freshdesk.
These transformations produce datasets that are more suitable for reporting and visualization than the original raw-source structures.

---

# Technology Stack

### Data Processing

* Python
* Pandas
* NumPy
* Regular Expressions
* hashlib
* Jupyter Notebook

### Business Intelligence

* Microsoft Power BI
* DAX
* Power Query

### Data Sources

* Redmine
* Freshdesk
* Microsoft Excel

---

# Project Workflow

```text
Raw Redmine Data ─────┐
                      │
                      │
Raw Freshdesk Data ───┤
                      ├──> Data Cleaning
Client Reference ─────┘
                      │
                      ▼
              Data Anonymization
                      │
                      ▼
              Data Transformation
                      │
                      ▼
            Processed Excel Dataset
                      │
                      ▼
                 Power BI Dashboard
```

---

# Key Analytics

The dashboard supports analysis of several operational metrics.

### Ticket Volume

Monitor the number of tickets created and closed across different time periods.

### Ticket Status

Analyze the distribution of:

* Open
* Resolved
* Closed

### Priority

Analyze ticket distribution across:

* Critical
* High
* Medium
* Low

### Aging

Measure how long tickets remain active before closure or based on the defined reference date.

### Resolution Duration

Analyze the time required to resolve and close tickets.

### Overdue Tickets

Identify tickets that have exceeded their expected due date.

### Critical Open Tickets

Highlight high-priority operational issues that remain unresolved.

### Consultant Workload

Compare ticket volume and workload across consultants.

### Client Activity

Identify clients generating the highest number of support tickets and analyze their support activity.

---

# Privacy & Data Protection

This repository is intended for **portfolio and demonstration purposes**.

The source notebook explicitly documents that sensitive client names, employee/consultant information, contact details, ticket identifiers, and other confidential information were replaced or masked before producing the demonstration dataset.

No original organizational identifiers are intentionally included in the portfolio dataset.

The anonymization process was designed to preserve the **analytical structure and relationships of the data** while reducing exposure of confidential information.

---

# Repository Structure

```text
support-ticket-analytics/
│
├── README.md
├── Final RM_DF Dataset Masking.ipynb
├── Redmine Freshdesk Dataset Masked.xlsx
├── Support Ticket Dashboard.pbix
```

> File and folder names may vary depending on the final repository organization.

---

This project provided practical experience in:

* Data cleaning and preprocessing
* Data anonymization and privacy-preserving transformations
* Python and Pandas
* Exploratory Data Analysis
* Data transformation
* Handling multiple data sources
* Creating analytics-ready datasets
* Power BI dashboard development
* DAX measures
* Interactive filtering
* KPI development
* Time-series analysis
* Operational and business intelligence reporting

---

# Disclaimer

This project is a **portfolio demonstration** based on anonymized and transformed support-ticket data.

The dashboard and notebook are intended to demonstrate technical skills in **data preparation, anonymization, analytics, and business intelligence** and should not be interpreted as representing the actual confidential data, systems, or performance of any organization.

---

## Author

**Vhan Randolp Pena**

Computer Engineering — Data Science

Tools: Python • Pandas • Power BI • DAX • Excel • Data Analytics • Business Intelligence
