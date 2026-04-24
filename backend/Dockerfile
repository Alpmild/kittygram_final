# Используем официальный легковесный образ Python
FROM python:3.10

# Устанавливаем рабочую директорию внутри контейнера
WORKDIR /app

# Копируем файл зависимостей
COPY requirements.txt .

# Обновляем pip и устанавливаем зависимости
RUN pip install --upgrade pip && \
    pip install -r requirements.txt --no-cache-dir

# Копируем весь остальной код бэкенда в контейнер
COPY . .

# Команда для запуска приложения через Gunicorn
# (Убедитесь, что gunicorn добавлен в ваш requirements.txt)
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "kittygram_backend.wsgi"]
