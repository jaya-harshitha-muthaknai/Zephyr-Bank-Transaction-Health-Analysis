# 🏦 Zephyr Bank Transaction Health Monitoring & Fraud Analytics

## 📌 Project Overview

Built an end-to-end Business Analytics solution for a simulated UK fintech bank to monitor transaction health, identify fraud patterns, analyze revenue leakage, and support executive decision-making.

The project combines Business Analysis and Data Analytics practices, covering requirement gathering, business documentation, SQL analysis, data validation, and Power BI dashboard development.

### Project Outcomes

* Identified fraud concentration patterns across customer segments and regions
* Measured revenue leakage across transaction types
* Analyzed customer and merchant risk exposure
* Evaluated channel and device-level fraud trends
* Developed executive KPI dashboards for business stakeholders
* Delivered actionable recommendations for Risk, Finance, Product, and Compliance teams

---

## 🎯 Business Problem

Zephyr Bank lacked a centralized view of transaction health across its digital banking ecosystem.

As a result:

* Fraud exposure was difficult to identify
* Revenue leakage was not measurable
* High-risk customers were not prioritized
* Merchant category risks were unclear
* Channel performance issues remained hidden
* Executive stakeholders lacked consolidated KPI reporting

The objective of this project was to create a reporting framework that improves visibility into fraud exposure, revenue performance, customer risk, and operational effectiveness.

---

## 👥 Stakeholders

* Risk Team
* Finance Team
* Product Team
* Compliance Team
* Executive Leadership

---

## 🎯 Business Objectives

* Monitor fraud exposure
* Detect revenue leakage
* Identify high-risk customers
* Assess merchant category risk
* Improve channel performance visibility
* Support executive decision-making

---

## 📊 Success Metrics

The project was designed to support:

* Fraud concentration visibility
* Revenue leakage identification
* Customer risk prioritization
* Merchant risk monitoring
* Channel performance visibility
* Executive KPI reporting

---

## 🧩 Business Analysis Approach

### Requirement Gathering

Business requirements were gathered based on stakeholder needs across Risk, Finance, Product, and Compliance functions.

### Business Requirements Document (BRD)

Created a BRD to define:

* Business objectives
* Stakeholders
* Scope
* Assumptions
* Constraints
* Success metrics
* Reporting requirements

### Functional Requirements Document (FRD)

Translated business requirements into measurable analytical requirements, including:

* Fraud analysis
* Revenue analysis
* Customer risk analysis
* Merchant risk analysis
* Channel risk analysis
* Executive KPI reporting

### Requirement Traceability Matrix (RTM)

Created an RTM to map:

Business Requirements → Functional Requirements → Dashboard Insights → Recommendations

This ensured that every business requirement was traceable to a measurable analytical outcome.

---

## 📂 Dataset Overview

### Domain

UK Fintech Banking

### Project Type

Business Analytics Case Study

### Dataset Coverage

January 2026 – May 2026

### Dataset Size

~1,500 Transactions

### Data Model

#### Fact Table

* fact_transactions

#### Dimension Tables

* dim_customer
* dim_transaction_type
* dim_merchant_category

### Data Available

* Transaction Amount
* Transaction Status
* Fraud Flags
* Customer Segments
* Regions
* Merchant Categories
* Device Types
* Channels
* Fees Charged
* FX Rates

> Note: This is a simulated case-study dataset created for analytical and reporting purposes.

---

## 🔄 Project Methodology

1. Requirement Gathering
2. Stakeholder Analysis
3. BRD Preparation
4. FRD Preparation
5. RTM Creation
6. Data Understanding
7. Data Cleaning & Validation
8. SQL Analysis
9. KPI Development
10. Power BI Dashboard Design
11. Business Recommendations

---

## 🧹 Data Preparation

Before analysis, the dataset was validated and prepared through:

* Missing value checks
* Transaction status validation
* Data type verification
* Fee calculation validation
* Fraud flag consistency checks
* Dimension and fact table relationship validation

---

## 🛠 Tools & Technologies

| Tool     | Purpose                  |
| -------- | ------------------------ |
| SQL      | Business Query Analysis  |
| Python   | Data Cleaning & Analysis |
| Pandas   | Data Transformation      |
| Excel    | Data Validation          |
| Power BI | Dashboard Development    |
| GitHub   | Version Control          |

---

## 🗄 SQL Analysis Performed

The following analyses were performed using SQL:

* Fraud concentration by customer segment
* Regional fraud analysis
* Revenue leakage calculations
* Expected vs Actual revenue comparison
* Customer risk ranking
* Merchant risk analysis
* Channel and device fraud analysis
* Domestic vs International transaction comparison
* Executive KPI generation

