# yamdb_final
yamdb_final
![example workflow](https://github.com/Ampolirosinvest/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)


## Описание

REST API для социальной сети блогеров Yatube.
Развернут на боевом сервере в ЯндексОблако.
На Github в README.db в начале проекта можно увидеть статут работы проекта.
Проект - http://84.252.143.113/admin/


Проект отзывов YaMDb в рамках обучения на Яндекс Практикум. Благодаря этому проекту можно оставлять отзывы на произведения в различных категориях (например -книги, фильмы, музыка). Благодарные или возмущённые пользователи оставляют к произведениям текстовые отзывы и оценивают произведение по шкале от 1 до 10. Исходя из среднего значения оценое формируется рейтинг произведения. На одно произведение уникальный пользователь может оставить только один отзыв.

## Характеристики

Аутентификация по JWT-токену

Работает со всеми модулями социальной YaMDb: произведениями, отзывами, категориями, жанрами, комментариями.

Получение списка всех категорий, добавление новой категории, удаление категории.

Получение списка всех жанров, добавление жанра, удаление жанра.

Получение списка всех произведений, добавление произведения, удаление произведения.

Получение информации о произведении, частичное обновление информации о произведении.

Получение списка всех отзывов, добавление нового отзыва, полуение отзыва по id.

Частичное обновление отзыва по id, удаление отзыва по id.

Получение списка всех комментариев к отзыву, добавление комментария к отзыву, получение комментария к отзыву.

Частичное обновление комментария к отзыву, удаление комментария к отзыву.

Получение списка всех пользователей, добавление пользователя, получение пользователя по username.

Изменение данных пользователя по username, удаление пользователя по username.

Получение данных своей учетной записи, Изменение данных своей учетной записи.

Поддерживает методы GET, POST, PUT, PATCH, DELETE

Предоставляет данные в формате JSON


## Стек технологий

- Django REST Framework v.3.12.4- написание проекта на Python v.3.7+
- Simple JWT(djangorestframework-simplejwt v.4.7.2) - работа с JWT-токеном
- Git v.2.35.1 - управление версиями
- Docker — программное обеспечение для автоматизации развёртывания и управления приложениями 
в средах с поддержкой контейнеризации
- Nginx - веб-сервер и почтовый прокси-сервер, работающий на Unix-подобных операционных системах
- PostgreSQL - свободная объектно-реляционная система управления базами данных (СУБД)

## Подготовка ПО

### Инструкция для Windows

Установите программное обеспечение: скачайте установочные файлы и запустите их.

Python: https://python.org/downloads/

Visual Studio Code: https://visualstudio.com/download/

Git: https://git-scm.com/download/win/

Docker: https://www.docker.com/products/docker-desktop/

### Инструкция для Linux (Ubuntu)

Запустите программу Терминал.

1) Сперва установите Python, для этого в терминале выполните команду. Перед установкой терминал попросит вас ввести пароль администратора — сделайте это.
```
sudo apt-get install python3.7 
```
2) По такой же схеме установите Git
```
sudo apt-get install git 
```
3)Чтобы установить редактор вам понадобится менеджер пакетов `snap`. Установите его командой
```
sudo apt install snap 
```
4) Устанавливаем редактор Visual Studio Code из дополнительного набора пакетов:
```
sudo snap install code --classic 
```
5) После того, как всё скачается и установится, вы сможете запустить Visual Studio Code командой `code` в терминале.

### Лоакльный запуск проекта

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

4) Установите виртуальное окружение
```
python3 -m venv venv
```
5) Активируйте виртуальное окружение
```
. venv/Scripts/activate
```
5) Установите зависимости внутри виртуального окружения
```
pip install -r requirements.txt
```

### Подготовка локального ПО для установки Docker

1) Windows 10: Корпоративная и Pro

Для Корпоративной и Pro-версий Windows виртуализация настраивается на основе гипервизора Hyper-V.
Включите его: перейдите в Панель управления — Программы и компоненты — Включение и отключение компонентов Windows -активируйте пункт Hyper-V - перезагрузите компьютер

2) Windows 10 Home

Для корректной работы Docker в Windows 10 Home установите подсистему Linux (WSL2), описание действией смотрите на официальнос странице - https://docs.microsoft.com/ru-ru/windows/wsl/install

3) Windows 7

Для настройки системы виртуализации в Windows 7:
- скачайте и установите специальную программу для работы с виртуальными машинами, например, VMWare или VirtualBox;
- скачайте образ Ubuntu;
- установите Docker по инструкции для Linux (она ниже в этом уроке).

