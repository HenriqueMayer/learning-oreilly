### Getting Started

- Docker Edition: **Community Edition** (CE) and **Enterprise Edition** (EE)
- Installation: Follow the official Docker installation guide for your operating system: https://docs.docker.com/engine/install/ubuntu/
- Post-installation steps: Manage Docker as a non-root user by adding your user to the `docker` group.
- Verify installation: Run `docker --version` and `docker run hello-world` to ensure Docker is installed correctly.
- Basic Commands:
    - `docker pull [image_name]`: Download a Docker image from a registry.
    - `docker run [image_name]`: Create and start a container from an image.
    - `docker ps`: List running containers.
    - `docker ps -a`: List all containers (running and stopped).
    - `docker stop [container_id]`: Stop a running container.
    - `docker rm [container_id]`: Remove a stopped container.
    - `docker images`: List all downloaded Docker images.
    - `docker rmi [image_name]`: Remove a Docker image.

- If you receive permission errors: `sudo usermod -aG docker $USER` and `newgrp docker` to apply the changes.