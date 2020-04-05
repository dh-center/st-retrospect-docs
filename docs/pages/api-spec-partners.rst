API - партнёры
============================================================
Методы для работы с партнерскими маршрутами и локациями (:term:`Location`). **Для использования всех нижеперечисленных методов требуется авторизация.**

Base URL: ``http://learnsql.ru:8000``


Получение информации о партнере по его id
----------------------------------------------------

**Метод**

GET

**URL**

``BASE_URL/api/partner/getById``

**GET-параметры запроса**

+------------+-------------+------------+--------------+
| Параметр   | Назначение  | Тип данных | Обязательный |
+============+=============+============+==============+
| id         | ID партнера | int        | да           |
+------------+-------------+------------+--------------+

**Ответ**

Status: 200 OK

.. code-block:: json

    {
      "partner": {
          "id": 1,
          "description": "Описание",
          "routes": [
              {
                  "id": 7,
                  "name": "От ИТМО на Ломоносова до Достоевской",
                  "description": "Описание",
                  "image_url": "",
                  "author": null,
                  "route_type_id": 1,
                  "duration": 10
              }
          ],
          "locations": [
              {
                  "id": 2411,
                  "lat": 59.927659,
                  "lon": 30.3429,
                  "wiki_url": "http://www.citywalls.ru/house745.html",
                  "icon_url": "",
                  "address": "Улица Рубинштейна, 23",
                  "value": 0.0,
                  "instances": [
                      {
                          "id": 1366,
                          "name": "Жилой комплекс Петербургской купеческой управы",
                          "description": "Описание",
                          "image_url": "https://images.st-retrospect.dh-center.ru/eyJidWNrZXQiOiJzdC1yZXRyb3NwZWN0LWltYWdlcyIsImtleSI6ImxvY2F0aW9ucy9sb2NhdGlvbi00NzMtbWFpbjE1ODIxMDU5MTc2MzYuanBlZyJ9",
                          "start_date": "1911",
                          "end_date": "",
                          "was_built": null,
                          "was_demolished": false,
                          "location_id": 2411,
                          "persons": [
                              {
                                  "id": 675,
                                  "first_name": "Сергей",
                                  "last_name": "Довлатов",
                                  "patronymic": "Донатович",
                                  "description": "Описание",
                                  "birth_date": "03.09.1941",
                                  "death_date": "24.08.1990",
                                  "image_url": "https://upload.wikimedia.org/wikipedia/ru/thumb/c/c9/%D0%A1%D0%B5%D1%80%D0%B3%D0%B5%D0%B9_%D0%94%D0%BE%D0%B2%D0%BB%D0%B0%D1%82%D0%BE%D0%B2.jpg/345px-%D0%A1%D0%B5%D1%80%D0%B3%D0%B5%D0%B9_%D0%94%D0%BE%D0%B2%D0%BB%D0%B0%D1%82%D0%BE%D0%B2.jpg",
                                  "tags": [
                                      {
                                          "id": 22506,
                                          "name": "Название тега"
                                      }
                                  ],
                                  "relation": {
                                      "quote": "Описание связи",
                                      "relation_type_id": 2
                                  }
                              }
                          ],
                          "tags": [
                              {
                                  "id": 22506,
                                  "name": "Название тега"
                              }
                          ],
                          "location_types": [
                              {
                                  "id": 2,
                                  "name": "жилой дом"
                              }
                          ],
                          "action_tags": []
                      }
                  ],
                  "description": ""
              }
          ]
      }
    }

Метод возвращает подробную информацию о партнере, включая его маршруты (:term:`Route`) и локации. О локациях возвращается информация о всех инстансах (:term:`LocationInstance`) каждой локации (:term:`Location`), связанных персонах (:term:`Person`) и тегах (:term:`Tag`).


Получение партнерских локаций вблизи от пользователя
----------------------------------------------------

**Метод**

GET

**URL**

``BASE_URL/api/partner/getLocations``

**GET-параметры запроса**

+------------+------------------------+------------+--------------+
| Параметр   | Назначение             | Тип данных | Обязательный |
+============+========================+============+==============+
| lat        | latitude пользователя  | float      | да           |
+------------+------------------------+------------+--------------+
| lon        | longitude пользователя | float      | да           |
+------------+------------------------+------------+--------------+
| radius     | Радиус поиска в метрах | int        | нет          |
+------------+------------------------+------------+--------------+

Значение *radius* по умолчанию = 1500

**Ответ**

Status: 200 OK

.. code-block:: json

    {
      "locations": [
          {
              "id": 2411,
              "lat": 59.927659,
              "lon": 30.3429,
              "wiki_url": "http://www.citywalls.ru/house745.html",
              "icon_url": "",
              "address": "Улица Рубинштейна, 23",
              "value": 0.0,
              "instances": [
                  {
                      "id": 1366,
                      "name": "Жилой комплекс Петербургской купеческой управы",
                      "description": "Описание",
                      "image_url": "https://images.st-retrospect.dh-center.ru/eyJidWNrZXQiOiJzdC1yZXRyb3NwZWN0LWltYWdlcyIsImtleSI6ImxvY2F0aW9ucy9sb2NhdGlvbi00NzMtbWFpbjE1ODIxMDU5MTc2MzYuanBlZyJ9",
                      "start_date": "1911",
                      "end_date": "",
                      "was_built": null,
                      "was_demolished": false,
                      "location_id": 2411,
                      "persons": [
                          {
                              "id": 675,
                              "first_name": "Сергей",
                              "last_name": "Довлатов",
                              "patronymic": "Донатович",
                              "description": "Описание",
                              "birth_date": "03.09.1941",
                              "death_date": "24.08.1990",
                              "image_url": "https://upload.wikimedia.org/wikipedia/ru/thumb/c/c9/%D0%A1%D0%B5%D1%80%D0%B3%D0%B5%D0%B9_%D0%94%D0%BE%D0%B2%D0%BB%D0%B0%D1%82%D0%BE%D0%B2.jpg/345px-%D0%A1%D0%B5%D1%80%D0%B3%D0%B5%D0%B9_%D0%94%D0%BE%D0%B2%D0%BB%D0%B0%D1%82%D0%BE%D0%B2.jpg",
                              "tags": [
                                  {
                                      "id": 22506,
                                      "name": "Название тега"
                                  }
                              ],
                              "relation": {
                                  "quote": "Описание связи",
                                  "relation_type_id": 2
                              }
                          }
                      ],
                      "tags": [
                          {
                              "id": 22506,
                              "name": "Название тега"
                          }
                      ],
                      "location_types": [
                          {
                              "id": 2,
                              "name": "жилой дом"
                          }
                      ],
                      "action_tags": []
                  }
              ],
              "description": ""
          }
      ]
    }

В ответе содержится список партнерских локаций со всеми инстансами, удовлетворяющих условию радиуса поиска. В случае ненахождения локаций вблизи переданной координаты возвращается пустой список.
