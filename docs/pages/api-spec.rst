Спецификация API
============================================================
Спецификация формата обмена данными между фронтендом и бэкендом.

Base API URL
-------------------------------------------

**dev**: <TBD>

**prod**: <TBD>


Запрос на регистрацию пользователя
-------------------------------------------

**Метод**

POST

**URL**

``BASE_URL/auth/users/``

**POST-параметры запроса**

+------------+------------+
| Параметр   | Тип данных |
+============+============+
| username   | Строка     |
+------------+------------+
| password   | Строка     |
+------------+------------+

**Ответ в случае успешной регистрации**

Status: 201 Created

.. code-block:: json

    {
        "email": "",
        "username": "username",
        "id": 4
    }

**Ответ в случае, если пользователь с таким username уже существует**

Status: 400 Bad Request

.. code-block:: json

    {
        "username": [
            "A user with that username already exists."
        ]
    }

**Ответ в случае отсутствия какого-либо параметра**

Status: 400 Bad Request

.. code-block:: json

    {
        "username": [
            "This field is required."
        ],
        "password": [
            "This field is required."
        ]
    }

Запрос на авторизацию пользователя и получение токена
------------------------------------------------------

**Метод**

POST

**URL**

``BASE_URL/auth/token/login/``

**POST-параметры запроса**

+------------+------------+
| Параметр   | Тип данных |
+============+============+
| username   | Строка     |
+------------+------------+
| password   | Строка     |
+------------+------------+

**Ответ при успешной авторизации**

Status: 200 OK

.. code-block:: json

    {
     "auth_token": "c89061a66e1241fda2fa870d22e5ecd7ebc29dfe"
    }

**Ответ при неверном пароле/отсутствии какого-либо параметра**

Status: 400 Bad Request

.. code-block:: json

    {
        "non_field_errors": [
            "Unable to log in with provided credentials."
        ]
    }

Запрос на изменение username/password пользователя
------------------------------------------------------

**Метод**

POST

**URL**

``BASE_URL/auth/users/set_username`` - изменение username

``BASE_URL/auth/users/set_password`` - изменение password

**Заголовки**

::

  Authorization: Token c89061a66e1241fda2fa870d22e5ecd7ebc29dfe

POST-параметры запроса: **изменение username**

+------------------+-----------------+------------+
| Параметр         | Значение        | Тип данных |
+==================+=================+============+
| new_username     | Новый логин     | Строка     |
+------------------+-----------------+------------+
| current_password | Текущий пароль  | Строка     |
+------------------+-----------------+------------+

POST-параметры запроса: **изменение password**

+------------------+-----------------+------------+
| Параметр         | Значение        | Тип данных |
+==================+=================+============+
| new_password     | Новый пароль    | Строка     |
+------------------+-----------------+------------+
| current_password | Текущий пароль  | Строка     |
+------------------+-----------------+------------+

**Ответ при успешном изменении**

Status: 204 No Content

**Ответ при упущении обязательного параметра**

Status: 400 Bad Request

.. code-block:: json

  {
      "new_username": [
          "This field is required."
      ]
  }

Запрос на получение информации о текущем пользователе
------------------------------------------------------

**Метод**

GET

**URL**

``BASE_URL/auth/users/me/``

**Заголовки**

::

  Authorization: Token c89061a66e1241fda2fa870d22e5ecd7ebc29dfe

**Ответ при успешном запросе**

Status: 200 OK

.. code-block:: json

  {
      "email": "",
      "id": 4,
      "username": "new_user_name"
  }

**Ответ при невалидном/непереданном токене**

Status: 401 Unauthorized

.. code-block:: json

  {
      "detail": "Authentication credentials were not provided."
  }

Запрос списка рекомендуемых маршрутов для пользователя
------------------------------------------------------

**Метод**

GET

**URL**

``BASE_URL/<TBD>``

**Заголовки**

::

  Authorization: Token c89061a66e1241fda2fa870d22e5ecd7ebc29dfe
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
            "duration": "hh:mm",
            "photoLink": "link",
            "tags": [
              "tag1",
              "tag2",
            ]
          }
        ]
      }
    }

Запрос списка сохраненных маршрутов для пользователя
------------------------------------------------------

**Метод**

GET

**URL**

``BASE_URL/<TBD>``

**Заголовки**

::

  Authorization: Token c89061a66e1241fda2fa870d22e5ecd7ebc29dfe
  accept-language: ru

**Ответ**

Status: 200 OK

.. code-block:: json

    {
      "data": {
        "savedRoutes": [
          {
            "id": "5db32b6977c44a187bef2c8f",
            "name": "Маршрут для отчета",
            "duration": "hh:mm",
            "photoLink": "link",
            "tags": [
              "tag1",
              "tag2",
            ]
          }
        ]
      }
    }

Запрос маршрутов по ключевому слову и времени
------------------------------------------------------

**Метод**

GET

**URL**

``BASE_URL/<TBD>``

**Заголовки**

::

  Authorization: Token c89061a66e1241fda2fa870d22e5ecd7ebc29dfe
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
            "duration": "hh:mm",
            "photoLink": "link",
            "tags": [
              "tag1",
              "tag2",
            ]
          }
        ]
      }
    }

Запрос популярных тегов
------------------------------------------------------

**Метод**

GET

**URL**

``BASE_URL/<TBD>``

**Заголовки**

::

  Authorization: Token c89061a66e1241fda2fa870d22e5ecd7ebc29dfe
  accept-language: ru

**Ответ**

Status: 200 OK

.. code-block:: json

    {
      "data": {
        "tags": [
          {
            "id": "5db32b6977c44a187bef2c8f",
            "name": "Tag1",
            "icon": "icon_url"
          }
        ]
      }
    }

Запрос ближайших партнерских локаций
------------------------------------------------------

**Метод**

GET

**URL**

``BASE_URL/<TBD>``

**Заголовки**

::

  Authorization: Token c89061a66e1241fda2fa870d22e5ecd7ebc29dfe
  accept-language: ru

**Параметры запроса**

?latitude=59.03456&longitude=30.123456

**Ответ**

Status: 200 OK

.. code-block:: json

    {
      "data": {
        "locations": [
          {
            "id": "5db32b6977c44a187bef2c8f",
            "name": "Библиотека Пушкина",
            "description": "Эта локация очень хороша",
            "latitude": 59.03456,
            "longitude": 30.123456
          }
        ]
      }
    }

Запрос маршрута по id
------------------------------------------------------

**Метод**

GET

**URL**

``BASE_URL/<TBD>``

**Заголовки**

::

  Authorization: Token c89061a66e1241fda2fa870d22e5ecd7ebc29dfe
  accept-language: ru

**Ответ**

Status: 200 OK

.. code-block:: json

    {
      "data": {
        "id": "5db32b6977c44a187bef2c8f",
        "name": "Маршрут для отчета",
        "description": "Этот маршрут...",
        "duration": "hh:mm",
        "photoLink": "link",
        "tags": [
          "tag1",
          "tag2",
        ],
        "locationInstances": [
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
    }

Запрос на сохранение маршрута для пользователя
------------------------------------------------------

**Метод**

POST

**URL**

``BASE_URL/<TBD>``

**Заголовки**

::

    Authorization: Token c89061a66e1241fda2fa870d22e5ecd7ebc29dfe

**Тело запроса**

.. code-block:: json

   {
      "routeId": "5db32b6977c44a187bef2c8f"
   }

**Ответ**

Status: 200 OK
