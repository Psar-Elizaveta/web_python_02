## Docker-команда FROM вказує базовий образ контейнера
## Наш базовий образ - це Linux з попередньо встановленим python-3.10
FROM python:3.10

# Встановимо змінну середовища
ENV APP_HOME /app

# Встановимо робочу директорію всередині контейнера
WORKDIR $APP_HOME

# Скопіюємо інші файли в робочу директорію контейнера

# Встановимо залежності всередині контейнера
COPY pyproject.toml $APP_HOME/pyproject.toml
COPY pyproject.poetry.lock $APP_HOME/poetry.lock

RUN pip install poetry
RUN poetry config virtualenvs.create false && poetry install --only main

# Позначимо порт, де працює застосунок всередині контейнера
EXPOSE 5000

# Запустимо наш застосунок всередині контейнера
ENTRYPOINT ["python", "app.py"]

# Використовуємо офіційний образ Python



#FROM python:3.8
#
## Встановлюємо Poetry
#RUN curl -sSL https://install.python-poetry.org | python -
#
## Копіюємо файли проекту в контейнер
#COPY . /app
#WORKDIR /app
#
## Встановлюємо залежності з використанням Poetry
#RUN poetry install
#
## Запускаємо наш додаток
#CMD ["python", "app.py"]
