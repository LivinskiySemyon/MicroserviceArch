# MVC Restful API

FastAPI приложение с аутентификацией на основе JWT и использованием БД PostgreSQL.

## Технологический стек

- **Веб-фреймворк**: FastAPI
- **ORM**: SQLAlchemy 2.0 (Async)
- **Миграции**: Alembic
- **База данных**: PostgreSQL 16 
- **DevOps**: Docker Compose

## Сервисы

### 1. **Backend** (articles + comments)
- Порт: 8000 (внутренний), 80 (gateway)
- БД: db-main (articles, comments, tags)
- Функции: управление статьями и комментариями
- Авторизация: проверка JWT токена

### 2. **Users API** (управление пользователями)
- Порт: 8001 (внутренний), 80 (gateway)
- БД: db-users (users)
- Функции: регистрация, логин, управление профилем
- Авторизация: создание JWT токенов

### 3. **API Gateway** (Nginx)
- Порт: 80 (HTTP), 443 (HTTPS)
- Маршрутизация:
  - `/api/users/*` → users-api:8001
  - `/api/*` → backend:8000
  - `/` → backend:8000

## Data Ownership

Каждый микросервис владеет своими данными:
- **Backend**: articles, comments, tags
- **Users API**: users
- **Связь**: `author_id` в Article/Comment - логическая ссылка, БЕЗ foreign key

## Запуск и остановка приложения
   
- **Запуск приложения**
  
   ```bash
   docker-compose up -d
   ```
   
- **Остановка приложения**:
   ```bash
   docker-compose down
   ```

## Ссылки
- **Развернутое приложение**: https://microservicearch.onrender.com
- **Swagger UI**: https://microservicearch.onrender.com/docs
