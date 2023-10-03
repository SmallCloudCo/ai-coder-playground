# Use an official Python runtime as a parent image
FROM python:3.8-slim-buster

# Install system dependencies
RUN apt-get update && apt-get install -y \
    gcc \
    postgresql \
    libpq-dev \
    --no-install-recommends && rm -rf /var/lib/apt/lists/*

# Set the working directory in the container
WORKDIR /app

# Add requirements.txt to the container
COPY requirements.txt .

# Install Django and other Python dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Create new Django project if it does not exist
RUN if [ ! -d ai_coder_be ]; then \
        django-admin startproject ai_coder_be . ; \
    fi

# Make port 8000 available to the world outside this container
EXPOSE 8000

# Run Django
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
