# Automated AML Transaction Monitoring & Sanctions Screening Model

This is an automated Anti-Money Laundering (AML) system created using **Microsoft Excel** and **Power Query**. It automatically collects daily transaction data, checks names against international sanctions lists, flags suspicious or high-value transfers, and creates clean reports for compliance teams.

---

## Business Problem & Objectives

Checking transactions manually creates big challenges for financial teams:
- **High Volume:** It is hard to handle hundreds of daily CSV files manually.
- **Data Mistakes:** Formatting errors, blank spaces, or incorrect data types can lead to missed risks or false alarms.
- **Audit Tracking:** Compliance teams need a clean, step-by-step process that regulators can easily audit.

This project solves these problems by creating an automated pipeline that turns raw daily files into clear, actionable safety alerts.

---

## Key Technical Features

- **Automatic File Ingestion:** Power Query automatically reads and combines all new daily CSV files from the `Transactions/` folder.
- **Data Matching (Left Joins):** The system connects daily transactions with the global sanctions database (`Sanctions.csv`) to spot flagged individuals immediately.
- **Smart Conditional Rules:** The model assigns a clear `Final AML Status` to every transaction:
  - `SANCTIONS REVIEW`: Matched with a sanctions list (Highest Risk).
  - `TRANSACTION REVIEW`: Exceeds safe money thresholds or high-risk rules.
  - `NORMAL`: Clean transaction with no issues.
- **Clean Data Handling (`null` values):** Text columns use proper data types. Instead of leaving random zeros (`0`), clean rows show empty (`null`) cells so pivot tables and formulas remain accurate.
- **Visual Alerting:** Conditional formatting automatically highlights high-risk rows in red and yellow for quick analyst review.

---

## Repository Structure

```text
.
├── Output/
│   └── AML_Review_Report.xlsx      # Final compliance alert output dashboard
├── Reference_Data/
│   └── Sanctions.csv               # Global sanctions & watchlist database
├── Transactions/
│   ├── 2026-08-01.csv              # Daily transaction feeds
│   ├── 2026-08-02.csv
│   ├── 2026-08-03.csv
│   └── 2026-08-04.csv
└── DAY 27_Final Project.xlsx       # Main Excel Workbook with Power Query ETL
