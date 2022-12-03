FROM python:3.8

RUN apt-get update && \
    apt-get install --no-install-recommends -y make python3-dev tree &&  \
    apt-get clean

# Install Poetry
RUN curl -sSL https://install.python-poetry.org | POETRY_VERSION=1.2.0 POETRY_HOME=/opt/poetry python - && \
    cd /usr/local/bin && \
    ln -s /opt/poetry/bin/poetry && \
    poetry config virtualenvs.create false

WORKDIR /app/
ENV PYTHONPATH=/app

COPY ./lib /app/lib
COPY ./app1/pyproject.toml ./app1/poetry.lock* /app/app1/
WORKDIR /app/app1
RUN poetry install --no-root --only main --no-ansi

COPY ./app1 /app/app1
RUN tree /app
CMD ["python3", "/app/app1/app1/main.py"]
