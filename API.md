# Архив результатов испытания


## RESTful API

1. [Темы] (#1-Темы)
  1. [Получение темы] (#11-Получение-темы-get-themesid) `GET /themes/:id`
  2. [Создание темы] (#12-Создание-темы-post-themes) `POST /themes`
  3. [Редактирование темы] (#13-Редактирование-темы-put-themesid) `PUT /themes/:id`
  4. [Удаление темы] (#14-Удаление-темы-delete-themesid) `DELETE /themes/:id`
2. [Объекты] (#2-Объекты)
  1. [Получение объекта] (#21-Получение-объекта-get-objectsid) `GET /objects/:id`
  2. [Получение объекта в контексте темы] (#22-Получение-объекта-в-контексте-темы-get-objectsidthemesid) `GET /objects/:id/themes/:id`
  3. [Редактирование объекта] (#23-Редактирование-объекта-put-objectsid) `PUT /objects/:id`
  4. [Редактирование объекта в теме] (#24-Редактирование-объекта-в-теме-put-objectsidthemesid) `PUT /objects/:id/themes/:id`
  5. [Удаление объекта из темы] (#25-Удаление-объекта-из-темы-delete-objectsidthemesid) `DELETE /objects/:id/themes/:id`
3. [Испытания] (#3-Испытания)
  1. [Получение испытания] (#31-Получение-испытания-get-experimentsid) `GET /experiments/:id`
  2. [Создание испытания] (#32-Создание-испытания-post-experiments) `POST /experiments`
  3. [Редактирование испытания] (#33-Редактирование-испытания-put-experimentsid) `PUT /experiments/:id`
  4. [Удаление испытания] (#34-Удаление-испытания-delete-experimentsid) `DELETE /experiments/:id`
4. [История] (#4-История)
  1. [Получение истории] (#41-Получение-истории-get-historyid) `GET /history/:id`
  2. [Получение истории в контексте темы (для объекта)] (#42-Получение-истории-в-контексте-темы-для-объекта-get-historyidthemesid) `GET /history/:id/themes/:id`
5. [Поиск] (#5-Поиск)
  1. [Получение результатов] (#51-Получение-результатов-get-searchparams) `GET /search/:params`
  2. [Получение всех тем] (#52-Получение-всех-тем-get-searchthemes) `GET /search/themes`
  3. [Поиск по изделиям] (#53-Поиск-по-изделиям-get-searchproductsparams) `GET /search/products/:params`
  4. [Поиск по составным частям] (#54-Поиск-по-составным-частям-get-searchcomponentsparams) `GET /search/components/:params`
  5. [Поиск по узлам] (#55-Поиск-по-узлам-get-searchunitsparams) `GET /search/units/:params`
6. [Места проведения и отделы] (#6-Места-проведения-и-отделы)
  1. [Получение мест] (#61-Получение-мест-get-placeslocations) `GET /places/locations`
  2. [Получение отделов] (#62-Получение-отделов-get-placesdepts) `GET /places/depts`
7. [Информация о пользователе] (#7-Информация-о-пользователе)
  1. [Получение информации] (#71-Получение-информации-get-userinfo) `GET /userinfo`
8. [Отчеты] (#8-Отчеты)
  1. [Отправка списка целей для генерации отчета] (#81-Отправка-списка-целей-для-генерации-отчета-post-reports) `POST /reports`
9. [Статусы] (#9-Статусы)
  1. [Статусы тем] (#91-Статусы-тем)
  2. [Статусы объектов] (#92-Статусы-объектов)
  3. [Статусы испытаний] (#93-Статусы-испытаний)
  4. [Статусы задач] (#94-Статусы-задач)


## 1. Темы

### 1.1. Получение темы `GET /themes/:id`
**Request**
```http
GET /themes/6516c43c-b2e7-459d-a793-17b60b478445 HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK

{
  "name": "Название темы",
  "status": "Статус темы",
  "objects": [
    {
      "id": "817139c0-dfdc-4928-a375-7cd5a18d1f3c",
      "name": "Изделие1",
      "status": "Статус изделия1",
      "type": 0
    },
    {
      "id": "cbec02ca-999a-4645-830e-8dee5dbb6054",
      "name": "Изделие2",
      "status": "Статус изделия2",
      "type": 0
    }
  ],
  "isReadonly": true
}
```

### 1.2. Создание темы `POST /themes`

**Request**
```http
POST /themes HTTP/1.1

{
  "name": "Название темы",
  "objects": [
    {
      "id": "55f8b311-1f06-496e-abb8-a83dc8e72556"
    },
    {
      "id": "4f5c6f5a-ff97-411e-8bd3-09770101f123"
    },
    {
      "name": "Новый объект"
    }
  ],
  "status": "Статус темы"
}
```
**Response**
```http
HTTP/1.1 201 Created

{
  "id": "9e015079-d11d-4bf2-bed7-53a562f86caa"
}
```

### 1.3. Редактирование темы `PUT /themes/:id`

**Request**
```http
PUT /themes/d4ccab6c-b004-4506-9793-f22a7728a1d8 HTTP/1.1

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
  "status": "Статус темы"
}
```
**Response**
```http
HTTP/1.1 200 OK
```

### 1.4. Удаление темы `DELETE /themes/:id`

**Request**
```http
PUT /themes/01c7c18c-2196-4284-b3a2-527f1df3d8c2 HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK
```


## 2. Объекты

### 2.1. Получение объекта `GET /objects/:id`
**Request**
```http
GET /objects/6516c43c-b2e7-459d-a793-17b60b478445 HTTP/1.1
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
      "type": 1
    },
    {
      "id": "9c8550f3-95a9-418e-a593-b9f5d5ab548d",
      "name": "Название объекта2",
      "type": 1
    }
  ],
  "type": 0,
  "isReadonly": true
}
```
```http
HTTP/1.1 200 OK

{
  "name": "Название объекта",
  "parentObject": 
  {
    "id": "ded2c20d-f02f-40d5-8133-46af19163993",
    "name": "Название родительского объекта",
    "type": 0
  },
  "type": 1,
  "isReadonly": true
}
```

### 2.2. Получение объекта в контексте темы `GET /objects/:id/themes/:id`
**Request**
```http
GET /objects/6516c43c-b2e7-459d-a793-17b60b478445/themes/7d113f55-97e2-4ebd-a2eb-8dd316801be6 HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK

{
  "name": "Название составной части",
  "theme": 
  {
    "id": "8cf4694d-3ba8-467e-882a-100c3b822fa7",
    "name": "Название темы"
  },
  "parentObject": 
  {
    "id": "8cf4694d-3ba8-467e-882a-100c3b822fa7",
    "name": "Название изделия",
    "type": 0
  },
  "objects": [
    {
      "id": "817139c0-dfdc-4928-a375-7cd5a18d1f3c",
      "name": "Узел1",
      "status": "Статус узла1",
      "type": 2
    },
    {
      "id": "cbec02ca-999a-4645-830e-8dee5dbb6054",
      "name": "Узел2",
      "status": "Статус узла2",
      "type": 2
    }
  ],
  "status": "Статус объекта",
  "experiments": [
    {
      "id": "23544374-08dc-46b1-bb1c-2b4a8cb4a691",
      "name": "Название испытания1",
      "status": "Статус испытания1"
    },
    {
      "id": "b1372926-10dd-4040-a276-80986678f6a3",
      "name": "Название испытания2",
      "status": "Статус испытания2"
    },
    {
      "id": "eba84e8d-3449-4094-801c-3b9f30e62474",
      "name": "Название испытания3",
      "status": "Статус испытания3"
    }
  ],
  "type": 1,
  "isReadonly": true
}
```

### 2.3. Редактирование объекта `PUT /objects/:id`

**Request**
```http
PUT /objects/d4ccab6c-b004-4506-9793-f22a7728a1d8 HTTP/1.1

{
  "name": "Название объекта",
  "type": 0
}
```
**Response**
```http
HTTP/1.1 200 OK
```

### 2.4. Редактирование объекта в теме `PUT /objects/:id/themes/:id`

**Request**
```http
PUT /objects/d4ccab6c-b004-4506-9793-f22a7728a1d8/themes/0a68f229-6506-4bc4-96e4-9aa792403fde HTTP/1.1

{
  "name": "Название объекта",
  "status": "Статус объекта",
  "objects": [
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

### 2.5. Удаление объекта из темы `DELETE /objects/:id/themes/:id`

**Request**
```http
DELETE /objects/d4ccab6c-b004-4506-9793-f22a7728a1d8/themes/286fe904-4ac7-4c82-a036-af13eac64d12 HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK
```


## 3. Испытания

### 3.1. Получение испытания `GET /experiments/:id`

**Request**
```http
GET /experiments/50fd1615-4bf3-4f37-8fb3-fa0abfd64fa5 HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK

{
  "name": "Название программы",
  "location": "Место проведения",
  "dept": "Название отдела",
  "objects": [
    {
      "id": "817139c0-dfdc-4928-a375-7cd5a18d1f3c",
      "name": "Изделие1",
      "type": 0
    },
    {
      "id": "eec0dcf8-33a3-452f-80c9-200bdc16bd82",
      "name": "Составная часть1",
      "type": 1
    },
    {
      "id": "86956055-6058-426c-b730-7d2c7f963cdc",
      "name": "Составная часть2",
      "type": 1
    },
    {
      "id": "5e9299cd-fb98-42a6-a31e-43a3945a8be2",
      "name": "Узел1",
      "type": 2
    },
    {
      "id": "2174ebbe-2c00-40a7-b322-427cfac06d24",
      "name": "Узел2",
      "type": 2
    },
    {
      "id": "cbec02ca-999a-4645-830e-8dee5dbb6054",
      "name": "Изделие2",
      "type": 0  
    }	
  ],
  "reason": "Основание для испытания",
  "tasks": [
    {
      "id": "3e11ec53-df59-443f-93e5-d0ced1b9a066",
      "name": "Название задачи1",
      "dept": "Отдел/Цех",
      "planBegin": "2013-23-09 00:00",
      "planEnd": "2013-24-09 00:00",
      "finishDate": "2013-25-09 00:00",
      "docs": [
        "файл.doc",
        "Документ №1"
      ],
      "notes": "Примечание",
      "status": "Статус задачи1"
    },
    {
      "id": "db087811-26e3-4234-a879-7c4f43530579",
      "name": "Название задачи2",
      "dept": "Отдел/Цех",
      "planBegin": "2013-26-09 00:00",
      "planEnd": "2013-27-09 00:00",
      "finishDate": "2013-28-09 00:00",
      "docs": [
        "файл.doc",
        "Документ №1"
      ],
      "notes": "Примечание",
      "status": "Статус задачи2",
      "additionalParams": {
        "extConditions": [
       	  {
       	    "name": "Температура",
       	    "value": 36.6
       	  },
       	  {
       	    "name": "Влажность",
       	    "value": 234
       	  },
       	  {
       	    "name": "Давление",
       	    "value": 5367
       	  }
        ],
        "equipment": [
          "Объект1 (k шт.)",
          "Объект2 (l шт.)",
          "Объект3 (m шт.)",
          "Объект4 (n шт.)"
        ]
      }
    }
  ],
  "status": "Статус испытания",
  "reports": [
    "отчет.doc",
    "Акт №1"
  ],
  "conclusion": "Заключение",
  "isReadonly": true
}
```

### 3.2. Создание испытания `POST /experiments`

**Request**
```http
POST /experiments HTTP/1.1

{
  "name": "Название программы",
  "location": "Место проведения",
  "dept": "Название отдела",
  "objects": [
    {
      "id": "817139c0-dfdc-4928-a375-7cd5a18d1f3c",
      "name": "Изделие1",
      "type": 0
    },
    {
      "id": "eec0dcf8-33a3-452f-80c9-200bdc16bd82",
      "name": "Составная часть1",
      "type": 1
    },
    {
      "id": "86956055-6058-426c-b730-7d2c7f963cdc",
      "name": "Составная часть2",
      "type": 1
    },
    {
      "id": "5e9299cd-fb98-42a6-a31e-43a3945a8be2",
      "name": "Узел1",
      "type": 2
    },
    {
      "id": "2174ebbe-2c00-40a7-b322-427cfac06d24",
      "name": "Узел2",
      "type": 2
    },
    {
      "id": "cbec02ca-999a-4645-830e-8dee5dbb6054",
      "name": "Изделие2",
      "type": 0  
    }	
  ],
  "reason": "Основание для испытания",
  "tasks": [
    {
      "id": "874a3836-d801-479e-8566-28fc9ca428f0"
    },
    {
      "id": "480f84c8-c378-4cf5-a4e3-5cc9c5ef15d4"
    }
  ],
  "status": "Статус испытания",
  "filesToUpload": [] // файлы для загрузки
}
```
**Response**
```http
HTTP/1.1 201 Created

{
  "id": "9e015079-d11d-4bf2-bed7-53a562f86caa"
}
```

### 3.3. Редактирование испытания `PUT /experiments/:id`

**Request**
```http
PUT /experiments/d4ccab6c-b004-4506-9793-f22a7728a1d8 HTTP/1.1

{
  "name": "Название программы",
  "location": "Место проведения",
  "dept": "Название отдела",
  "objects": [
    {
      "id": "817139c0-dfdc-4928-a375-7cd5a18d1f3c",
      "name": "Изделие1",
      "type": 0
    },
    {
      "id": "eec0dcf8-33a3-452f-80c9-200bdc16bd82",
      "name": "Составная часть1",
      "type": 1
    },
    {
      "id": "86956055-6058-426c-b730-7d2c7f963cdc",
      "name": "Составная часть2",
      "type": 1
    },
    {
      "id": "5e9299cd-fb98-42a6-a31e-43a3945a8be2",
      "name": "Узел1",
      "type": 2
    },
    {
      "id": "2174ebbe-2c00-40a7-b322-427cfac06d24",
      "name": "Узел2",
      "type": 2
    },
    {
      "id": "cbec02ca-999a-4645-830e-8dee5dbb6054",
      "name": "Изделие2",
      "type": 0  
    }	
  ],
  "reason": "Основание для испытания",
  "tasks": [
    {
      "id": "874a3836-d801-479e-8566-28fc9ca428f0"
    },
    {
      "id": "480f84c8-c378-4cf5-a4e3-5cc9c5ef15d4"
    }
  ],
  "status": "Статус испытания",
  "reports": [
    "отчет.doc",
    "Акт №1"
  ],
  "conclusion": "Заключение",
  "filesToUpload": [] // файлы для загрузки
}
```
**Response**
```http
HTTP/1.1 200 OK
```

### 3.4. Удаление испытания `DELETE /experiments/:id`

**Request**
```http
DELETE /experiments/d4ccab6c-b004-4506-9793-f22a7728a1d8 HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK
```


## 4. История

### 4.1. Получение истории `GET /history/:id`

**Request**
```http
GET /history/772de9b9-9f39-4ae4-bda5-7138f44b6e84 HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK

[
  {
    "author": "Фамилия И.О.",
    "datetime": "Nov 1 2013 17:45:00 GMT+0600",
    "changed": {
      "name": "Новое название"
    }
  },
  {
    "author": "Фамилия И.О.",
    "datetime": "Oct 30 2013 15:56:00 GMT+0600",
    "changed": {
      "name": "Новое название",
      "status": "Новый статус"
    }
  },
  {
    "author": "Фамилия И.О.",
    "datetime": "Oct 22 2013 15:54:00 GMT+0600",
    "changed": {
      "object": {
        "id": "c6dda2d9-dc23-44fc-84b4-24b3c57470f1",
        "name": "Наименование нового объекта"
      }
    }
  },
  {
    "author": "Фамилия И.О.",
    "datetime": "Oct 01 2013 12:56:00 GMT+0600",
    "changed": {
      "object": {
        "id": "c6dda2d9-dc23-44fc-84b4-24b3c57470f1",
        "name": "Наименование удаленного объекта",
        "isDeleted": true
      }
    }
  },
  {
    "author": "Фамилия И.О.",
    "datetime": "Sep 25 2013 15:09:00 GMT+0600",
    "changed": {
      "task": {
        "id":  "85b42f27-0ee4-4131-a9ec-cd0f4e73fd0b",
        "name": "Название новой задачи"
      }
    }
  },
  {
    "author": "Фамилия И.О.",
    "datetime": "Aug 24 2013 18:32:00 GMT+0600",
    "changed": {
      "task": {
        "id":  "85b42f27-0ee4-4131-a9ec-cd0f4e73fd0b",
        "name": "Задача с новым статусом",
        "status": "Новый статус"
      }
    }
  },
  {
    "author": "Фамилия И.О.",
    "datetime": "Aug 23 2013 18:32:00 GMT+0600",
    "changed": {
      "experiment": {
        "id": "65a48c27-1ee8-3451-a9ec-cd0f4e45416b",
        "name": "Название нового эксперимента"
      }
    }
  }
]
```

### 4.2. Получение истории в контексте темы (для объекта) `GET /history/:id/themes/:id`

**Request**
```http
GET /history/772de9b9-9f39-4ae4-bda5-7138f44b6e84 HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK

[
  {
    "author": "Фамилия И.О.",
    "datetime": "Nov 1 2013 17:45:00 GMT+0600",
    "changed": {
      "name": "Новое название"
    }
  },
  {
    "author": "Фамилия И.О.",
    "datetime": "Oct 30 2013 15:56:00 GMT+0600",
    "changed": {
      "name": "Новое название",
      "status": "Новый статус"
    }
  },
  {
    "author": "Фамилия И.О.",
    "datetime": "Oct 22 2013 15:54:00 GMT+0600",
    "changed": {
      "object": {
        "id": "c6dda2d9-dc23-44fc-84b4-24b3c57470f1",
        "name": "Наименование нового объекта"
      }
    }
  },
  {
    "author": "Фамилия И.О.",
    "datetime": "Oct 01 2013 12:56:00 GMT+0600",
    "changed": {
      "object": {
        "id": "c6dda2d9-dc23-44fc-84b4-24b3c57470f1",
        "name": "Наименование удаленного объекта",
        "isDeleted": true
      }
    }
  },
  {
    "author": "Фамилия И.О.",
    "datetime": "Aug 24 2013 18:32:00 GMT+0600",
    "changed": {
      "task": {
        "id":  "85b42f27-0ee4-4131-a9ec-cd0f4e73fd0b",
        "name": "Задача с новым статусом",
        "status": "Новый статус"
      }
    }
  },
  {
    "author": "Фамилия И.О.",
    "datetime": "Aug 23 2013 18:32:00 GMT+0600",
    "changed": {
      "experiment": {
        "id": "65a48c27-1ee8-3451-a9ec-cd0f4e45416b",
        "name": "Название нового эксперимента"
      }
    }
  }
]
```


## 5. Поиск

### 5.1. Получение результатов `GET /search/:params`

**Request**
```http
GET /search?q=поисковый+запрос&firstdate=01.01.2001&lastdate=12.12.2012 HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK

{
  "themes": [
    {
      "id": "a8d7322b-81e3-4e98-afc7-f71f45057a37",
      "name": "Название темы1",
      "status": "Статус темы1"
    },
    {
      "id": "73580df4-ef64-410b-a224-f4f18389aff7",
      "name": "Название темы2",
      "status": "Статус темы2"
    }
  ],
  "objects": [
    {
      "id": "a8d7322b-81e3-4e98-afc7-f71f45057a37",
      "name": "Название объекта1",
      "type": 0
    },
    {
      "id": "73580df4-ef64-410b-a224-f4f18389aff7",
      "name": "Название объекта2",
      "type": 1
    },
    {
      "id": "f828c8de-da40-41e4-9e4b-7c6c004bcb00",
      "name": "Название объекта3",
      "type": 2
    }
  ],
  "experiments": [
    {
      "id": "a8d7322b-81e3-4e98-afc7-f71f45057a37",
      "name": "Название испытания1",
      "status": "Статус испытания1"
    },
    {
      "id": "73580df4-ef64-410b-a224-f4f18389aff7",
      "name": "Название испытания2",
      "status": "Статус испытания2"
    }
  ]
}
```

### 5.2. Получение всех тем `GET /search/themes`

**Request**
```http
GET /search HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK

[
  {
    "id": "a8d7322b-81e3-4e98-afc7-f71f45057a37",
    "name": "Название темы1",
    "status": "Статус темы1"
  },
  {
    "id": "73580df4-ef64-410b-a224-f4f18389aff7",
    "name": "Название темы2",
    "status": "Статус темы2"
  },
  {
    "id": "1695e36a-5b29-46e0-a4db-2f01944cca45",
    "name": "Название темы3",
    "status": "Статус темы3"
  },
  {
    "id": "361fbe91-dd50-45a8-8a4b-43faa80062b0",
    "name": "Название темы4",
    "status": "Статус темы4"
  },
  {
    "id": "27715feb-b5a3-47e9-ae29-a7ab49eeca52",
    "name": "Название темы5",
    "status": "Статус темы5"
  }
]
```

### 5.3. Поиск по изделиям `GET /search/products/:params`

**Request**
```http
GET /search/products?q=поисковый+запрос HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK

[
  {
    "id": "a8d7322b-81e3-4e98-afc7-f71f45057a37",
    "name": "Название объекта1"
  },
  {
    "id": "73580df4-ef64-410b-a224-f4f18389aff7",
    "name": "Название объекта2"
  }
]
```

### 5.4. Поиск по составным частям `GET /search/components/:params`

**Request**
```http
GET /search/components?q=поисковый+запрос HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK

[
  {
    "id": "a8d7322b-81e3-4e98-afc7-f71f45057a37",
    "name": "Название объекта1"
  },
  {
    "id": "73580df4-ef64-410b-a224-f4f18389aff7",
    "name": "Название объекта2"
  }
]
```

### 5.5. Поиск по узлам `GET /search/units/:params`

**Request**
```http
GET /search/units?q=поисковый+запрос HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK

[
  {
    "id": "a8d7322b-81e3-4e98-afc7-f71f45057a37",
    "name": "Название объекта1"
  },
  {
    "id": "73580df4-ef64-410b-a224-f4f18389aff7",
    "name": "Название объекта2"
  }
]
```


## 6. Места проведения и отделы

### 6.1. Получение мест `GET /places/locations`

**Request**
```http
GET /places/locations HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK

[
  "Название места1",
  "Название места2",
  "Название места3"
]
```

### 6.2. Получение отделов `GET /places/depts`

**Request**
```http
GET /places/depts HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK

[
  "Название отдела1",
  "Название отдела2",
  "Название отдела3"
]
```


## 7. Информация о пользователе

### 7.1. Получение информации `GET /userinfo`

**Request**
```http
GET /userinfo HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK

{
  "name": "Имя пользователя",
  "role": 0
}
```


## 8. Отчеты

### 8.1. Отправка списка целей для генерации отчета `POST /reports`

**Request**
```http
POST /reports HTTP/1.1

[
  "9e015079-d11d-4bf2-bed7-53a562f86caa",
  "e26ff474-71e9-46c7-b518-b08f069d309f",
  "08f68cfd-ead0-43b6-ba07-e77bbd3c6429",
  "ea1dbf21-fa5e-46ed-b805-4aca78d49b08"
]
```
**Response**
```http
HTTP/1.1 201 Created

"http://127.0.0.1/reports/894185c5-709f-450c-9789-fb0470b6a2eb.xls"
```


## 9. Статусы

### 9.1. Статусы тем

```
[
  {
    "name": "Этап 'ЭП'",
    "type": 1
  },
  {
    "name": "Этап 'ТП'",
    "type": 1
  },
  {
    "name": "Разработка РКД",
    "type": 1
  },
  {
    "name": "Проведение ПИ",
    "type": 1
  },
  {
    "name": "Проведение ГИ",
    "type": 1
  },
  {
    "name": "Работы приостановлены",
    "type": 0
  },
  {
    "name": "Работы завершены",
    "type": 2
  }
]
```

### 9.2. Статусы объектов

```
[
  {
    "name": "Отработка начата",
    "type": 1
  },
  {
    "name": "Отработка завершена",
    "type": 2
  },
  {
    "name": "Отработка отменена",
    "type": 0
  }
]
```

### 9.3. Статусы испытаний

```
[
  {
    "name": "Работа начата",
    "type": 1
  },
  {
    "name": "Испытание проведено",
    "type": 2
  },
  {
    "name": "Работа завершена",
    "type": 2
  },
  {
    "name": "Работа отменена",
    "type": 0
  }
]
```

### 9.4. Статусы задач

```
[
  {
    "name": "Не выполнено",
    "type": 0
  },
  {
    "name": "Выполнено",
    "type": 2
  },
  {
    "name": "Не заказано",
    "type": 0
  },
  {
    "name": "Заказано",
    "type": 2
  },
  {
    "name": "Изготовлено",
    "type": 2
  },
  {
    "name": "Результаты положительные",
    "type": 2
  },
  {
    "name": "Результаты отрицательные",
    "type": 0    
  },
  {
    "name": "Работу продолжить",
    "type": 2
  },
  {
    "name": "Работу прекратить",
    "type": 0
  }
]
```
