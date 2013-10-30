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
  3. [Создание объекта] (#23-Создание-объекта-post-objects) `POST /objects`
  4. [Редактирование объекта] (#24-Редактирование-объекта-put-objectsid) `PUT /objects/:id`
  5. [Редактирование объекта в теме] (#25-Редактирование-объекта-в-теме-put-objectsidthemesid) `PUT /objects/:id/themes/:id`
  6. [Удаление объекта] (#26-Удаление-объекта-delete-objectsid) `DELETE /objects/:id`
  7. [Удаление объекта из темы] (#27-Удаление-объекта-из-темы-delete-objectsidthemesid) `DELETE /objects/:id/themes/:id`
3. [Испытания] (#3-Испытания)
  1. [Получение испытания] (#31-Получение-испытания-get-experimentsid) `GET /experiments/:id`
  2. [Создание испытания] (#32-Создание-испытания-post-experiments) `POST /experiments`
  3. [Редактирование испытания] (#33-Редактирование-испытания-put-experimentsid) `PUT /experiments/:id`
  4. [Удаление испытания] (#34-Удаление-испытания-delete-experimentsid) `DELETE /experiments/:id`
4. [Задачи] (#4-Задачи)
  1. [Получение задачи] (#41-Получение-задачи-get-tasksid) `GET /tasks/:id`
  2. [Создание задачи] (#42-Создание-задачи-post-tasks) `POST /tasks`
  3. [Редактирование задачи] (#43-Редактирование-задачи-put-tasksid) `PUT /tasks/:id`
  4. [Удаление задачи] (#44-Удаление-задачи-delete-tasksid) `DELETE /tasks/:id`
5. [История] (#5-История)
  1. [Получение истории] (#51-Получение-истории-get-historyid) `GET /history/:id`
6. [Поиск] (#6-Поиск)
  1. [Получение результатов] (#61-Получение-результатов-get-searchparams) `GET /search/:params`
7. [Места проведения и отделы] (#7-Места-проведения-и-отделы)
  1. [Получение мест] (#71-Получение-мест-get-placeslocations) `GET /places/locations`
  2. [Получение отделов] (#72-Получение-отделов-get-placesdepts) `GET /places/depts`
8. [Информация о пользователе] (#8-Информация-о-пользователе)
  1. [Получение информации] (#81-Получение-информации-get-userinfo) `GET /userinfo`
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
      "id": "ded2c20d-f02f-40d5-8133-46af19163993",
      "name": "Название объекта1",
      "status": "Статус объекта1",
    },
    {
      "id": "9c8550f3-95a9-418e-a593-b9f5d5ab548d",
      "name": "Название объекта2",
      "status": "Статус объекта2"
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
    },
    {
      "id": "9c8550f3-95a9-418e-a593-b9f5d5ab548d",
      "name": "Название объекта2",
    }
  ],
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
  "name": "Название объекта",
  "theme": {
    "id": "8cf4694d-3ba8-467e-882a-100c3b822fa7",
    "name": "Название темы"
  },
  "objects": [
    {
      "id": "ded2c20d-f02f-40d5-8133-46af19163993",
      "name": "Название объекта1",
      "status": "Статус объекта1",
    },
    {
      "id": "9c8550f3-95a9-418e-a593-b9f5d5ab548d",
      "name": "Название объекта2",
      "status": "Статус объекта2"
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
  "isReadonly": true
}
```

### 2.3. Создание объекта `POST /objects`

**Request**
```http
POST /objects HTTP/1.1

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

### 2.4. Редактирование объекта `PUT /objects/:id`

**Request**
```http
PUT /objects/d4ccab6c-b004-4506-9793-f22a7728a1d8 HTTP/1.1

{
  "name": "Название объекта"
}
```
**Response**
```http
HTTP/1.1 200 OK
```

### 2.5. Редактирование объекта в теме `PUT /objects/:id/themes/:id`

**Request**
```http
PUT /objects/d4ccab6c-b004-4506-9793-f22a7728a1d8/themes/0a68f229-6506-4bc4-96e4-9aa792403fde HTTP/1.1

{
  "status": "Статус объекта",
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

### 2.6. Удаление объекта `DELETE /objects/:id`

**Request**
```http
DELETE /objects/d4ccab6c-b004-4506-9793-f22a7728a1d8 HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK
```

### 2.7. Удаление объекта из темы `DELETE /objects/:id/themes/:id`

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
      "objects": [
        {
          "id": "eec0dcf8-33a3-452f-80c9-200bdc16bd82",
          "name": "Составная часть1"
        },
        {
          "id": "86956055-6058-426c-b730-7d2c7f963cdc",
          "name": "Составная часть2",
          "objects": [
            {
    	      "id": "5e9299cd-fb98-42a6-a31e-43a3945a8be2",
              "name": "Узел1"
    	    },
    	    {
    	      "id": "2174ebbe-2c00-40a7-b322-427cfac06d24",
              "name": "Узел2"
    	    }
          ]
        }		
      ]
    },
    {
      "id": "cbec02ca-999a-4645-830e-8dee5dbb6054",
      "name": "Изделие2"    
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
      "id": "817139c0-dfdc-4928-a375-7cd5a18d1f3c"
      "objects": [
	{
	  "id": "eec0dcf8-33a3-452f-80c9-200bdc16bd82"
	},
	{
	  "id": "86956055-6058-426c-b730-7d2c7f963cdc",
	  "objects": [
	    {
	      "id": "5e9299cd-fb98-42a6-a31e-43a3945a8be2"
	    },
	    {
	      "id": "2174ebbe-2c00-40a7-b322-427cfac06d24"
	    }
	  ]
	}		
      ]
    },
    {
      "id": "cbec02ca-999a-4645-830e-8dee5dbb6054"
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
  "status": "Статус испытания"
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
      "id": "817139c0-dfdc-4928-a375-7cd5a18d1f3c"
      "objects": [
	{
	  "id": "eec0dcf8-33a3-452f-80c9-200bdc16bd82"
	},
	{
	  "id": "86956055-6058-426c-b730-7d2c7f963cdc",
	  "objects": [
	    {
	      "id": "5e9299cd-fb98-42a6-a31e-43a3945a8be2"
	    },
	    {
	      "id": "2174ebbe-2c00-40a7-b322-427cfac06d24"
	    }
	  ]
	}		
      ]
    },
    {
      "id": "cbec02ca-999a-4645-830e-8dee5dbb6054"
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
  "conclusion": "Заключение"
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


## 4. Задачи

### 4.1. Получение задачи `GET /tasks/:id`

**Request**
```http
GET /tasks/50fd1615-4bf3-4f37-8fb3-fa0abfd64fa5 HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK

{
  "name": "Название задачи",
  "dept": "Отдел/Цех",
  "planBegin": "2013-23-09 00:00",
  "planEnd": "2013-24-09 00:00",
  "finishDate": "2013-25-09 00:00",
  "docs": [
    "файл.doc",
    "Документ №1"
  ],
  "notes": "Примечание",
  "status": "Статус задачи",  
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
  },
  "isReadonly": true
}
```

### 4.2. Создание задачи `POST /tasks`

**Request**
```http
POST /tasks HTTP/1.1

{
  "name": "Название задачи",
  "dept": "Отдел/Цех",
  "planBegin": "2013-23-09 00:00",
  "planEnd": "2013-24-09 00:00",
  "docs": [
    "файл.doc",
    "Документ №1"
  ],
  "notes": "Примечание",
  "status": "Статус задачи",  
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
```
**Response**
```http
HTTP/1.1 201 Created

{
  "id": "9e015079-d11d-4bf2-bed7-53a562f86caa"
}
```

### 4.3. Редактирование задачи `PUT /tasks/:id`

**Request**
```http
PUT /tasks/d4ccab6c-b004-4506-9793-f22a7728a1d8 HTTP/1.1

{
  "name": "Название задачи",
  "dept": "Отдел/Цех",
  "planBegin": "2013-23-09 00:00",
  "planEnd": "2013-24-09 00:00",
  "finishDate": "2013-25-09 00:00"
  "docs": [
    "файл.doc",
    "Документ №1"
  ],
  "notes": "Примечание",
  "status": "Статус задачи",  
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
```
**Response**
```http
HTTP/1.1 200 OK
```

### 4.4. Удаление задачи `DELETE /tasks/:id`

**Request**
```http
DELETE /tasks/d4ccab6c-b004-4506-9793-f22a7728a1d8 HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK
```


## 5. История

### 5.1. Получение истории `GET /history/:id`

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
    "datetime": "2014-10-24 17:42",
    "changed": {
      "name": "Новое название"
    }
  },
  {
    "author": "Фамилия И.О.",
    "datetime": "2014-10-24 17:42",
    "changed": {
      "status": "Новый статус"
    }
  },
  {
    "author": "Фамилия И.О.",
    "datetime": "2014-10-24 17:42",
    "changed": {
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
    "datetime": "2014-10-24 17:42",
    "changed": {
      "objects": [
        {
          "id": "c6dda2d9-dc23-44fc-84b4-24b3c57470f1",
          "name": "Удаленный объект",
          "isDeleted": true
        }
      ]
    }
  },
  {
    "author": "Фамилия И.О.",
    "datetime": "2014-10-24 17:42",
    "changed": {
      "objects": [
        {
          "id": "c6dda2d9-dc23-44fc-84b4-24b3c57470f1",
          "name": "Объект с новым статусом",
          "status": "Новый статус"
        }
      ]
    }
  },
  {
    "author": "Фамилия И.О.",
    "datetime": "2014-10-24 17:42",
    "changed": {
      "experiments": [
        {
          "id":  "85b42f27-0ee4-4131-a9ec-cd0f4e73fd0b",
          "name": "Новый эксперимент"
        }
      ]
    }
  }
]
```


## 6. Поиск

### 6.1. Получение результатов `GET /search/:params`

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
      "name": "Название объекта1"
    },
    {
      "id": "73580df4-ef64-410b-a224-f4f18389aff7",
      "name": "Название объекта2"
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


## 7. Места проведения и отделы

### 7.1. Получение мест `GET /places/locations`

**Request**
```http
GET /places/locations HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK

{
  "locations": [
    {
      "name": "Название места1"
    },
    {
      "name": "Название места2"
    }
  ]
}
```

### 7.2. Получение отделов `GET /places/depts`

**Request**
```http
GET /places/depts HTTP/1.1
```
**Response**
```http
HTTP/1.1 200 OK

{
  "depts": [
    {
      "name": "Название отдела1"
    },
    {
      "name": "Название отдела2"
    }
  ]
}
```


## 8. Информация о пользователе

### 8.1. Получение информации `GET /userinfo`

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


## 9. Статусы

### 9.1. Статусы тем

```
{
  "statuses": [
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
}
```

### 9.2. Статусы объектов

```
{
  "statuses": [
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
}
```

### 9.3. Статусы испытаний

```
{
  "statuses": [
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
}
```

### 9.4. Статусы задач

```
{
  "statuses": [
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
}
```
