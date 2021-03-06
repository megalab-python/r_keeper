- [О проекте](#о-проекте)
  - [Требования](#требования)
  - [Этапы](#этапы)
  - [Настройка проекта](#настройка-проекта)
    - [pipenv](#pipenv)
    - [black, flake8, mypy, isort](#black-flake8-mypy-isort)
      - [black](#black)
      - [isort](#isort)
      - [flake8](#flake8)
      - [mypy](#mypy)
    - [pre-commit](#pre-commit)

## О проекте

В большинстве общепит заведений на сегодняшний день используется приложение r-keeper.

Оно помогает управлять различными процессами от заказа клиентом до ведения учета.

В данном задании вы должны будете реализовать API, который иммитирует работу данного приложения.

### Требования

Вам нужно реализовать следующий функционал:

Как официант, я могу оформить заказ для клиента, который может выбрать любое блюдо в любом желаемом количестве.

Как персонал, я могу поменять статус заказанного блюда клиента на один из следующих:

- Поступил заказ
- Готовится
- Приготовлено
- Заказ отдан

### Этапы

Данный проект будет разрабатываться поэтапно. Далее представлены основные этапы:

1. Составление ER диаграммы
2. Создание моделей по сущностям в ERD
3. Интеграция DRF
   1. Написание классов для сериализации данных (serializers) моделей
   2. Написание контроллеров для обработки HTTP запросов
4. Тестирование функционала
5. Документирвоание приложения
6. Контейнеризация приложения
7. Развертывание на herokuapp.com


### Настройка проекта

#### pipenv

В проетке используется пакетный менеджер [pipenv](https://pipenv.pypa.io/en/latest/)

Ознакомьтесь с тем как его использовать в документации.

Для начала нужно будет установить зависимости:

`pipenv install --pre --dev`

Далее, чтобы использовать CLI установленных библиотек, надо будет запускать их через pipenv. Например:

`pipenv run django-admin startproject r_keeper .`

#### black, flake8, mypy, isort

Перечисленные инструменты используются для форматирования и поддержания стилистики кода. Так как Ваш код будет читаться кем-то помимо Вас, важно соблюдать правила конвенции. 

> HINT: Чтобы вручную не менять код, можно использовать эти инструменты, которые будут менять код за Вас. Также можно настроить Ваш IDE таким образом, чтобы при нажатии определенных комбинаций на клавиатуре, Ваш IDE запускал их.

Пример запуска команд через консоль:

##### [black](https://black.readthedocs.io/en/stable/)
`pipenv run black --line-length=79 .`

##### [isort](https://pycqa.github.io/isort/)
`pipenv run isort --profile=black`

##### [flake8](https://flake8.pycqa.org/en/latest/)
`pipenv run flake8 .`

##### [mypy](https://mypy.readthedocs.io/en/stable/)
`pipenv run mypy`


#### pre-commit

Самостоятельно тяжело проверить действительно ли Ваш код соответствует стилистике, поэтому разработчики создали такой инструмент как pre-commit. Он построен на событиях, которые называются git hooks. Прежде, чем Ваш код будет залит в репозиторий, данная утилита может запускать ряд проверок.

Таким образом, можно объединить предыдущие инструменты с этим. Для этого в репозитории имеется .pre-commit-config.yaml.

Прежде, чем начать разработку, Вам нужно будет установить [pre-commit](https://pre-commit.com/)

И затем выполнить комманду:

`pre-commit install`