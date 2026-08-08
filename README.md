# Real-Time Property Rental, Maintenance & Amenity Management Platform

Full MERN stack internship project: JWT-authenticated tenant/admin dashboards, maintenance ticketing, amenity booking with conflict prevention, and real-time updates via Socket.io.

## Project Structure

```
.
├── backend/     Node.js + Express + MongoDB API (see backend/README.md)
└── frontend/    React (Vite) + Tailwind CSS client
```

## Quick Start

### 1. Backend

```bash
cd backend
npm install
cp .env.example .env
```

Edit `.env`:
- `MONGO_URI` → your MongoDB Atlas connection string
- `JWT_SECRET` → any long random string

```bash
npm run seed   # creates an admin user + sample amenities
npm run dev    # starts the API on http://localhost:5000
```

Seeded admin login: `admin@propertyplatform.com` / `Admin@123`

### 2. Frontend

```bash
cd frontend
npm install
npm run dev    # starts the client on http://localhost:5173
```

The frontend's `.env` already points to `http://localhost:5000/api` — update `VITE_API_URL` / `VITE_SOCKET_URL` if your backend runs elsewhere.

### 3. Try it out

1. Open `http://localhost:5173`
2. Log in as the seeded admin, or register a new tenant account
3. As admin: add a Property, review Maintenance requests, manage Amenities/Bookings
4. As tenant: submit a maintenance request, book an amenity, watch the admin's dashboard update in real time (Socket.io)

## Features Implemented

- JWT auth (register/login), bcrypt password hashing, role-based route protection (tenant/admin)
- Properties CRUD (admin)
- Maintenance requests: tenant submits & tracks; admin updates status (Pending → In Progress → Completed)
- Amenities CRUD (admin); tenant browsing & booking
- Bookings with **conflict prevention** (overlapping time-slot detection per amenity/date)
- Real-time Socket.io events: `maintenance:created`, `maintenance:updated`, `booking:created`, `booking:cancelled`
- Tenant & Admin dashboards with stat cards and Recharts visualizations (pie/bar/line)
- Pagination, search, and filtering on list endpoints
- Centralized error handling, rate limiting, Helmet, Mongo sanitization, payload size limits

## Notes for Your Internship Evaluation

- Backend follows MVC: `models/ controllers/ routes/ middleware/ config/ utils/ socket/`
- Frontend follows a scalable structure: `pages/ components/ layouts/ context/ services/ hooks/`
- All secrets are environment-driven (`.env`, gitignored) — no hardcoded credentials
- See `backend/README.md` for API-only setup/testing instructions

## Suggested Next Steps (not included, extend as needed)

- Nodemailer email notifications on status changes
- Multer-based image uploads for properties
- Automated tests (Jest/Supertest for backend, React Testing Library for frontend)
- Deployment: Vercel (frontend), Render/Railway (backend), MongoDB Atlas (already configured)
# REAL-TIME-PROPERTY-RENTAL-MAINTENANCE-AMENITY-MANAGEMENT-PLATFORM
