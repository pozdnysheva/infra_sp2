# Проект YaMDb - сервис отзывов на произведения

### Технологии:
- Python 3.7
- Django 2.2
- Django REST framework 3.12
- библиотека Simple JWT - работа с JWT-токеном
- база данных PostgreSQL

### 
Сервис собирает отзывы на произведения различных категорий (например: книги, песни, фильмы). Произведению может быть присвоен жанр. Каждое произведение получает рейтинг на основе оценок пользователей (от 1 до 10).

С помощью этого проекта можно:
* Читать отзывы на произведения различных категорий и жанров, а также ставить им оценки
* Добавлять, изменять и удалять собственные отзывы
* Оставлять комментарии к отзывам

Работа над проектом велась командная. Я отвечала за создание моделей и представлений, настройку прав доступа к эндпойнтам для жанров, категорий и произведений. Я реализовала добавление оценки и отзывов к произведениям, а также комментариев к отзывам (с учетом прав доступа).

#### Документация доступна после запуска сервера по адресу:
```
http://localhost/redoc/
```
## Как запустить проект, используя Docker (база данных PostgreSQL):
1) Клонируйте репозитроий с проектом:
```
git clone https://github.com/pozdnysheva/infra_sp2.git
```
2) В папке infra создайте файл .env, в котором пропишите следующие переменные окружения:
```
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
```

3) С помощью Dockerfile и docker-compose.yaml разверните проект:
```
docker-compose up -d --build
```
4) В новом окне терминала узнайте id контейнера infra_web и войдите в контейнер:
```
docker container ls
```
```
docker exec -it <CONTAINER_ID> bash
```
5) В контейнере выполните миграции, создайте суперпользователя и заполните базу начальными данными:
```
python manage.py migrate

python manage.py createsuperuser

python manage.py loaddata fixtures.json

python manage.py collectstatic
```

### Авторы:
- [Позднышева Наталья](https://github.com/pozdnysheva "Github page")
- [Цеков Давид](https://github.com/TsekovDavid "Github page")
