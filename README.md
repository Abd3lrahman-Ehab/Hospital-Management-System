# 🏥 Hospital Management System

A full-stack Hospital Management System built with the **MERN Stack** (MongoDB, Express.js, React, Node.js), featuring **Redux** for state management, **TailwindCSS** for styling, and **Framer Motion** for animations.

## 📋 Overview

This system streamlines hospital operations by providing role-based interfaces for **Admins**, **Doctors**, **Nurses**, and **Patients**. It covers appointment scheduling, medical records management, staff management, department organization, and communication between healthcare providers and patients.

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| **Frontend** | React 18 + Vite, TailwindCSS, Framer Motion, Redux Toolkit |
| **Backend** | Node.js, Express.js |
| **Database** | MongoDB (Mongoose ODM) |
| **Authentication** | JWT + bcrypt |
| **Security** | Rate Limiting, CORS, Role-based Access Control |

## ✨ Features

### Patient Portal
- Register/Login with secure authentication
- Book appointments with available doctors
- View appointment history
- Manage medications & medical history
- Contact hospital via contact form

### Doctor Portal
- View assigned appointments
- Manage patient communications
- Update profile information

### Nurse Portal
- Manage patient medications
- Bed management
- Update profile information

### Admin Dashboard
- Dashboard with real-time statistics (patients, doctors, nurses, departments, queries)
- Full CRUD for Doctors, Nurses, Patients, and Departments
- View contact form submissions
- Newsletter management

## 🔗 Web Services / API Endpoints

The backend exposes **31 RESTful API endpoints** across 6 controllers:

### Auth (`/auth`)
| Method | Endpoint | Description | Request Body |
|--------|----------|-------------|-------------|
| POST | `/auth/register` | Register new patient | `{ userName, email, password }` |
| POST | `/auth/login` | Login (patient/doctor/nurse) | `{ email, password }` |
| GET | `/auth/logout` | Logout & clear token | — |

### User (`/user`)
| Method | Endpoint | Description | Request Body / Params |
|--------|----------|-------------|----------------------|
| POST | `/user/add-contact-us` | Submit contact form | `{ name, phone, email, message }` |
| GET | `/user/get-users` | Get all users | — |
| PUT | `/user/profile-update` | Update user profile | `{ userId, updatedProfile }` |
| GET | `/user/get-medications/:userEmail` | Get medications | param: `userEmail` |
| POST | `/user/add-medications/:userEmail` | Add medication | `{ name, dosage, frequency }` |

### Doctor (`/doctor`)
| Method | Endpoint | Description | Request Body / Params |
|--------|----------|-------------|----------------------|
| GET | `/doctor/get-doctors` | Get all doctors | — |
| PUT | `/doctor/profile-update` | Update doctor profile | `{ userId, updatedProfile }` |
| DELETE | `/doctor/delete-doctor/:id` | Delete a doctor | param: `id` |
| POST | `/doctor/add-doctor` | Add new doctor | `{ name, email, specialization }` |
| GET | `/doctor/get-appointments/:id` | Get doctor's appointments | param: `id` |
| POST | `/doctor/add-message` | Send message | `{ email, message, from }` |
| GET | `/doctor/get-message/:email` | Get messages | param: `email` |

### Nurse (`/nurse`)
| Method | Endpoint | Description | Request Body / Params |
|--------|----------|-------------|----------------------|
| GET | `/nurse/get-nurses` | Get nurses (with dept) | — |
| GET | `/nurse/get-allNurses` | Get all nurses | — |
| POST | `/nurse/add-nurse` | Add new nurse | `{ name, email, department }` |
| PUT | `/nurse/profile-update` | Update nurse profile | `{ userId, updatedProfile }` |

### Appointment (`/appointment`)
| Method | Endpoint | Description | Request Body / Params |
|--------|----------|-------------|----------------------|
| GET | `/appointment/get-appointments/:email` | Get user's appointments | param: `email` |
| GET | `/appointment/get-appointment/:id` | Get doctor's appointments | param: `id` |
| POST | `/appointment/add-appointment` | Book appointment | `{ doctor, patient, appointmentDate, reason, phone, email, time }` |

### Admin (`/admin`)
| Method | Endpoint | Description | Request Body / Params |
|--------|----------|-------------|----------------------|
| GET | `/admin/get-users` | Get all patients | — |
| DELETE | `/admin/delete-user/:id` | Delete a patient | param: `id` |
| GET | `/admin/get-contacts` | Get contact submissions | — |
| POST | `/admin/add-department` | Add department | `{ name, description, head, staff }` |
| DELETE | `/admin/delete-department/:id` | Delete department | param: `id` |
| GET | `/admin/get-department` | Get all departments | — |
| GET | `/admin/get-count` | Get dashboard stats | — |
| POST | `/admin/new-letter` | Send newsletter | `{ email }` |
| GET | `/admin/get-sent-newsletter` | Get sent newsletters | — |

## 📁 Project Structure

```
Hospital-Management-System/
├── backend/
│   ├── controllers/        # Route handlers (auth, user, doctor, nurse, appointment, admin)
│   ├── db/                 # MongoDB connection
│   ├── middlewares/        # CORS, auth, rate limiting, error handling
│   ├── models/             # Mongoose schemas (8 models)
│   ├── server.js           # Express app entry point
│   └── package.json
├── frontend/
│   ├── src/
│   │   ├── components/     # React components (Admin, Auth, Patient, Profile, Routes, Shared)
│   │   ├── page/           # Page-level components
│   │   ├── redux/          # Redux store & slices
│   │   ├── App.jsx         # Main app with routing
│   │   └── main.jsx        # Entry point
│   └── package.json
├── postman/                # Postman test collection
└── README.md
```

## 🚀 Getting Started

### Prerequisites
- [Node.js](https://nodejs.org/) (v18+)
- [MongoDB](https://www.mongodb.com/try/download/community)

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/<YOUR_USERNAME>/Hospital-Management-System.git
   cd Hospital-Management-System
   ```

2. **Setup Backend:**
   ```bash
   cd backend
   npm install
   ```

3. **Create `.env` file in `/backend`:**
   ```env
   DB_URI=mongodb://localhost:27017/hospital_db
   jwtsecret=your_jwt_secret_key
   PORT=4451
   ```

4. **Setup Frontend:**
   ```bash
   cd ../frontend
   npm install
   ```

5. **Run the application:**
   ```bash
   # Terminal 1 - Backend
   cd backend && npm start

   # Terminal 2 - Frontend
   cd frontend && npm run dev
   ```

## 🧪 Testing

- Postman collection available in `/postman/HMS_Tests.postman_collection.json`
- Import into Postman and run the full test suite
- See the test demo video for walkthrough

## 👥 Team Members

<!-- UPDATE THIS WITH YOUR ACTUAL TEAM INFO -->
| Name | Role | Responsibilities |
|------|------|-----------------|
| Member 1 | Team Lead / Backend | API development, authentication, database design |
| Member 2 | Frontend | React components, Redux state management, UI/UX |
| Member 3 | Full Stack | Doctor & Nurse modules, testing |
| Member 4 | Frontend / Testing | Patient portal, Postman tests, documentation |
| Member 5 | Backend / DevOps | Admin module, deployment, API documentation |

## 📄 License

This project is developed for academic purposes.
