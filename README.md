# Отчёт кафе — проект с сайтом документации

Тот же код, что в стартовом архиве, с описаниями в формате Google. Каждый
случай из главы 4.4 здесь встречается в рабочем коде: функция без параметров,
значение по умолчанию, возврат None, исключение, изменение аргумента на месте,
генератор, пара значений, работа с файлом, служебное имя с подчёркиванием,
класс, dataclass, модуль и пакет.

## Запуск

    python3 -m venv .venv
    source .venv/bin/activate        # Windows: .venv\Scripts\activate
    pip install -r requirements.txt
    python main.py

## Проверки

    python -m pytest -v                       # 12 тестов
    python -m doctest app/utils/formatter.py  # примеры из докстринга
    mypy app                                  # типы расставлены, ошибок нет
    ruff check app                            # замечаний нет

## Формат описаний

Google: разделы Args, Returns, Raises, Yields, Attributes. Правила проверки
заданы в pyproject.toml: набор «D» и конвенция google, для папки тестов
правила отключены.

## Как посмотреть описания без редактора

    python -c "import app.services.orders as m; help(m)"

## Документация

Сайт собирается Sphinx из докстрингов пакета app, тема Furo.

    pip install -r docs/requirements.txt
    SPHINX_APIDOC_OPTIONS=members sphinx-apidoc -f -M -o docs/source/api app
    sphinx-build -M html docs/source docs/build -E -W --keep-going

Готовый сайт — docs/build/html/index.html. Публикация на GitHub Pages
описана в .github/workflows/docs.yml: сборка при каждой отправке в main.
Страницы в docs/source/api создаёт sphinx-apidoc, руками их не правят.
