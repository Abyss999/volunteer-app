# Volunteer App

A full‑stack volunteer management site built with React / TypeScript (front‑end) and Flask / PostgreSQL (back‑end).

---

## 🚀 Prerequisites

- **Node.js** ≥ 16 & **npm** (or Yarn)
- **Python** ≥ 3.11 & **pip**
- **PostgreSQL** (e.g. via [pgAdmin4](https://www.pgadmin.org/))
- **Docker Desktop** (for MailHog)

---

## 🛠️ Environment Variables

### Frontend

Create a file at `frontend/.env`:

```dotenv
# API base URL for dev
VITE_API_URL=http://localhost:5000
DEVELOPMENT_DB_URL=http://127.0.0.1:5000
```

### Backend

Create a file at `frontend/.env`:

```dotenv
SECRET_KEY=your_secret_key_here
DATABASE_URL=postgresql://postgres:password@localhost:5432/volunteer_app

# Email (MailHog)
MAIL_SERVER=localhost
MAIL_PORT=1025
MAIL_USE_TLS=false
MAIL_USE_SSL=false
MAIL_USERNAME=
MAIL_PASSWORD=
MAIL_DEFAULT_SENDER="Volunteer App <no-reply@localhost>"

# CORS / front-end origin
FRONTEND_ORIGIN=http://localhost:5173

# JWT
JWT_SECRET_KEY=super-dev-jwt-secret-change-me
```


## 🏃‍♂️ Quick Start

1. **Start MailHog**

   ```bash
   docker run -d -p 1025:1025 -p 8025:8025 mailhog/mailhog
   ```

   Access the UI at [http://localhost:8025](http://localhost:8025).

2. **Set up the database**

   * Open pgAdmin4, connect to `localhost`, password `password`.
   * Create a database named `volunteer_app`.

3. **Backend**

```bash
cd backend

# Activate virtual environment
source ../venv/bin/activate  # On macOS/Linux
# OR
..\venv\Scripts\activate     # On Windows

# Install dependencies
pip install -r requirements.txt

# Set PYTHONPATH to avoid import errors
export PYTHONPATH=/path/to/volunteer-app/backend:$PYTHONPATH  # On macOS/Linux
# OR
set PYTHONPATH=C:\path\to\volunteer-app\backend;%PYTHONPATH%  # On Windows

# Run database migrations
# If you encounter "multiple heads" error, run these commands:
flask db stamp c80074fb66b1
flask db stamp cc63c1ca15b1
flask db upgrade fae995670737

# Otherwise, simply run:
flask db upgrade

# Start the Flask server (runs at http://localhost:5000)
flask run
```

4. **Frontend**

   ```bash
   cd frontend
   npm install
   npm run dev           # starts at http://localhost:5173
   ```

---

## 🔍 Usage

* **Register** at `/auth/register` → check MailHog for your verification email
* **Login** at `/auth/login` → you’ll receive a JWT
* Now you can explore the dashboard, create events, etc.

---

## 🧪 Testing

* Test the backend with `cd backend && pytest`