---

## 📊 Dashboard Pages

### 1. Executive Summary

Provides a high-level overview of business KPIs and transaction health.

**Dashboard Screenshot**

```text
/images/Executive_Summary.png<img width="1376" height="675" alt="Executive_Summary" src="https://github.com/user-attachments/assets/c9ddf01c-3524-4ca6-baec-efa7c3078b9d" />

```

---

### 2. Fraud & Revenue Analysis

Analyzes fraud concentration and revenue performance across customer segments.

**Dashboard Screenshot**

```text
<img width="1418" height="826" alt="Fraud_Revenue_Analysis_dasboard" src="https://github.com/user-attachments/assets/2a11c133-1313-4c9d-9365-3d0c02d0c2c9" />

```

---

### 3. Revenue Leakage Analysis

Evaluates expected fees versus actual fees charged to identify revenue leakage opportunities.

**Dashboard Screenshot**

```text
<img width="1375" height="772" alt="Revenue_Lekage_Anlysis_Dashboard" src="https://github.com/user-attachments/assets/12d02bf7-fc96-4a85-a8d3-0eadbc8bca67" />
```

---

### 4. Customer Risk Analysis

Identifies customers contributing significantly to fraud exposure and risk concentration.

**Dashboard Screenshot**

```text
<img width="1373" height="766" alt="Customer_Risk_Anlysis" src="https://github.com/user-attachments/assets/cb369c23-e15c-4dde-91cd-b0338ae76183" />

```

---

### 5. Fraud Risk Drivers & Hotspots

Analyzes fraud concentration across regions, channels, devices, and merchant categories.

**Dashboard Screenshot**

```text
<img width="1385" height="777" alt="Risk_and_Revenue_Insights" src="https://github.com/user-attachments/assets/18b72065-5900-4e31-89f5-d2ce494c7174" />

```

---

## 🔍 Key Insights

* Fraud events were concentrated within specific customer segments and regions.
* Revenue leakage opportunities were identified across selected transaction types.
* Customer risk exposure was unevenly distributed across the customer base.
* Merchant categories demonstrated varying fraud risk profiles.
* Fraud activity varied across channels and device types.
* Executive KPI reporting improved visibility into transaction health metrics.

---

## 💡 Recommendations

### Risk Team

* Strengthen monitoring for high-risk customer groups.
* Implement customer risk scoring models.
* Increase monitoring of high-risk merchant categories.

### Finance Team

* Review transaction fee application processes.
* Monitor revenue leakage through periodic audits.
* Establish automated fee reconciliation controls.

### Product Team

* Investigate transaction failure patterns.
* Monitor channel-specific performance trends.
* Improve visibility into fraud-related operational issues.

### Compliance Team

* Prioritize reviews of high-risk customer activity.
* Monitor transactions associated with elevated risk categories.

---

## 📁 Project Structure

```bash
Zephyr-Bank-Transaction-Health-Monitoring
│
├── Data
│   ├── fact_transactions_updated.csv
│   ├── dim_customer.csv
│   ├── dim_transaction_type.csv
│   └── dim_merchant_category.csv
│
├── Documents
│   ├── Business Requirements Document.docx
│   ├── Functional Requirements Document.docx
│   ├── RTM (Requirement Traceability Matrix).docx
│   ├── CHALLENGE_BRIEF.md
│   └── DATA_DICTIONARY.md
│
├── Notebook
│   └── investigation.ipynb
│
├── PowerBI
│   └── Data.pbix
│
├── Images
│   ├── Executive_Summary.png
│   ├── Fraud_Revenue_Analysis.png
│   ├── Revenue_Leakage_Analysis.png
│   ├── Customer_Risk_Analysis.png
│   └── Risk_and_Revenue_Insights.png
│
└── README.md
```

---

## 🚀 Business Impact

This project demonstrates the complete lifecycle of a Business Analyst and Data Analyst engagement:

* Requirement Gathering
* Stakeholder Analysis
* BRD Creation
* FRD Development
* RTM Preparation
* Data Validation
* SQL Analysis
* Business Reporting
* Dashboard Development
* Executive Reporting

The solution provides visibility into fraud trends, revenue leakage, customer risk patterns, and operational performance, enabling informed decision-making for business stakeholders.

---

---

## Key Competencies Demonstrated

• Requirement Gathering
• Stakeholder Analysis
• BRD & FRD Documentation
• Requirement Traceability Matrix (RTM)
• SQL Analysis
• Data Validation
• KPI Development
• Dashboard Design
• Business Reporting
• Executive Reporting
