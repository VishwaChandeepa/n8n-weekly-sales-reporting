# Weekly Sales Reporting Automation

An n8n automation workflow that automates the weekly sales reporting process.

## 📌 Project Overview

This project automates a repetitive weekly sales reporting task.

The workflow retrieves sales data from a legacy data warehouse through an API, separates sales orders based on their status, calculates the total value of Booked orders, and prepares a report of Processing orders for Sales Managers.

## 🏗️ Workflow Architecture

The workflow is designed as an automated sales reporting pipeline:

```text
┌─────────────────────────┐
│   Monday 9:00 AM        │
│   Schedule Trigger      │
└────────────┬────────────┘
             │
             ▼
┌─────────────────────────┐
│ Get Data From           │
│ Warehouse API           │
└────────────┬────────────┘
             │
             ▼
┌─────────────────────────┐
│     Upsert Orders       │
│     n8n Data Table      │
└────────────┬────────────┘
             │
             ▼
┌─────────────────────────┐
│   Check Order Status    │
│   & Employee Name       │
└────────────┬────────────┘
             │
       ┌─────┴─────┐
       │           │
       ▼           ▼
┌─────────────┐ ┌──────────────────────┐
│ Processing  │ │ Calculate Booked     │
│ Sales Data  │ │ Orders & Total Value │
└──────┬──────┘ └──────────┬───────────┘
       │                   │
       ▼                   ▼
┌─────────────┐   ┌────────────────────┐
│ Processing  │   │ Discord            │
│ Sales Report│   │ Weekly Summary     │
└─────────────┘   └────────────────────┘
```

### Architecture Flow

**Schedule → Data Retrieval → Data Storage → Order Validation → Sales Processing → Reporting & Notification**

The architecture contains two main outcomes:

* **Booked Orders:** The workflow calculates the number of Booked orders and their total sales value, then sends the weekly summary to Discord.
* **Processing Orders:** The workflow prepares the relevant Processing order data for Sales Managers.

## 🔄 Workflow

The automation performs the following steps:

1. Runs automatically every Monday.
2. Retrieves sales data through an API.
3. Processes the sales data.
4. Identifies Booked sales orders.
5. Calculates the total Booked sales.
6. Announces the Booked sales total through Discord.
7. Identifies Processing sales orders.
8. Creates a table/report of Processing orders for Sales Managers.

## 🛠️ Technologies

* n8n
* REST API
* JavaScript
* Discord
* Workflow Automation

## 🎯 Objective

The objective is to reduce manual work, minimize calculation errors, and ensure that the weekly sales report is prepared consistently and on time.

## 📁 Project Structure

```text
weekly-sales-reporting/
│
├── weekly-sales-reporting.json
└── README.md
```

## 🚀 How to Import

1. Open n8n.
2. Import the `weekly-sales-reporting.json` workflow.
3. Configure any required credentials or environment-specific settings.
4. Review the workflow.
5. Execute the workflow or wait for the scheduled execution.

## ⚠️ Credentials

No passwords, API keys, access tokens, or other sensitive credentials should be committed to this repository.

## 📚 Learning Project

This project was created as part of my learning journey with n8n and workflow automation.
