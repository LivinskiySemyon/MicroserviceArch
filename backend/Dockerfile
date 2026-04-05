FROM python:3.11-alpine
WORKDIR /app

RUN apk update && apk add --no-cache \
    gcc \
    g++ \
    postgresql-client \
    postgresql-dev \
    musl-dev

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

RUN adduser -D -u 1000 appuser && chown -R appuser:appuser /app
USER appuser

EXPOSE 10000

CMD sh -c "echo 'Starting Blog API...' && \
           echo 'Checking database connection...' && \
           echo 'Running database migrations...' && \
           alembic upgrade head && \
           echo 'Starting uvicorn server...' && \
           exec uvicorn src.main:app --host 0.0.0.0 --port 10000"
