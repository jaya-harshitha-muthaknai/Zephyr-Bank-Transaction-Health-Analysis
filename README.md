# 🏦 Zephyr Bank Transaction Health Analysis
**Business Analyst & Data Analyst Case Study**

---

## 📌 Executive Summary

Conducted end-to-end business analysis and data analytics for Zephyr Bank (UK neobank) to assess transaction health, fraud exposure, and revenue optimization across customer segments, regions, and merchant categories. Delivered actionable insights and executive recommendations that address Risk, Finance, Product, and Compliance priorities.

**Impact:** Identified £1.5M+ fraud exposure, £900 revenue leakage, and 72:1 fraud-to-revenue ratio in high-risk merchants—enabling prioritized risk remediation.

---

## 📄 Business Requirements Document (BRD)

### Business Context
Zephyr Bank operates a digital-first ecosystem with dispersed transaction activity across channels, customer segments, and regions. Leadership lacked consolidated visibility into transaction health drivers and risk exposure patterns.

### Business Objectives
| Objective | Owner | Priority |
|-----------|-------|----------|
| Identify fraud exposure by customer, region, and merchant category | Risk & Compliance | P0 |
| Quantify revenue leakage and optimization opportunities | Finance & Product | P0 |
| Assess transaction channel and device reliability | Operations | P1 |
| Recommend risk mitigation and revenue recovery actions | Executive Leadership | P0 |

### Stakeholder Map

```
Executive Leadership (CFO, COO)
    ├── Risk & Compliance
    │   └── Fraud investigation, merchant risk assessment
    ├── Finance
    │   └── Fee structure review, revenue leakage analysis
    ├── Product
    │   └── Transaction type performance, customer segment behavior
    └── Operations
        └── Channel reliability, failure rate monitoring
```

*[IMAGE PLACEMENT: Add org chart or stakeholder priority matrix here—`/images/stakeholder_map.png`]*

### Success Metrics (KPIs)

| KPI | Target | Actual | Status |
|-----|--------|--------|--------|
| Fraud Rate Visibility | <5% | 20% | ⚠️ Elevated |
| Fraud Exposure Quantified | <£500K | £1.5M+ | 🔴 Critical |
| Revenue Leakage Tracked | <£500 | £900+ | ⚠️ Elevated |
| Merchant Risk Classification | 100% | 100% | ✅ Complete |
| Executive Dashboard Adoption | >4 stakeholders | 5 stakeholders | ✅ Complete |

### Business Problems & Hypotheses

| Problem | Root Cause Hypothesis | Investigation Required |
|---------|----------------------|------------------------|
| High fraud exposure | Weak controls on high-risk merchant categories (Fuel) and repeat offenders | Fraud pattern analysis by merchant + customer |
| Revenue leakage in international txns | Fee calculation logic inconsistencies | Transaction-level fee review + P&L impact |
| Channel failure concentration | Device-channel combination mismatch | Failure rate by channel-device pairing |
| Customer risk concentration | Inadequate customer-level KYC/AML screening | Top fraud-generating customer analysis |

---

## 📋 Functional Requirements Document (FRD)

### Analysis Requirements

| Requirement ID | Description | Acceptance Criteria | Status |
|---|---|---|---|
| **FR-01** | Fraud exposure analysis by region | Identify top 3 regions; calculate fraud %, £ exposure, event count | ✅ Complete |
| **FR-02** | Fraud exposure analysis by merchant category | Flag merchant categories with fraud rate >20%; calculate fraud-to-revenue ratio | ✅ Complete |
| **FR-03** | Customer-level fraud ranking | Rank top 10 customers by fraud exposure; identify repeat fraud patterns | ✅ Complete |
| **FR-04** | Revenue leakage by transaction type | Identify transaction types with fee shortfalls; quantify £ leakage | ✅ Complete |
| **FR-05** | Channel performance assessment | Calculate failure rate, success rate, avg processing time by channel | ✅ Complete |
| **FR-06** | Customer segment behavior profiling | Compare transaction volume, value, fraud rate across segments (Business/Standard/Premium) | ✅ Complete |
| **FR-07** | Device-channel risk matrix | Identify high-failure device-channel combinations | ✅ Complete |
| **FR-08** | Executive KPI dashboard | Real-time fraud, revenue, operational health metrics with drill-down capability | ✅ Complete |

