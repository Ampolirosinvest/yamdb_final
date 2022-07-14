# API_YaMDb

REST API для социальной сети блогеров Yatube.

## Запуск проекта локально

1) После установки ПО откройте VSCode и откройте терминал (Терминал - Создать терминал). Внизу справа 
нажмите `+` и выберите Git Bash (если предпочитаете пользоваться стандартной командной строкой 
powershell, то используйте их).

2) В командной строке войдите в директорию, где планируете развернуть проект. Например:
```
cd /c/Dev/
```
3) Необходимо склонировать репозитарий проекта:
```
git clone https://github.com/Ampolirosinvest/yamdb_final.git
```
Теперь ваш проект будет храниться в дериктории например: `/c/Dev/yamdb_final`

4) Необходимо собрать docker контейнеры по инструкции docker-compose

Пересобираем docker-image и создаем docker-container
```
docker-compose up -d --build 
```
Если с первого раза не собирается, - повторить.

5) Провести миграции в контейнер web
```
docker-compose exec web python manage.py migrate
```
6) Создать суперпользователя
```
docker-compose exec web python manage.py createsuperuser
```
7) Подключить статику
```
docker-compose exec web python manage.py collectstatic --no-input
```
Теперь проект доступен по адресу `http://localhost/`

С помощью команды *pytest* вы можете запустить тесты и проверить работу модулей

C помощью *flake8* вы можете проверить оформление кода

9) Можно создать пользователя после запуска проекта(Postman):
```
http://127.0.0.1:8000/v1/auth/signup/
```
отправить POST-запрос:

    {
        "username": "XXXXX",
        "email": "XXXXX"
    }

10) В проекте в папке `sent_emails` появится сгенерированное письмо с кодом подтвержения. Скопируйте этот код, он потребуется для получения токена к зарегистрированной учетной записи

## Аутентификация

