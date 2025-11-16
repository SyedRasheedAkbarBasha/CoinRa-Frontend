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

### 🎯 Dream Savings Table

```sql
CREATE TABLE dream_savings (
    id SERIAL PRIMARY KEY,
    user_id VARCHAR(255) NOT NULL,
    title VARCHAR(255) NOT NULL,
    amount DECIMAL(10,2) NOT NULL,
    created_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

---

## 🚀 Getting Started

### 📌 Prerequisites

- Node.js 16+
- PostgreSQL database (Neon recommended)
- Redis instance (Upstash recommended)

---

## ⚙️ Installation & Setup

### 1️⃣ Clone the repository

```bash
git clone https://github.com/yourusername/wallet-management-backend.git
cd wallet-management-backend
```

### 2️⃣ Install dependencies

```bash
npm install
```

### 3️⃣ Configure environment variables  
Create a **.env** file:

```ini
DATABASE_URL=your_neon_postgresql_connection_string
UPSTASH_REDIS_REST_URL=your_redis_url
UPSTASH_REDIS_REST_TOKEN=your_redis_token
PORT=5001
NODE_ENV=development
API_URL=your_deployment_url
```

### 4️⃣ Initialize the database

_No manual steps required—tables are auto-created on first server start._

### 5️⃣ Run the server

```bash
cd backend
npm start
```

---

## 📡 API Endpoints

### 📍 Transactions

- **GET /api/transactions/:userId** — Fetch all transactions  
- **POST /api/transactions** — Create a transaction  
- **DELETE /api/transactions/:id** — Delete a transaction  
- **GET /api/transactions/summary/:userId** — Get balance, income & expenses  

---

## 🎯 Dream Savings

- **GET /api/transactions/dream-savings/:userId** — Get all savings goals  
- **POST /api/transactions/dream-savings/:userId** — Add savings goal  
- **DELETE /api/transactions/dream-savings/:userId** — Delete savings goal  

---

## ❤️ Health Check

```plaintext
GET /health
```

---

## 🔒 Security Features

- Redis-based rate limiting (100 requests / 60 seconds)  
- Input validation & error handling  
- CORS configuration  
- Parameterized SQL queries (SQL injection safe)  

---

## ⚙️ Configuration Details

### 🕒 Cron Job  
- Pings **/health** every 14 minutes in production  
- Keeps the deployment active  

### 🚦 Rate Limiting  
- Implemented using Redis sliding window algorithm  
- Protects API from abuse & DDoS attempts  

---

## 🚀 Deployment

- Pre-configured for deployment on **Render**  
- Add all environment variables in the hosting platform  
- Backend auto-creates tables on first boot  

---

## 🤝 Contributing

Contributions are welcome!  
Open issues or submit pull requests to enhance the project.