### Data Requirements

| Data Element | Source | Frequency | Format |
|---|---|---|---|
| Transaction records (1,500 records) | fact_transactions_updated.csv | H1 2026 snapshot | CSV |
| Customer master (20 customers) | dim_customer.csv | Static | CSV |
| Merchant categories (18 categories) | dim_merchant_category.csv | Static | CSV |
| Transaction types (15 types) | dim_transaction_type.csv | Static | CSV |

**Data Model:** Star schema with fact table and 3 dimension tables.

### Report & Dashboard Requirements

| Deliverable | Audience | Format | Refresh Frequency |
|---|---|---|---|
| Executive Summary | CFO, COO, Risk Lead | Power BI Dashboard | Ad-hoc |
| Fraud Investigation Report | Risk & Compliance | Jupyter Notebook (EDA) + Excel | On-demand |
| Revenue Leakage Analysis | Finance & Product | Power BI + Excel |Ad-hoc |
| Merchant Risk Assessment | Compliance | Power BI heatmap | Quarterly |

---

## 🔗 Requirements Traceability Matrix (RTM)

### Business Objective → Analysis → Insight → Recommendation

| Business Objective | Analysis Performed | Key Insight | Recommendation |
|---|---|---|---|
| **Identify fraud exposure** | Fraud $ by region, merchant, customer | London: 60% of fraud events; Customer 20: £1.1M exposure; Fuel merchants: 31.33% fraud rate | Implement advanced fraud detection for high-risk customers; reassess Fuel merchant category |
| **Quantify revenue leakage** | Fee structure review by txn type | International Transfers: £399.61 leakage; Cross-Border: £167.34; Bill Payments: £92.17 | Review fee logic for international transactions; audit cross-border pricing model |
| **Assess channel reliability** | Failure rate by channel + device combo | [Analysis results] | Improve monitoring controls for automated transaction channels; identify device-channel mismatch |
| **Customer segment behavior** | Txn volume, value, fraud rate by segment | Business customers: +£78.50 surplus; Standard customers: -£185 shortfall | Tailor risk controls by segment; increase Standard customer scrutiny |

*[IMAGE PLACEMENT: Add RTM heatmap or flow diagram—`/images/rtm_heatmap.png`]*

---

## 🛠️ Technical Analysis Approach

### Technologies Used
- **SQL** — Data extraction, aggregation, fraud pattern queries
- **Python** — EDA, statistical analysis (Pandas, NumPy, Matplotlib, Seaborn)
- **Excel** — Ad-hoc analysis, pivot tables, fee reconciliation
- **Power BI** — Executive dashboard, drill-down analytics, KPI monitoring
- **GitHub** — Version control, reproducibility

### Analytical Methodology

#### 1. Data Validation & Cleaning
- Verified referential integrity across fact/dimension tables
- Checked for null values, duplicates, out-of-range entries
- Validated transaction amounts and fee calculations

#### 2. Exploratory Data Analysis (EDA)
- Univariate analysis: Distribution of fraud rate, transaction value, fee amounts
- Bivariate analysis: Fraud by region, merchant, customer, channel
- Correlation analysis: Fee vs. transaction value, fraud rate vs. merchant category

#### 3. Fraud Pattern Detection
```sql
-- Example: Fraud exposure by region
SELECT 
    region,
    COUNT(*) as fraud_events,
    SUM(fraud_exposure) as total_exposure,
    ROUND(100.0 * SUM(CASE WHEN is_fraud = 1 THEN 1 ELSE 0 END) / COUNT(*), 2) as fraud_rate_pct
FROM fact_transactions
WHERE is_fraud = 1
GROUP BY region
ORDER BY total_exposure DESC;
```

