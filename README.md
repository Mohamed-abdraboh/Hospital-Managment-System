# 🏥 MEDICA — Hospital Management System

A full-stack Hospital Management System designed to streamline patient registration, doctor workflows, appointments, lab reports, billing, and payments across a modern healthcare facility.

---

## 📑 Table of Contents

1. [Project Overview](#-project-overview)
2. [Architecture](#-architecture)
3. [Tech Stack](#-tech-stack)
4. [Key Features](#-key-features)
5. [Modules](#-modules)
6. [Getting Started](#-getting-started)
7. [Environment Variables](#-environment-variables)
8. [API Documentation](#-api-documentation)
9. [Project Structure](#-project-structure)

---

## 📋 Project Overview

**MEDICA** is a comprehensive Hospital Management System that covers the full patient lifecycle — from registration and appointment booking to lab testing, diagnosis, ward admission, billing, and online payment. It caters to multiple roles: **Admin**, **Doctor**, **Nurse/Staff**, and **Patient**.

Each patient is assigned a unique ID that links all records across departments, enabling seamless care coordination.

---

## 🏗 Architecture

```
┌─────────────────────────────────┐
│         React Frontend          │  ← Port 3000
│     (Redux + TailwindCSS)       │
└────────────────┬────────────────┘
                 │ REST API / WebSocket
┌────────────────▼────────────────┐
│      Spring Boot Backend        │  ← Port 8080
│   (REST API + WebSocket + JWT)  │
└──┬──────────┬────────┬──────────┘
   │          │        │
   ▼          ▼        ▼
PostgreSQL  Elasticsearch  AWS S3
(Primary)  (Search Index) (File Storage)
```

---

## 🛠 Tech Stack

### Backend
| Technology | Version | Purpose |
|---|---|---|
| Spring Boot | 3.2.4 | Core application framework |
| Spring Security | 6 | Authentication & authorization |
| Spring Data JPA | — | ORM / database access |
| Spring WebSocket | — | Real-time chat & notifications |
| Spring Data Elasticsearch | — | Full-text search |
| Spring Mail | 3.2.5 | Email / OTP notifications |
| PostgreSQL | 15+ | Primary relational database |
| JWT (jjwt) | 0.12.5 | Stateless authentication |
| Stripe Java SDK | 26.0.0 | Online payment processing |
| AWS SDK S3 | 1.12.707 | File & image storage |
| Springdoc OpenAPI UI | 2.5.0 | Swagger API documentation |
| MapStruct | 1.4.2 | DTO mapping |
| Lombok | 1.18.30 | Boilerplate reduction |
| QueryDSL | — | Type-safe JPA queries |
| Thymeleaf | — | Email templates |
| Java | 17 | Language version |
| Maven | 3+ | Build tool |

### Frontend
| Technology | Version | Purpose |
|---|---|---|
| React | 18 | UI framework |
| Redux Toolkit | — | State management |
| React Router | — | Client-side routing |
| TailwindCSS | 3 | Utility-first styling |
| Axios | — | HTTP client |
| PDF generation | — | Reports & invoices |

---

## ✨ Key Features

- 🔐 **JWT Authentication** — Secure stateless auth with role-based access control (RBAC)
- 📧 **OTP via Email** — Verification and password reset flows using Spring Mail + Thymeleaf templates
- 👨‍⚕️ **Doctor Management** — Profiles, scheduling, and patient assignments
- 🗓 **Appointment Booking** — Schedule, manage and track outpatient appointments
- 🏥 **Ward & Admission** — Inpatient admission, ward assignment, and discharge workflows
- 🧪 **Lab Tests & Reports** — Request lab tests, manage results, and generate reports
- 💊 **Medication & Diagnoses** — Prescriptions and diagnosis tracking per patient visit
- 🩺 **Examinations** — Clinical examination records linked to patient history
- 🧾 **Billing & Invoicing** — Automated bill generation with itemized services
- 💳 **Online Payments** — Stripe integration for secure payment processing
- 📂 **File Storage** — AWS S3 for medical documents and images
- 🔍 **Elasticsearch** — Full-text search across patient and clinical records
- 💬 **Real-time Chat** — WebSocket-based messaging between staff
- 📊 **Dashboard** — Summary statistics and analytics for administrators
- 📄 **PDF Reports** — Exportable reports from the React frontend

---

## 📦 Modules

| Module | Description |
|---|---|
| `auth` | Registration, login, JWT issuance, token refresh |
| `user` | User profile management, role assignment |
| `otp` | OTP generation, email delivery, and verification |
| `patient` | Patient registration, profile, unique ID assignment |
| `patienthistory` | Full patient medical history across visits |
| `doctor` | Doctor profiles, specializations, scheduling |
| `appointment` | OPD appointment booking and management |
| `admission` | Inpatient admission and discharge |
| `ward` | Ward and bed management |
| `examination` | Clinical examination records |
| `diagnoses` | Diagnosis entries per visit |
| `medication` | Prescriptions and medication tracking |
| `labtest` | Lab test requests and cataloging |
| `labreport` | Lab result entry and reporting |
| `bill` | Bill creation and itemization |
| `billservice` | Bill line items / services pricing |
| `payment` | Stripe-based payment processing |
| `chat` | WebSocket real-time messaging |
| `dashboard` | Aggregate statistics and KPIs |
| `email` | Transactional email service |

---

## 🚀 Getting Started

### Prerequisites

- Java 17+
- Maven 3.8+
- PostgreSQL 15+ (running locally or Docker)
- Elasticsearch 8+ (optional, for search features)
- Node.js 18+ and npm (for the React frontend)
- An AWS S3 bucket (for file uploads)
- A Stripe account (for payment features)

### 1. Clone the Repository

```bash
git clone https://github.com/Mohamed-abdraboh/Hospital-Managment-System.git
cd Hospital-Managment-System
```

### 2. Configure the Backend

Copy the example environment file and fill in your values:

```bash
cd backend-spring/medica
cp src/main/resources/application.properties.example src/main/resources/application.properties
# Edit application.properties with your database, AWS, Stripe, and mail credentials
```

### 3. Run the Backend

```bash
./mvnw spring-boot:run
```

The API will be available at `http://localhost:8080`.

### 4. Run the React Frontend

```bash
cd react
npm install
npm start
```

The frontend will be available at `http://localhost:3000`.

---

## ⚙️ Environment Variables

| Variable | Description |
|---|---|
| `spring.datasource.url` | PostgreSQL JDBC URL |
| `spring.datasource.username` | Database username |
| `spring.datasource.password` | Database password |
| `jwt.secret` | Secret key for JWT signing |
| `jwt.expiration` | JWT token expiration (ms) |
| `spring.mail.host` | SMTP host (e.g. smtp.gmail.com) |
| `spring.mail.username` | Email sender address |
| `spring.mail.password` | Email sender password / app password |
| `aws.s3.bucket` | S3 bucket name |
| `aws.s3.access-key` | AWS access key ID |
| `aws.s3.secret-key` | AWS secret access key |
| `aws.s3.region` | AWS region (e.g. `us-east-1`) |
| `stripe.secret-key` | Stripe secret API key |
| `spring.elasticsearch.uris` | Elasticsearch URI |

---

## 📖 API Documentation

Interactive Swagger UI is available at:

```
http://localhost:8080/swagger-ui/index.html
```

OpenAPI JSON spec:

```
http://localhost:8080/v3/api-docs
```

---

## 📁 Project Structure

```
Hospital-Managment-System/
├── backend-spring/
│   └── medica/
│       ├── pom.xml
│       └── src/
│           └── main/
│               ├── java/org/hms/medica/
│               │   ├── admission/
│               │   ├── appointment/
│               │   ├── auth/
│               │   ├── bill/
│               │   ├── billservice/
│               │   ├── chat/
│               │   ├── config/
│               │   ├── dashboard/
│               │   ├── diagnoses/
│               │   ├── doctor/
│               │   ├── email/
│               │   ├── examination/
│               │   ├── labreport/
│               │   ├── labtest/
│               │   ├── medication/
│               │   ├── otp/
│               │   ├── patient/
│               │   ├── patienthistory/
│               │   ├── payment/
│               │   ├── user/
│               │   └── ward/
│               └── resources/
├── react/                    # React + Redux frontend
    └── src/
        ├── components/       # Feature components
        ├── redux/            # State management
        ├── router/           # App routing
        └── util/             # Helpers & utilities

```

---

## 📄 License

This project is intended for educational and portfolio purposes.
