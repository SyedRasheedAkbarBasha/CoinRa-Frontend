# 🧾 Wallet Management System Backend

A **Node.js + Express** backend for managing personal finances, transactions, dream savings, and financial summaries — powered by **PostgreSQL (Neon)** and **Redis** for secure and scalable performance.

---

## 📋 Overview

The **Wallet Management System Backend** is a RESTful API built to manage user transactions, savings goals, and financial summaries. It includes rate limiting, cron jobs, optimized queries, and secure database operations to ensure reliability and performance.

---

## ✨ Features

- **Transaction Management** – Create, delete, and retrieve transactions  
- **Dream Savings Goals** – Add and track long-term savings purposes  
- **Financial Summary** – Balance, income, and expense calculations  
- **Rate Limiting** – Redis-based request throttling  
- **Health Monitoring** – Cron job to keep server alive  
- **Secure Data Handling** – PostgreSQL with robust transaction logic  

---

## 🛠️ Technologies Used

- **Node.js** – Runtime environment  
- **Express.js** – API framework  
- **PostgreSQL** – Database  
- **Neon** – Serverless PostgreSQL hosting  
- **Redis** – Rate limiting and caching  
- **Cron** – Scheduled tasks  
- **CORS** – API access control  

---

## 🗄️ Database Schema

### 🧮 Transactions Table

```sql
CREATE TABLE transactions(
    id SERIAL PRIMARY KEY,
    user_id VARCHAR(255) NOT NULL,
    title VARCHAR(255) NOT NULL,
    amount DECIMAL(10,2) NOT NULL,
    category VARCHAR(255) NOT NULL,
    created_at DATE NOT NULL DEFAULT CURRENT_DATE
);
```
```
## 🎯 Dream Savings Table

Copy code
CREATE TABLE dream_savings (
    id SERIAL PRIMARY KEY,
    user_id VARCHAR(255) NOT NULL,
    title VARCHAR(255) NOT NULL,
    amount DECIMAL(10,2) NOT NULL,
    created_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
🚀 Getting Started
📌 Prerequisites
Node.js 16+

PostgreSQL database (Neon recommended)

Redis instance (Upstash recommended)

⚙️ Installation & Setup
1️⃣ Clone the repository
bash
Copy code
git clone https://github.com/yourusername/wallet-management-backend.git
cd wallet-management-backend
2️⃣ Install dependencies
bash
Copy code
npm install
3️⃣ Configure environment variables
Create a .env file:

ini
Copy code
DATABASE_URL=your_neon_postgresql_connection_string
UPSTASH_REDIS_REST_URL=your_redis_url
UPSTASH_REDIS_REST_TOKEN=your_redis_token
PORT=5001
NODE_ENV=development
API_URL=your_deployment_url
4️⃣ Initialize the database
Tables are auto-created on first server start.

5️⃣ Run the server
bash
Copy code
cd backend
npm start
📡 API Endpoints
📍 Transactions
Method	Endpoint	Description
GET	/api/transactions/:userId	Fetch all transactions
POST	/api/transactions	Create transaction
DELETE	/api/transactions/:id	Delete transaction
GET	/api/transactions/summary/:userId	Get balance/income/expense

🎯 Dream Savings
Method	Endpoint	Description
GET	/api/transactions/dream-savings/:userId	Get all savings goals
POST	/api/transactions/dream-savings/:userId	Add savings goal
DELETE	/api/transactions/dream-savings/:userId	Delete savings goal

❤️ Health Check
Method	Endpoint	Description
GET	/health	System status

🔒 Security Features
Redis-based rate limiting (100 requests / 60 seconds)

Error handling and input validation

CORS protection

SQL injection prevention (parameterized queries)

⚙️ Configuration Details
🕒 Cron Job
Pings /health every 14 minutes in production

Keeps deployment active

🚦 Rate Limiting
Redis sliding window algorithm

Protects API from abuse and DDoS

🚀 Deployment
The backend is optimized for platforms like Render, Railway, Vercel Functions, etc.

Deployment steps:

Add environment variables in dashboard

Ensure Neon PostgreSQL URL is correct

Ensure Redis credentials are valid

Start server — tables auto-create on first run

🤝 Contributing
Contributions are welcome!
Feel free to open issues or submit pull requests for improvements.
