# Local Development Setup

This guide provides step-by-step instructions to set up your local development environment for the UK PCW application.

## 1. Clone the Repository

Open your terminal or command prompt and run:

```bash
git clone git@github.com:your-org/your-pcw-project.git
cd your-pcw-project
```

## 2. Install Backend Dependencies (Python Example)

Navigate to the backend service directory (e.g., `services/backend-api`):

```bash
cd services/backend-api
python -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
pip install -r requirements.txt
```

## 3. Install Frontend Dependencies (Node.js/npm Example)

Navigate to the frontend application directory (e.g., `apps/frontend-web`):

```bash
cd apps/frontend-web
npm install  # Or `yarn install` if using Yarn
```

## 4. Database & External Services Setup (Docker Compose)

Many services (e.g., PostgreSQL, Redis, Kafka) are run locally using Docker Compose.

From the project root directory:

```bash
docker-compose -f docker-compose.local.yml up -d
```

This will start all required local services in detached mode.

## 5. Environment Variables

Each service will require specific environment variables. Typically, `.env.example` files are provided in each service directory. Copy these to `.env` and fill in the appropriate values.

```bash
cp services/backend-api/.env.example services/backend-api/.env
# Edit services/backend-api/.env

cp apps/frontend-web/.env.example apps/frontend-web/.env
# Edit apps/frontend-web/.env
```

## 6. Run the Application

### Run Backend Services (Example)

```bash
cd services/backend-api
source venv/bin/activate
python manage.py runserver
```

### Run Frontend Application (Example)

```bash
cd apps/frontend-web
npm start
```

Refer to the `README.md` within each service/app directory for specific running instructions.

## 7. Initial Database Setup

For relational databases, you might need to run migrations and seed data:

```bash
cd services/backend-api
source venv/bin/activate
python manage.py migrate
python manage.py loaddata initial_data.json # If applicable
```

Your local development environment should now be fully operational.