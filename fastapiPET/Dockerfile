# Use a imagem oficial do Python 3.10
FROM python:3.10.12-slim

# Define variáveis de ambiente
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# Atualize o sistema e instale dependências
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        gcc \
        python3-dev \
        musl-dev \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Instale o Poetry
RUN pip install --upgrade pip \
    && pip install poetry

# Configure o diretório de trabalho
WORKDIR /app

# Copie o arquivo de dependências do projeto e instale as dependências
COPY pyproject.toml poetry.lock /app/
RUN poetry config virtualenvs.create false \
    && poetry install --no-interaction --no-ansi

# Copie o código fonte para o contêiner
COPY . /app

# Execute o servidor FastAPI
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