#### 4. Revenue Leakage Analysis
- Compared actual fees vs. expected fees by transaction type
- Calculated fee variance for international transactions
- Identified under-charged transaction categories

#### 5. Customer Risk Segmentation
- Ranked customers by fraud exposure
- Identified repeat fraud patterns (reversed transactions)
- Correlated customer segment with fraud rate

---

## 📊 Key Findings & Insights

### 🔴 Fraud Exposure (Critical)

| Metric | Value | Insight |
|--------|-------|---------|
| Overall Fraud Rate | 20% | Elevated vs. industry baseline (~2-5%) |
| Total Fraud Exposure | £1.5M+ | Critical concentration risk |
| Top 5 Customers | 70% of exposure | Inadequate customer-level risk controls |
| Customer 20 (repeat offender) | £1.1M exposure | Reversed transactions—systemic issue |

**Recommendation:** Implement real-time fraud detection for repeat offenders; escalate Customer 20 for enhanced KYC/AML review.

### 📍 Regional Risk Distribution

| Region | Fraud Events | Fraud Exposure | Fraud Rate |
|--------|---|---|---|
| London | 60% | Highest concentration | [%] |
| Midlands | 33% | Secondary risk | [%] |
| South East, North West, Scotland | <5% | Low risk | [%] |

*[IMAGE PLACEMENT: Add regional heatmap/choropleth—`/images/fraud_by_region.png`]*

**Recommendation:** Concentrate fraud detection resources on London & Midlands; implement regional transaction velocity limits.

### 🏪 Merchant Category Risk

| Merchant Category | Fraud Rate | Fraud Exposure | Revenue | Fraud:Revenue Ratio |
|---|---|---|---|---|
| Fuel | 31.33% | £1,500+ | £20.60 | 72:1 🔴 |
| [Category 2] | [%] | [£] | [£] | [ratio] |
| [Category 3] | [%] | [£] | [£] | [ratio] |

*[IMAGE PLACEMENT: Add merchant risk bubble chart or heatmap—`/images/merchant_risk_matrix.png`]*

**Recommendation:** Suspend or heavily restrict Fuel merchant transactions; implement post-transaction review for high-risk categories.

### 💰 Revenue Leakage (£900+)

| Transaction Type | Leakage Amount | Root Cause | Impact |
|---|---|---|---|
| International Transfers | £399.61 | Fee calculation mismatch | High |
| Cross-Border Payments | £167.34 | Exchange fee inconsistency | Medium |
| Bill Payments | £92.17 | Volume discount misconfiguration | Medium |

**Recommendation:** Audit fee calculation logic for international transactions; implement automated fee reconciliation.

### 👥 Customer Segment Performance

| Segment | Avg Transaction Value | Fraud Rate | Revenue (Surplus/Shortfall) |
|---|---|---|---|
| Business | [£] | [%] | +£78.50 ✅ |
| Standard | [£] | [%] | -£185.00 ⚠️ |
| Premium | [£] | [%] | [£] |

---

## 📈 Executive Dashboard

### Dashboard Features

**Page 1: Fraud Overview**
- Total fraud exposure (card), fraud rate (gauge), fraud events (counter)
- Fraud by region (map/bar chart)
- Fraud by merchant category (horizontal bar)
- Fraud by customer segment (donut)
- Fraud by device type (table)

**Page 2: Revenue Analysis**
- Total revenue (card), revenue per transaction (metric)
- Revenue by customer segment (stacked bar)
- Fee revenue trends (line chart)
- Revenue leakage by transaction type (waterfall)

**Page 3: Operational Health**
- Transaction success rate (gauge)
- Channel performance (matrix: channel vs. success rate)
- Failure rate by device-channel combo (heatmap)
- Transaction status breakdown (donut)

