# Creating a New Project

1. Create a new directory for your project, and navigate to it in your terminal.

```
$ mkdir myproject
$ cd myproject
```

2. Create a Dockerfile in the project directory. This file specifies the image that will be used for the container and any additional dependencies that need to be installed.

```
# Dockerfile

# Use an official Python runtime as a parent image
FROM python:3.9-slim-buster

# Set the working directory to /app
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app
COPY requirements.txt /app/requirements.txt

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

EXPOSE 5000

# Define the command that will run when the container starts
CMD flask --app app run --host=0.0.0.0
```

3. Create a docker-compose.yml file in the project directory. This file defines the services that will be run by Docker Compose, and any dependencies between them.

```
# docker-compose.yml

version: '3'
services:
  web:
    build: .
    ports:
      - "8000:8000"
```

4. Create a requirements.txt file in the project directory. This file lists the Python packages that your project depends on.

```
# requirements.txt

flask
```

5. Create your Python code. For example, you can create a simple Flask application in app.py:

```
# app.py

from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello, World!'
```

6. Build and run the containers with Docker Compose.

```
$ docker-compose up --build
```

This command will build the image for your Python app, create a container from that image, and start the container. The --build flag tells Docker Compose to rebuild the image if any of the files it depends on have changed.

7. Test your app by visiting http://localhost:5000/ in your web browser. You should see the message "Hello, World!".

That's it! You've successfully set up a Python project in Docker with Docker Compose.
