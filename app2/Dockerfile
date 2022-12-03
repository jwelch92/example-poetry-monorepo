FROM python:3.8

RUN apt-get update && \
    apt-get install --no-install-recommends -y make python3-dev &&  \
    apt-get clean

# Install Poetry
RUN curl -sSL https://install.python-poetry.org | POETRY_VERSION=1.2.0 POETRY_HOME=/opt/poetry python - && \
    cd /usr/local/bin && \
    ln -s /opt/poetry/bin/poetry && \
    poetry config virtualenvs.create false

WORKDIR /app/
ENV PYTHONPATH=/app

COPY ./pyproject.toml ./poetry.lock* /app/
RUN poetry install --no-root --no-dev --no-ansi

COPY ./app2 ./app

CMD ["python3", "/app/main.py"]
