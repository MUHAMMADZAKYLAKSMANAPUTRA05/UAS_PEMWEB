# 📦 Stocks Management System 

**Stock** Stock adalah solusi manajemen inventaris yang kuat dan intuitif yang dibangun menggunakan Laravel dan FilamentPHP, dirancang untuk menyederhanakan pengelolaan stok, pesanan, pemasok, dan peran pengguna — semuanya dalam satu sistem terintegrasi.

Baik Anda mengelola gudang, bisnis kecil, maupun operasi skala besar, StockX menyediakan semua alat yang Anda butuhkan untuk menjaga inventaris tetap tertata dan terkendali.


## 🚀 Key Features

### 📦 Inventory Management
- **Product Categories** – Create, update, soft-delete, and manage product categories.
- **Suppliers** – Maintain supplier records with full CRUD capabilities.
- **Products** – Track products with key details like quantity, supplier, pricing, and category.

### 📑 Order Management
- **Order Handling** – Create and manage orders with automatic stock validation and dynamic inventory updates.
- **Stock Validation** – Ensure product availability during order processing.
- **Low Stock Alerts** – Email notifications when stock dips below a set threshold.

### 👥 User & Role Management
- **User Admin** – Create, edit, and manage users with role assignments.
- **Role-Based Access Control (RBAC)** – Fine-tuned permission handling with **Filament Shield**.

### 🔔 Notifications
- **Low Stock Emails** – Automatic alerts to notify admins when stock is low.

### 📊 Dashboard & Analytics
- **Interactive Charts** – Visualize sales and inventory trends.
- **Quick Stats** – Glance at total users, products, orders, and alerts.

### 🧭 Global Search
- **Smart Search** – Look up products, orders, and suppliers with rich result details.
- **Quick Navigation** – Jump straight to the item’s page from search results.

### 🔍 Filters & Tabs
- **Order Filters** – Filter by custom timeframes like today, this week, or this year.
- **Supplier Tabs** – Organize suppliers by product categories.

### 🔐 Authentication & Security
- **Secure Login** – Full auth system with email verification.
- **Permissions System** – Restrict access by user roles for enhanced security.

## 🖼️ Screenshots

Here’s a quick peek at what StockX looks like in action:

- **Dashboard**  
  ![Dashboard](./screenshots/127.0.0.1_8000_stocks-manager%20(9).png)
  ![Dashboard](./screenshots/127.0.0.1_8000_stocks-manager%20(15).png)

- **Products**  
  ![Products](./screenshots/127.0.0.1_8000_stocks-manager%20(8).png)
  ![Products](./screenshots/127.0.0.1_8000_stocks-manager%20(16).png)

- **Orders**  
  ![Orders](./screenshots/127.0.0.1_8000_stocks-manager%20(7).png)
  ![Orders](./screenshots/127.0.0.1_8000_stocks-manager_orders.png)

- **Create Order**  
  ![Create Order](./screenshots/127.0.0.1_8000_stocks-manager%20(10).png)

- **Roles**  
  ![Roles](./screenshots/127.0.0.1_8000_stocks-manager%20(12).png)

- **Edit Role**  
  ![Edit Role](./screenshots/127.0.0.1_8000_stocks-manager%20(13).png)

- **Email Notification (Low Stock)**  
  ![Email](./screenshots/Screenshot%20from%202025-04-04%2005-00-18.png)


## ⚙️ Deployment Guide

### 📋 Prerequisites

You only need **Docker** and **Docker Compose** installed on your system. All other dependencies (PHP, Composer, Node.js, MySQL, etc.) are handled inside containers.

- **Docker** ≥ 20.10
- **Docker Compose** ≥ 1.29

> If you prefer manual installation, see the [Manual Setup](#manual-setup) section below.

### 🐳 Docker Deployment (Recommended)

#### 1. Clone the Repository
```bash
git clone https://github.com/abogo-nono/StocksX.git
cd StocksX
```

#### 2. Copy and Configure Environment Variables
```bash
cp .env.example .env
# Edit .env as needed (DB, mail, etc.)
```

#### 3. Build and Start the Containers
```bash
docker-compose up --build -d
```

- This will build the app container, set up MySQL, and run all necessary services.
- All dependencies are installed automatically inside the containers.

#### 4. Run Migrations, Seeders, and Setup Commands
```bash
docker-compose exec app php artisan migrate --seed
docker-compose exec app php artisan storage:link
docker-compose exec app php artisan make:filament-user
docker-compose exec app php artisan shield:install --fresh
docker-compose exec app php artisan shield:generate --all
docker-compose exec app php artisan shield:super-admin --user=1
```

#### 5. Access the Application
- Visit [http://localhost:9000](http://localhost:9000) (or the port you mapped)

---

### 🛠️ Manual Setup (For Development/Advanced Users)

If you want to run the app without Docker, follow these steps:

#### Prerequisites
- **PHP** ≥ 8.2  
- **Composer** ≥ 2.3  
- **Node.js** ≥ 18.8  
- **NPM** ≥ 8.18  
- **MySQL** ≥ 8.0  
- **Mailpit** – For testing email notifications  

#### Installation Steps

1. Install dependencies:
```bash
composer install
npm install
```
2. Build frontend assets:
```bash
npm run build
```
3. Set up `.env` and database as described above.
4. Run migrations, seeders, and setup commands as above.
5. Start the Laravel server:
```bash
php artisan serve
```
6. (Optional) Start Vite dev server for hot reload:
```bash
npm run dev
```
