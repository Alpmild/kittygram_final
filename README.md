# Kittygram

Kittygram — это социальная сеть для любителей котиков. Проект позволяет пользователям делиться фотографиями своих питомцев, указывать их достижения и характеристики. Это полноценное фулстек-приложение, упакованное в Docker-контейнеры и настроенное для автоматического деплоя через CI/CD.

## Описание и функции

Проект создан как учебная площадка для отработки навыков контейнеризации и настройки серверного окружения.

**Основные функции:**
* **Управление питомцами:** Добавление, просмотр, редактирование и удаление карточек котиков.
* **Достижения:** Возможность указывать уникальные черты и достижения каждого питомца.
* **Фотогалерея:** Загрузка и хранение изображений.
* **Авторизация:** Личные кабинеты для пользователей.
* **API:** RESTful API для взаимодействия фронтенда с бэкендом.

## Стек технологий

Проект построен на современной архитектуре с использованием следующих технологий:

* **Backend:** Python 3.10, Django, Django REST Framework (DRF)
* **Frontend:** React (JavaScript)
* **Database:** PostgreSQL
* **Web Server:** Gunicorn, Nginx (как Reverse Proxy)
* **Infrastructure:** Docker, Docker Compose
* **CI/CD:** GitHub Actions (автоматическое тестирование и сборка образов на Docker Hub)

## Как развернуть проект

### 1. Подготовка
Убедитесь, что на вашем компьютере установлены **Docker** и **Docker Compose**.

### 2. Клонирование репозитория
```bash
git clone [https://github.com/ваш_логин/kittygram_final.git](https://github.com/ваш_логин/kittygram_final.git)
cd kittygram_final
```

### 3. Настройка переменных окружения (.env)
```
# Настройки базы данных (PostgreSQL)
POSTGRES_DB=kittygram
POSTGRES_USER=kittygram_user
POSTGRES_PASSWORD=kittygram_password
DB_HOST=db
DB_PORT=5432

# Настройки Django
SECRET_KEY=ваш_очень_секретный_ключ
DEBUG=False
ALLOWED_HOSTS=127.0.0.1, localhost
```

### 4. Запуск в Docker
```
docker compose up -d --build
```

### 5. Миграции и статика
```
# Применяем миграции
docker compose exec backend python manage.py migrate

# Собираем статику админки
docker compose exec backend python manage.py collectstatic --no-input
```
