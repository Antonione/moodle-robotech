# 📘 Moodle + PostgreSQL via Docker Compose


This project sets up a production-ready Moodle environment using Docker Compose, with PostgreSQL as the database, network isolation, data persistence, and external environment variables for security.

🇧🇷 Este projeto também está disponível em [Português](README.pt-br.md)

---

## 📦 Services

| Service   | Image              | Port      | Description                        |
|-----------|--------------------|-----------|------------------------------------|
| `moodle`  | `bitnami/moodle:4` | `8080`    | Moodle LMS application             |
| `postgres`| `postgres:15`      | `5432`    | PostgreSQL database                |

---

## 🔐 Secure Architecture

✅ Database isolated in internal network  
✅ Encrypted communication between containers  
✅ Credentials stored in `.env` (not versioned)  
✅ Persistent volumes for critical data  
✅ Healthchecks for self-recovery 

---

## 🛠️ Prerequisites

- DDocker Engine ≥ 20.10
- Docker Compose ≥ 2.0
- 4GB RAM minimum (8GB recommended)

[Install Docker on Ubuntu](https://docs.docker.com/engine/install/ubuntu/)

---

## 🚀 How to Use

### 1. Clone the repository

```bash
git clone https://github.com/seu-usuario/moodle-pj.git
cd moodle-pj
```

### 2. Configure environment variables

Create and edit the `.env` file with the required settings:

```bash
touch .env 
nano .env  # Or use your preferred editor (vim, code, etc.)
```

Add the following configurations (replace with your actual values):

```bash

# Moodle admin user
MOODLE_USERNAME=admin
MOODLE_PASSWORD=admin123
MOODLE_EMAIL=antonione@gmail.com

# Database configuration
MOODLE_DATABASE_TYPE=pgsql
MOODLE_DATABASE_HOST=postgres
MOODLE_DATABASE_PORT_NUMBER=5432
MOODLE_DATABASE_NAME=moodle_db
MOODLE_DATABASE_USER=moodle_user
MOODLE_DATABASE_PASSWORD=senhaforte123

POSTGRES_DB=moodle_db
POSTGRES_USER=moodle_user
POSTGRES_PASSWORD=senhaforte123
```
⚠️ Important:

- Never use default passwords like 'admin123' in production
- Generate strong passwords with: `openssl rand -base64 12`
- Keep the `.env` sfile secure and out of version control
- Use unique names for database and users


### 3. Start the containers

```bash
docker compose up -d
```

### 4. Access Moodle

Local: http://localhost:8080

**Moodle will be automatically installed on first run using the data from** `.env`.