#### Demo

- Use the `ls -l /var/lib/docker` command to view Docker's storage structure on the host system
- This directory contains subdirectories for images, containers, volumes, and other Docker-managed data
- Key subdirectories:
    ```
    total 40
    drwx--x--x  5 root root 4096 Jan 10 13:11 buildkit
    drwx--x--- 10 root root 4096 Jan 10 18:53 containers
    -rw-------  1 root root   36 Jan  9 17:56 engine-id
    drwxr-x---  3 root root 4096 Jan  9 17:56 network
    drwx------  3 root root 4096 Jan  9 17:56 plugins
    drwx--x---  3 root root 4096 Jan  9 17:58 rootfs
    drwx------  2 root root 4096 Jan 11 14:27 runtimes
    drwx------  2 root root 4096 Jan  9 17:56 swarm
    drwx------  2 root root 4096 Jan 11 14:27 tmp
    drwx-----x  4 root root 4096 Jan 11 14:27 volumes
    ```

- Each subdirectory serves a specific purpose:
    - `containers/`: Stores data related to individual containers, including their writable layers and metadata
    - `images/`: Contains image layers and metadata for Docker images
    - `volumes/`: Holds data for Docker volumes used for persistent storage
    - `network/`: Manages network configurations and settings for Docker networks
- Understanding this structure helps in troubleshooting storage-related issues and managing Docker's data effectively.

#### Information

- `docker history [IMAGE]`: Displays the history of an image, showing the layers that make up the image
- `docker system df`: Provides a summary of Docker's disk usage, including images, containers, and volumes
    - `docker system df -v`: Provides a more detailed view of Docker's disk usage, including individual layers and volumes
- `docker volume ls`: Lists all Docker volumes on the system
- `docker volume inspect [VOLUME]`: Shows detailed information about a specific Docker volume


