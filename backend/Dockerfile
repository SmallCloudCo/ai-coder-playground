# Use an official Python runtime as a parent image
FROM python:3.8-slim-buster

# Install system dependencies
RUN apt-get update && apt-get install -y \
    gcc \
    postgresql \
    libpq-dev \
    --no-install-recommends && rm -rf /var/lib/apt/lists/*

# Set environment variables for Django
ENV DJANGO_SETTINGS_MODULE ai-coder-be.settings

# Set the working directory in the container
WORKDIR /app

# Add requirements.txt to the container
COPY requirements.txt .

# Install Django and other Python dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Create new Django project if manage.py is not present
RUN if [ ! -f manage.py ]; then \
        django-admin startproject ai-coder-be . ; \
    fi

# Copy the current directory contents into the container
COPY . /app

# Make port 8000 available to the world outside this container
EXPOSE 8000

# Run Django
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
