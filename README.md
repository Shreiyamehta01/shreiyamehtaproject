Xeno FDE Internship Assignment – Multi-Tenant Shopify Data Ingestion & Insights Service

This project implements a multi-tenant service to ingest data from Shopify (customers, orders, products) and display insights in a dashboard.

🚀 Features Implemented

Connects to Shopify APIs to fetch:

Customers

Orders

Products

Multi-tenant support with isolated data per store

Stores data in PostgreSQL (configurable RDBMS)

Simple React.js dashboard (email/password auth) showing:

Total customers, orders, and revenue

Orders by date (with filtering)

Top 5 customers by spend

Trend charts for key metrics

🛠 Tech Stack

Backend: Java Spring Boot (REST APIs)

Frontend: React.js (deployed separately)

Database: PostgreSQL

ORM: Hibernate

Deployment: Render / Railway / Vercel (choose one)

⚙️ Setup Instructions

Clone this repo

git clone https://github.com/Shreiyamehta01/shreiyamehtaproject.git
cd shreiyamehtaproject


Configure database credentials in application.properties

Run backend:

./mvnw spring-boot:run


Run frontend:

cd frontend
npm install
npm start

🏗 Architecture
Shopify API → Spring Boot Service (multi-tenant DB) → PostgreSQL
                                   ↓
                             React Dashboard

📚 Documentation
1. Assumptions

Each Shopify store = one tenant, identified by a unique tenant_id.

All Shopify credentials (API key, secret, store URL) are stored securely per tenant.

Data sync is scheduled every X minutes via a cron job or triggered by Shopify webhooks.

Basic email/password authentication is used for the dashboard.

PostgreSQL is used as the main RDBMS; Hibernate handles ORM.

2. High-Level Architecture
+---------------------+         +------------------------+         +----------------+
|  Shopify Stores     |  --->   |  Spring Boot Service   |  --->   |  PostgreSQL DB |
|  (Customers, Orders,|         |  (Multi-tenant APIs)   |         | (Isolated data |
|  Products)          |         +------------------------+         |   per tenant)  |
+---------------------+                                               |
         |                                                            |
         v                                                            v
                        +------------------------+
                        | React Dashboard (UI)  |
                        +------------------------+


(You can also upload an image of this diagram to docs/architecture.png and link it here.)

3. APIs
Method	Endpoint	Description
GET	/api/{tenant}/customers	List all customers for a tenant
GET	/api/{tenant}/orders	List orders with optional date filters
GET	/api/{tenant}/products	List products
POST	/api/{tenant}/sync	Trigger manual data sync from Shopify
4. Data Models

tenants
tenant_id (PK), name, shopify_api_key, shopify_api_secret, shop_url

customers
id (PK), tenant_id (FK), name, email, phone, created_at

orders
id (PK), tenant_id (FK), order_date, amount, customer_id (FK)

products
id (PK), tenant_id (FK), title, sku, price, created_at

5. Next Steps to Productionize

Add Redis/RabbitMQ for asynchronous ingestion of large data sets.

Implement OAuth for secure Shopify authentication per tenant.

Build automated tests and CI/CD pipelines.

Improve the dashboard with more metrics and filters.

Use a secrets manager or environment variables for API credentials.

📹 Demo Video

(Add your demo video link here when ready.)
