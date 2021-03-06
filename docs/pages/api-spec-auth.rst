API - авторизация и пользовательские методы
============================================================
Описание схемы авторизации клиентских приложений сервером и методов, связанных с пользователем.

Base API URL
-------------------------------------------

http://learnsql.ru:8000

Сервер использует Token-авторизацию. Полученный после предоставления пользовательских данных токен необходимо в дальнейшем передавать в заголовке запроса.
``Authorization: Token XXXXX``

POST-данные отправляются в формате JSON с заголовком `Content-Type: application/json`

Для установки языка возвращаемого контента нужно передать заголовок `Language`. Доступны значения: ru, en


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
| username   | string     |
+------------+------------+
| password   | string     |
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
| username   | string     |
+------------+------------+
| password   | string     |
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
| new_username     | Новый логин     | string     |
+------------------+-----------------+------------+
| current_password | Текущий пароль  | string     |
+------------------+-----------------+------------+

POST-параметры запроса: **изменение password**

+------------------+-----------------+------------+
| Параметр         | Значение        | Тип данных |
+==================+=================+============+
| new_password     | Новый пароль    | string     |
+------------------+-----------------+------------+
| current_password | Текущий пароль  | string     |
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
