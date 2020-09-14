# PWS-15_d9_api

## Доступен в Heroku по адресу:
https://whispering-reef-52117.herokuapp.com/

## Установка и запуск (все действия через коммандную строку)
  - скачать проект и перейти в директорию проекта
```
$ git clone https://github.com/LovingFox/PWS-15_d9_api
$ cd PWS-15_d9_api
```

  - создать виртуальное окружение
```
$ python -m venv env
```

  - применить виртуальное окружение
```
### Если у вас Linux:
$ source env/bin/activate
### Если у вас Windows:
$ env\Scripts\activate.bat
```

 - установить зависимости
```
$ pip install -r requirements.txt
```

  - загрузить фикстуры в качестве примеров
```
$ python manage.py loaddata data.json
```

  - запустить сервер
```
$ python manage.py runserver
```

## Использование

#### Категории
API: /categories/

Allow: GET, POST, HEAD, OPTIONS

Пример содержания для POST создания новой Категории:
```json
{
    "name": "Название категории"
}
```

API: /categories/<cat_id>

Allow: GET, PUT, PATCH, DELETE, HEAD, OPTIONS

Пример ответа GET /categories/1:
```json
{
    "id": 1,
    "name": "Название категории"
}
```

#### Посты
Для GET и для POST/PUT/PATCH "Постов" используются разные сериализаторы вложенных объектов. Для GET сериализатор вложенных объектов будет выводить все их данные, а для POST/PUT/PATCH десериализатор для вложенных элементов принимает только их id.

API: /

Allow: GET, POST, HEAD, OPTIONS

Пример содержания для POST нового Поста:
```json
{
    "title": "Заголовок поста",
    "status": "P",
    "content": "Содержание поста",
    "category": 1,
    "author": 1
}
```

API: /<post_id>

Allow: GET, PUT, PATCH, DELETE, HEAD, OPTIONS

Пример ответа GET /1:
```json
{
    "id": 1,
    "author": {
        "id": 1,
        "username": "admin",
        "first_name": "",
        "last_name": ""
    },
    "category": {
        "id": 1,
        "name": "Название категории"
    },
    "title": "Заголовок поста",
    "status": "P",
    "content": "Содержание поста",
    "updated": "2020-09-12T06:47:28.548000Z",
    "publication_date": "2020-09-12T06:47:28.548000Z"
}
```

#### Авторы
Данные Авторов можно только смотреть, изменять нельзя


API: /authors/

API: /authors/<author_id>

Allow: GET, HEAD, OPTIONS

Пример ответа на GET /authors/
```json
[
    {
        "id": 2,
        "username": "megauser",
        "first_name": "Mega",
        "last_name": "User"
    },
    {
        "id": 1,
        "username": "admin",
        "first_name": "",
        "last_name": ""
    }
]
```

## Админка
/admin

admin

pass
