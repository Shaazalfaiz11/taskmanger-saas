# TaskFlow — Team Task Management SaaS

A full-stack, production-grade **Team Task Manager** with Role-Based Access Control (RBAC), real-time activity logging, and a professional Corporate White & Blue UI.

## 🚀 Live Demo Url :https://taskmanager-saas-flax.vercel.app/signup

- **Frontend**: [Deployed on Vercel](https://your-frontend.vercel.app)
- **Backend**: [Deployed on Render/](https://your-backend.onrender.com)

---

## ✨ Features

### Core Features
- **Authentication** — Secure signup/login with JWT tokens and bcrypt password hashing
- **Role-Based Access Control** — Admin and Member roles with granular permissions
- **Project Management** — Create and organize projects, assign tasks per project
- **Task CRUD** — Full create, read, update, delete with validation
- **Task Assignment** — Admins assign tasks to specific team members
- **Due Dates** — Track deadlines with overdue detection

### Standout Features ⭐
- **Task Priority System** — Low / Medium / High / Urgent with color-coded badges
- **Search** — Real-time search across task titles and descriptions
- **Kanban Board** — Toggle between Grid and Kanban (drag-column) views
- **Activity Log / Audit Trail** — Track who did what, when (task created, updated, deleted)
- **Team Members Page** — View all members with workload stats and completion progress bars
- **Dashboard Analytics** — Completion rate, task distribution stats, live activity feed sidebar
- **Toast Notifications** — Elegant, non-intrusive feedback for all user actions

### UI/UX
- **Corporate White & Blue** design system
- **Responsive** — Works on mobile, tablet, and desktop
- **Smooth Animations** — Fade-in, slide, and scale transitions
- **Inter Font** — Premium Google Font typography

---

## 🛠 Tech Stack

| Layer | Technology |
|-------|-----------|
| **Frontend** | React 18, Vite, Tailwind CSS v4 |
| **Backend** | Node.js, Express.js |
| **Database** | PostgreSQL (Neon cloud) |
| **ORM** | Sequelize |
| **Auth** | JWT + bcrypt |
| **Validation** | express-validator |
| **Deployment** | Vercel (frontend) + Railway/Render (backend) |

---

## 📁 Project Structure

```
├── client/                  # React Frontend
│   ├── src/
│   │   ├── api/             # Axios instance with interceptors
│   │   ├── components/      # Reusable UI components
│   │   │   ├── Navbar.jsx
│   │   │   ├── TaskCard.jsx
│   │   │   ├── TaskForm.jsx
│   │   │   ├── ProjectForm.jsx
│   │   │   └── ProtectedRoute.jsx
│   │   ├── context/         # React Context (Auth, Toast)
│   │   ├── pages/           # Page components
│   │   │   ├── Login.jsx
│   │   │   ├── Signup.jsx
│   │   │   ├── Dashboard.jsx
│   │   │   └── TeamMembers.jsx
│   │   ├── App.jsx
│   │   └── index.css        # Global styles & design tokens
│   └── package.json
│
├── server/                  # Express Backend
│   ├── config/              # Database configuration
│   ├── controllers/         # Route handlers
│   │   ├── authController.js
│   │   ├── taskController.js
│   │   ├── projectController.js
│   │   ├── userController.js
│   │   └── activityController.js
│   ├── middleware/           # Auth, validation, error handling
│   ├── models/              # Sequelize models
│   │   ├── User.js
│   │   ├── Task.js
│   │   ├── Project.js
│   │   └── ActivityLog.js
│   ├── routes/              # API routes
│   └── server.js            # Entry point
│
├── package.json             # Root scripts
├── railway.toml             # Railway deployment config
└── README.md
```

---

## 🔧 Setup & Installation

### Prerequisites
- Node.js 18+
- PostgreSQL database (or Neon/Supabase cloud DB)

### 1. Clone the repo
```bash
git clone https://github.com/yourusername/task-management-saas.git
cd task-management-saas
```

### 2. Install dependencies
```bash
# Install server dependencies
cd server && npm install

# Install client dependencies
cd ../client && npm install
```

### 3. Configure environment variables

Create `server/.env`:
```env
PORT=5000
DATABASE_URL=postgresql://user:password@host/database?sslmode=require
JWT_SECRET=your_secret_key
JWT_EXPIRES_IN=7d
NODE_ENV=development
```

Create `client/.env`:
```env
VITE_API_URL=http://localhost:5000/api
```

### 4. Run the application
```bash
# Terminal 1 — Start backend
cd server && npm start

# Terminal 2 — Start frontend
cd client && npm run dev
```

The app will be available at `http://localhost:5173`

---

## 📡 API Endpoints

### Authentication
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/signup` | Register a new user |
| POST | `/api/auth/login` | Login and get JWT |
| GET | `/api/auth/me` | Get current user |

### Tasks
| Method | Endpoint | Access | Description |
|--------|----------|--------|-------------|
| GET | `/api/tasks` | All | Get tasks (with filters: status, priority, search, projectId) |
| POST | `/api/tasks` | Admin | Create a task |
| GET | `/api/tasks/:id` | All | Get single task |
| PUT | `/api/tasks/:id` | All | Update task (members: status only) |
| DELETE | `/api/tasks/:id` | Admin | Delete a task |

### Projects
| Method | Endpoint | Access | Description |
|--------|----------|--------|-------------|
| GET | `/api/projects` | Admin | Get all projects |
| POST | `/api/projects` | Admin | Create a project |

### Users
| Method | Endpoint | Access | Description |
|--------|----------|--------|-------------|
| GET | `/api/users` | Admin | Get all users |

### Activity Log
| Method | Endpoint | Access | Description |
|--------|----------|--------|-------------|
| GET | `/api/activity` | All | Get activity logs (paginated) |

---

## 👥 Roles & Permissions

| Action | Admin | Member |
|--------|-------|--------|
| Create tasks | ✅ | ❌ |
| Assign tasks | ✅ | ❌ |
| Delete tasks | ✅ | ❌ |
| Edit task details | ✅ | ❌ |
| Change task status | ✅ | ✅ |
| View assigned tasks | ✅ (all) | ✅ (own) |
| Manage projects | ✅ | ❌ |
| View team members | ✅ | ❌ |
| View activity log | ✅ | ✅ |

---

## 🚢 Deployment

### Railway (Full-stack)
1. Connect GitHub repo to Railway
2. Add environment variables in Railway dashboard
3. Deploy — Railway auto-detects `railway.toml`

### Vercel (Frontend) + Render (Backend)
1. Deploy `client/` to Vercel with `VITE_API_URL` env variable
2. Deploy `server/` to Render with `DATABASE_URL`, `JWT_SECRET`, `CLIENT_URL`

---

## 📄 License

MIT License — Free for educational and commercial use.
