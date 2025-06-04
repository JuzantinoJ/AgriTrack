# AgriTrack: Smart Farm Logbook

This scaffold sets up your fullstack project using **React + TypeScript** (frontend) and **Django + Django REST Framework** (backend), ready to be containerized with Docker and deployed to AWS.

## 🚀 Getting Started (Docker)

Clone the repo:

```bash
git clone git@github.com:your-username/agritrack.git
cd agritrack

---

## 📁 Folder Structure
```
agritrack/
├── backend/                   # Django backend
│   ├── agritrack_api/         # Django project folder
│   ├── farm_logs/             # Django app
│   ├── manage.py
│   ├── requirements.txt
│   └── Dockerfile
│
├── frontend/                  # React + TypeScript frontend
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── App.tsx
│   │   └── main.tsx
│   ├── package.json
│   └── Dockerfile
│
├── docker-compose.yml        # Connect frontend & backend
├── .env                      # Environment variables
├── README.md                 # Project overview
└── terraform/                # Terraform AWS deployment (optional)
    ├── main.tf
    ├── variables.tf
    └── outputs.tf
```

---

## 🔧 Backend Setup (Django)
- `farm_logs/models.py`: Define models for logs
- `views.py` and `serializers.py`: Create CRUD API
- JWT setup via `djangorestframework-simplejwt`
- `requirements.txt`:
```txt
django
djangorestframework
djangorestframework-simplejwt
django-cors-headers
psycopg2-binary
```

---

## 💻 Frontend Setup (React + TS)
- React app initialized with `Vite`
- Use `axios` to connect to the backend
- Create components:
  - `FarmLogList.tsx`
  - `FarmLogForm.tsx`
  - `Dashboard.tsx`

---

## 🐳 Docker & Docker Compose
### docker-compose.yml
```yaml
version: '3.8'
services:
  backend:
    build: ./backend
    volumes:
      - ./backend:/app
    ports:
      - "8000:8000"
    env_file: .env
    depends_on:
      - db

  frontend:
    build: ./frontend
    volumes:
      - ./frontend:/app
    ports:
      - "3000:3000"
    depends_on:
      - backend

  db:
    image: postgres
    restart: always
    environment:
      POSTGRES_DB: agritrack
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: postgres
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
```

---

## ☁️ AWS Hosting Options
- EC2 for manual deployment OR
- ECS Fargate for managed containers
- Use RDS PostgreSQL
- Static frontend can be deployed to S3 + CloudFront

---

## 🔐 IAM Roles
- CloudAdmin: Full access
- SecurityAdmin: IAM, GuardDuty, CloudWatch
- AppAdmin: Deploy app only (no user or VPC management)

---

Would you like help initializing the React + Django apps, or generating the Terraform files for AWS setup?
