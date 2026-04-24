# CAWMS Release Package - Standalone Deployment Guide

## System Requirements

- Docker Engine 24.0+
- Docker Compose 2.20+
- Available disk space: >= 5GB
- Memory: >= 4GB

## Package Contents

```
.
├── docker-compose.yml          # Docker Compose deployment configuration
├── .env.example                # Environment variable template
├── database/
│   ├── cawms_final_clean.sql   # Complete database script (schema + data)
│   └── cawms_data_only_clean.sql # Data-only script
├── deployment/nginx/           # Nginx configuration files
├── images/
│   ├── backend.tar             # Backend image (cawms-backend:release)
│   └── frontend.tar            # Frontend image (cawms-frontend:release)
└── README.md                   # This file
```

## Quick Deployment Steps

### 1. Load Docker Images

```bash
docker load -i images/backend.tar
docker load -i images/frontend.tar
```

### 2. Configure Environment Variables

```bash
cp .env.example .env
# Edit .env and change all passwords (especially MYSQL_ROOT_PASSWORD, MYSQL_PASSWORD, REDIS_PASSWORD, JWT_SECRET)
```

### 3. Start Services

```bash
docker-compose up -d
```

### 4. Wait for Services to Be Ready

The first startup takes approximately 1-2 minutes (MySQL initializing the database):

```bash
docker-compose ps
```

### 5. Access the System

- Frontend UI: http://localhost
- Backend API: http://localhost:8080/api
- Health Check: http://localhost:8080/actuator/health

## Default Account

| Account | Password | Role |
|---------|----------|------|
| admin   | admin123 | Super Admin |

> **Note**: Please change the default password immediately after deployment.

## Common Commands

```bash
# View logs
docker-compose logs -f

# View backend logs
docker-compose logs -f backend

# Stop services
docker-compose down

# Stop and remove data volumes (use with caution)
docker-compose down -v

# Restart services
docker-compose restart

# Enter MySQL
docker-compose exec mysql mysql -u root -p${MYSQL_ROOT_PASSWORD} cawms
```

## Database Notes

- `cawms_final_clean.sql`: Contains complete table schema and all test/business data, automatically imported on first deployment
- `cawms_data_only_clean.sql`: Contains INSERT statements only, suitable for environments with existing table schema

## Important Notes

1. **Security**: In production environments, make sure to change all default passwords in `.env`, especially `JWT_SECRET` (recommended: a 64-character random string)
2. **Ports**: By default, ports 80 (Nginx) and 8080 (Backend API) are used. If there are conflicts, modify `docker-compose.yml`
3. **Data Persistence**: MySQL data is stored in the Docker Volume `mysql_data`; deleting the volume will result in data loss
4. **Timezone**: The default timezone is Asia/Ho_Chi_Minh. To change it, adjust the `TZ` variable in `.env`

## Technical Support

If you encounter any deployment issues, please check the health status of each container:

```bash
docker-compose ps
docker-compose logs --tail 50
```
