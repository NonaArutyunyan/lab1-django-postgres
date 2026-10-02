# lab1-django-postgres
# Corporate IS — Lab 1

Лабораторная работа №1: окружение, Django, PostgreSQL через Docker Compose.

## Стек
- Python 3.x, Django 5.x
- PostgreSQL 16 (Docker)
- Docker Compose

## Как запустить

1. Склонировать репозиторий:
   git clone <URL>
   cd lab1-django-postgres

2. Создать и активировать окружение:
   python -m venv venv
   venv\Scripts\activate   (Windows)

3. Установить зависимости:
   pip install django psycopg2-binary python-dotenv

4. Создать `.env` с содержимым:
   POSTGRES_DB=corporate_is
   POSTGRES_USER=corporate_is
   POSTGRES_PASSWORD=corporate_is_password
   POSTGRES_HOST=localhost
   POSTGRES_PORT=5432

5. Поднять базу:
   docker compose up -d

6. Применить миграции и запустить сервер:
   python manage.py migrate
   python manage.py runserver

7. Открыть http://127.0.0.1:8000/admin/

## Идея мини-ИС для итогового проекта
<здесь напиши 2–3 предложения — что за система, кто пользователи, какие сущности>

Например: "CRM для отдела продаж: учёт клиентов, сделок и задач менеджеров.
Сущности: Client, Deal, Task. Пользователи: менеджеры и руководитель."

## REST API

Эндпоинты:

- `GET    /api/employees/` — список сотрудников
- `POST   /api/employees/` — создать сотрудника
- `GET    /api/employees/<id>/` — один сотрудник
- `PATCH  /api/employees/<id>/` — частичное обновление
- `DELETE /api/employees/<id>/` — удалить
- `GET    /api/departments/` — список отделов (аналогично CRUD)

Пример запроса:

    curl http://127.0.0.1:8000/api/employees/

Создание сотрудника:

    curl -X POST http://127.0.0.1:8000/api/employees/ \
      -H "Content-Type: application/json" \
      -d '{"full_name": "Иванова Анна", "position": "Менеджер", "hired_at": "2026-09-15", "department": 1}'