### Установка Docker на на Windows 10/11 и MacOS

Зайдите на официальный сайт проекта и скачайте установочный файл Docker Desktop для вашей операционной системы - https://www.docker.com/products/docker-desktop/

Запустите его и следуйте инструкциям по установке. Для Windows программа предложит установить необходимые компоненты для WSL2. Поставьте галочку, если будете использовать эту систему виртуализации.

После установки запустите приложение. Программа предложит принять лицензионное соглашение. Ознакомьтесь со всеми терминами, поставьте галочку возле пункта I accept the terms и нажмите кнопку Accept.

Далее вы можете пройти стартовое руководство. Нажмите кнопку Start, если хотите это сделать, а если нет — нажимайте Skip tutorial и переходите к рабочему пространству.

Docker Desktop готов к работе! Зелёная полоска с китом в левом нижнем углу окна приложения означает, что сервис успешно запустился.

### Установка Docker на Linux

Скачать и выполнить официальный скрипт:
```
# Установка утилиты для скачивания файлов
sudo apt install curl
# Эта команда скачает скрипт для установки докера
curl -fsSL https://get.docker.com -o get-docker.sh
# Эта команда запустит его
sh get-docker.sh  
```

### Подключение к боевому серверу

Подключение по логину и паролю

Чтобы войти на сервер, нужно знать адрес сервера, имя пользователя и пароль. Адрес сервера указывается по IP-адресу или по доменному имени. Команда для подключения вводится в формате ssh username@server_address
```
ssh admin@84.201.161.196
# admin: имя пользователя, под которым будет выполнено подключение к серверу
# 84.201.161.196: ip-адрес сервера 
```

Подключение по ssh-ключу

Для большей безопасности при подключении по SSH вместо логина и пароля применяют пары криптографических ключей.

Получить ssh-ключ
```
cat ~/.ssh/id_rsa.pub 
```

Пример подключения
```
ssh-copy-id ~/.ssh/id_rsa.pub admin@84.201.161.196
```

### Подготовка боевого сервера

Для начала войдите на свой сервер, который развернут в яндекс облаке

1) Остановите службу nginx
```
 sudo systemctl stop nginx
```

2) Установите docker
```
sudo apt install docker.io
```

3) Установите docker-compose
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

Скопируйте файлы docker-compose.yaml и nginx/default.conf из вашего проекта на сервер в home/<ваш_username>/docker-compose.yaml и home/<ваш_username>/nginx/default.conf соответственно

Теперь боевой сервер готов к разворачиванию на нем контейнеров, которые мы задеплоим на сервер согласно инструкции workflow.

### Подготовка секретных данных

1)Зайдите в репозиторий на Github - sittings - secrets -actions

2) Жмем New repository secret и добавляем следующие значения:

HOST - ip вашего удалённого сервера

USER - имя пользователя

SSH_KEY

PASSPHRASE - пароль

DB_ENGINE - можно использовать значение 'django.db.backends.postgresql'

POSTGRES_USER - можно использовать значение postgres 

POSTGRES_PASSWORD  - можно использовать значение postgres

DB_HOST - можно использовать значение db

DB_PORT - можно использовать значение 5432

DOCKER_PASSWORD - пароль от dockerhub

DOCKER_USERNAME - имя пользователя dockerhub

TELEGRAM_TO - id вашего телеграм аккаунта

TELEGRAM_TOKEN - токен телеграм-бота (в workflow настроена отправка ботом сообщения об успешном деплое проекта на удалённый сервер)

### Описание сборки проекта

В проекте в папке .github/workflows в файле `yamdb_workflow.yml` описан список операций.

При выполнении команды git push проект заливается в репозитарий и начинается проверка проекта
согласно описанным операциям:

1) Проверка кода на соответствие стандарту PEP8

2) Сборка и доставка докер-образа для контейнера `web` на Docker Hub

3) Автоматический деплой проекта на боевой сервер

4) Отправка уведомления в Telegram о том, что процесс деплоя успешно завершился

На Github в репозитарии во вкладке Actions можно увидеть процесс проверки проекта по workflow.

### Последние приготовления:

На боевом сервере необходимо провести миграции, создать суперпользователя и подключить статику

1) Миграции 
``` 
sudo docker-compose exec web python manage.py makemigrations reviews 
``` 
``` 
sudo docker-compose exec web python manage.py migrate --run-syncdb
``` 

