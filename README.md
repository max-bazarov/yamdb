# YaMDb API
[![Yamdb workflow](https://github.com/max-bazarov/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)](https://github.com/max-bazarov/yamdb_final/actions/workflows/yamdb_workflow.yml)

## Описание
Проект YaMDb собирает отзывы (Review) пользователей на произведения (Title). Произведения делятся на категории: «Книги», «Фильмы», «Музыка».
Список категорий (Category) может быть расширен администратором (например, можно добавить категорию «Изобразительное искусство» или «Ювелирка»).
В каждой категории есть произведения: книги, фильмы или музыка.

Произведению может быть присвоен жанр (Genre) из списка предустановленных (например, «Сказка», «Рок» или «Артхаус»). 
Новые жанры может создавать только администратор.

Благодарные или возмущённые пользователи оставляют к произведениям текстовые отзывы (Review) и ставят произведению оценку в диапазоне от одного до десяти (целое число); из пользовательских оценок формируется усреднённая оценка произведения — рейтинг (целое число). На одно произведение пользователь может оставить только один отзыв.

## Технологии
- Python 3.10.4
- Django REST Framework
- PostgreSQL
- Docker
- Nginx
- Gunicorn

## Установка и запуск
- Склонируйте репозиторий на свой компьютер
- Измените файл .env.dist на .env и заполните его
- Убедитесь, что у вас установлен Docker и Docker Compose последних версий
- Запустите проект командой `docker-compose up`
- При первом запуске проекта необходимо выполнить миграции командой `docker-compose exec web python manage.py migrate`
- Создайте суперпользователя командой `docker-compose exec web python manage.py createsuperuser`
- Соберите статику командой `docker-compose exec web python manage.py collectstatic`
- Проект доступен по адресу http://localhost/ 

## Пример запросов
- Регистрация пользователя
```
POST /api/v1/auth/signup/
{
    "email": "test@test.com",
    "username": "test"
}
```
- Получение JWT-токена
```
POST /api/v1/auth/token/
{
    "username": "test",
    "confirmation_code": "12345"
}
```
- Получение списка всех категорий
```
GET /api/v1/categories/
```
