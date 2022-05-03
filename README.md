![example workflow](https://github.com/ivanshtepaweb/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

### Описание проекта YaMDb:

Вы можете найти любимое произведение в проекте YaMDb. 
Это может быть книга, фильм или музыкальное произведение. Есть возможность поделиться своим мнением через комментарии,
читать отзывы и ставить им оценки.

Проект реализован через RESTful API (включая Django и Django REST Framework).

Позволяет делать запросы к моделям проекта: Произведения, Категории, Жанры, Рейтинг, Отзывы.

Поддерживает методы GET, POST, PUT, PATCH, DELETE

Предоставляет данные в формате JSON

### Как запустить проект:

Для начала убедитесь, что у вас установлен Docker командой:

```
docker -v
```

Клонируйте репозиторий и перейдите в него в командной строке:

```
https://github.com/ivanshtepaweb/yamdb_final
cd yamdb_final
```

Перейдите в папку с проектом и создайте и активируйте виртуальное окружение:

```
cd api_yamdb
python3 -m venv env
```

```
source venv/Scripts/activate
```

```
python3 -m pip install --upgrade pip
```

Установите зависимости из файла requirements.txt:

```
pip install -r requirements.txt
```

Перейдите в папку с файлом docker-compose.yaml:

```
cd infra
```

Разверните контейнеры:

```
docker-compose up -d --build
```

Выполните миграции, создайте суперпользователя, соберите статику:

```
docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py createsuperuser
docker-compose exec web python manage.py collectstatic --no-input
```


Создайте дамп (резервную копию) базы:

```
docker-compose exec web python manage.py dumpdata > fixtures.json
```


Примеры запросов:

Пример POST-запроса для аутентифицированного пользователя: добавление нового произведения. POST .../api/v1/titles/

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
       {}
    ],
    "category": {
        "name": "string",
        "slug": "string"
    }
}
```

Пример POST-запроса для аутентифицированного пользователя: добавление комментария к отзыву. POST .../api/v1/titles/{title_id}/reviews/{review_id}/comments/

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

Пример GET-запроса для любого пользователя: получение списка всех отзывов. GET .../api/v1/titles/{title_id}/reviews/


Пример ответа:

```
[
    {
    "count": 0,
    "next": "string",
    "previous": "string",
    "results": []
    }
]
```
## Приложение работает по ссылкам:
http://51.250.29.254/admin/
http://51.250.29.254/redoc/
http://51.250.29.254/api/v1/


### Автор проекта yamdb_final:
Иван Штепа  
https://github.com/ivanshtepaweb/

