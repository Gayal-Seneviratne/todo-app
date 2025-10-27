# Todo Application

A full-stack Todo application with React frontend, Node.js/Express backend, and MySQL database.

## Architecture

- **Frontend**: React + TypeScript + Vite
- **Backend**: Node.js + Express + TypeORM
- **Database**: MySQL 8.0

## Prerequisites

- Docker Desktop installed and running
- Docker Compose installed
- Git installed

## Getting Started

### Step 1: Clone the Repositories

First, create a project directory and clone both frontend and backend repositories:

```bash
# Create project directory
mkdir Todo
cd Todo

# Clone backend repository
git clone https://github.com/Gayal-Seneviratne/todo-backend.git "Todo - Backend"

# Clone frontend repository
git clone https://github.com/Gayal-Seneviratne/todo-frontend.git "Todo - Frontend"
```

### Step 2: Create Docker Compose File

Create a `docker-compose.yml` file in the `Todo` directory with the configuration provided in this repository, or download it from the setup instructions.

### Step 3: Configure Environment Variables

1. **Backend Environment Variables**
   
   Navigate to the backend directory and create a `.env` file:
   ```bash
   cd "Todo - Backend"
   cp .env.example .env
   ```
   
   The `.env` file should contain:
   ```env
   DB_HOST=mysql
   DB_PORT=3306
   DB_USERNAME=todo_user
   DB_PASSWORD=todo_password
   DB_NAME=todo_db
   PORT=4000
   ```

2. **Frontend Environment Variables**
   
   Navigate to the frontend directory and create a `.env` file:
   ```bash
   cd ../Todo - Frontend
   cp .env.example .env
   ```
   
   The `.env` file should contain:
   ```env
   VITE_API_URL=http://localhost:4001/api
   ```

### Step 4: Return to Root Directory

```bash
cd ..
```

### Step 5: Start All Services

Now you can start all services with a single command:

```bash
docker-compose up --build
```

This command will:
- Pull and start MySQL 8.0 database
- Build and start the backend API
- Build and start the frontend application
- Create the database and run migrations automatically

### Step 6: Access the Application

Once all services are up and running, you can access:
- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:4001/api
- **MySQL Database**: localhost:3307

## Quick Start Summary

```bash
# 1. Create and navigate to project directory
mkdir Todo && cd Todo

# 2. Clone repositories
git clone https://github.com/Gayal-Seneviratne/todo-backend.git "Todo - Backend"
git clone https://github.com/Gayal-Seneviratne/todo-frontend.git "Todo - Frontend"

# 3. Create docker-compose.yml in the Todo directory (copy from repository)

# 4. Setup backend .env
cd "Todo - Backend" && cp .env.example .env && cd ..

# 5. Setup frontend .env
cd "Todo - Frontend" && cp .env.example .env && cd ..

# 6. Start all services
docker-compose up --build
```

### Stopping Services

To stop all services:
```bash
docker-compose down
```

To stop and remove volumes (database data will be lost):
```bash
docker-compose down -v
```

## Service Details

### MySQL Database
- **Port**: 3307 (external) → 3306 (internal)
- **Database**: `todo_db`
- **User**: `todo_user`
- **Password**: `todo_password`
- **Root Password**: `rootpassword`

### Backend API
- **Port**: 4001 (external) → 4000 (internal)
- **Tech Stack**: Node.js 18, Express, TypeORM
- **Dockerfile**: `Todo - Backend/Dockerfile`

### Frontend
- **Port**: 3000
- **Tech Stack**: React 19, TypeScript, Vite
- **Dockerfile**: `Todo - Frontend/Dockerfile`

## Environment Variables

### Backend (`Todo - Backend/.env`)
```env
DB_HOST=mysql
DB_PORT=3306
DB_USERNAME=todo_user
DB_PASSWORD=todo_password
DB_NAME=todo_db
PORT=4000
```

### Frontend (`Todo - Frontend/.env`)
```env
VITE_API_URL=http://localhost:4001/api
```

## Development

### Running Individual Services Locally

#### Backend
```bash
cd "Todo - Backend"
npm install
npm run dev
```

#### Frontend
```bash
cd "Todo - Frontend"
npm install
npm run dev
```

### Running Tests

#### Backend Tests
```bash
cd "Todo - Backend"
npm test
```

#### Frontend Tests
```bash
cd "Todo - Frontend"
npm test
```

## Troubleshooting

### Port Conflicts
If you encounter port conflicts, you can modify the ports in `docker-compose.yml`:
- MySQL: Change `3307:3306` to another port
- Backend: Change `4001:4000` to another port
- Frontend: Change `3000:3000` to another port

### Database Connection Issues
Ensure MySQL container is healthy before backend starts. The `docker-compose.yml` includes health checks to manage this automatically.

### Viewing Logs
To view logs for all services:
```bash
docker-compose logs -f
```

To view logs for a specific service:
```bash
docker-compose logs -f backend
docker-compose logs -f frontend
docker-compose logs -f mysql
```

## Project Structure

```
Todo/
├── docker-compose.yml          # Docker Compose configuration
├── README.md                   # This file
├── Todo - Backend/             # Backend API
│   ├── Dockerfile
│   ├── package.json
│   └── src/
└── Todo - Frontend/            # Frontend application
    ├── Dockerfile
    ├── package.json
    └── src/
```

## License

MIT
