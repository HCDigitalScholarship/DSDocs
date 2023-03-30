# Digital Scholarship Project Basics

## Background

Digital scholarship projects are often worked by many people at once, and are passed down through many generations of students. In order to keep projects maintable, in 2023 the DS team undertook the project of moving all existing projects into Docker containers. Moving forward, all new projects should be created with Docker in the first place to help with long-term sustainability. 

This documenation includes a high-level overview of how DS projects should be configured, as well as a basic example project to get you started.

## The Building Blocks

There are a few main components that will be a part of every DS project. You should become familiar with these tools:

### 1. Docker
Docker is a containerization platform that allows developers to package an application and all of its dependencies into a single, portable unit called a container. Containers are lightweight, isolated environments that can run anywhere, making them ideal for building and deploying applications across multiple environments. Docker is widely used in the software development industry to streamline the development, testing, and deployment process. With Docker, developers can build, ship, and run applications quickly and easily, without worrying about compatibility issues or conflicts with other software.

To use Docker, you'll need to install Docker on your computer or server. Once you've installed Docker, you can use the Docker command-line interface (CLI) to create and manage containers. The basic steps to using Docker are as follows:

- Write a Dockerfile: A Dockerfile is a text file that contains instructions for building a Docker image. The Docker image is a snapshot of an application and its dependencies at a particular point in time.
- Build the Docker image: Use the Docker CLI to build the Docker image using the instructions in the Dockerfile.
- Run the Docker container: Use the Docker CLI to start the Docker container, which will run the application in an isolated environment.

### 2. Docker Compose
Docker Compose is a tool that allows developers to define and run multi-container Docker applications. With Docker Compose, you can define the configuration of your application in a YAML file, and Docker Compose will automatically create and start the necessary containers. Docker Compose is useful when you need to run multiple containers together, such as a web server and a database.

To use Docker Compose, you'll need to create a docker-compose.yml file that defines the services that make up your application. You can then use the Docker Compose CLI to start and stop your application. The basic steps to using Docker Compose are as follows:

- Define your services: Create a docker-compose.yml file that defines the services that make up your application, including the images to use, the ports to expose, and the environment variables to set.
- Start your application: Use the Docker Compose CLI to start your application, which will create and start the necessary containers.
- Stop your application: Use the Docker Compose CLI to stop your application, which will stop and remove the containers.


### 3. Dokku
Dokku is a lightweight and easy-to-use platform-as-a-service (PaaS) that allows developers to deploy and manage applications using Docker containers. With Dokku, you can deploy applications to your own server, without having to rely on third-party PaaS providers. Dokku provides a simple and intuitive command-line interface for managing applications, and integrates with popular tools like Git.
To use Dokku, you'll need to install Dokku on your server. Once you've installed Dokku, you can use the Dokku CLI to create and manage applications. The basic steps to using Dokku are as follows:

Create a new application: Use the Dokku CLI to create a new application, which will create a Docker container for your application.

- Configure your application: Use the Dokku CLI to set configuration variables for your application, such as environment variables and network settings.
- Deploy your application: Use Git to push your application code to your Dokku server, which will build and deploy the application to a Docker container (you'll need to ask your server admin for this information).
- Manage your application: Use the Dokku CLI to manage your application, including scaling the number of containers, viewing logs, and restarting the application.

**Deploying with Dokku**

How to configure your Dokku remote repository for deployment to dev and production. 

1. First, make sure that you have Dokku installed on your server and that you have created a new application using the Dokku CLI.

2. Next, navigate to the root directory of your local Git repository in your terminal or command prompt.

3. To add a Dokku Git remote, use the following command, replacing "example.com" with the IP address or domain name of your Dokku server, and "myapp" with the name of your Dokku application:

```
git remote add dokku dokku@example.com:myapp
```

4. Verify that the Dokku Git remote has been added by running the following command:

```
git remote -v
```

You should see a list of your Git remotes, including "dokku".

Once you have added the Dokku Git remote, you can deploy your application to Dokku using the following command:

`git push dokku main` or `git push dokku master`

This will push the latest changes to the "main" branch of your Git repository to your Dokku server, which will build and deploy the application to a Docker container.

