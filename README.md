# GlacioLive - login using local database and backend

## 🛠 Project Structure

GL1/
├── backend/
│   ├── app/
│   │   ├── __init__.py      # Required for package recognition
│   │   ├── main.py          # FastAPI entry point
│   │   ├── database.py      # SQLAlchemy & MySQL config
│   │   ├── crud.py          # Database operations
│   │   ├── models.py        # SQLAlchemy models
│   │   ├── schemas.py       # Pydantic schemas
│   │   ├── routes/
│   │   │   ├── __init__.py
│   │   │   └── auth.py      # Auth endpoints
│   │   └── utils/
│   │       ├── auth.py      # JWT logic
│   │       └── hashing.py   # Password encryption
│   ├── .env                 # Database credentials (Secret)
│   └── requirements.txt     # Dependencies
└── frontend/
    └── login.html           # 3D UI & Logic


# Ensure u have mysql installed, create following database

CREATE DATABASE glaciolive_db;

# Navigate to the backend/ directory and create a .env file: replace "YOUR_USER" and "YOUR_PASSWORD" with your connection name nd password

DATABASE_URL=mysql+pymysql://YOUR_USER:YOUR_PASSWORD@localhost:3306/glaciolive_db 
SECRET_KEY=your_very_secret_key_here
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30

# Navigate to backend
cd backend

# Create virtual environment
python -m venv venv

# Activate virtual environment (Windows)
.\venv\Scripts\activate

# Install required packages
pip install -r requirements.txt

# Using the module flag to ensure proper package recognition
python -m uvicorn app.main:app --reload

# Security Features

JWT Authentication: Secure token-based sessions.
Bcrypt Hashing: Passwords are never stored in plain text.
CORS Middleware: Configured to allow frontend-backend communication.