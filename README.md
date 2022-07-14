# yamdb_final
yamdb_final
![example workflow](https://github.com/Ampolirosinvest/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)


## Описание

REST API для социальной сети блогеров Yatube.
Развернут на боевом сервере в ЯндексОблако.
На Github в README.db можно увидеть статут работы проекта.
https://github.com/Ampolirosinvest/yamdb_final/blob/master/README.md
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

## Лоакльный запуск проекта и примеры

 Функции проекта смотри в README api_yamdb

## Описание сборки проекта

В проекте в папке .github/workflows в файле `yamdb_workflow.yml` описан список операций.

При выполнении команды git push проект заливается в репозитарий и начинается проверка проекта
согласно описанным операциям:

1) Проверка кода на соответствие стандарту PEP8

2) Сборка и доставка докер-образа для контейнера `web` на Docker Hub

3) Автоматический деплой проекта на боевой сервер

4) Отправка уведомления в Telegram о том, что процесс деплоя успешно завершился

На Github в репозитарии во вкладке Actions можно увидеть процесс проверки проекта по workflow.
