# Use an official Python runtime as a parent image
FROM python:3.8-slim-buster as builder

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

# Use an official Python runtime as a parent image
FROM python:3.8-slim-buster

# Set the working directory in the container
WORKDIR /app/ai_coder_be

# Copy the Django project from the builder image
COPY --from=builder /app/ai_coder_be /app/ai_coder_be

# Make port 8000 available to the world outside this container
EXPOSE 8000

# Run Django
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
