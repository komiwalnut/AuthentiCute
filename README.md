# AuthentiCute

A beautiful and secure User Authentication and Management System built with FastAPI, PostgreSQL, and modern web technologies.

## Features

- 🔐 Secure user authentication with JWT tokens
- 📧 Email verification using Mailgun
- 🎨 Beautiful, responsive UI with Tailwind CSS
- 🚀 FastAPI backend with automatic API documentation
- 🗄️ PostgreSQL database with SQLAlchemy ORM
- 🔒 Password reset functionality
- 👤 User profile management
- 🔑 Google OAuth integration
- 🛡️ Rate limiting and abuse prevention
- 📝 Comprehensive error handling and logging
- 🐳 Docker support for easy deployment

## Quick Start

### Prerequisites

- Python 3.12+
- Docker and Docker Compose
- Mailgun account for email verification
- Google Cloud Console account for OAuth

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/komiwalnut/AuthentiCute.git
   cd AuthentiCute
   ```

2. **Set up environment variables**
   ```bash
   cp env.example .env
   # Edit .env with your actual configuration
   ```

3. **Set up Google OAuth (Optional but Recommended)**
   
   a. Go to [Google Cloud Console](https://console.cloud.google.com/)

   b. Create a new project or select an existing one
   
   c. Enable the Google+ API
   
   d. Go to "Credentials" and create an OAuth 2.0 Client ID
   
   e. Set the authorized redirect URI to: `http://localhost:8000/api/auth/google/callback`
   
   f. Copy the Client ID and Client Secret to your `.env` file:
   ```
   GOOGLE_CLIENT_ID=your-google-client-id
   GOOGLE_CLIENT_SECRET=your-google-client-secret
   GOOGLE_REDIRECT_URI=http://localhost:8000/api/auth/google/callback
   ```

4. **Start the application with Docker Compose**
   ```bash
   docker-compose up --build
   ```

5. **Access the application**
   - Frontend: http://localhost:8000
   - API Documentation: http://localhost:8000/docs
   - Database Health Check: http://localhost:8000/api/db-health

## Database Configuration

The application now uses a local PostgreSQL database running in Docker, which is perfect for both development and AWS EC2 deployment.

### Database Details
- **Database Name**: authenticute
- **Username**: authenticute_user
- **Password**: authenticute_password
- **Host**: postgres (within Docker network) or localhost (external access)
- **Port**: 5432

## Docker Commands

```bash
# Build and start all services
docker-compose up --build

# Stop all services
docker-compose down

# Stop and remove volumes (WARNING: This will delete all data)
docker-compose down -v

# View logs
docker-compose logs -f
```

## Project Structure

```
AuthentiCute/
├── app/
│   ├── __init__.py
│   ├── main.py              # FastAPI application
│   ├── database.py          # Database configuration
│   ├── models/              # Database models
│   │   ├── __init__.py
│   │   ├── user.py
│   │   ├── session.py
│   │   └── token.py
│   ├── schemas/             # Pydantic schemas
│   │   ├── __init__.py
│   │   ├── auth.py
│   │   └── user.py
│   ├── routes/              # API routes
│   │   ├── __init__.py
│   │   ├── auth.py
│   │   └── user.py
│   └── utils/               # Utility functions
│       ├── __init__.py
│       ├── auth_utils.py
│       ├── client_utils.py
│       ├── db_utils.py
│       ├── error_handlers.py
│       ├── oauth_utils.py
│       ├── rate_limiter.py
│       ├── session_utils.py
│       └── token_utils.py
├── templates/               # HTML templates
│   ├── base.html
│   ├── index.html
│   ├── login.html
│   ├── signup.html
│   ├── dashboard.html
│   ├── forgot-password.html
│   ├── reset-password.html
│   └── verify-email.html
├── static/                  # Static files (CSS, JS, images)
│   ├── css/
│   │   └── style.css
│   └── authenticute_logo.svg
├── migrations/              # Database migrations
│   ├── env.py
│   ├── script.py.mako
│   └── versions/
├── requirements.txt         # Python dependencies
├── docker-compose.yml       # Docker Compose configuration
├── Dockerfile              # Docker image configuration
├── env.example             # Environment variables template
├── alembic.ini            # Alembic configuration
├── run.py                 # Application runner
└── README.md              # This file
```

## License

This project is for educational purposes.
