# Архив результатов испытания


## RESTful API

1. [Темы] (#1-Темы)
  1. [Получение темы] (#11-Получение-темы-get-themeid) `GET /theme/:id`
  2. [История изменения темы] (#12-История-изменения-темы-get-themeidhistory) `GET /theme/:id/history`
  3. [Поиск темы] (#13-Поиск-темы-get-themesearchparams) `GET /theme/search/:params`
  4. [Создание темы] (#14-Создание-темы-post-theme) `POST /theme`
  5. [Редактирование темы] (#15-Редактирование-темы-put-themeid) `PUT /theme/:id`
  6. [Удаление темы] (#16-Удаление-темы-delete-themeid) `DELETE /theme/:id`
2. [Объекты] (#2-Объекты)
  1. [Получение объекта] (#21-Получение-объекта-get-objectid) `GET /object/:id`
  2. [Получение объекта в контексте темы] (#22-Получение-объекта-в-контексте-темы-get-objectidthemeid) `GET /object/:id/theme/:id`
  3. [История изменения объекта в теме] (#23-История-изменения-объекта-в-теме-get-objectidhistoryid) `GET /object/:id/history/:id`
  4. [Поиск объекта] (#24-Поиск-объекта-get-objectsearchparams) `GET /object/search/:params`
  5. [Создание объекта] (#25-Создание-объекта-post-object) `POST /object`
  6. [Редактирование объекта] (#26-Редактирование-объекта-put-objectid) `PUT /object/:id`
  7. [Редактирование объекта в теме] (#27-Редактирование-объекта-в-теме-put-objectidthemeid) `PUT /object/:id/theme/:id`
  8. [Удаление объекта] (#28-Удаление-объекта-delete-objectid) `DELETE /object/:id`
  9. [Удаление объекта из темы] (#29-Удаление-объекта-из-темы-delete-objectidthemeid) `DELETE /object/:id/theme/:id`
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

### 1.2. История изменения темы `GET /theme/:id/history`
**Request**
```http
GET /theme/50fd1615-4bf3-4f37-8fb3-fa0abfd64fa5/history HTTP/1.1
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

### 1.3. Поиск темы `GET /theme/search/:params`
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
      "id": "73580df4-ef64-410b-a224-f4f18389aff7",
      "name": "Название темы2",
      "status": 1
    }
  ]
}
```

### 1.4. Создание темы `POST /theme`

**Request**
```http
POST /theme HTTP/1.1

{
  "name": "Название темы",
  "objects": [
    {
      "id": "55f8b311-1f06-496e-abb8-a83dc8e72556"
    },
    {
      "id": "4f5c6f5a-ff97-411e-8bd3-09770101f123"
    }
  ],
  status: 0
}
```
**Response**
```http
HTTP/1.1 201 Created

{
    "id": "9e015079-d11d-4bf2-bed7-53a562f86caa"
}
```

### 1.5. Редактирование темы `PUT /theme/:id`

**Request**
```http
PUT /theme/d4ccab6c-b004-4506-9793-f22a7728a1d8 HTTP/1.1

{
  "name": "Название темы",
  "objects": [
    {
      "id": "f4805cbc-201b-4b2b-8eeb-fd0f25955b14"
    },
    {
      "id": "0b73cf36-bb0c-4819-aa9d-2da11ad61e75"
    }
  ],
  status: 0
}
```
**Response**
```http
HTTP/1.1 200 OK
```

### 1.6. Удаление темы `DELETE /theme/:id`

**Request**
```http
PUT /theme/01c7c18c-2196-4284-b3a2-527f1df3d8c2 HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK
```


## 2. Объекты

### 2.1. Получение объекта `GET /object/:id`
**Request**
```http
GET /object/6516c43c-b2e7-459d-a793-17b60b478445 HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK

{
  "name": "Название объекта",
  "objects": [
    {
      "id": "ded2c20d-f02f-40d5-8133-46af19163993",
      "name": "Название объекта1",
    },
    {
      "id": "9c8550f3-95a9-418e-a593-b9f5d5ab548d",
      "name": "Название объекта2",
    }
  ]
}
```

### 2.2. Получение объекта в контексте темы `GET /object/:id/theme/:id`
**Request**
```http
GET /object/6516c43c-b2e7-459d-a793-17b60b478445/theme/7d113f55-97e2-4ebd-a2eb-8dd316801be6 HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK

{
  "name": "Название объекта",
  "theme": {
    "id": "8cf4694d-3ba8-467e-882a-100c3b822fa7",
    "name": "Название темы"
  },
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
  ],
  "status": 0,
  "experiments": [
    {
      "id": "23544374-08dc-46b1-bb1c-2b4a8cb4a691",
      "name": "Название испытания1",
      "status": 0
    },
    {
      "id": "b1372926-10dd-4040-a276-80986678f6a3",
      "name": "Название испытания2",
      "status": 1
    },
    {
      "id": "eba84e8d-3449-4094-801c-3b9f30e62474",
      "name": "Название испытания3",
      "status": 2
    }
  ]
}
```

### 2.3. История изменения объекта в теме `GET /object/:id/history/:id`
**Request**
```http
GET /object/567eea32-54d6-49a1-8c33-dcc0dd0a3d8a/history/bcd25224-b57f-44aa-9689-0f71d07fa2ee HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK

{
  "history": [
    {
      "author": "Фамилия И.О.",
      "datetime": "2014-10-24 17:42",
      "experiments": [
        {
          "id": "f774eea5-11f4-46c1-ad4c-05e0cdd3839e"
          "name": "Новый эксперимент"
        }
      ]
    },
    {
      "author": "Фамилия И.О.",
      "datetime": "2013-09-23 16:41",
      "status": 1
    },
    {
      "author": "Фамилия И.О.",
      "datetime": "2012-08-22 15:40",
      "objects": [
        {
          "id": "c6dda2d9-dc23-44fc-84b4-24b3c57470f1",
          "name": "Новый объект"
        }
      ]
    },
    {
      "author": "Фамилия И.О.",
      "datetime": "2011-07-21 14:39",
      "objects": [
        {
          "id": "c6dda2d9-dc23-44fc-84b4-24b3c57470f1",
          "name": "Удаленный объект",
          "isdeleted": true
        }
      ]
    },
    {
      "author": "Фамилия И.О.",
      "datetime": "2010-06-20 13:38",
      "objects": [
        {
          "id": "c6dda2d9-dc23-44fc-84b4-24b3c57470f1",
          "name": "Объект с новым статусом",
          "status": 2
        }
      ]
    }
  ]
}
```

### 2.4. Поиск объекта `GET /object/search/:params`

**Request**
```http
GET /object/search?q=поисковый+запрос HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK

{
  "objects": [
    {
      "id": "a8d7322b-81e3-4e98-afc7-f71f45057a37",
      "name": "Название объекта1"
    },
    {
      "id": "73580df4-ef64-410b-a224-f4f18389aff7",
      "name": "Название объекта2"
    }
  ]
}
```

### 2.5. Создание объекта `POST /object`

**Request**
```http
POST /object HTTP/1.1

{
  "name": "Название объекта",
  "objects": [
    {
      "id": "55f8b311-1f06-496e-abb8-a83dc8e72556"
    },
    {
      "id": "4f5c6f5a-ff97-411e-8bd3-09770101f123"
    }
  ]
}
```
**Response**
```http
HTTP/1.1 201 Created

{
    "id": "9e015079-d11d-4bf2-bed7-53a562f86caa"
}
```

### 2.6. Редактирование объекта `PUT /object/:id`

**Request**
```http
PUT /object/d4ccab6c-b004-4506-9793-f22a7728a1d8 HTTP/1.1

{
  "name": "Название объекта"
}
```
**Response**
```http
HTTP/1.1 200 OK
```

### 2.7. Редактирование объекта в теме `PUT /object/:id/theme/:id`

**Request**
```http
PUT /object/d4ccab6c-b004-4506-9793-f22a7728a1d8/theme/0a68f229-6506-4bc4-96e4-9aa792403fde HTTP/1.1

{
  "status": 1,
  "experiments": [
    {
      "id": "c0090788-7d44-4d85-9b44-aa5105e432de"
    },
    {
      "id": "54d33321-0e56-4028-9ba1-349f3a173d17"
    }
  ]
}
```
**Response**
```http
HTTP/1.1 200 OK
```

### 2.8. Удаление объекта `DELETE /object/:id`

**Request**
```http
PUT /object/d4ccab6c-b004-4506-9793-f22a7728a1d8 HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK
```

### 2.9. Удаление объекта из темы `DELETE /object/:id/theme/:id`

**Request**
```http
PUT /object/d4ccab6c-b004-4506-9793-f22a7728a1d8/theme/286fe904-4ac7-4c82-a036-af13eac64d12 HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK
```


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
