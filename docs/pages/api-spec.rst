################
Спецификация API
################

Спецификация формата обмена данными между фронтендом и бэкендом.

Запрос на регистрацию в приложении
==================================================================

**Метод**:

POST

**URL**

<TBD>

**Тело запроса**:

.. code-block:: json

   {
      "username": "username",
      "password": "password"
   }

**Ответ**

Status: 201 Created

Запрос на получение авторизационного токена для входа в приложение
==================================================================

**Метод**:

GET

**URL**

<TBD>

**Параметры запроса**:

?username=username&password=password

**Ответ**

Status: 200 OK

.. code-block:: json

   {
      "data": {
         "accessToken": "eyJhbGciOiJIUzI1NiIsInr6cCI6IkpXVCJ9"
      }
   }

Запрос списка рекомендуемых маршрутов для пользователя
==================================================================

**Метод**:

GET

**URL**

<TBD>

**Заголовки**

Authorization: Bearer eyJhbGciOiJIUzI1NiIsInr6cCI6IkpXVCJ9

accept-language: ru

**Ответ**

Status: 200 OK

.. code-block:: json

    {
      "data": {
        "routes": [
          {
            "id": "5db32b6977c44a187bef2c8f",
            "name": "Маршрут для отчета",
            "description": "Этот маршрут...",
            "duration": "hh:mm",
            "photoLink": "link",
            "tags": [
              "tag1",
              "tag2",
            ],
            "locationsInstance": [
              {
                "id": "5e6410a6acb47b0039f197a9",
                "name": "ИТМО ",
                "description": "ИТМО ",
                "photoLinks": [
                  "link"
                ]
              }
            ]
          }
        ]
      }
    }

Запрос маршрутов по ключевому слову и времени
==================================================================

**Метод**:

GET

**URL**

<TBD>

**Заголовки**

Authorization: Bearer eyJhbGciOiJIUzI1NiIsInr6cCI6IkpXVCJ9

accept-language: ru

**Параметры запроса**

?query=query&duration=hh:mm

**Ответ**

Status: 200 OK

.. code-block:: json

    {
      "data": {
        "routes": [
          {
            "id": "5db32b6977c44a187bef2c8f",
            "name": "Маршрут для отчета",
            "description": "Этот маршрут...",
            "duration": "hh:mm",
            "photoLink": "link",
            "tags": [
              "tag1",
              "tag2",
            ],
            "locationsInstance": [
              {
                "id": "5e6410a6acb47b0039f197a9",
                "name": "ИТМО ",
                "description": "ИТМО ",
                "photoLinks": [
                  "link"
                ]
              }
            ]
          }
        ]
      }
    }
