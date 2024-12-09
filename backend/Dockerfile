# Dockerfile-backend

# Imagem base
FROM python:3.9

# Definir o diretório de trabalho no container
WORKDIR /app

# Copiar os arquivos de dependências e instalar
COPY requirements.txt /app/requirements.txt
RUN pip install --no-cache-dir --upgrade -r /app/requirements.txt

COPY . /app

# Copiar o script wait-for-it.sh
COPY wait-for-it.sh /app/wait-for-it.sh
RUN chmod +x /app/wait-for-it.sh

# Comando para executar a aplicação
CMD ["/app/wait-for-it.sh", "postgres:5432", "--", "uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]