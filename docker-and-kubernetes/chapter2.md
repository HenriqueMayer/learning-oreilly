### Containers and Virtual Machines

- Virtualization:
    - Hardware - Host operating system - Hypervisor - [Guest OS]
    - The hypervisor is the translate **Host <--> Hypervisor <---> Guest OS**
    - If you need strong isolation between different envs
    - If you are dealing with legacy applications
    - If you want to replicate a complete system env for testing or development

- Containerization:
    - Hardware - Host operating system - **Container Engine**
    - Plataform-agnostic
    - If you are building modern, cloud-native applications using architecture.
    - If ypu need to scale your applications quickly and efficiently

---
- Docker Components:
    1. Docker Client: Docker CLI or API calls
    2. Docker Host: REST API, Docker Daemon, Containers, Image Cache
    3. Image Registry: Storing images

    - Running a container from a image
    1. ```docker run``` with the image
    2. Docker CLI --> REST API
    3. Check if the docker image is not in the **DockerHost/ImageCache** --> Check the **ImageRegistry** (network)
    4. **DockerHost** instantiates a new container based on the image

    - Building and pushing an Image
    1. ```docker build``` in the CLI
    2. Sends a request to the host's REST API (this also includes the Dockerfile and context)
    3. **DockerHost** builds the image according to the Dockerfile
    4. **DockerHost** tags the image and stores it locally
    5. ```docker push``` CLI (push to the Image Registry)
---