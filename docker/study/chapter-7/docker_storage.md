#### Docker Storage

1. **How manages data in Filesystem?**
   - `/var/lib/docker/` is the default directory where Docker stores its data, including images, containers, volumes, and networks.

2. **Layered Architecture:**
    - Docker images are built using a layered filesystem, where each layer represents a set of filesystem changes (e.g., adding files, installing packages). This allows for efficient storage and sharing of data between images and containers.
    - If we have two **Dockerfiles** that both use the same base image (e.g., `ubuntu:latest`), Docker will only store one copy of that base image layer on disk, saving space.
   - In this scenario:
        - **Image Layer**
        - Layer 1: `ubuntu:latest` (shared base layer)
        - Layer 2: Changes made by Dockerfile A
        - `docker run`
        - **Container Layer** (READ-WRITE)
        - **Layer 3**
            - This layer is created when a container is started from an image. It allows for modifications to be made to the container's filesystem without affecting the underlying image layers.
            - Volumes and bind mounts can be used to persist data beyond the lifecycle of a container.

#### Storage Drivers:
   - Docker uses storage drivers to manage how data is stored and accessed on the host filesystem. Common storage drivers include:
        - **Overlay2**: The default storage driver for most Linux distributions, which uses a union filesystem to layer multiple filesystems.
        - **AUFS**: An older storage driver that also uses a union filesystem but is less commonly used now.
        - **Device Mapper**: A block-level storage driver that provides advanced features like thin provisioning and snapshotting.
        - **Btrfs**: A modern filesystem that includes built-in support for snapshots and subvolumes.