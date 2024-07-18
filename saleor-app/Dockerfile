FROM python:3.9-slim

# Ustawienie zmiennych środowiskowych
ENV PYTHONUNBUFFERED 1

# Tworzenie katalogu dla aplikacji
WORKDIR /app

# Instalacja zależności systemowych
RUN apt-get update && \
    apt-get install -y \
    build-essential \
    libpq-dev \
    libjpeg-dev \
    zlib1g-dev \
    gettext

# Instalacja zależności Python
COPY requirements.txt /app/
RUN pip install --upgrade pip && pip install -r requirements.txt

# Kopiowanie kodu aplikacji
COPY . /app/

# Komenda startowa dla aplikacji
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "saleor.wsgi:application"]