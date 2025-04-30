# Health Hub System

A full-stack health management system built with Django (backend) and React (frontend).

## Features
- User authentication (doctors, nurses, staff)
- Client management
- Program enrollment
- Appointments
- Prescriptions
- Health metrics
- Reports

## Tech Stack
- **Backend:** Django, Django REST Framework, PostgreSQL
- **Frontend:** React, Material-UI
- **Containerization:** Docker, docker-compose

---

## Requirements
- Docker & Docker Compose
- (For local development) Python 3.12+, Node.js 20+

---

## Quick Start (Docker Compose)

1. **Clone the repository:**
   ```sh
   git clone <your-repo-url>
   cd health__hub
   ```

2. **Set up environment variables:**
   Create a `.env` file in `health_system/` with:
   ```env
   DEBUG=1
   SECRET_KEY=your-secret-key
   DJANGO_ALLOWED_HOSTS=localhost 127.0.0.1 [::1]
   SQL_ENGINE=django.db.backends.postgresql
   SQL_DATABASE=healthdb
   SQL_USER=healthuser
   SQL_PASSWORD=healthpass
   SQL_HOST=db
   SQL_PORT=5432
   
   # Email, etc. as needed
   ```

3. **Build and run the stack:**
   ```sh
   docker-compose up --build
   ```
   - Backend: http://localhost:8000/
   - Frontend: http://localhost:3000/

4. **Create a superuser (first time only):**
   ```sh
   docker-compose exec backend python manage.py createsuperuser
   ```

---

## Local Development (without Docker)

### Backend
1. Install Python dependencies:
   ```sh
   cd health_system
   python -m venv venv
   source venv/bin/activate  # or venv\Scripts\activate on Windows
   pip install --upgrade pip
   pip install -r requirements.txt
   ```
2. Set up `.env` as above.
3. Run migrations:
   ```sh
   python manage.py migrate
   ```
4. Start the server:
   ```sh
   python manage.py runserver
   ```

### Frontend
1. Install Node dependencies:
   ```sh
   cd frontend
   npm install
   ```
2. Start the React app:
   ```sh
   npm start
   ```

---

## Useful Commands
- Run backend tests: `python manage.py test`
- Run frontend tests: `npm test`
- Build frontend for production: `npm run build`

---

## Notes
- The backend expects PostgreSQL. You can change DB settings in `.env`.
- The frontend expects the backend at `http://localhost:8000/` (see `src/services/api.js`).
- For production, set `DEBUG=0` and configure allowed hosts, static/media, etc.

---

## License
MIT
