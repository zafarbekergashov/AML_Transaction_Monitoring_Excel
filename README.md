# 🛡️ Automated AML Transaction Monitoring & Sanctions Screening Model

An end-to-end operational Anti-Money Laundering (AML) monitoring system built using **Microsoft Excel** and **Power Query (M-Code)**. This project automates daily transaction ingestion, performs automated sanctions cross-referencing, enforces risk-based threshold scoring, and outputs formatted compliance exception reports.

---

## 🚀 Business Problem & Objectives

Financial compliance teams face significant operational risks when managing daily transaction monitoring manually:
- **Scalability:** Handling volume growth across multiple daily CSV data feeds.
- **Data Integrity:** Preventing false positives/negatives caused by formatting inconsistencies, blank values, or improper data typing.
- **Auditability:** Maintaining a clear, repeatable ETL pipeline for regulatory compliance audits.

This project solves these challenges by establishing an automated ETL pipeline that transforms raw multi-source data into real-time actionable compliance metrics.

---

## 🛠️ Excel & Power Query Technical Highlights

- **Automated Folder Ingestion (ETL Pipeline):** Designed a dynamic Power Query pipeline (`Transactions/`) that automatically fetches, parses, and consolidates daily `.csv` files without breaking schema consistency.
- **Relational Merges (JOIN Logic):** Applied Left Outer Joins between live transaction streams and global watchlists (`Reference_Data/Sanctions.csv`) to detect sanctioned individuals and entities.
- **Advanced Conditional Logic:** Built multi-layered conditional metrics (`Final AML Status`) using M-code logic to classify entries into:
  - `SANCTIONS REVIEW` (High-priority watchlists hits)
  - `TRANSACTION REVIEW` (High-value / high-risk threshold breaches)
  - `NORMAL` (Compliant transactions)
- **Data Hygiene & Null Handling:** Enforced strict data typing (Text, Currency, Date) and systematically replaced dummy placeholder zeros (`0`) with native standard `null` values to preserve analytical accuracy for downstream auditing (`COUNTA`, PivotTables).
- **Dynamic Formatting:** Applied logic-driven Conditional Formatting in Excel to visually prioritize high-risk compliance alerts for analysts.

---

## 📂 Repository Architecture

```text
.
├── Output/
│   └── AML_Review_Report.xlsx      # Final compliance alert output dashboard
├── Reference_Data/
│   └── Sanctions.csv               # Global sanctions & watchlist database
├── Transactions/
│   ├── 2026-08-01.csv              # Daily operational data feeds
│   ├── 2026-08-02.csv
│   ├── 2026-08-03.csv
│   └── 2026-08-04.csv
└── DAY 27_Final Project.xlsx       # Main Excel Workbook with Power Query ETL Pipeline
