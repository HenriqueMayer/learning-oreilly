#### Docker Compose

- **Docker Compose** is a tool for defining and running multi-container Docker applications. It uses a YAML file to configure the application’s services, networks, and volumes.
    - **What is a YAML file?**
        - YAML (YAML Ain't Markup Language) is a human-readable data serialization standard that can be used in conjunction with all programming languages and is often used to write configuration files.
        - It uses indentation to represent the structure of the data, making it easy to read and write.
- **What is the difference between Dockerfile and Docker Compose?**
    - A **Dockerfile** is used to build a single Docker image by specifying the steps needed to create that image.
    - **Docker Compose**, on the other hand, is used to define and manage multi-container applications. It allows you to define multiple services (containers), their configurations, networks, and volumes in a single `docker-compose.yml` file.

- E.g., A simple `docker-compose.yml` file to run a web application with a database might look like this:
    ```yaml
    services:
        web:
            image: my-web-app:latest
        database:
            image: postgres:latest
            environment:
                POSTGRES_USER: user
                POSTGRES_PASSWORD: password
        messaging:
            image: rabbitmq:latest
        orchestration:
            image: my-orchestration-service:latest
    ```
    - `docker-compose up -d`: This command starts the services defined in the `docker-compose.yml` file in detached mode.
    - `docker-compose down`: This command stops and removes the containers, networks, and volumes created by `docker-compose up`.

- **Connect containers**:
    - `docker run --link <container_name>:<alias> <image_name>`: This command links a new container to an existing container, allowing them to communicate with each other using the specified alias.
    - E.g., `docker run --link my-postgres-db:db my-web-app`: This command links the `my-web-app` container to the `my-postgres-db` container, allowing the web application to access the database using the alias `db`.

- **Real World Use Cases**:
    - **Microservices architecture**: Each microservice can run in its own container, and Docker Compose can manage the entire application stack.
    - **Development environments**: Developers can use Docker Compose to set up and tear down complex development environments with multiple services quickly.
    - **Testing**: Automated tests can be run in isolated environments using Docker Compose, ensuring consistency across different test runs.
    - **Continuous Integration/Continuous Deployment (CI/CD)**: Docker Compose can be integrated into CI/CD pipelines to build, test, and deploy multi-container applications.
    ```yaml
    services:
      web:
        image: my-web-app:latest
        ports:
          - "80:80"
        depends_on:
          - database
          - messaging
      database:
        image: postgres:latest
        environment:
          POSTGRES_USER: user
          POSTGRES_PASSWORD: password
      messaging:
        image: rabbitmq:latest
      orchestration:
        image: my-orchestration-service:latest
    ```
    - You can use `build: ./path_to_dockerfile` instead of `image: image_name` to build the image from a Dockerfile in the specified path.
    - **Note**: The `version` field is optional in modern Docker Compose (v1.27.0+) and deprecated. The Compose Specification format is now recommended, which doesn't require specifying a version.

#### Setting Up Docker Compose

1. **Install Docker Compose**:
    - Follow the official installation guide: https://docs.docker.com/compose/install/ **or** https://docs.docker.com/compose/install/linux/#install-the-plugin-manually
2. **Create a `docker-compose.yml` file**:
    - Define your services, networks, and volumes in this file.
3. **Run Docker Compose**:
    - Use `docker-compose up` to start your application.