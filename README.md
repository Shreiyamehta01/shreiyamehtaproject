# Xeno FDE Internship Assignment – Multi-Tenant Shopify Data Ingestion & Insights Service

This project implements a multi-tenant service to ingest data from Shopify (customers, orders, products) and display insights in a dashboard.

## 🚀 Features Implemented
- Connects to Shopify APIs to fetch:
  - Customers
  - Orders
  - Products
- Multi-tenant support with isolated data per store
- Stores data in **PostgreSQL** (configurable RDBMS)
- Simple **React.js** dashboard (email/password auth) showing:
  - Total customers, orders, and revenue
  - Orders by date (with filtering)
  - Top 5 customers by spend
  - Trend charts for key metrics

## 🛠 Tech Stack
- **Backend**: Java Spring Boot (REST APIs)
- **Frontend**: React.js (deployed separately)
- **Database**: PostgreSQL
- **ORM**: Hibernate
- **Deployment**: Render / Railway / Vercel (choose one)

## ⚙️ Setup Instructions
1. Clone this repo  
   ```bash
   git clone https://github.com/Shreiyamehta01/shreiyamehtaproject.git
   cd shreiyamehtaproject
