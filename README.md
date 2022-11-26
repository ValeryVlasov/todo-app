# todo-app

# Микросервис для создания списков дел

## Список используемых технологий:

* [Gin](https://github.com/gin-gonic/gin) - HTTP Go Framework
* [Postgres](https://github.com/lib/pq) - СУБД PostgreSQL
* [Docker](https://www.docker.com/) - Docker
* [viper](https://github.com/spf13/viper) - Работа с файлами конфигурации
* [sqlx](https://github.com/jmoiron/sqlx) - Работа с БД
* [migrate](https://github.com/golang-migrate/migrate) - Миграции в БД

## Для запуска приложения:

``` bash
make build && make run
```

Если приложение запускается впервые, необходимо применить миграции к базе данных:

``` bash
make migrate
```

# Примеры запросов/ответов

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/altimetry-cosmonaut-24747535/workspace/9b7c651f-7961-43ec-99a6-3af777ee7f1e/documentation/17406947-515440b7-8466-465d-bc3e-a49c8e40cc53)

### Зарегистрировать пользователя
``` bash
POST localhost:8000/auth/sign-up
# Body(json)
{
    "name": "Name",
    "username": "Username",
    "password": "qwerty"
}
```

### Войти за пользователя
``` bash
POST localhost:8000/auth/sign-in
# Body(json)
{
    "username": "Username",
    "password": "qwerty"
}
```

### Создать список
``` bash
POST http://localhost:8000/api/lists
# Body(json)
{
    "title": "myList",
    "description": "descriptionOfMyList"
}
```

### Добавить элемент в список
``` bash
POST http://localhost:8000/api/lists/<list_id>/items
# Body(json)
{
    "title": "Bananas",
    "description": "Yellow and tasty"
}
```

### Изменить элемент
``` bash
PUT http://localhost:8000/api/items/<item id>
{
    "done": true
}
```

### Посмотреть предметы списка
``` bash
GET http://localhost:8000/api/lists
# Body response
{
    "data": [
        {
            "id": 1,
            "title": "myList",
            "description": "descriptionOfMyList"
        },
        {
            "id": 2,
            "title": "TodoList",
            "description": "Very important things"
        }
    ]
}
```

### Посмотреть элементы списка
``` bash
GET http://localhost:8000/api/lists/<list id>/items
# Body response
[
    {
        "id": 1,
        "title": "Bananas",
        "description": "Yellow and tasty",
        "done": false
    },
    {
        "id": 2,
        "title": "Watermelon",
        "description": "green outside and round",
        "done": true
    }
]
```

### Удаление списка
``` bash
DELETE http://localhost:8000/api/lists/2
# Body response
{
    "status": "ok"
}
```

### Удаление элемента
``` bash
DELETE http://localhost:8000/api/items/2
# Body response
{
    "status": "ok"
}
```
