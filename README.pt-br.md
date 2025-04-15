# 📘 Moodle + PostgreSQL via Docker Compose


Este projeto configura um ambiente Moodle pronto para produção usando Docker Compose, com PostgreSQL como banco de dados, isolamento de rede, persistência de dados e variáveis de ambiente externas para segurança.

---

## 📦 Serviços

| Serviço   | Imagem             | Porta     | Descrição                          |
|-----------|--------------------|-----------|------------------------------------|
| `moodle`  | `bitnami/moodle:4` | `8080`    | Aplicação Moodle (LMS)             |
| `postgres`| `postgres:15`      | `5432`    | Banco de dados PostgreSQL          |

---

## 🔐 Arquitetura Segura

✅ Banco de dados isolado em rede interna  
✅ Comunicação criptografada entre containers  
✅ Credenciais armazenadas em `.env` (não versionado)  
✅ Volumes persistentes para dados críticos  
✅ Healthchecks para auto-recuperação 

---

## 🛠️ Pré-requisitos

- Docker Engine ≥ 20.10
- Docker Compose ≥ 2.0
- 4GB RAM mínimo (8GB recomendado)

[Instalação do Docker no Ubuntu](https://docs.docker.com/engine/install/ubuntu/)

---

## 🚀 Como usar

### 1. Clone o repositório

```bash
git clone https://github.com/seu-usuario/moodle-pj.git
cd moodle-pj
```

### 2. Configure as variáveis de ambiente

Crie e edite o arquivo `.env` com as configurações necessárias:

```bash
touch .env 
nano .env  # Ou use seu editor preferido (vim, code, etc.)
```

Adicione as seguintes configurações (substitua pelos seus valores reais):

```bash
# Usuário administrador do Moodle
MOODLE_USERNAME=admin
MOODLE_PASSWORD=admin123
MOODLE_EMAIL=antonione@gmail.com

# Configuração do banco de dados
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
⚠️ Importante:

- Nunca use senhas padrão como 'admin123' em produção
- Gere senhas fortes com: `openssl rand -base64 12`
- Mantenha o arquivo `.env` seguro e fora do versionamento
- Use nomes únicos para banco de dados e usuários


### 3. Suba os containers

```bash
docker compose up -d
```

### 4. Acessar o Moodle

Local: http://localhost:8080

**O Moodle será instalado automaticamente na primeira vez, usando os dados do** `.env.`