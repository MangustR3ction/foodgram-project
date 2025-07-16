# Foodgram - Платформа для обмена рецептами

## Описание проекта

Foodgram - это веб-приложение для публикации и обмена кулинарными рецептами. Пользователи могут создавать рецепты, подписываться на других авторов, добавлять рецепты в избранное и формировать список покупок.

## Технологии

### Backend
- **Django** - веб-фреймворк
- **Django REST Framework** - API
- **PostgreSQL** - база данных
- **Docker** - контейнеризация

### Frontend
- **React** - JavaScript библиотека
- **CSS Modules** - стилизация
- **Docker** - контейнеризация

### Инфраструктура
- **Nginx** - веб-сервер
- **Docker Compose** - оркестрация контейнеров
- **GitHub Actions** - CI/CD

## Структура проекта

```
foodgram-project/
├── backend/                 # Django приложение
│   ├── api/                # API endpoints
│   ├── recipes/            # Модели рецептов
│   ├── users/              # Модели пользователей
│   ├── core/               # Общие компоненты
│   └── requirements.txt    # Python зависимости
├── frontend/               # React приложение
│   ├── src/
│   │   ├── components/     # React компоненты
│   │   ├── pages/          # Страницы приложения
│   │   ├── contexts/       # React контексты
│   │   └── api/            # API клиент
│   └── package.json        # Node.js зависимости
├── infra/                  # Инфраструктура
│   ├── docker-compose.yml  # Docker Compose конфигурация
│   └── nginx.conf          # Nginx конфигурация
└── docs/                   # Документация API
```

## Установка и запуск

### Локальная разработка

1. **Клонируйте репозиторий:**
```bash
git clone <repository-url>
cd foodgram-project
```

2. **Backend (Django):**
```bash
cd backend
python -m venv venv
source venv/bin/activate  # Linux/Mac
# или
venv\Scripts\activate     # Windows
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

3. **Frontend (React):**
```bash
cd frontend
npm install
npm start
```

### Docker (рекомендуется)

1. **Создайте файл .env в корне проекта:**
```env
DOCKER_USERNAME=your_docker_username
DB_ENGINE=django.db.backends.postgresql
DB_NAME=foodgram_db
POSTGRES_USER=foodgram_user
POSTGRES_PASSWORD=your_password
DB_HOST=db
DB_PORT=5432
DJ_SECRET_KEY=your_secret_key
```

2. **Запустите с помощью Docker Compose:**
```bash
cd infra
docker-compose up -d
```

## Автоматический деплой

Проект настроен для автоматического деплоя через GitHub Actions. При пуше в ветку `main` или `master`:

1. Запускаются тесты
2. Собираются Docker образы
3. Образы публикуются в Docker Hub
4. Происходит деплой на сервер
5. Отправляется уведомление в Telegram

### Необходимые секреты в GitHub:

- `DOCKER_USERNAME` - имя пользователя Docker Hub
- `DOCKER_PASSWORD` - пароль Docker Hub
- `HOST` - IP адрес сервера
- `USER` - имя пользователя на сервере
- `SSH_KEY` - приватный SSH ключ
- `SSH_PASSPHRASE` - пароль SSH ключа
- `DB_ENGINE` - движок базы данных
- `DB_NAME` - имя базы данных
- `POSTGRES_USER` - пользователь PostgreSQL
- `POSTGRES_PASSWORD` - пароль PostgreSQL
- `DB_HOST` - хост базы данных
- `DB_PORT` - порт базы данных
- `DJ_SECRET_KEY` - секретный ключ Django
- `TELEGRAM_TO` - ID чата Telegram
- `TELEGRAM_TOKEN` - токен бота Telegram

## API Endpoints

### Аутентификация
- `POST /api/auth/token/login/` - получение токена
- `POST /api/auth/token/logout/` - выход

### Пользователи
- `GET /api/users/` - список пользователей
- `GET /api/users/{id}/` - профиль пользователя
- `POST /api/users/` - регистрация

### Рецепты
- `GET /api/recipes/` - список рецептов
- `POST /api/recipes/` - создание рецепта
- `GET /api/recipes/{id}/` - детали рецепта
- `PUT /api/recipes/{id}/` - обновление рецепта
- `DELETE /api/recipes/{id}/` - удаление рецепта

### Подписки
- `GET /api/users/subscriptions/` - список подписок
- `POST /api/users/{id}/subscribe/` - подписка на пользователя
- `DELETE /api/users/{id}/subscribe/` - отписка

### Избранное
- `GET /api/recipes/favorite/` - избранные рецепты
- `POST /api/recipes/{id}/favorite/` - добавить в избранное
- `DELETE /api/recipes/{id}/favorite/` - убрать из избранного

### Список покупок
- `GET /api/recipes/download_shopping_cart/` - скачать список покупок
- `POST /api/recipes/{id}/shopping_cart/` - добавить в список покупок
- `DELETE /api/recipes/{id}/shopping_cart/` - убрать из списка покупок

## Функциональность

### Для авторизованных пользователей:
- Создание, редактирование и удаление рецептов
- Подписка на других авторов
- Добавление рецептов в избранное
- Формирование списка покупок
- Скачивание списка покупок

### Для всех пользователей:
- Просмотр рецептов
- Просмотр профилей авторов
- Фильтрация рецептов по тегам

## Разработка

### Запуск тестов
```bash
cd backend
python manage.py test
```

### Линтинг
```bash
cd backend
flake8 .
```

### Миграции
```bash
cd backend
python manage.py makemigrations
python manage.py migrate
```

## Автор

