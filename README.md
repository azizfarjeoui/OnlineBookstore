# 📚 Online Bookstore — Java Servlet Web Application

> A user-friendly web-based bookstore that enables customers to browse, purchase books online, and receive payment receipts — while giving administrators full control over inventory and sales history.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Architecture](#architecture)
- [Installation](#installation)
- [Database Setup](#database-setup)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [License](#license)

---

## 📌 Overview

**Online Bookstore** is a mini web application developed using **Java Servlets, JDBC, and MySQL**. It provides a simple and intuitive interface for users to register, browse available books, purchase them, and receive payment receipts. Administrators have a dedicated panel to manage the entire book inventory and monitor sales history.

This project was built as a practical implementation of **HTTP Servlets in Java**, demonstrating core backend concepts including request handling, session management, database connectivity via JDBC, and role-based access control.

---

## ✨ Features

### 👤 User
- 📝 **Register / Login** — Create a new account or log in to an existing one
- 📖 **Browse Books** — View all available books with details and prices
- 🛒 **Select & Buy** — Add books to cart with desired quantity
- 💳 **Purchase** — Complete the buying process securely
- 🧾 **Payment Receipt** — Download or view a receipt after successful payment

### 🔑 Admin
- ➕ **Add New Books** — Insert new books into the inventory
- 👁️ **View All Books** — Monitor current stock and details
- ❌ **Remove Books** — Delete books no longer available
- 🔢 **Manage Quantity** — Increase or decrease book stock
- 💰 **Change Price** — Update pricing for any book
- 📊 **Sales History** — Track and maintain complete book selling records

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | HTML, CSS, JavaScript, Bootstrap |
| **Backend** | Java (JDK 8+), HTTP Servlets |
| **Database Connectivity** | JDBC |
| **Database** | MySQL |
| **Server** | Apache Tomcat |

---

## 🏗️ Architecture

The project follows a classic **MVC-like Servlet architecture**:

```
Client (Browser)
      │
      ▼
 HTTP Request
      │
      ▼
 Servlet (Controller)
      │
      ├── Business Logic (Java Classes)
      │
      └── JDBC → MySQL Database
      │
      ▼
 JSP / HTML Response → Client
```

---

## 📁 Project Structure

```
OnlineBookstore/
├── src/
│   ├── servlets/
│   │   ├── LoginServlet.java
│   │   ├── RegisterServlet.java
│   │   ├── BookServlet.java
│   │   ├── CartServlet.java
│   │   ├── PaymentServlet.java
│   │   └── AdminServlet.java
│   ├── dao/
│   │   ├── UserDAO.java
│   │   ├── BookDAO.java
│   │   └── OrderDAO.java
│   ├── model/
│   │   ├── User.java
│   │   ├── Book.java
│   │   └── Order.java
│   └── utils/
│       └── DBConnection.java
├── WebContent/
│   ├── index.html
│   ├── login.html
│   ├── register.html
│   ├── books.jsp
│   ├── cart.jsp
│   ├── receipt.jsp
│   ├── admin/
│   │   ├── dashboard.jsp
│   │   ├── addBook.jsp
│   │   └── salesHistory.jsp
│   └── css/ js/
├── WEB-INF/
│   └── web.xml
└── README.md
```

---

## ⚙️ Installation

### Prerequisites

- Java JDK 8+
- Apache Tomcat 9+
- MySQL Server
- Eclipse IDE / IntelliJ IDEA (with Dynamic Web Project support)

### Steps

```bash
# 1. Clone the repository
git clone https://github.com/your-username/online-bookstore.git

# 2. Import the project into Eclipse as a Dynamic Web Project

# 3. Set up the database (see below)

# 4. Configure DB connection in DBConnection.java
#    Update: host, port, database name, username, password

# 5. Deploy the project to Apache Tomcat

# 6. Access the application at:
http://localhost:8080/OnlineBookstore/
```

---

## 🗄️ Database Setup

Run the following SQL script to set up the database:

```sql
CREATE DATABASE bookstore;
USE bookstore;

CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    role ENUM('user', 'admin') DEFAULT 'user'
);

CREATE TABLE books (
    id INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(100) NOT NULL,
    author VARCHAR(100),
    price DECIMAL(10,2) NOT NULL,
    quantity INT NOT NULL
);

CREATE TABLE orders (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT,
    book_id INT,
    quantity INT,
    total_price DECIMAL(10,2),
    order_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id),
    FOREIGN KEY (book_id) REFERENCES books(id)
);
```

---

## 🚀 Usage

### As a User
1. Go to the homepage and **Register** or **Login**
2. Browse the **Books catalog**
3. Select books and choose the **quantity**
4. Click **Buy** to complete the purchase
5. View and save your **Payment Receipt**

### As an Admin
1. Login with admin credentials
2. Access the **Admin Dashboard**
3. Add, remove, or update books and prices
4. Monitor **Sales History**

---

## 📄 License

This project is licensed under the MIT License.

---

> Built with ☕ by **Aziz** — TEK-UP University, ING-4-SSIR