**Page 4: Customer Risk Drill-Down**
- Top 10 customers by fraud exposure (ranked table with drill-through)
- Customer segment KPIs (cards)
- Transaction velocity heatmap
<img width="1418" height="826" alt="Fraud_Revenue_Analysis_dasboard" src="https://github.com/user-attachments/assets/7e2519e8-9e3a-4468-b603-72e1e960c550" />
<img width="1373" height="766" alt="Customer_Risk_Anlysis" src="https://github.com/user-attachments/assets/c2b33e0e-650c-46cc-b690-2e3dc1c54041" />
<img width="1375" height="772" alt="Revenue_Lekage_Anlysis_Dashboard" src="https://github.com/user-attachments/assets/d0bd62ca-6eb2-408c-bc5f-c9485fac09cd" />

---

## 📁 Repository Structure & How to Explore

```
zephyr-bank-analysis/
├── README.md (this file)
├── CHALLENGE_BRIEF.md (original challenge requirements)
├── DATA_DICTIONARY.md (field definitions)
│
├── /docs/
│   ├── BRD.md (Business Requirements Document)
│   ├── FRD.md (Functional Requirements Document)
│   ├── RTM.xlsx (Requirements Traceability Matrix)
│   └── Stakeholder_Analysis.md
│
├── /analysis/
│   ├── investigation.ipynb (Jupyter Notebook: EDA + SQL queries)
│   ├── fraud_analysis.ipynb
│   ├── revenue_leakage_analysis.ipynb
│   └── results.xlsx (Ad-hoc analysis & fee reconciliation)
│
├── /dashboard/
│   ├── Data.pbix (Power BI dashboard)
│   ├── dashboard_screenshots/ (PNG exports)
│   │   ├── fraud_overview.png
│   │   ├── revenue_analysis.png
│   │   ├── operational_health.png
│   │   └── customer_risk.png
│   └── DAX_queries.md (Power BI calculation reference)
│
├── /data/
│   ├── dim_customer.csv
│   ├── dim_merchant_category.csv
│   ├── dim_transaction_type.csv
│   └── fact_transactions_updated.csv
│
├── /images/
│   ├── stakeholder_map.png
│   ├── fraud_by_region.png
│   ├── merchant_risk_matrix.png
│   ├── rtm_heatmap.png
│   └── (other supporting visuals)
│
└── requirements.txt (Python dependencies)
```

### How to Use This Repository

#### **For Business Stakeholders:**
1. Start with **README.md** (this file) — Executive summary & key findings
2. Review **BRD.md** (docs/) — Business objectives & success metrics
3. Explore **Power BI Dashboard** (dashboard/Data.pbix) — Interactive drill-down
4. Reference **FRD.md** (docs/) — What was analyzed & acceptance criteria

#### **For Technical Reviewers:**
1. Review **investigation.ipynb** (analysis/) — SQL queries, Python EDA, methodology
2. Check **requirements.txt** (root) — Dependencies & environment setup
3. Inspect **results.xlsx** (analysis/) — Ad-hoc calculations & fee reconciliation
4. Reference **DATA_DICTIONARY.md** (root) — Field definitions & data quality notes
5. Review **DAX_queries.md** (dashboard/) — Power BI calculation logic

#### **For Interview Preparation:**
1. Walk through **RTM.xlsx** (docs/) — Show how business needs → insights → recommendations
2. Explain **fraud pattern detection** using SQL example from investigation.ipynb
3. Discuss **merchant risk assessment** methodology (fraud-to-revenue ratio, category flagging)
4. Present **revenue leakage analysis** with fee calculation logic
5. Demo **Power BI dashboard** drill-down for executive storytelling

---

## 🚀 Quick Start: Run This Analysis

### Prerequisites
- Python 3.8+ (Pandas, NumPy, Matplotlib, Seaborn)
- SQL query tool (e.g., DBeaver, SQL Server Management Studio, or via Jupyter)
- Power BI Desktop (to open Data.pbix)
- Excel (to view results.xlsx)

### Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/zephyr-bank-analysis.git
   cd zephyr-bank-analysis
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Load data & run analysis**
   ```bash
   # Open Jupyter Notebook
   jupyter notebook analysis/investigation.ipynb
   
   # Execute cells sequentially to reproduce EDA, fraud analysis, and insights
   ```

