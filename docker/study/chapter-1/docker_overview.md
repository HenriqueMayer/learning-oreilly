### Why do you need docker?

- **Example**: WebServer - Database - Messaging - Orchestration
- **Problem**: Different environments - Dependencies - Versions - Configurations
- **Solution**: Containerization - Isolation - Portability - Consistency

### What are Containers?

- Containers are lightweight, standalone, and executable software packages that include everything needed to run a piece of software, including the code, runtime, system tools, libraries, and settings.
- Containers share the host system's kernel but run in isolated user spaces, ensuring that applications run consistently across different environments.
- Containers are more efficient than traditional virtual machines because they do not require a full operating system for each instance, leading to faster startup times and lower resource consumption.
- **"Sharing the kernel"** means that multiple containers can run on the same host operating system without the overhead of running separate OS instances, allowing for better resource utilization and performance.

### What is Docker?

- Docker is an open-source platform that automates the deployment, scaling, and management of applications using containerization technology.
- Docker provides tools and services to create, deploy, and run applications in containers, making it easier to develop, ship, and run applications consistently across different environments.
- Docker includes components such as the **Docker Engine** (the runtime that builds and runs containers), **Docker Hub** (a cloud-based registry for sharing container images), and **Docker Compose** (a tool for defining and running multi-container Docker applications).
- Docker simplifies the containerization process, allowing developers to package applications and their dependencies into a single container image that can be easily shared and deployed.

### Docker Architecture

- Docker follows a client-server architecture, where the Docker client communicates with the Docker daemon (server) to build, run, and manage containers.
- The Docker client sends commands to the Docker daemon, which performs the requested actions, such as building images, running containers, and managing container lifecycle.
- Docker images are read-only templates that contain the application code, libraries, and dependencies needed to run a container. Containers are instances of these images that run in isolated environments.
- Docker uses a layered filesystem, where each layer represents a set of changes to the image. This allows for efficient storage and sharing of images, as common layers can be reused across multiple images.
- Docker registries, such as Docker Hub, are repositories for storing and distributing Docker images. Users can push and pull images to and from these registries.

### Containers vs Images

- **Docker Image**: A Docker image is a lightweight, standalone, and executable package that includes everything needed to run a piece of software, such as the code, runtime, libraries, environment variables, and configuration files. Images are read-only templates used to create containers. They are built using a series of layers, with each layer representing a set of changes or additions to the base image.
- **Docker Container**: A Docker container is a runtime instance of a Docker image. It is a lightweight, isolated environment that runs the application defined in the image. Containers share the host system's kernel but have their own filesystem, network, and process space. Containers can be started, stopped, moved, and deleted independently of the underlying image.
- In summary, a Docker image is a static blueprint for creating containers, while a Docker container is a dynamic, running instance of that blueprint.

