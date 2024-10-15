# To-Do App

## Описание

Это простое To-Do приложение, разработанное на Flask с использованием PostgreSQL. Оно позволяет добавлять, редактировать, удалять и просматривать задачи. Аутентификация осуществляется с помощью JWT-токенов. Для удобства разработки приложение упаковано с помощью Docker Compose.

## Функционал

- Аутентификация через JWT (один пользователь: `admin` / `password`)
- Просмотр всех задач
- Добавление новых задач
- Редактирование существующих задач
- Удаление задач

## Используемые технологии

- Flask
- SQLAlchemy
- PostgreSQL
- JWT (Flask-JWT-Extended)
- Docker и Docker Compose

## Требования

- Docker
- Docker Compose

## Установка и запуск

1. Клонируйте репозиторий:

    ```bash
    git clone https://github.com/lolevan/todo-app.git
    ```

2. Перейдите в директорию проекта:

    ```bash
    cd todo-app
    ```

3. Соберите и запустите контейнеры Docker:

    ```bash
    docker-compose up --build
    ```

4. Приложение будет доступно по адресу [http://localhost:5000](http://localhost:5000).

## Тестирование с использованием `curl`

### 1. Аутентификация (один юзуер)

```bash
curl -X POST http://localhost:5000/login \
-H "Content-Type: application/json" \
-d '{
    "username": "admin",
    "password": "password"
}'
```

**Ответ:**
```json
{
    "access_token": "<your_jwt_token>"
}
```

### 2. Получение списка задач

```bash
curl -X GET http://localhost:5000/tasks \
-H "Authorization: Bearer <your_jwt_token>"
```

### 3. Создание новой задачи

```bash
curl -X POST http://localhost:5000/tasks \
-H "Content-Type: application/json" \
-H "Authorization: Bearer <your_jwt_token>" \
-d '{
    "title": "Купить продукты",
    "description": "Купить молоко, яйца, хлеб"
}'
```

### 4. Обновление задачи

```bash
curl -X PUT http://localhost:5000/tasks/1 \
-H "Content-Type: application/json" \
-H "Authorization: Bearer <your_jwt_token>" \
-d '{
    "title": "Купить продукты и напитки",
    "description": "Добавить сок и чай"
}'
```

### 5. Удаление задачи

```bash
curl -X DELETE http://localhost:5000/tasks/1 \
-H "Authorization: Bearer <your_jwt_token>"
```

## Лицензия

Этот проект распространяется под лицензией MIT.

---

Этот `README.md` поможет пользователям понять, как установить, запустить и протестировать ваше приложение. Вы можете дополнительно настроить его под свои нужды и указать репозиторий, если необходимо.
