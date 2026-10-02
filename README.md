# Honda Sales AI Automation

An end-to-end automated Honda sales analytics and reporting system built with **n8n, MySQL, OpenAI, Gmail, and Google Drive**.

The project automates the complete journey from receiving sales data to storing, analyzing, interpreting, and emailing business insights.

---

## 🚀 Project Overview

This project demonstrates an end-to-end business automation workflow for Honda sales data.

The automation:

1. Receives a sales-data email through Gmail.
2. Retrieves the incoming message.
3. Downloads the sales file through Google Drive.
4. Extracts data from the Excel/XLSX file.
5. Inserts or updates records in an Aiven-hosted MySQL database.
6. Performs SQL-based sales analysis.
7. Combines the analytical results.
8. Sends the results to an AI model for business interpretation.
9. Generates an HTML sales report.
10. Sends the final report through Gmail.

The objective is to transform raw sales data into an automated, client-ready business report with AI-generated recommendations.

---

## 🏗️ Architecture

```text
                         ┌───────────────────┐
                         │    Gmail Trigger  │
                         └─────────┬─────────┘
                                   │
                                   ▼
                         ┌───────────────────┐
                         │    Get Message    │
                         └─────────┬─────────┘
                                   │
                                   ▼
                         ┌───────────────────┐
                         │ Google Drive      │
                         │ Download File     │
                         └─────────┬─────────┘
                                   │
                                   ▼
                         ┌───────────────────┐
                         │ Extract XLSX Data │
                         └─────────┬─────────┘
                                   │
                                   ▼
                         ┌───────────────────┐
                         │ MySQL Database    │
                         │ Insert / Update   │
                         └─────────┬─────────┘
                                   │
                    ┌──────────────┴──────────────┐
                    │                             │
                    ▼                             ▼
          ┌──────────────────┐          ┌──────────────────┐
          │ State-wise Sales │          │ Overall Summary  │
          │ SQL Analysis     │          │ SQL Analysis     │
          └─────────┬────────┘          └─────────┬────────┘
                    │                             │
                    └──────────────┬──────────────┘
                                   │
                                   ▼
                         ┌───────────────────┐
                         │ Merge Analysis    │
                         │ Results           │
                         └─────────┬─────────┘
                                   │
                                   ▼
                         ┌───────────────────┐
                         │ OpenAI / AI Model │
                         │ Business Analysis │
                         └─────────┬─────────┘
                                   │
                                   ▼
                         ┌───────────────────┐
                         │ HTML Report       │
                         │ Generation        │
                         └─────────┬─────────┘
                                   │
                                   ▼
                         ┌───────────────────┐
                         │ Gmail             │
                         │ Send Report       │
                         └───────────────────┘
