# 🏦 E-Banking System

A secure **full-stack online banking application** built with **Spring Boot, React.js, Spring Security, JWT, Redis, MySQL, and Razorpay**. The application provides secure user onboarding, bank account management, deposits, fund transfers, transaction tracking, and an administrative dashboard.

---

## 🚀 Features

### 👤 User Features

* User registration with email verification
* OTP-based account verification
* Secure login using JWT authentication
* Password validation and secure password handling
* Create and manage bank accounts
* View account balance
* Deposit money using Razorpay
* Transfer funds between bank accounts
* View transaction history
* View credit and debit transactions
* Password reset functionality
* Responsive dark-mode user interface

### 🛡️ Admin Features

* Secure admin authentication
* View registered users
* View bank accounts
* Approve pending bank accounts
* Block and unblock accounts
* View account details
* View all banking transactions
* Manage user and account access

---

## 🛠️ Tech Stack

### Backend

* Java
* Spring Boot
* Spring Security
* JWT
* Spring Data JPA / Hibernate
* REST APIs
* MySQL
* Redis
* JavaMail

### Frontend

* React.js
* React Router
* Axios
* Bootstrap
* JavaScript
* HTML
* CSS

### Payment

* Razorpay Payment Gateway

### Development Tools

* Git
* GitHub
* Postman
* Maven
* IntelliJ IDEA / Eclipse
* VS Code

---

## 🏗️ System Architecture

```text
                    ┌──────────────────────┐
                    │      React.js        │
                    │      Frontend        │
                    └──────────┬───────────┘
                               │
                            Axios
                               │
                               ▼
                    ┌──────────────────────┐
                    │    Spring Boot       │
                    │      REST API        │
                    └──────────┬───────────┘
                               │
              ┌────────────────┼────────────────┐
              │                │                │
              ▼                ▼                ▼
       ┌────────────┐   ┌────────────┐   ┌────────────┐
       │   MySQL    │   │   Redis    │   │  Razorpay  │
       │  Database  │   │    OTP     │   │  Payments  │
       └────────────┘   └────────────┘   └────────────┘
```

---

## 🔐 Authentication & Security

The application uses **Spring Security and JWT** to provide stateless authentication.

### Authentication Flow

```text
User Login
    │
    ▼
Credentials Validation
    │
    ▼
Spring Security
    │
    ▼
JWT Token Generated
    │
    ▼
Token Sent to React
    │
    ▼
Axios Interceptor
    │
    ▼
JWT Added to API Requests
    │
    ▼
JWT Filter Validates Token
    │
    ▼
Protected API Access
```

### Security Features

* JWT-based stateless authentication
* Custom JWT authentication filter
* Spring Security authorization
* Role-based access control
* Password hashing
* Protected REST endpoints
* DTO-based request validation
* Global exception handling
* OTP-based email verification

---

## 📧 OTP Verification

The application uses **email-based OTP verification** during user registration.

### Flow

```text
User Registration
       │
       ▼
Generate OTP
       │
       ▼
Store OTP Temporarily in Redis
       │
       ▼
Send OTP via Email
       │
       ▼
User Enters OTP
       │
       ▼
Verify OTP
       │
       ▼
Complete Registration
```

Redis is used for temporary OTP storage rather than permanently storing OTP information in the database.

---

## 💳 Razorpay Payment Integration

The application integrates **Razorpay** to allow users to deposit money into their bank accounts.

### Deposit Flow

```text
User Selects Deposit Amount
          │
          ▼
Spring Boot Creates Razorpay Order
          │
          ▼
Razorpay Checkout
          │
          ▼
User Completes Payment
          │
          ▼
Payment Response
          │
          ▼
Backend Verifies Payment
          │
          ▼
Transaction Created
          │
          ▼
Account Balance Updated
```

Payment verification is performed on the backend before updating the user's banking balance and transaction records.

---

## 🏦 Bank Account Management

Users can create and manage their bank accounts with validated information such as:

* Name
* PAN
* Aadhaar
* Address
* Account details

New accounts remain **inactive/pending until approved by an administrator**.

Administrators can:

* Approve accounts
* Block accounts
* Unblock accounts
* View account information

---

## 💰 Transaction Management

The application maintains transaction records for banking operations.

Each transaction contains information such as:

* Transaction type
* Credit / Debit
* Transaction amount
* Previous balance
* Updated balance
* Timestamp
* Account information

Supported operations include:

* Deposits
* Fund transfers
* Credit transactions
* Debit transactions
* Transaction history

---

## 👨‍💼 Admin Dashboard

The admin module provides centralized management of the banking system.

### Admin capabilities

* View all users
* View pending accounts
* Approve accounts
* Block/unblock accounts
* View bank account details
* View transactions
* Manage user access

---

## 🎨 Frontend

The frontend is developed using **React.js** with a responsive dark-mode interface.

### Frontend Technologies

* React.js
* React Router
* Axios
* Bootstrap
* JavaScript
* HTML5
* CSS3

### Frontend Features