Выполните POST-запрос *localhost:8000/v1/auth/token/* передав поля username и confirmation_code(см. пункт 9 и 10).

API вернет JWT-токен в формате:

    {
        "token": "ХХХХХXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
    }
    
token - наш токен, который необходимо передать в заголовке Authorization: Bearer <токен> при отправке запросов

Теперь пользователь считается авторизованным и может полноценно использовать текущий проект по отзывам произведений.

## Примеры запросов

### Регистрация пользователей и выдача токенов

Регистрация нового пользователя

Получить код подтверждения на переданный email.
Права доступа: Доступно без токена.
Использовать имя 'me' в качестве username запрещено.
Поля email и username должны быть уникальными.
```
POST http://127.0.0.1:8000/api/v1/auth/signup/
```
Пример запроса:
```
{
"email": "string",
"username": "string"
}
```
Пример ответа:
```
{
"email": "string",
"username": "string"
}
```
Получение JWT-токена

Получение JWT-токена в обмен на username и confirmation code.
Права доступа: Доступно без токена.
```
POST http://127.0.0.1:8000/api/v1/auth/token/
```
Пример запроса:
```
{
"username": "string",
"confirmation_code": "string"
}
```
Пример ответа:
```
{
  "token": "string"
}
```
### Категории

Получение списка всех категорий

Получить список всех категорий
Права доступа: Доступно без токена
```
GET http://127.0.0.1:8000/api/v1/categories/
```
Пример ответа:
```
[
  {
    "count": 0,
    "next": "string",
    "previous": "string",
    "results": [
      {
        "name": "string",
        "slug": "string"
      }
    ]
  }
]
```
Добавление новой категории

Создать категорию.
Права доступа: Администратор.
Поле slug каждой категории должно быть уникальным.
```
POST http://127.0.0.1:8000/api/v1/categories/
```
Пример запроса:
```
{
  "name": "string",
  "slug": "string"
}
```
Пример ответа:
```
{
  "name": "string",
  "slug": "string"
}
```
Удаление категории

Удалить категорию.
Права доступа: Администратор.
```
DELETE http://127.0.0.1:8000/api/v1/categories/{slug}/
```

### Жанры
Получение списка всех жанров

Получить список всех жанров.
Права доступа: Доступно без токена
```
GET http://127.0.0.1:8000/api/v1/genres/
```
Пример ответа:
```
[
  {
    "count": 0,
    "next": "string",
    "previous": "string",
    "results": [
      {
        "name": "string",
        "slug": "string"
      }
    ]
  }
]
```
Добавление жанра

Добавить жанр.
Права доступа: Администратор.
Поле slug каждого жанра должно быть уникальным.
```
POST http://127.0.0.1:8000/api/v1/genres/
```
Пример запроса:
```
{
  "name": "string",
  "slug": "string"
}
```
Удаление жанра

Удалить жанр.
Права доступа: Администратор.
```
DELETE http://127.0.0.1:8000/api/v1/genres/{slug}/
```

### Произведения (Titles)
Получение списка всех произведений

Получить список всех объектов.
Права доступа: Доступно без токена
```
GET http://127.0.0.1:8000/api/v1/titles/
```
Пример ответа:
```
[
  {
    "count": 0,
    "next": "string",
    "previous": "string",
    "results": [
      {
        "id": 0,
        "name": "string",
        "year": 0,
        "rating": 0,
        "description": "string",
        "genre": [
          {
            "name": "string",
            "slug": "string"
          }
        ],
        "category": {
          "name": "string",
          "slug": "string"
        }
      }
    ]
  }
]
```
Добавление произведения

Добавить новое произведение.
Права доступа: Администратор.
Нельзя добавлять произведения, которые еще не вышли (год выпуска не может быть больше текущего).
При добавлении нового произведения требуется указать уже существующие категорию и жанр.
```
POST http://127.0.0.1:8000/api/v1/titles/
```
Пример запроса:
```
{
  "name": "string",
  "year": 0,
  "description": "string",
  "genre": [
    "string"
  ],
  "category": "string"
}
```
Пример ответа:
```
{
  "id": 0,
  "name": "string",
  "year": 0,
  "rating": 0,
  "description": "string",
  "genre": [
    {
      "name": "string",
      "slug": "string"
    }
  ],
  "category": {
    "name": "string",
    "slug": "string"
  }
}
```
Получение информации о произведении

Информация о произведении
Права доступа: Доступно без токена
```
GET http://127.0.0.1:8000/api/v1/titles/{titles_id}/
```
Пример ответа:
```
{
  "id": 0,
  "name": "string",
  "year": 0,
  "rating": 0,
  "description": "string",
  "genre": [
    {
      "name": "string",
      "slug": "string"
    }
  ],
  "category": {
    "name": "string",
    "slug": "string"
  }
}
```
Частичное обновление информации о произведении

Обновить информацию о произведении
Права доступа: Администратор
```
PATCH http://127.0.0.1:8000/api/v1/titles/{titles_id}/
```
Пример запроса:
```
{
  "name": "string",
  "year": 0,
  "description": "string",
  "genre": [
    "string"
  ],
  "category": "string"
}
```
Пример ответа:
```
{
  "id": 0,
  "name": "string",
  "year": 0,
  "rating": 0,
  "description": "string",
  "genre": [
    {
      "name": "string",
      "slug": "string"
    }
  ],
  "category": {
    "name": "string",
    "slug": "string"
  }
}
```
Удаление произведения

Удалить произведение.
Права доступа: Администратор.
```
http://127.0.0.1:8000/api/v1/titles/{titles_id}/
```

### Отзывы (Reviews)
Получение списка всех отзывов

Получить список всех отзывов.
Права доступа: Доступно без токена.
```
GET http://127.0.0.1:8000/api/v1/titles/{title_id}/reviews/
```
Пример ответа:
```
[
  {
    "count": 0,
    "next": "string",
    "previous": "string",
    "results": [
      {
        "id": 0,
        "text": "string",
        "author": "string",
        "score": 1,
        "pub_date": "2019-08-24T14:15:22Z"
      }
    ]
  }
]
```
Добавление нового отзыва

Добавить новый отзыв. Пользователь может оставить только один отзыв на произведение.
Права доступа: Аутентифицированные пользователи.
```
POST http://127.0.0.1:8000/api/v1/titles/{title_id}/reviews/
```
Пример запроса:
```
{
  "text": "string",
  "score": 1
}
```
Пример ответа:
```
{
  "id": 0,
  "text": "string",
  "author": "string",
  "score": 1,
  "pub_date": "2019-08-24T14:15:22Z"
}
```
Полуение отзыва по id

Получить отзыв по id для указанного произведения.
Права доступа: Доступно без токена.
```
GET http://127.0.0.1:8000/api/v1/titles/{title_id}/reviews/{review_id}/
```
Пример ответа:
```
{
  "id": 0,
  "text": "string",
  "author": "string",
  "score": 1,
  "pub_date": "2019-08-24T14:15:22Z"
}
```
Частичное обновление отзыва по id

Частично обновить отзыв по id.
Права доступа: Автор отзыва, модератор или администратор.
```
PATCH http://127.0.0.1:8000/api/v1/titles/{title_id}/reviews/{review_id}/
```
Пример запроса:
```
{
  "text": "string",
  "score": 1
}
```
Пример ответа:
```
{
  "id": 0,
  "text": "string",
  "author": "string",
  "score": 1,
  "pub_date": "2019-08-24T14:15:22Z"
}
```
Удаление отзыва по id

Удалить отзыв по id
Права доступа: Автор отзыва, модератор или администратор.
```
DELETE http://127.0.0.1:8000/api/v1/titles/{title_id}/reviews/{review_id}/
```

### Комментарии к отзывам (Comments)
Получение списка всех комментариев к отзыву

Получить список всех комментариев к отзыву по id
Права доступа: Доступно без токена.
```
GET http://127.0.0.1:8000/api/v1/titles/{title_id}/reviews/{review_id}/comments/
```
Пример ответа:
```
[
  {
    "count": 0,
    "next": "string",
    "previous": "string",
    "results": [
      {
        "id": 0,
        "text": "string",
        "author": "string",
        "pub_date": "2019-08-24T14:15:22Z"
      }
    ]
  }
]
```
Добавление комментария к отзыву

Добавить новый комментарий для отзыва.
Права доступа: Аутентифицированные пользователи.
```
POST http://127.0.0.1:8000/api/v1/titles/{title_id}/reviews/{review_id}/comments/
```
Пример запроса:
```
{
  "text": "string"
}
```
Пример ответа:
```
{
  "id": 0,
  "text": "string",
  "author": "string",
  "pub_date": "2019-08-24T14:15:22Z"
}
```
Получение комментария к отзыву

Получить комментарий для отзыва по id.
Права доступа: Доступно без токена.
```
GET http://127.0.0.1:8000/api/v1/titles/{title_id}/reviews/{review_id}/comments/{comment_id}/
```
Пример ответа:
```
{
  "id": 0,
  "text": "string",
  "author": "string",
  "pub_date": "2019-08-24T14:15:22Z"
}
```
Частичное обновление комментария к отзыву

Частично обновить комментарий к отзыву по id.
Права доступа: Автор комментария, модератор или администратор.
```
PATCH http://127.0.0.1:8000/api/v1/titles/{title_id}/reviews/{review_id}/comments/{comment_id}/
```
Пример запроса:
```
{
  "text": "string"
}
```
Пример ответа:
```
{
  "id": 0,
  "text": "string",
  "author": "string",
  "pub_date": "2019-08-24T14:15:22Z"
}
```
Удаление комментария к отзыву

Удалить комментарий к отзыву по id.
Права доступа: Автор комментария, модератор или администратор.
```
DELETE http://127.0.0.1:8000/api/v1/titles/{title_id}/reviews/{review_id}/comments/{comment_id}/
```

### Пользователи (Users)
Получение списка всех пользователей

Получить список всех пользователей.
Права доступа: Администратор
```
GET http://127.0.0.1:8000/api/v1/users/
```
Пример ответа:
```
[
  {
    "count": 0,
    "next": "string",
    "previous": "string",
    "results": [
      {
        "username": "string",
        "email": "user@example.com",
        "first_name": "string",
        "last_name": "string",
        "bio": "string",
        "role": "user"
      }
    ]
  }
]
```
Добавление пользователя

Добавить нового пользователя.
Права доступа: Администратор
Поля email и username должны быть уникальными
```
POST http://127.0.0.1:8000/api/v1/users/
```
Пример запроса:
```
{
  "username": "string",
  "email": "user@example.com",
  "first_name": "string",
  "last_name": "string",
  "bio": "string",
  "role": "user"
}
```
Пример ответа:
```
{
  "username": "string",
  "email": "user@example.com",
  "first_name": "string",
  "last_name": "string",
  "bio": "string",
  "role": "user"
}
```
Получение пользователя по username

Получить пользователя по username.
Права доступа: Администратор
```
GET http://127.0.0.1:8000/api/v1/users/{username}/
```
Пример запроса:
```
{
  "username": "string",
  "email": "user@example.com",
  "first_name": "string",
  "last_name": "string",
  "bio": "string",
  "role": "user"
}
```
Изменение данных пользователя по username

Изменить данные пользователя по username.
Права доступа: Администратор.
Поля email и username должны быть уникальными.
```
PATCH http://127.0.0.1:8000/api/v1/users/{username}/
```
Пример запроса:
```
{
  "username": "string",
  "email": "user@example.com",
  "first_name": "string",
  "last_name": "string",
  "bio": "string",
  "role": "user"
}
```
Пример ответа:
```
{
  "username": "string",
  "email": "user@example.com",
  "first_name": "string",
  "last_name": "string",
  "bio": "string",
  "role": "user"
}
```
Удаление пользователя по username

Удалить пользователя по username.
Права доступа: Администратор.
```
DELETE http://127.0.0.1:8000/api/v1/users/{username}/
```
Получение данных своей учетной записи

Получить данные своей учетной записи
Права доступа: Любой авторизованный пользователь
```
GET http://127.0.0.1:8000/api/v1/users/me/
```
Пример ответа:
```
{
  "username": "string",
  "email": "user@example.com",
  "first_name": "string",
  "last_name": "string",
  "bio": "string",
  "role": "user"
}
```
Изменение данных своей учетной записи

Изменить данные своей учетной записи
Права доступа: Любой авторизованный пользователь
Поля email и username должны быть уникальными.
```
PATCH http://127.0.0.1:8000/api/v1/users/me/
```
Пример запроса:
```
{
  "username": "string",
  "email": "user@example.com",
  "first_name": "string",
  "last_name": "string",
  "bio": "string"
}
```
Пример ответа:
```
{
  "username": "string",
  "email": "user@example.com",
  "first_name": "string",
  "last_name": "string",
  "bio": "string",
  "role": "user"
}
```