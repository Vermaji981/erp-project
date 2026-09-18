# SecureERP - Production-Ready Full-Stack MERN ERP Application

**SecureERP** is a complete, scalable, and enterprise-grade Enterprise Resource Planning (ERP) application engineered with the MERN stack (MongoDB, Express.js, React.js, Node.js). It includes authentication with JWT & bcrypt, granular Role-Based Access Control (RBAC), automatic stock tracking on sales and purchases, invoice printing, attendance and leave management, payroll formula calculation, security audit logging, system notifications, and interactive analytics.

---

## 🛠️ Technology Stack

- **Frontend**: React.js (Vite), React Router DOM (v6), Recharts, Lucide Icons, Custom CSS System
- **Backend**: Node.js, Express.js, Mongoose ORM, Express-Validator, Morgan
- **Database**: MongoDB (with Mongoose models & indexes, plus MongoDB Memory Server fallback for dev)
- **Security & Auth**: JWT (JSON Web Tokens), bcryptjs, Helmet, CORS, Express Rate Limit
- **HTTP Client**: Axios with Interceptors

---

## 📁 Directory & File Architecture

```
erp/
├── backend/
│   ├── config/
│   │   └── db.js                 # Database connection & memory fallback
│   ├── controllers/
│   │   ├── authController.js     # User registration, login, profile & user admin
│   │   ├── employeeController.js # Employee CRUD, search, filter, pagination
│   │   ├── departmentController.js# Department management & manager assignment
│   │   ├── productController.js  # Products catalog & low-stock alerts
│   │   ├── inventoryController.js# Stock tracking metrics & manual adjustments
│   │   ├── supplierController.js # Supplier CRUD & purchase history
│   │   ├── customerController.js # Customer CRM & order history
│   │   ├── purchaseController.js # Purchase orders & auto inventory inflow
│   │   ├── salesController.js    # Sales POS, stock check, auto stock outflow & invoice creation
│   │   ├── invoiceController.js  # Invoice listing & printable tax invoice
│   │   ├── attendanceController.js# Daily attendance marking & summaries
│   │   ├── leaveController.js    # Employee leave applications & approval workflow
│   │   ├── expenseController.js  # Ledger expenses & category filtering
│   │   ├── payrollController.js  # Monthly salary slips & formula calculations
│   │   ├── reportController.js   # Financial P&L, revenue & executive dashboard data
│   │   ├── auditLogController.js # Audit logs for administrative actions
│   │   └── notificationController.js# System alert notification triggers
│   ├── middleware/
│   │   ├── authMiddleware.js     # JWT token authentication validator
│   │   ├── roleMiddleware.js     # Granular RBAC role validator
│   │   ├── errorMiddleware.js    # Centralized HTTP error handler
│   │   └── validationMiddleware.js# Express-validator error handler
│   ├── models/                   # 15 Mongoose schemas
│   ├── routes/                   # 17 Express REST API routers
│   ├── utils/                    # Audit logger utility
│   ├── validators/               # Input validation rules
│   ├── .env                      # Environment variables
│   ├── server.js                 # Server entry point
│   ├── seed.js                   # Comprehensive database seeder
│   └── package.json
│
└── frontend/
    ├── src/
    │   ├── components/           # Navbar, Sidebar, Modal, Table, StatsCard, Badge, PrintableInvoice
    │   ├── context/              # AuthContext (JWT auth state & role checking)
    │   ├── pages/                # 19 Module page views
    │   ├── services/             # Axios API client with interceptors
    │   ├── App.jsx               # Protected & Role-Protected route definitions
    │   ├── main.jsx
    │   └── index.css             # Enterprise design system
    ├── index.html
    ├── vite.config.js
    └── package.json
```

---

## 🔐 Role-Based Access Control (RBAC) Matrix

