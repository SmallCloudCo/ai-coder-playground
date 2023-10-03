# Use an official Python runtime as a parent image
FROM python:3.8-slim-buster

# Set the working directory in the Docker image
WORKDIR /ai_coder_be

# Install Django
RUN pip install Django

# Create a new Django project named ai_coder_be
RUN django-admin startproject ai_coder_be .

# Copy the requirements.txt file from your project directory (on your machine) to the Docker image
COPY requirements.txt .

# Run pip install to install the dependencies listed in requirements.txt
RUN pip install -r requirements.txt

# Copy the rest of your project directory (on your machine) into the Docker image
COPY . .

# Set the default command for the Docker image to python manage.py runserver
CMD ["python", "manage.py", "runserver"]
