# Архив результатов испытания


## RESTful API

1. [Темы] (#1-Темы)
  1. [Получение темы] (#11-Получение-темы-get-themeid) `GET /theme/:id`
  2. [Поиск темы] (#12-Поиск-темы-get-themesearchparams) `GET /theme/search/:params`
  3. [История изменения темы] (#13-История-изменения-темы-get-themeidhistory) `GET /theme/:id/history`
  4. [История изменения объекта темы] (#14-История-изменения-объекта-темы-get-themeidobjecthistoryid) `GET /theme/:id/objecthistory/:id`
  5. [Создание темы] (#15-Создание-темы-post-theme) `POST /theme`
  6. [Редактирование темы] (#16-Редактирование-темы-put-themeid) `PUT /theme/:id`
  7. [Удаление темы] (#17-Удаление-темы-delete-themeid) `DELETE /theme/:id`
2. [Объекты] (#2-Объекты)
  1. [Получение объекта] (#21-Получение-объекта-get-objectid) `GET /object/:id`
  2. [Поиск объекта] (#22-Поиск-объекта-get-objectsearchparams) `GET /object/search/:params`
  3. [Создание объекта] (#23-Создание-объекта-post-object) `POST /object`
  4. [Редактирование объекта] (#24-Редактирование-объекта-put-objectid) `PUT /object/:id`
  5. [Удаление объекта] (#25-Удаление-объекта-delete-objectid) `DELETE /object/:id`
3. [Испытания] (#3-Испытания)
  1. [Получение испытания] (#31-Получение-испытания-get-experimentid) `GET /experiment/:id`
  2. [Поиск испытания] (#32-Поиск-испытания-get-experimentsearchparams) `GET /experiment/search/:params`
  3. [Создание испытания] (#33-Создание-испытания-post-experiment) `POST /experiment`
  4. [Редактирование испытания] (#34-Редактирование-испытания-put-experimentid) `PUT /experiment/:id`
  5. [Удаление испытания] (#35-Удаление-испытания-delete-experimentid) `DELETE /experiment/:id`
4. [Задачи] (#4-Задачи)
  1. [Получение задачи] (#41-Получение-задачи-get-taskid) `GET /task/:id`
  2. [Создание задачи] (#42-Создание-задачи-post-task) `POST /task`
  3. [Редактирование задачи] (#43-Редактирование-задачи-put-taskid) `PUT /task/:id`
  4. [Удаление задачи] (#44-Удаление-задачи-delete-taskid) `DELETE /task/:id`
5. [Места проведения] (#5-Места-проведения)
  1. [Получение места] (#51-Получение-места-get-locationid) `GET /location/:id`
  2. [Поиск места] (#52-Поиск-места-get-locationsearchparams) `GET /location/search/:params`
  3. [Создание места] (#53-Создание-места-post-location) `POST /location`
  4. [Редактирование места] (#54-Редактирование-места-put-locationid) `PUT /location/:id`
  5. [Удаление места] (#55-Удаление-места-delete-locationid) `DELETE /location/:id`


## 1. Темы

### 1.1. Получение темы `GET /theme/:id`
**Request**
```http
GET /theme/6516c43c-b2e7-459d-a793-17b60b478445 HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK

{
  "name": "Название темы",
  "status": 0,
  "objects": [
    {
      "id": "ded2c20d-f02f-40d5-8133-46af19163993",
      "name": "Название объекта1",
      "status": 0,
    },
    {
      "id": "9c8550f3-95a9-418e-a593-b9f5d5ab548d",
      "name": "Название объекта2",
      "status": 1
    }
  ]
}
```

### 1.2. Поиск темы `GET /theme/search/:params`
**Request**
```http
GET /theme/search?q=поисковый+запрос&firstdate=01.01.2001&lastdate=12.12.2012 HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK

{
  "themes": [
    {
      "id": "a8d7322b-81e3-4e98-afc7-f71f45057a37",
      "name": "Название темы1",
      "status": 0
    },
    {
      "id": "a8d7322b-81e3-4e98-afc7-f71f45057a37",
      "name": "Название темы2",
      "status": 1
    }
  ]
}
```

### 1.3. История изменения темы `GET /theme/:id/history`
**Request**
```http
GET /theme/history/ HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK

{
  "history": [
    {
      "author": "Фамилия И.О.",
      "datetime": "2014-10-24 17:42",
      "theme": {
        "name": "Новое название"
      }
    },
    {
      "author": "Фамилия И.О.",
      "datetime": "2013-09-23 16:41",
      "theme": {
        "status": 1
      }
    },
    {
      "author": "Фамилия И.О.",
      "datetime": "2012-08-22 15:40",
      "theme": {
        "objects": [
          {
            "id": "c6dda2d9-dc23-44fc-84b4-24b3c57470f1",
            "name": "Новый объект"
          }
        ]
      }
    },
    {
      "author": "Фамилия И.О.",
      "datetime": "2011-07-21 14:39",
      "theme": {
        "objects": [
          {
            "id": "c6dda2d9-dc23-44fc-84b4-24b3c57470f1",
            "name": "Удаленный объект",
            "isdeleted": true
          }
        ]
      }
    },
    {
      "author": "Фамилия И.О.",
      "datetime": "2010-06-20 13:38",
      "theme": {
        "objects": [
          {
            "id": "c6dda2d9-dc23-44fc-84b4-24b3c57470f1",
            "name": "Объект с новым статусом",
            "status": 2
          }
        ]
      }
    }
  ]
}
```

### 1.4. История изменения объекта темы `GET /theme/:id/objecthistory/:id`

### 1.5. Создание темы `POST /theme`

### 1.6. Редактирование темы `PUT /theme/:id`

### 1.7. Удаление темы `DELETE /theme/:id`


## 2. Объекты

### 2.1. Получение объекта `GET /object/:id`

### 2.2. Поиск объекта `GET /object/search/:params`

### 2.3. Создание объекта `POST /object`

### 2.4. Редактирование объекта `PUT /object/:id`

### 2.5. Удаление объекта `DELETE /object/:id`


## 3. Испытания

### 3.1. Получение испытания `GET /experiment/:id`

### 3.2. Поиск испытания `GET /experiment/search/:params`

### 3.3. Создание испытания `POST /experiment`

### 3.4. Редактирование испытания `PUT /experiment/:id`

### 3.5. Удаление испытания `DELETE /experiment/:id`


## 4. Задачи

### 4.1. Получение задачи `GET /task/:id`

### 4.2. Создание задачи `POST /task`

### 4.3. Редактирование задачи `PUT /task/:id`

### 4.4. Удаление задачи `DELETE /task/:id`


## 5. Места проведения

### 5.1. Получение места `GET /location/:id`

### 5.2. Поиск места `GET /location/search/:params`

### 5.3. Создание места `POST /location`

### 5.4. Редактирование места `PUT /location/:id`

### 5.5. Удаление места `DELETE /location/:id`