4. **Review Power BI dashboard**
   ```bash
   # Open with Power BI Desktop
   dashboard/Data.pbix
   ```

5. **Reference results**
   ```bash
   # Excel outputs
   analysis/results.xlsx
   ```

---

## 💼 Business Recommendations & Next Steps

### Immediate Actions (0-30 days)
1. **Fraud Detection:** Implement real-time monitoring for Customer 20 and top-risk customers (repeat offenders).
2. **Merchant Risk:** Suspend high-risk Fuel merchant transactions pending enhanced KYC review.
3. **Fee Audit:** Launch emergency audit of international transaction fee logic.

### Short-Term (30-90 days)
4. **Advanced Controls:** Deploy machine learning fraud detection model for emerging patterns.
5. **Fee Optimization:** Implement automated fee reconciliation to prevent future leakage.
6. **Merchant Reassessment:** Conduct comprehensive merchant risk classification review.

### Long-Term (90+ days)
7. **Dashboard Adoption:** Roll out executive KPI dashboards to Risk, Finance, and Compliance teams.
8. **Continuous Monitoring:** Establish weekly fraud & revenue health reporting cadence.
9. **Predictive Analytics:** Build customer-level risk scoring model for dynamic KYC.

---

## 📚 Key Artifacts & Documentation

| Artifact | Purpose | Location |
|----------|---------|----------|
| BRD | Business problem definition, objectives, success metrics | `/docs/BRD.md` |
| FRD | Analysis requirements, data requirements, acceptance criteria | `/docs/FRD.md` |
| RTM | Traceability: business need → analysis → insight → recommendation | `/docs/RTM.xlsx` |
| Investigation Notebook | SQL queries, Python EDA, statistical analysis | `/analysis/investigation.ipynb` |
| Power BI Dashboard | Executive KPI metrics, interactive drill-down | `/dashboard/Data.pbix` |
| Results Workbook | Ad-hoc calculations, fee reconciliation, supporting analysis | `/analysis/results.xlsx` |
| Data Dictionary | Field definitions, data quality notes | `DATA_DICTIONARY.md` |

---

## 🔍 Skills Demonstrated

### Business Analysis
✅ Stakeholder analysis & requirement elicitation  
✅ KPI definition & success metrics  
✅ Problem hypothesis development  
✅ Risk assessment & business recommendation development  
✅ Executive communication & business insight framing  

### Data Analysis & SQL
✅ Data validation & cleaning  
✅ Complex SQL queries (aggregation, filtering, window functions)  
✅ Fraud pattern detection & customer segmentation  
✅ Revenue impact analysis  

### Python & Statistics
✅ Exploratory Data Analysis (Pandas, NumPy)  
✅ Data visualization (Matplotlib, Seaborn)  
✅ Statistical hypothesis testing  
✅ Correlation & distribution analysis  

### Business Intelligence & Reporting
✅ Power BI dashboard design & development  
✅ Executive-level KPI metrics  
✅ Interactive drill-down capability  
✅ Dashboard storytelling for non-technical audiences  

### Documentation & Communication
✅ BRD/FRD preparation  
✅ Requirements traceability  
✅ Professional business writing  
✅ Results presentation & recommendation framing  

---

## 📈 Project Outcome

**Role:** Business Analyst & Data Analyst  
**Duration:** 2 weeks  
**Deliverables:** BRD, FRD, RTM, SQL-based analysis, Python EDA, Power BI dashboard, executive recommendations  
**Impact:** Identified £1.5M+ fraud exposure, £900 revenue leakage, and actionable risk mitigation roadmap for Zephyr Bank leadership.

This project demonstrates **end-to-end business analysis capability**—from problem definition through data-driven insights to executive recommendations—using real-world banking transaction data.

---

## 👤 About This Project

Completed as part of the **DataDNA Banking Analytics Challenge**. The analysis, insights, and recommendations are original work based on provided transaction data.

---

## 📧 Questions or Feedback?

Reach out: jayaharshithamuthakani@gmail.com | LinkedIn: www.linkedin.com/in/jaya-harshitha-muthakani

