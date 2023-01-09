FROM python:3.10.8-slim

WORKDIR /app

COPY api_yamdb/ .

COPY requirements.txt .

RUN pip3 install -r requirements.txt --no-cache-dir

CMD ["gunicorn", "api_yamdb.wsgi:application", "--bind", "0:8000" ]