# MVC Restful API

FastAPI приложение с аутентификацией на основе JWT и использованием БД PostgreSQL.

## Технологический стек

- **Services**: FastAPI, Python 3.11
- **Database**: PostgreSQL 16 
- **ORM**: SQLAlchemy 2.0 (Async)
- **Migrations**: Alembic
- **DevOps**: Docker Compose

## Возможности

- Управление пользователями, статьями, комментариями
- Аутентификация и авторизация на основе JWT
- База данных PostgreSQL
- Docker

## 🚀 Быстрый старт

Для запуска вам понадобятся **Docker** и **Docker Compose**.

1. **Настройка переменных окружения**:
   Создайте файл `.env` на основе примера:
   ```bash
   # Windows
   copy env.example .env
   
   # Linux/Mac
   cp env.example .env
   ```

2. **Запуск приложения**:
   ```bash
   docker-compose up -d
   ```

3. **Миграции применяются автоматически** при старте контейнеров.
   
4. **Остановка**:
   ```bash
   docker-compose down
   ```


- **Полная очистка** (удаление контейнеров и данных баз данных):
  ```bash
  docker-compose down -v
  ```
http://localhost:8000/docs
