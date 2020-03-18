# st-retrospect-docs
[![Documentation Status](https://readthedocs.org/projects/st-retrospect-docs/badge/?version=latest)](https://st-retrospect-docs.readthedocs.io/en/latest/?badge=latest)

Документация проекта st-retrospect.

Инструменты
-----------
- Python 3.7 и [Sphinx 2.4.4](https://www.sphinx-doc.org/en/master/) для сборки.
- [Readthedocs](https://docs.readthedocs.io/) в качестве хостинга.
- [ReStructuredText](https://docs22.readthedocs.io/en/latest/rst-markup.html) для написания документации 

Структура документации
----------------------

- Стартовая страница располагается по пути `docs/index.rst`
- Отдельные статьи находятся в папке `docs/pages`
- Конфигурация документации `docs/conf.py`

Локальная сборка документации
-----------------------------

В папке docs запустить команду

`make html`

Требуется библиотека *Sphinx*.

По пути docs/_build/html/index.html располагается начальная страница сгенерированной документации.

Как внести вклад
----------------

Вся документация хранится в файлах с расширением .rst и использует синтаксис ReStructuredText. Для внесения изменений
достаточно редактировать текст внутри файлов.

При создании новой статьи, файл необходимо поместить в папку `docs/pages`, и указать на него ссылку в `docs/index.rst`.

Пример:
1. Создаём файл `docs/pages/example.rst`
2. Наполняем файл содержанием. В начале статьи необходимо указать название, а следующей строкой выделить его знаками *=*
   
   Пример: 
   ```
    Название статьи
    ===============
    ```
3. Указываем путь к файлу в секции toctree файла `docs/index.rst`

    Пример:
    ```
    Добро пожаловать в документацию st-retrospect-docs!
    ===================================================
    
    .. toctree::
       :maxdepth: 2
       :caption: Содержание:
    
       pages/glossary
       pages/schema
       ...
       pages/example
    ```