* Protected routes
* Role-based navigation
* Axios token interceptor
* Form validation
* Toast notifications
* Responsive UI
* User and admin dashboards
* API integration with Spring Boot

---

## 📂 Project Structure

### Backend

```text
backend/
├── src/
│   └── main/
│       ├── java/
│       │   └── .../
│       │       ├── controller/
│       │       ├── service/
│       │       ├── repository/
│       │       ├── entity/
│       │       ├── dto/
│       │       ├── mapper/
│       │       ├── security/
│       │       ├── exception/
│       │       └── config/
│       │
│       └── resources/
│           └── application.properties
│
└── pom.xml
```

### Frontend

```text
frontend/
├── src/
│   ├── components/
│   ├── pages/
│   ├── services/
│   ├── routes/
│   ├── context/
│   └── App.jsx
│
├── public/
└── package.json
```

---

## ⚙️ Installation & Setup

### Prerequisites

Make sure the following are installed:

* Java 17+
* Maven
* Node.js
* npm
* MySQL
* Redis

---

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/e-banking-springboot-rest-api.git

cd e-banking-springboot-rest-api
```

---

### 2. Configure MySQL

Create the database:

```sql
CREATE DATABASE ebanking;
```

Update the database configuration in:

```text
backend/src/main/resources/application.properties
```

Example:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/ebanking
spring.datasource.username=YOUR_USERNAME
spring.datasource.password=YOUR_PASSWORD

spring.jpa.hibernate.ddl-auto=update
```

---

### 3. Configure Redis

Make sure Redis is running locally.

Example configuration:

```properties
spring.data.redis.host=localhost
spring.data.redis.port=6379
```

---

### 4. Configure Email

Add your email configuration:

```properties
spring.mail.host=smtp.gmail.com
spring.mail.port=587
spring.mail.username=YOUR_EMAIL
spring.mail.password=YOUR_APP_PASSWORD
spring.mail.properties.mail.smtp.auth=true
spring.mail.properties.mail.smtp.starttls.enable=true
```

> Use environment variables or a secure configuration method for credentials. Do not commit passwords, API keys, or secrets to GitHub.

---

### 5. Configure Razorpay

Add your Razorpay credentials securely:

```properties
razorpay.key.id=YOUR_KEY_ID
razorpay.key.secret=YOUR_KEY_SECRET
```

Do not commit real Razorpay credentials to the repository.

---

### 6. Start the Backend

Navigate to the backend directory:

```bash
cd backend
```

Build the project:

```bash
mvn clean install
```

Run the application:

```bash
mvn spring-boot:run
```

---

### 7. Start the Frontend

Open another terminal:

```bash
cd frontend
npm install
npm start
```

The frontend will connect to the Spring Boot REST API.

---

## 🔌 API Modules

The backend provides REST APIs for major banking operations, including:

| Module         | Operations                            |
| -------------- | ------------------------------------- |
| Authentication | Registration, Login, OTP Verification |
| Users          | User Management                       |
| Accounts       | Create, Approve, Block, Unblock       |
| Transactions   | Deposit, Transfer, History            |
| Admin          | User and Account Management           |
| Payments       | Razorpay Order & Payment Verification |

---

## 🧠 Key Learning Outcomes

Through this project, I gained practical experience in:

* Building full-stack applications using **Spring Boot and React**
* Designing and developing **REST APIs**
* Implementing **JWT authentication**
* Configuring **Spring Security**
* Implementing **role-based authorization**
* Working with **MySQL and JPA/Hibernate**
* Using **Redis for temporary data storage**
* Implementing **OTP-based email verification**
* Integrating a third-party **payment gateway**
* Building responsive React interfaces
* Handling frontend-backend API communication
* Implementing layered backend architecture
* Exception handling and request validation

---

## ⚠️ Challenges Faced

### 1. JWT Authentication

Implemented a custom JWT filter to validate authentication tokens for protected API endpoints.

### 2. Role-Based Authorization

Configured Spring Security to differentiate between **ADMIN** and **USER** roles and restrict access to protected operations.

### 3. Razorpay Integration

Handled Razorpay order creation, checkout integration, and backend payment verification before updating account balances.

### 4. OTP Management

Used Redis to temporarily store OTP information during registration and verification.

### 5. Frontend-Backend Integration

Connected React components with Spring Boot REST APIs using Axios and implemented token-based request handling.

---

## 🔮 Future Enhancements

* Add transaction pagination and advanced filtering
* Add downloadable transaction statements
* Implement two-factor authentication
* Add email/SMS transaction notifications
* Add advanced admin analytics
* Add account statement generation
* Deploy backend and frontend to cloud infrastructure
* Add automated unit and integration testing

---

## 👨‍💻 Author

**Maruti Naik**

Computer Science & Engineering
Java | Spring Boot | React | REST APIs | MySQL

### Connect With Me

* GitHub: `https://github.com/Maruti1887`
---

## ⭐ Project Highlights

> A full-stack banking application demonstrating secure authentication, role-based authorization, REST API development, payment gateway integration, OTP verification, Redis caching, database management, and modern React frontend development.
