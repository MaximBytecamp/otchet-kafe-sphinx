Запуск и проверки
=================

Программа читает файл смены ``data/smena.csv`` и печатает выручку
по каждому официанту. Суммы в файле записаны в копейках.

Установка
---------

1. Создайте окружение и установите зависимости.
2. Запустите программу из корня проекта.

.. code-block:: console

   python -m venv .venv
   pip install -r requirements.txt
   python main.py

Проверки
--------

* ``python -m pytest -v`` — двенадцать тестов;
* ``mypy app`` — проверка типов;
* ``ruff check app`` — проверка докстрингов.

.. note::

   Расчёт выручки описан в функции :func:`app.services.orders.revenue_by_waiter`,
   формат суммы — в :func:`app.utils.formatter.format_kopeks`.

Формат файла смены описан на странице `документации модуля csv
<https://docs.python.org/3/library/csv.html>`_.
