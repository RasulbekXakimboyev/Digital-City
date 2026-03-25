# 🏙️ Raqamli Tuproqqal'a - Digital Services Platform

**Modern, production-ready digital services aggregator platform for city residents**

[![Django](https://img.shields.io/badge/Django-4.2.7-green.svg)](https://www.djangoproject.com/)
[![DRF](https://img.shields.io/badge/DRF-3.14.0-red.svg)](https://www.django-rest-framework.org/)
[![Python](https://img.shields.io/badge/Python-3.11-blue.svg)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## Features

### Modern Frontend
- **Tailwind CSS** - Modern utility-first CSS framework
- **Dark Mode** - Smooth theme switching with persistent storage
- **Responsive Design** - Mobile-first, fully responsive layouts
- **Animations** - Smooth micro-interactions and transitions
- **Advanced Search** - Real-time search with autocomplete
- **Interactive Cards** - Beautiful service cards with hover effects

### Backend Enhancements
- **API Versioning** - `/api/v1/`, `/api/v2/` support
- **JWT Authentication** - Secure token-based authentication
- **Comprehensive Documentation** - Auto-generated Swagger/OpenAPI docs
- **Advanced Filtering** - Price ranges, ratings, distance, availability
- **Geolocation Search** - Distance-based search using Haversine formula
- **Caching** - Redis caching for optimal performance
- **Rate Limiting** - Per-user and per-endpoint rate limits

### Security
- **HTTPS Enforcement** - Secure headers and SSL redirect
- **CSRF Protection** - Enhanced CSRF tokens
- **XSS Prevention** - Content sanitization
- **SQL Injection Protection** - Parameterized queries
- **Secure Headers** - HSTS, X-Frame-Options, CSP

### Services
- **Ovqatlanish joylari** - Restoranlar, kafelar, fast food
- **Sartarosh / Go'zallik saloni** - Online navbat olish
- **Stomatologiya / Klinikalar** - Shifokor jadvali, navbat olish
- **Uyga chaqirish xizmatlari** - Sartarosh, ustalar, yetkazib beruvchilar
- **Transport / Taxi** - Yaqin taxi yoki servis markazlari
- **Tozalash / Maishiy xizmatlar** - Kir yuvish, uyni tozalash
- **Ijtimoiy yordam / Volontyorlik** - Ehtiyojmandlarga yordam
- **Mahalliy e'lonlar** - Ish o'rinlari, sotuvlar, e'lonlar
- **Favqulodda xizmatlar** - 103, 101, 102, 1050

## Quick Start

### Prerequisites
- Python 3.11+
- PostgreSQL 15+ (or SQLite for development)
- Redis 7+
- Node.js (for frontend assets, optional)

### Installation

1. **Clone the repository**
```bash
git clone <repository-url>
cd digital_city
```

2. **Create virtual environment**
```bash
python -m venv .venv
source .venv/bin/activate  # Linux/Mac
# or
.venv\Scripts\activate  # Windows
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

4. **Configure environment variables**
```bash
cp .env.example .env
# Edit .env with your settings
```

5. **Run migrations**
```bash
python manage.py migrate
```

6. **Create superuser**
```bash
python manage.py createsuperuser
```

7. **Collect static files**
```bash
python manage.py collectstatic --noinput
```

8. **Run development server**
```bash
python manage.py runserver
```

Visit `http://localhost:8000` to see the application!

## Docker Deployment

### Using Docker Compose

1. **Start all services**
```bash
docker-compose up -d
```

2. **Run migrations**
```bash
docker-compose exec web python manage.py migrate
```

3. **Create superuser**
```bash
docker-compose exec web python manage.py createsuperuser
```

4. **Collect static files**
```bash
docker-compose exec web python manage.py collectstatic --noinput
```

5. **View logs**
```bash
docker-compose logs -f web
```

### Services
- **web** - Django application (port 8000)
- **db** - PostgreSQL database (port 5432)
- **redis** - Redis cache (port 6379)
- **celery** - Background task worker
- **celery-beat** - Scheduled task scheduler

## API Documentation

### Interactive Documentation
- **Swagger UI**: `http://localhost:8000/api/docs/`
- **ReDoc**: `http://localhost:8000/api/redoc/`
- **OpenAPI Schema**: `http://localhost:8000/api/schema/`

### API Endpoints

#### Authentication
```
POST /api/v1/auth/token/          # Obtain JWT token
POST /api/v1/auth/token/refresh/  # Refresh JWT token
POST /api/v1/auth/token/verify/   # Verify JWT token
```

#### Core Endpoints
```
GET  /api/v1/categories/           # List service categories
GET  /api/v1/locations/            # List locations
GET  /api/v1/locations/nearby/    # Find nearby locations
GET  /api/v1/locations/search/    # Search locations
GET  /api/v1/status/               # API status
```

#### Service Endpoints
```
GET  /api/v1/food/                 # Food services
GET  /api/v1/beauty/               # Beauty salons
GET  /api/v1/medical/              # Medical clinics
GET  /api/v1/home/                 # Home services
GET  /api/v1/transport/            # Transport services
GET  /api/v1/cleaning/             # Cleaning services
GET  /api/v1/social/               # Social assistance
GET  /api/v1/announcements/        # Announcements
GET  /api/v1/emergency/            # Emergency services
```

### Example API Request

```bash
# Get JWT token
curl -X POST http://localhost:8000/api/v1/auth/token/ \
  -H "Content-Type: application/json" \
  -d '{"email": "user@example.com", "password": "password123"}'

# Use token for authenticated requests
curl -X GET http://localhost:8000/api/v1/categories/ \
  -H "Authorization: Bearer YOUR_ACCESS_TOKEN"
```

## Project Structure

```
digital_city/
├── core/                    # Core app (categories, locations)
├── food_services/          # Food services app
├── beauty_salons/           # Beauty salons app
├── medical_clinics/        # Medical clinics app
├── home_services/           # Home services app
├── transport_services/     # Transport services app
├── cleaning_services/      # Cleaning services app
├── social_assistance/      # Social assistance app
├── announcements/          # Announcements app
├── emergency_services/     # Emergency services app
├── raaqamli_tuproqqala/    # Project settings
├── templates/              # HTML templates
├── static/                 # Static files
├── media/                  # User uploaded files
├── logs/                   # Application logs
├── Dockerfile              # Docker configuration
├── docker-compose.yml      # Docker Compose configuration
├── gunicorn_config.py      # Gunicorn configuration
├── requirements.txt       # Python dependencies
└── README.md              # This file
```

## 🔧 Configuration

### Environment Variables

Key environment variables (see `.env.example` for full list):

```bash
# Django
SECRET_KEY=your-secret-key-here
DEBUG=False
ALLOWED_HOSTS=yourdomain.com,www.yourdomain.com

# Database
DB_ENGINE=django.db.backends.postgresql
DB_NAME=tuproqqala_db
DB_USER=postgres
DB_PASSWORD=your_password
DB_HOST=localhost
DB_PORT=5432

# Redis
REDIS_URL=redis://127.0.0.1:6379/1

# Email
EMAIL_BACKEND=django.core.mail.backends.smtp.EmailBackend
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USE_TLS=True
EMAIL_HOST_USER=your-email@gmail.com
EMAIL_HOST_PASSWORD=your-app-password
```

## Testing

```bash
# Run all tests
python manage.py test

# Run with coverage
coverage run --source='.' manage.py test
coverage report
coverage html
```

## Production Deployment

### Using Gunicorn

```bash
gunicorn --config gunicorn_config.py raaqamli_tuproqqala.wsgi:application
```

### Using Docker

```bash
docker-compose -f docker-compose.yml up -d
```

### Environment Checklist

- [ ] Set `DEBUG=False`
- [ ] Set secure `SECRET_KEY`
- [ ] Configure `ALLOWED_HOSTS`
- [ ] Set up PostgreSQL database
- [ ] Configure Redis
- [ ] Set up email backend
- [ ] Configure static files (CDN recommended)
- [ ] Set up SSL/HTTPS
- [ ] Configure logging
- [ ] Set up monitoring (Sentry)
- [ ] Configure backups

## Development

### Running Celery

```bash
# Start Celery worker
celery -A raaqamli_tuproqqala worker --loglevel=info

# Start Celery beat (scheduler)
celery -A raaqamli_tuproqqala beat --loglevel=info
```

### Database Migrations

```bash
# Create migrations
python manage.py makemigrations

# Apply migrations
python manage.py migrate

# Show migration status
python manage.py showmigrations
```

### Static Files

```bash
# Collect static files
python manage.py collectstatic

# Find static files
python manage.py findstatic
```

## Performance Optimization

- **Database Indexing** - Indexes on frequently queried fields
- **Query Optimization** - `select_related()` and `prefetch_related()`
- **Caching** - Redis caching for expensive queries
- **Connection Pooling** - Database connection pooling
- **CDN Integration** - Static files via CDN
- **Image Optimization** - Automatic resizing and compression

## Security Best Practices

- ✅ HTTPS enforcement
- ✅ Secure headers (HSTS, CSP, X-Frame-Options)
- ✅ CSRF protection
- ✅ XSS prevention
- ✅ SQL injection protection
- ✅ Rate limiting
- ✅ Input validation
- ✅ File upload security
- ✅ Password hashing (bcrypt)
- ✅ JWT token expiration


## Contributors

Raqamli Tuproqqal'a Development Team

## Support

For support, email info@tuproqqala.uz or open an issue in the repository.

## Roadmap

- [ ] Real-time features with WebSockets
- [ ] AI/ML recommendations
- [ ] Mobile app (React Native)
- [ ] Payment integration
- [ ] Multi-language support (Uzbek, Russian, English)
- [ ] Advanced analytics dashboard
- [ ] Booking system enhancements
- [ ] Review moderation system

---

**Built with ❤️ for the digital transformation of Tuproqqal'a**
