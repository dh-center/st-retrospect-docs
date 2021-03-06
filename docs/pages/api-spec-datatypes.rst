API - типы данных в БД
============================================================
Вспомогательные методы для получения всех значений перечислений, используемых в качестве сущностей базы данных.

Base URL: ``http://learnsql.ru:8000``


Получение списка типов маршрутов
-------------------------------------------

**Метод**

GET

**URL**

``BASE_URL/api/db/getRouteTypes``

**Ответ**

Status: 200 OK

.. code-block:: json

    {
      [
        {
            "id": 1,
            "name": "TestRouteType",
            "is_strict": false
        }
      ]
    }


Получение списка типов локаций
-------------------------------------------

**Метод**

GET

**URL**

``BASE_URL/api/db/getLocationTypes``

**Ответ**

Status: 200 OK

.. code-block:: json

    {
      [
        {
            "id": 1,
            "name": "доходный дом"
        },
        {
            "id": 2,
            "name": "жилой дом"
        },
        {
            "id": 3,
            "name": "учебное заведение"
        }
      ]
    }


Получение списка типов связей
-------------------------------------------

**Метод**

GET

**URL**

``BASE_URL/api/db/getRelationTypes``

**Ответ**

Status: 200 OK

.. code-block:: json

    {
      [
        {
            "id": 1,
            "name": "бывал"
        },
        {
            "id": 2,
            "name": "жил"
        }
      ]
    }

Возвращает список всех возможных связей (:term:`Relation`) между персоной (:term:`Person`) и инстансом локации (:term:`LocationInstance`).
