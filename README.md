# 🏥 DeccanCare Hospital Management System

A comprehensive, production-ready **Hospital Management System** built with the **MERN Stack** (MongoDB, Express.js, React.js, Node.js). DeccanCare streamlines hospital operations with role-based access control, intelligent patient management, appointment scheduling, prescription generation, lab report tracking, and AI-powered medicine information lookup.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation & Setup](#installation--setup)
- [Environment Configuration](#environment-configuration)
- [Running the Application](#running-the-application)
- [User Roles & Workflows](#user-roles--workflows)
- [API Documentation](#api-documentation)
- [Database Models](#database-models)
- [Core Features in Detail](#core-features-in-detail)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## 🎯 Overview

DeccanCare is a comprehensive Hospital Management System that automates and streamlines hospital operations including patient management, appointment scheduling, prescription generation, lab report tracking, and staff management. The system features multi-role access control with specialized dashboards for administrators, doctors, receptionists, lab technicians, and patients.

Key highlights:
- ✅ **Full-featured** hospital operations platform
- ✅ **AI-integrated** medicine lookup with Google Generative AI
- ✅ **Secure** JWT-based authentication with role-based access control (RBAC)
- ✅ **Responsive** modern UI with animations and dark mode
- ✅ **Scalable** MongoDB backend with indexed queries
- ✅ **Production-ready** with comprehensive error handling

---

## 🌟 Key Features

### 👨‍💼 Admin Dashboard
- User statistics and role-based employee breakdown
- Staff approval/rejection workflows for doctors, receptionists, and lab technicians
- User activity tracking and monthly analytics
- Multi-report generation (user reports, activity logs, approval histories)
- Dark mode toggle for enhanced usability
- Email notifications for staff status changes
- Comprehensive audit trails

### 👨‍⚕️ Doctor Portal
- **Patient Management**: Search by ID, name, email, or phone number
- **Appointment Scheduling**: View, create, and manage patient appointments
- **Prescription Creation**: Generate prescriptions with medications and dosage
- **PDF Generation**: Auto-generated prescription PDFs for patients
- **Medical History**: Complete patient history viewing with medications and allergies
- **Statistics Dashboard**: Appointment analytics, pending prescriptions, completion rates
- **Appointment Completion**: Mark appointments as completed with notes

### 👩‍💼 Receptionist Dashboard
- Patient registration with auto-generated custom patient IDs
- Appointment listing with filters and sorting options
- Doctor availability and list retrieval
- Quick statistics (total patients, today's appointments, pending actions)
- Patient search and information retrieval
- Appointment coordination

### 🧪 Lab Technician Portal
- Lab report creation and management
- **Test Type Support**: Blood, Urine, X-Ray, MRI, CT Scan, ECG, and Custom tests
- Result documentation with detailed notes
- File attachments for test reports
- Status tracking (Pending, Completed, Cancelled)
- Report history and archival

### 👤 Patient Portal
- **OTP-based Login**: Secure SMS/Email OTP authentication
- **Appointment Booking**: Multi-step wizard with doctor selection and available time slots
- **Prescription Access**: View medications, instructions, and download PDFs
- **Lab Reports**: Track and download test results
- **Medical History**: Complete health records with medications and allergies
- **Notification Management**: Real-time alerts with unread badges
- **Profile Management**: Edit personal and medical information

### 🧬 AI Medicine Search (GenAI Integration)
- Upload and parse prescription PDFs
- AI-powered medicine extraction using Google Generative AI
- Detailed drug information: side effects, dosage, precautions, descriptions
- Advanced medicine search with filters
- Comprehensive drug database interface

---

## 🛠 Tech Stack

### Frontend
| Technology | Purpose |
|-----------|---------|
| **React.js 18.2** | UI framework with component-based architecture |
| **Vite** | Next-generation frontend tooling for hot module reloading |
| **Tailwind CSS** | Utility-first CSS framework for responsive design |
| **Framer Motion** | Advanced animation library for smooth interactions |
| **React Router DOM** | Client-side routing and navigation |
| **Axios** | HTTP client with JWT token interceptors |
| **Recharts** | Data visualization and analytics charts |
| **React DatePicker** | Date selection component |
| **React Icons** | Comprehensive icon library |
| **TSParticles** | Animated background effects |
| **React Toastify** | Toast notifications system |

### Backend
| Technology | Purpose |
|-----------|---------|
| **Node.js** | JavaScript runtime environment |
| **Express.js** | Web application framework |
| **MongoDB** | NoSQL database for document storage |
| **Mongoose** | MongoDB object modeling |
| **JWT (jsonwebtoken)** | Token-based authentication |
| **Bcryptjs** | Password hashing and security |
| **Multer** | File upload handling |
| **PDFKit & pdf-parse** | PDF generation and parsing |
| **Nodemailer** | Email notifications |
| **Twilio** | SMS notifications (optional) |
| **Google Generative AI** | Gemini API for medicine information |
| **CORS** | Cross-origin resource sharing |

### Infrastructure
| Component | Details |
|-----------|---------|
| **Database** | MongoDB (local or cloud via MongoDB Atlas) |
| **API Server** | Express.js on Node.js (Port 5000) |
| **GenAI Service** | Separate backend service (Port 3001) |
| **Frontend Server** | Vite development server (Port 5173) |
| **Authentication** | JWT tokens with role-based middleware |

---

## 📁 Project Structure

```
HospitalManagementSystem/
├── backend/
│   ├── config/
│   │   └── db.js                    # MongoDB connection
│   ├── controllers/
│   │   ├── adminController.js       # Admin operations
│   │   ├── authController.js        # Authentication logic
│   │   ├── doctorController.js      # Doctor operations
│   │   ├── appointmentController.js # Appointment management
│   │   ├── prescriptionController.js # Prescription operations
│   │   ├── labController.js         # Lab report management
│   │   └── notificationController.js # Notification system
│   ├── middleware/
│   │   ├── authMiddleware.js        # JWT verification
│   │   ├── roleMiddleware.js        # Role-based access control
│   │   └── errorHandler.js          # Error handling
│   ├── models/
│   │   ├── User.js                  # User schema (Admin, Doctor, etc.)
│   │   ├── Patient.js               # Patient schema with medical records
│   │   ├── Appointment.js           # Appointment schema
│   │   ├── Prescription.js          # Prescription schema
│   │   ├── LabReport.js             # Lab report schema
│   │   └── Notification.js          # Notification schema
│   ├── routes/
│   │   ├── authRoutes.js            # Authentication endpoints
│   │   ├── adminRoutes.js           # Admin endpoints
│   │   ├── doctorRoutes.js          # Doctor endpoints
│   │   ├── patientRoutes.js         # Patient endpoints
│   │   ├── appointmentRoutes.js     # Appointment endpoints
│   │   ├── prescriptionRoutes.js    # Prescription endpoints
│   │   ├── labRoutes.js             # Lab endpoints
│   │   └── receptionistRoutes.js    # Receptionist endpoints
│   ├── genai-backend/               # Separate GenAI service
│   │   ├── routes/
│   │   └── server.js
│   ├── server.js                    # Express server entry point
│   ├── package.json
│   └── .env.example
│
├── frontend/
│   ├── src/
│   │   ├── api/
│   │   │   └── api.js               # Axios instance with interceptors
│   │   ├── components/
│   │   │   ├── NavBar.jsx           # Navigation component
│   │   │   ├── ProtectedRoute.jsx   # Route protection wrapper
│   │   │   └── ...                  # Other reusable components
│   │   ├── pages/
│   │   │   ├── Login.jsx            # Authentication page
│   │   │   ├── AdminDashboard.jsx   # Admin dashboard
│   │   │   ├── DoctorDashboard.jsx  # Doctor dashboard
│   │   │   ├── PatientDashboard.jsx # Patient dashboard
│   │   │   ├── LabTechDashboard.jsx # Lab technician dashboard
│   │   │   └── ...                  # Other pages
│   │   ├── utils/
│   │   │   ├── helpers.js           # Utility functions
│   │   │   └── csvParse.js          # CSV parsing utilities
│   │   ├── App.jsx                  # Main component
│   │   ├── main.jsx                 # React entry point
│   │   ├── index.css                # Global styles
│   │   └── App.css
│   ├── public/
│   ├── package.json
│   ├── vite.config.js               # Vite configuration
│   ├── tailwind.config.js           # Tailwind CSS config
│   ├── eslint.config.js             # ESLint configuration
│   └── index.html
│
├── README.md
├── .gitignore
└── LICENSE
```

---

## 📦 Prerequisites

- **Node.js** v14.0 or higher
- **npm** v6.0 or higher (or yarn)
- **MongoDB** v4.4+ (local installation or MongoDB Atlas cloud)
- **Git** for version control
- **API Keys** (for email, SMS, and AI services):
  - Google Generative AI (Gemini) API key
  - Email service credentials (Gmail with app password or similar)
  - Twilio account (optional for SMS notifications)

---

## 🚀 Installation & Setup

### Step 1: Clone the Repository

```bash
git clone https://github.com/vigneshwar315/HospitalManagementSystem.git
cd HospitalManagementSystem
```

### Step 2: Backend Setup

```bash
cd backend
npm install
```

### Step 3: GenAI Backend Setup

```bash
cd genai-backend
npm install
cd ..
```

### Step 4: Frontend Setup

```bash
cd ../frontend
npm install
cd ..
```

---

## 🔐 Environment Configuration

### Backend Environment Variables

Create a `.env` file in the `backend/` directory:

```env
# Server Configuration
PORT=5000
NODE_ENV=development

# Database Configuration
MONGO_URI=mongodb://localhost:27017/hospital-management
# Or use MongoDB Atlas:
# MONGO_URI=mongodb+srv://username:password@cluster.mongodb.net/hospital-management

# JWT Configuration
JWT_SECRET=your_super_secret_jwt_key_min_32_chars

# Email Configuration (Gmail)
EMAIL_USER=your-email@gmail.com
EMAIL_PASS=your-app-specific-password

# SMS Configuration (Twilio - Optional)
TWILIO_ACCOUNT_SID=your_twilio_account_sid
TWILIO_AUTH_TOKEN=your_twilio_auth_token
TWILIO_PHONE_NUMBER=+1234567890

# Frontend URL
FRONTEND_URL=http://localhost:5173

# File Upload
MAX_FILE_SIZE=5242880  # 5MB in bytes
```

### GenAI Backend Environment Variables

Create a `.env` file in the `backend/genai-backend/` directory:

```env
PORT=3001
GEMINI_API_KEY=your_google_generative_ai_api_key
NODE_ENV=development
```

### Frontend Environment Variables

Create a `.env` file in the `frontend/` directory:

```env
VITE_API_URL=http://localhost:5000/api
VITE_GENAI_URL=http://localhost:3001
```

---

## 🏃 Running the Application

### Option 1: Run All Services Simultaneously (Recommended)

Open three separate terminal windows:

**Terminal 1 - Backend Server:**
```bash
cd backend
npm start
# Server runs on http://localhost:5000
```

**Terminal 2 - GenAI Service:**
```bash
cd backend/genai-backend
npm start
# Service runs on http://localhost:3001
```

**Terminal 3 - Frontend Development Server:**
```bash
cd frontend
npm run dev
# Application runs on http://localhost:5173
```

Then open your browser and navigate to: **http://localhost:5173**

### Option 2: Production Build

```bash
# Backend runs as-is (npm start in backend/)

# Frontend production build:
cd frontend
npm run build
npm run preview  # Preview production build
```

---

## 👥 User Roles & Workflows

### 1. Admin Workflow
1. **Login** with admin credentials (default credentials set during setup)
2. **Dashboard**: View system statistics and user breakdown
3. **Staff Approvals**: Review and approve/reject doctor, receptionist, and technician applications
4. **User Management**: Manage users, view activity logs
5. **Reports**: Generate activity and usage reports
6. **Settings**: Configure system parameters

**Default Admin Credentials** (set after first setup)
```
Email: admin@hospital.com
Password: (set during initialization)
```

### 2. Doctor Workflow
1. **Registration** → Await admin approval
2. **Login** with approved credentials
3. **Patient Search**: Find patients by ID, name, or contact
4. **Appointments**: 
   - View scheduled appointments
   - Set availability slots
   - Complete appointments with notes
5. **Prescriptions**: 
   - Create prescriptions for patients
   - Specify medications with dosage
   - Generate PDF for patient
6. **Medical History**: Access complete patient records
7. **Dashboard Stats**: View appointments, prescriptions, completion rates

### 3. Receptionist Workflow
1. **Registration** → Await admin approval
2. **Login** with credentials
3. **Patient Registration**: Add new patients (auto-generates unique ID: `P-{timestamp}-{random}`)
4. **Appointments**: Coordinate and list appointments
5. **Doctor Lookup**: View available doctors
6. **Quick Stats**: See daily metrics

### 4. Lab Technician Workflow
1. **Registration** → Await admin approval
2. **Login** with credentials
3. **Manage Lab Reports**:
   - Create new reports
   - Select test type (Blood, Urine, X-Ray, MRI, CT Scan, ECG, Other)
   - Add results and attachments
4. **Report Status**: Track pending and completed reports
5. **Patient Reports**: Link reports to patient records

### 5. Patient Workflow
1. **Registration**: Self-register or via receptionist
2. **OTP Login**: 
   - Enter phone/email
   - Receive OTP via SMS/Email
   - Enter OTP to login
3. **Book Appointment**:
   - Select doctor
   - Choose available time slot
   - Confirm appointment
4. **View Medical Records**:
   - Medications and prescriptions
   - Lab reports
   - Medical history
5. **Notifications**: Receive alerts for appointments, prescriptions, lab reports
6. **Profile**: Update personal and medical information

---

## 📡 API Documentation

### Authentication Endpoints
```
POST   /api/auth/register        # User registration
POST   /api/auth/login           # User login with JWT
POST   /api/auth/patient-login   # Patient OTP login
POST   /api/auth/verify-otp      # OTP verification
POST   /api/auth/logout          # Logout
```

### Admin Endpoints
```
GET    /api/admin/users          # Get all users
GET    /api/admin/stats          # Dashboard statistics
GET    /api/admin/pending-approvals # Pending staff approvals
POST   /api/admin/approve-user   # Approve staff member
POST   /api/admin/reject-user    # Reject staff application
GET    /api/admin/reports        # Generate reports
```

### Doctor Endpoints
```
GET    /api/doctor/appointments  # List appointments
POST   /api/doctor/appointment   # Create appointment
PUT    /api/doctor/appointment/:id # Update appointment
GET    /api/doctor/patients      # List patients
GET    /api/doctor/patient/:id   # Get patient details
POST   /api/doctor/prescription  # Create prescription
GET    /api/doctor/prescriptions # List prescriptions
POST   /api/doctor/availability  # Set availability slots
```

### Patient Endpoints
```
POST   /api/patient/register     # Patient registration
GET    /api/patient/profile      # Get patient profile
PUT    /api/patient/profile      # Update profile
POST   /api/patient/appointment  # Book appointment
GET    /api/patient/appointments # Get my appointments
GET    /api/patient/prescriptions # Get my prescriptions
GET    /api/patient/lab-reports  # Get my lab reports
GET    /api/patient/medical-history # Get history
GET    /api/patient/notifications # Get notifications
```

### Appointment Endpoints
```
POST   /api/appointments         # Create appointment
GET    /api/appointments         # List appointments
GET    /api/appointments/:id     # Get appointment details
PUT    /api/appointments/:id     # Update appointment
DELETE /api/appointments/:id     # Cancel appointment
POST   /api/appointments/:id/complete # Mark complete
```

### Prescription Endpoints
```
POST   /api/prescriptions        # Create prescription
GET    /api/prescriptions        # List prescriptions
GET    /api/prescriptions/:id    # Get prescription
PUT    /api/prescriptions/:id    # Update prescription
POST   /api/prescriptions/:id/pdf # Generate PDF
```

### Lab Report Endpoints
```
POST   /api/lab/reports          # Create report
GET    /api/lab/reports          # List reports
GET    /api/lab/reports/:id      # Get report details
PUT    /api/lab/reports/:id      # Update report
POST   /api/lab/reports/:id/complete # Mark complete
```

### GenAI Endpoints
```
POST   /api/genai/extract-medicines # Extract from PDF prescription
GET    /api/genai/medicine/:name    # Get medicine information
```

---

## 💾 Database Models

### User Model
```javascript
{
  _id: ObjectId,
  name: String,
  email: String (unique),
  phone: String,
  password: String (hashed),
  role: Enum: ['admin', 'doctor', 'receptionist', 'lab_technician', 'patient'],
  isApproved: Boolean,
  specialization: String,      // For doctors
  workingHours: Object,        // For doctors
  department: String,          // For staff
  licenseNumber: String,       // For doctors
  createdAt: Date,
  updatedAt: Date
}
```

### Patient Model
```javascript
{
  _id: ObjectId,
  customId: String,            // P-{timestamp}-{random}
  name: String,
  email: String,
  phone: String,
  dateOfBirth: Date,
  gender: String,
  address: String,
  city: String,
  state: String,
  medications: [{
    name: String,
    dosage: String,
    frequency: String
  }],
  allergies: [String],
  medicalHistory: String,
  appointments: [ObjectId],    // References to Appointment
  prescriptions: [ObjectId],   // References to Prescription
  labReports: [ObjectId],      // References to LabReport
  billing: {
    totalBill: Number,
    paidAmount: Number,
    dueAmount: Number,
    paymentStatus: String
  },
  createdAt: Date,
  updatedAt: Date
}
```

### Appointment Model
```javascript
{
  _id: ObjectId,
  doctor: ObjectId,            // Reference to User (Doctor)
  patient: ObjectId,           // Reference to Patient
  date: Date,
  startTime: String,
  endTime: String,
  duration: Number,            // Minutes (15-120)
  status: Enum: ['scheduled', 'completed', 'cancelled'],
  notes: String,
  createdAt: Date,
  updatedAt: Date
}
```

### Prescription Model
```javascript
{
  _id: ObjectId,
  doctor: ObjectId,            // Reference to User (Doctor)
  patient: ObjectId,           // Reference to Patient
  appointment: ObjectId,       // Reference to Appointment
  diagnosis: String,
  medications: [{
    name: String,
    dosage: String,
    frequency: String,
    duration: String,
    instructions: String
  }],
  notes: String,
  pdfPath: String,             // File path for PDF
  createdAt: Date,
  updatedAt: Date
}
```

### LabReport Model
```javascript
{
  _id: ObjectId,
  patient: ObjectId,           // Reference to Patient
  technician: ObjectId,        // Reference to User (Lab Technician)
  testType: String,            // Blood, Urine, X-Ray, MRI, CT Scan, ECG, Other
  results: String,
  notes: String,
  attachments: [String],       // File paths
  status: Enum: ['pending', 'completed', 'cancelled'],
  createdAt: Date,
  updatedAt: Date
}
```

### Notification Model
```javascript
{
  _id: ObjectId,
  user: ObjectId,              // Reference to User
  type: Enum: ['appointment', 'prescription', 'lab_report', 'approval'],
  title: String,
  message: String,
  reference: ObjectId,         // Link to related document
  isRead: Boolean,
  createdAt: Date
}
```

---

## 🎯 Core Features in Detail

### Authentication & Authorization
- **JWT-based** token generation with 24-hour expiration
- **Role-Based Access Control (RBAC)** with middleware protection
- **OTP Verification** for patient login (SMS/Email)
- **Password Hashing** using bcryptjs with salt rounds
- **Token Refresh** mechanism for extended sessions

### Patient Management
- **Custom ID Generation**: `P-{timestamp}-{random}` format for easy reference
- **Comprehensive Medical Records**: Complete history of appointments, medications, allergies
- **Search Functionality**: Find patients by ID, name, email, or phone
- **Medical History Tracking**: Medications, allergies, diagnoses
- **Billing Integration**: Track total charges, payments, and balances

### Appointment System
- **Doctor Availability Slots**: Configurable working hours with day-wise availability
- **Customizable Duration**: 15 to 120 minutes (default 30 minutes)
- **Time Slot Generation**: Automatic slot generation based on doctor availability
- **Status Tracking**: Scheduled → Completed or Cancelled
- **Appointment Reminders**: Email/SMS notifications to patients and doctors

### Prescription Management
- **Medication Entry**: Track medications with dosage, frequency, and duration
- **PDF Generation**: Professional prescription PDFs with doctor details
- **Instruction Notes**: Additional instructions for patient medication
- **File Upload**: Support for prescription documents
- **Digital Record**: All prescriptions linked to patient and appointment

### Lab Report System
- **Multiple Test Types**: Blood, Urine, X-Ray, MRI, CT Scan, ECG, and custom tests
- **Result Documentation**: Detailed notes and findings
- **File Attachments**: Upload test result files (images, documents)
- **Status Workflow**: Pending → Completed with technician assignment
- **Report Archival**: Historical records for reference

### AI-Powered Medicine Lookup
- **PDF Prescription Parsing**: Upload and extract medicine names automatically
- **Google Generative AI**: Gemini API for detailed drug information
- **Medicine Information**: Side effects, dosage recommendations, precautions, contraindications
- **Search Interface**: Advanced search with filters and categories
- **Drug Database**: Comprehensive medicine repository

### Notification System
- **Multi-Channel**: Email, SMS (Twilio), and in-app notifications
- **Notification Types**: Appointments, prescriptions, lab reports, approvals
- **Unread Badges**: Counter display for unread notifications
- **Graceful Degradation**: SMS simulates if Twilio not configured
- **User Preferences**: Customize notification settings

---

## 🤝 Contributing

We welcome contributions! Here's how to get started:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** your changes (`git commit -m 'Add AmazingFeature'`)
4. **Push** to the branch (`git push origin feature/AmazingFeature`)
5. **Open** a Pull Request

### Coding Standards
- Follow ESLint configuration
- Use consistent naming conventions
- Write meaningful commit messages
- Test your changes before submitting PR
- Update documentation for new features

### Reporting Bugs
- Use the GitHub issue tracker
- Describe the bug clearly with steps to reproduce
- Include screenshots if applicable
- Mention your environment (Node version, OS, etc.)

---

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

---

## 📞 Contact & Support

- **Author**: Vigneshwar
- **GitHub**: [vigneshwar315](https://github.com/vigneshwar315)
- **Email**: For issues, use GitHub Issues
- **Project Repository**: [HospitalManagementSystem](https://github.com/vigneshwar315/HospitalManagementSystem)

---

## 🔗 Useful Links

- [MERN Stack Documentation](https://www.mongodb.com/mern-stack)
- [Express.js Official](https://expressjs.com/)
- [React.js Official](https://react.dev/)
- [MongoDB Documentation](https://docs.mongodb.com/)
- [JWT Explanation](https://jwt.io/introduction)
- [Google Generative AI Docs](https://ai.google.dev/)

---

## 📊 Application Statistics

- **5 User Roles** with specialized dashboards
- **7+ Core Modules** (Auth, Patients, Appointments, Prescriptions, Lab Reports, Admin, AI)
- **20+ API Endpoints** for comprehensive functionality
- **MongoDB Collections**: User, Patient, Appointment, Prescription, LabReport, Notification
- **Responsive Design**: Mobile, tablet, and desktop compatible
- **Dark Mode Support**: Available in admin dashboard

---

## 🚦 Development Roadmap

### Current Version (v1.0)
✅ Core hospital management functionality  
✅ RBAC authentication and authorization  
✅ Patient management system  
✅ Appointment scheduling  
✅ Prescription management  
✅ Lab report tracking  
✅ AI medicine information lookup  

### Planned Features (Future)
- [ ] Billing and payment integration (Razorpay/Stripe)
- [ ] SMS/Email templates customization
- [ ] Advanced analytics and reporting
- [ ] Telemedicine video consultation
- [ ] Medical imaging viewer
- [ ] Multi-hospital support
- [ ] Mobile app (React Native)
- [ ] Microservices architecture

---

## 🙏 Acknowledgements

- **Google Generative AI** for medicine information lookup
- **MongoDB** for reliable database
- **Tailwind CSS** for beautiful styling
- **Framer Motion** for smooth animations
- **React** community for amazing tools and libraries

---

⭐ If this project helped you, please consider giving it a star on GitHub!

---
