
# Yamdb_final #

![Build Status](https://github.com/Stepan-Solnyshkin/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)


## Описание: ##


Проект по запуску Docker-контейнера для проекта [YaMDb](https://github.com/Stepan-Solnyshkin/api_yamdb)


# Как запустить  проект:

Клонирование репозитория в командной строке:

```
bash
git clone https://github.com/Stepan-Solnyshkin/yamdb_final
```
### Шаблон .env файла:
*Создать .env файл нужно внутри директории infra/ (на одном уровне с docker-compose.yaml*
```
bash
touch .env
```
*Пример .env:*
```
SECRET_KEY = 'psupadupasecretkey228322lz@4zqj=rq&agdol^##zgl9(vs'
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=<пользователь>
POSTGRES_PASSWORD=<пароль>
DB_HOST=db
DB_PORT=5432
```

Запуск проект:

```
bash
docker-compose up -d --build 
```
Выполнение миграций, создание суперпользователя и перенос статики:
```
bash
docker-compose exec web python manage.py makemigrations
docker-compose exec web python manage.py migrate
winpty docker-compose exec web python manage.py createsuperuser
docker-compose exec web python manage.py collectstatic --no-input
```

Заполнение базы начальными данными:

```
bash
docker-compose exec web python manage.py loaddata fixtures.json
```

Сам проект, админ-панель и документацию искать по адресам:
```
http://localhost/
http://localhost/admin
http://localhost/redoc
```

**Над проектом работал:**

Степан Солнышкин | [Github](https://github.com/Stepan-Solnyshkin) |