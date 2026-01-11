#### Docker Engine

- **Docker Engine** is the core component of Docker that enables the building, shipping, and running of containerized applications. It consists of a server (the Docker daemon), a REST API, and a command-line interface (CLI) client.
- The **Docker daemon** (`dockerd`) is responsible for managing Docker objects such as images, containers, networks, and volumes. It listens for Docker API requests and performs the necessary actions to fulfill them.
- The **Docker CLI** (`docker`) is the command-line tool that allows users to interact with the Docker daemon. It provides various commands to manage Docker resources.
    - The `-H` flag specifies the Docker host to connect to, allowing you to manage remote Docker daemons.
    - Example command to connect to a remote Docker host:
      ```bash
      docker -H tcp://<DOCKER-HOST-IP>:2375 info
      ```
- Docker Engine uses a client-server architecture, where the CLI client communicates with the Docker daemon via REST API calls.
- Docker Engine supports containerization, allowing applications to run in **isolated environments** with their own filesystem, networking, and process space.
- It leverages Linux kernel features such as namespaces and cgroups to provide isolation and resource management for containers.
- Docker Engine supports multiple storage drivers (e.g., overlay2, aufs, btrfs) to manage the filesystem layers of Docker images and containers.
    - **What is a storage driver?**
      - A storage driver is a component of Docker that manages the way data is stored and retrieved for Docker images and containers. It handles the layering of filesystems, allowing for efficient storage and sharing of data between containers.
- It also supports various networking drivers (e.g., bridge, host, overlay) to facilitate communication between containers and external networks.
- Docker Engine can run on various operating systems, including Linux, Windows, and macOS, providing a consistent environment for containerized applications across different platforms.

#### Containerization with Docker Engine

- **Containerization** is a lightweight form of virtualization that allows applications to run in isolated environments called containers. Docker Engine provides the necessary tools and features to create, manage, and run containers.
- Containers share the host operating system's kernel but have their own filesystem, networking, and process space, ensuring isolation and consistency across different environments.
- Docker Engine uses images as the blueprint for creating containers. Images are built using a layered filesystem, allowing for efficient storage and distribution.
- Dockerfiles are used to define the instructions for building Docker images, specifying the base image, application code, dependencies, and configuration.
- **Docker Engine provides commands to manage containers**, such as `docker run`, `docker stop`, `docker start`, and `docker rm`.
- It also offers features like volume management for persistent storage and networking capabilities to connect containers.
- Docker Engine supports orchestration tools like **Docker Swarm** and **Kubernetes** **for managing multi-container applications at scale**.
- By using Docker Engine, developers can streamline the development, testing, and deployment of applications, ensuring consistency across different stages of the software lifecycle.

#### Namespace - PID (process ID)

- In Docker Engine, **namespaces** are a key feature t**hat provides isolation for containers**. The PID (Process ID) namespace is one of the namespaces used to isolate the process IDs of containers from the host system and other containers.
    - **What is the difference between the host system and a container regarding PIDs?**
      - The host system has its own set of process IDs (PIDs) for all running processes, while each container has its own PID namespace that isolates its processes from those on the host and other containers.
- When a container is created, Docker Engine assigns it its own PID namespace, which means that the processes running inside the container have their own set of process IDs that are separate from those on the host system.
- This isolation ensures that processes inside a container cannot see or interact with processes running on the host or in other containers, enhancing security and stability.
- For example, a process with `PID: 1` inside a container is the init process for that container, but it may have a different PID on the host system.
- The PID namespace allows for better resource management and prevents conflicts between processes running in different containers.
- Docker Engine uses other namespaces as well, such as the network namespace, mount namespace, and user namespace, to provide comprehensive isolation for containers.
- By leveraging namespaces, Docker Engine ensures that containers can run independently and securely on the same host system without interference.

#### Control Groups (cgroups)

- Control Groups (**cgroups**) are a Linux kernel feature used by Docker Engine to manage and limit the resource usage of containers. Cgroups allow Docker to allocate CPU, memory, disk I/O, and network bandwidth to containers in a controlled manner.
- Docker Engine uses cgroups to ensure that containers do not exceed their allocated resources, preventing one container from monopolizing system resources and affecting the performance of other containers or the host system.
- Cgroups provide fine-grained control over resource allocation, allowing administrators to set limits and priorities for different containers.
- For example, you can limit the amount of memory a container can use by specifying the `--memory` flag when running a container:
  ```bash
  docker run --memory="256m" my-container
  ```
- You can also limit CPU usage using the `--cpus` flag (this example limits the container to 1.5 CPU cores):
  ```bash
  docker run --cpus="1.5" my-container
  ```
- Docker Engine also uses cgroups to monitor resource usage and enforce policies, such as CPU shares and block I/O limits.
- Cgroups work in conjunction with namespaces to provide a complete isolation and resource management solution for containers.
- By using cgroups, Docker Engine ensures that containers can run efficiently and reliably, even in multi-tenant environments where multiple containers share the same host system.

#### Command Examples
- `docker ps -eaf` : Lists all running containers with detailed information.