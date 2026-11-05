FROM python:3.11-slim

WORKDIR /app

ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

COPY . .

RUN mkdir -p staticfiles

COPY static/ staticfiles/

EXPOSE 8000

CMD [ "gunicorn", "--bind", "0.0.0.0:8000", "SimplePageApp.wsgi:application" ]