2)Суперпользователь
``` 
sudo docker-compose exec web python manage.py createsuperuser 
``` 

3) Статика
``` 
sudo docker-compose exec web python manage.py collectstatic --no-input 
``` 

### Примеры запросов (Postman в помощь)

### Регистрация пользователей и выдача токенов

Регистрация нового пользователя

Получить код подтверждения на переданный email.
Права доступа: Доступно без токена.
Использовать имя 'me' в качестве username запрещено.
Поля email и username должны быть уникальными.
```
POST http://<ip-сервера>/api/v1/auth/signup/
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
POST http://<ip-сервера>/api/v1/auth/token/
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

confirmation_code приходит в папку проекта.

Зайтите на боевой сервер и откройте докер контейнер который отвечает за бекенд
```
sudo docker exec -it <CONTAINER ID> bash 
```

Узнать ID контейнера можно так(нам нужен контейнер `web`):
```
sudo docker container ls
```

Перейдите в папку `sent_emails` и откройте лог.

Внутри будет поле:

Код для токена: <ВАШ_КОД>

Выходим из докер контейнера
```
exit
```

Полученный токен внесите в Headers в формате:
```
Bearer <токен>
```

Теперь вы авторизованы и можно пользоваться другими функциями. Примеры ниже

### Категории

Получение списка всех категорий

Получить список всех категорий
Права доступа: Доступно без токена
```
GET http://<ip-сервера>/api/v1/categories/
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
POST http://<ip-сервера>/api/v1/categories/
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
DELETE http://<ip-сервера>/api/v1/categories/{slug}/
```

### Жанры
Получение списка всех жанров

Получить список всех жанров.
Права доступа: Доступно без токена
```
GET http://<ip-сервера>/api/v1/genres/
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
POST http://<ip-сервера>/api/v1/genres/
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
DELETE http://<ip-сервера>/api/v1/genres/{slug}/
```

### Произведения (Titles)
Получение списка всех произведений

Получить список всех объектов.
Права доступа: Доступно без токена
```
GET http://<ip-сервера>/api/v1/titles/
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
POST http://<ip-сервера>/api/v1/titles/
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
GET http://<ip-сервера>/api/v1/titles/{titles_id}/
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
PATCH http://<ip-сервера>/api/v1/titles/{titles_id}/
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
http://<ip-сервера>/api/v1/titles/{titles_id}/
```

### Отзывы (Reviews)
Получение списка всех отзывов

Получить список всех отзывов.
Права доступа: Доступно без токена.
```
GET http://<ip-сервера>/api/v1/titles/{title_id}/reviews/
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
POST http://<ip-сервера>/api/v1/titles/{title_id}/reviews/
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
GET http://<ip-сервера>/api/v1/titles/{title_id}/reviews/{review_id}/
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
PATCH http://<ip-сервера>/api/v1/titles/{title_id}/reviews/{review_id}/
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
DELETE http://<ip-сервера>/api/v1/titles/{title_id}/reviews/{review_id}/
```

### Комментарии к отзывам (Comments)
Получение списка всех комментариев к отзыву

Получить список всех комментариев к отзыву по id
Права доступа: Доступно без токена.
```
GET http://<ip-сервера>/api/v1/titles/{title_id}/reviews/{review_id}/comments/
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
POST http://<ip-сервера>/api/v1/titles/{title_id}/reviews/{review_id}/comments/
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
GET http://<ip-сервера>/api/v1/titles/{title_id}/reviews/{review_id}/comments/{comment_id}/
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
PATCH http://<ip-сервера>/api/v1/titles/{title_id}/reviews/{review_id}/comments/{comment_id}/
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
DELETE http://<ip-сервера>/api/v1/titles/{title_id}/reviews/{review_id}/comments/{comment_id}/
```

### Пользователи (Users)
Получение списка всех пользователей

Получить список всех пользователей.
Права доступа: Администратор
```
GET http://<ip-сервера>/api/v1/users/
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
POST http://<ip-сервера>/api/v1/users/
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
GET http://<ip-сервера>/api/v1/users/{username}/
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
PATCH http://<ip-сервера>/api/v1/users/{username}/
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
DELETE http://<ip-сервера>/api/v1/users/{username}/
```
Получение данных своей учетной записи

Получить данные своей учетной записи
Права доступа: Любой авторизованный пользователь
```
GET http://<ip-сервера>/api/v1/users/me/
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
PATCH http://<ip-сервера>/api/v1/users/me/
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