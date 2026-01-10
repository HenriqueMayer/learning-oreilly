#### What am I containerizing?

- **Flask**: A lightweight web application framework for Python.

#### How to create my own Image?

- **Manually**:
    1. OS - Ubuntu
    2. Update apt repo
    3. Install dependencies using apt
    4. Install Python dependencies using pip
    5. Copy source code to /opt folder
    6. Run the web server using "flask" command 

- **Using Dockerfile**:
    1. Create a file named `Dockerfile` in your project directory.
    2. Add the following content to the `Dockerfile`:
        ```Dockerfile
        FROM ubuntu:latest

        RUN apt-get update
        RUN apt-get install -y python3 python3-pip
        RUN pip3 install --break-system-packages flask

        COPY . /opt/my_flask_app

        ENV FLASK_APP=/opt/my_flask_app/app.py
        ENTRYPOINT ["flask", "run", "--host=0.0.0.0"]
        ```

#### Dockerfile

- Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image. Using docker build users can create an automated build that executes several command-line instructions in succession.
    - Instructions include:
        - **FROM**: Start from a base OS image or another image.
        - **RUN**: Install software packages (all dependency)
        - **COPY**: Copy files from host to image
        - **ENTRYPOINT**: Configure a container that will run as an executable
        - **CMD**: Provide defaults for an executing container

#### Layered Architecture

- Each instruction in a Dockerfile creates a new layer in the image. Layers are stacked on top of each other to form the final image.
- Layers are cached, so if you rebuild the image and some layers haven't changed, Docker will reuse the cached layers, speeding up the build process.
- This layered architecture allows for efficient storage and transfer of images, as only the layers that have changed need to be updated.
- E.g., (`docker history <image_id>`) shows the layers of an image:
    - Layer 1: Ubuntu base image (120MB)
    - Layer 2: Changes in apt packages (306MB)
    - Layer 3: Changes in pip packages (6.3MB)
    - Layer 4: Source code (226B)
    - Layer 5: Update Entrypoint with Flask command (0B)

#### Build Image

- To build the Docker image from the Dockerfile, use the following command in your terminal:
    ```bash
    docker build -t my_flask_app:latest .
    ```
    - `-t my_flask_app:latest`: Tags the image with the name `my_flask_app` and the tag `latest`.
    - `.`: Specifies the build context, which is the current directory.
- After the build is complete, you can verify that the image has been created by running:
    ```bash
    docker images
    ```

#### Failure
- If the layer 2 fails (e.g., network issue during apt-get), you can fix the issue and re-run the build command. Docker will use the cached layers for layers 1 and will only re-execute layer 2 and the subsequent layers.
- The same applies if you add new layers or modify existing ones. Only the affected layers and those that follow will be rebuilt, while the unchanged layers will be reused from the cache.

#### What can you containerize?
- You can containerize almost any application or service, including:
    - Web applications (e.g., Flask, Django, Node.js)
    - Databases (e.g., MySQL, PostgreSQL, MongoDB)
    - Development environments
    - Microservices
    - CI/CD tools (e.g., Jenkins, GitLab CI)
    - Message brokers (e.g., RabbitMQ, Kafka)
    - Caching systems (e.g., Redis, Memcached)
    - Monitoring tools (e.g., Prometheus, Grafana)
    - Evevrything that can run on a server can be containerized.

#### Best Practices for Creating Docker Images
- Use a minimal base image to reduce the size of the final image.
- Combine multiple RUN commands into a single command to reduce the number of layers.
- Use multi-stage builds to optimize the build process and reduce the final image size.
- Regularly update your base images to include security patches and updates.
- Keep your Dockerfiles organized and well-documented for easier maintenance.