| Module / Page        | Admin | Manager | HR  | Accountant | Employee |
| :------------------- | :---: | :-----: | :-: | :--------: | :------: |
| **Executive Dashboard** |  ✅   |   ✅    | ❌  |     ❌     |    ✅    |
| **User Admin**       |  ✅   |   ❌    | ❌  |     ❌     |    ❌    |
| **Employees**        |  ✅   |   ✅    | ✅  |     ❌     |    ❌    |
| **Departments**      |  ✅   |   ❌    | ✅  |     ❌     |    ❌    |
| **Products & Catalog**|  ✅   |   ✅    | ❌  |     ❌     |    ❌    |
| **Inventory Tracking**|  ✅   |   ✅    | ❌  |     ❌     |    ❌    |
| **Suppliers**        |  ✅   |   ✅    | ❌  |     ❌     |    ❌    |
| **Customers (CRM)**  |  ✅   |   ✅    | ❌  |     ❌     |    ❌    |
| **Purchase Orders**  |  ✅   |   ✅    | ❌  |     ✅     |    ❌    |
| **Sales & Invoices** |  ✅   |   ✅    | ❌  |     ✅     |    ❌    |
| **Attendance**       |  ✅   |   ❌    | ✅  |     ❌     |    ✅    |
| **Leave Management** |  ✅   |   ✅    | ✅  |     ❌     |    ✅    |
| **Expense Ledger**   |  ✅   |   ❌    | ❌  |     ✅     |    ❌    |
| **Payroll Slips**    |  ✅   |   ❌    | ❌  |     ✅     |    ❌    |
| **Reports Analytics**|  ✅   |   ✅    | ❌  |     ✅     |    ❌    |
| **Audit Trail Logs** |  ✅   |   ❌    | ❌  |     ❌     |    ❌    |

---

## ⚡ Quick Start & Local Setup

### 1. Backend Setup

```bash
cd backend

# Install dependencies
npm install

# Seed default database accounts and sample records
npm run seed

# Start development backend server (Port 5000)
npm run dev
```

> **Note**: If a local MongoDB instance is not running on your machine, `backend/config/db.js` will automatically spin up an **In-Memory MongoDB Server** fallback for immediate seamless testing!

### 2. Frontend Setup

```bash
cd frontend

# Install dependencies
npm install

# Start Vite React development server (Port 5173)
npm run dev
```

Open your browser at `http://localhost:5173`.

---

## 🔑 Default Seed Account Credentials

> ⚠️ **IMPORTANT**: Change default credentials before deploying to production!

| Role       | Email                   | Password        |
| :--------- | :---------------------- | :-------------- |
| **Admin**  | `hv0563163@gmail.com` | `Happy@2003`   |
| **Manager**| `manager@secureerp.com` | `Manager@12345` |
| **HR**     | `hr@secureerp.com`      | `Hr@123456789`  |
| **Accountant**| `accountant@secureerp.com` | `Accountant@123` |
| **Employee**| `employee@secureerp.com` | `Employee@123`  |

*Note: The login screen features single-click quick demo buttons to switch between roles instantly during testing!*

---

## 📡 REST API Overview

### Authentication & Users
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User authentication & JWT issuance
- `GET /api/auth/me` - Get current user profile
- `GET /api/auth/users` - Admin get all users
- `PUT /api/auth/users/:id` - Admin update user role/status

### Inventory & Core Business
- `GET /api/products` - List products (with pagination, search, category & low-stock filter)
- `POST /api/products` - Create new product
- `GET /api/inventory` - Stock metrics & valuation
- `POST /api/inventory/adjust` - Manual stock adjustment
- `POST /api/purchases` - Create purchase order (auto stock increase)
- `POST /api/sales` - Create sale order (stock availability check -> auto stock decrease -> auto invoice generation)
- `GET /api/invoices` - Get generated tax invoices

### HR & Finance
- `GET /api/employees` - List employees with department population
- `POST /api/attendance` - Mark daily attendance
- `POST /api/leaves` - Apply for leave
- `PUT /api/leaves/:id/approve` - HR/Manager approve leave request
- `POST /api/payroll` - Generate monthly salary slip
- `GET /api/reports/dashboard` - Executive KPI metrics & charts data
- `GET /api/audit-logs` - Admin security audit logs

---

## 🛡️ Security Features

1. **Password Hashing**: Passwords encrypted with `bcryptjs` (salt round 10). Passwords are never returned in JSON responses (`select: false`).
2. **JWT Authentication**: Secured stateless token authentication with expiration.
3. **Helmet HTTP Headers**: Protection against standard web security vulnerabilities.
4. **Rate Limiting**: `express-rate-limit` enforced on `/api/auth` endpoints.
5. **MongoDB Object Validation**: All ID parameters validated before DB queries to prevent CastErrors.
6. **Audit Trails**: Critical operations automatically generate entries in the `AuditLog` collection.

---

## 🚀 Production Deployment

1. Set `NODE_ENV=production` in `backend/.env`.
2. Configure a production MongoDB Atlas URI in `MONGO_URI`.
3. Set a strong secret string in `JWT_SECRET`.
4. Build frontend: `cd frontend && npm run build`.
5. Serve the built static files from `frontend/dist` or deploy backend and frontend independently (e.g. Render, Railway, Vercel).
