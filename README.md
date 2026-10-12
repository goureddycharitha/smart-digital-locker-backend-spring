# Smart Digital Locker - Backend (Spring Boot)

Spring Boot 3 REST API backend for the Smart Digital Locker vault application.

## Tech Stack
- **Java:** 21 / 25
- **Framework:** Spring Boot 3.4.3
- **Security:** Spring Security 6 (Stateless JWT Authentication & BCrypt)
- **Database:** MySQL 8 (Aiven MySQL / Local MySQL) with Spring Data JPA & Hibernate
- **Build Tool:** Maven 3.9+
- **Container:** Multi-stage Dockerfile (Eclipse Temurin JRE 21)

## Environment Variables
Configure the following environment variables (or copy `.env.example` to `.env`):

| Variable | Description | Default |
|---|---|---|
| `PORT` | HTTP port | `8080` |
| `DB_URL` | JDBC URL for MySQL (e.g. Aiven) | Required |
| `DB_USERNAME` | Database username | Required |
| `DB_PASSWORD` | Database password | Required |
| `JWT_SECRET` | 256-bit secret key for JWT signing | Required |
| `JWT_EXPIRATION_MS` | JWT expiration time in ms | `86400000` (24h) |
| `UPLOAD_DIR` | Storage path for uploaded files | `./uploads` |
| `ALLOWED_ORIGINS` | Comma-separated allowed CORS origins | `http://localhost:5173,http://localhost:3000` |

## Build & Run

### Local Maven
```bash
# Run tests
mvn test

# Package JAR
mvn clean package -DskipTests

# Run application
mvn spring-boot:run
```

### Docker
```bash
docker build -t smart-digital-locker-backend .
docker run -p 8080:8080 --env-file .env smart-digital-locker-backend
```
