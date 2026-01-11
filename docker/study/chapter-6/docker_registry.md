#### Docker Registry

- A Docker registry is a storage and distribution system for Docker images. It allows users to store, share, and manage Docker images in a centralized location.
- Docker Hub is the default public registry provided by Docker, but users can also set up private registries for their own use cases.
- To push an image to a Docker registry, you first need to tag the image with the registry's URL and then use the `docker push` command.
- To pull an image from a a Docker registry, you can use the `docker pull` command followed by the image name.
- Docker registries can be secured using authentication and authorization mechanisms to control access to images.
- Private registries can be set up using tools like Docker Registry, Harbor, or Nexus Repository.
- Using a Docker registry helps streamline the development and deployment process by enabling easy sharing and versioning of Docker images across teams and environments.
- Example commands:
  - **Tagging an image**: `docker tag my-image:latest my-registry.com/my-image:latest`
  - **Pushing an image**: `docker push my-registry.com/my-image:latest`
  - **Pulling an image**: `docker pull my-registry.com/my-image:latest`

#### How set up a private Docker registry?

- To set up a private Docker registry, you can use the official Docker Registry image. Here are the basic steps:
  1. Run the Docker Registry container:
     ```bash
     docker run -d -p 5000:5000 --name registry registry:2
     ```
  2. Tag your Docker image to point to your private registry:
     ```bash
     docker tag my-image:latest localhost:5000/my-image:latest
     ```
  3. Push the image to your private registry:
     ```bash
     docker push localhost:5000/my-image:latest
     ```
  4. Pull the image from your private registry:
     ```bash
     docker pull localhost:5000/my-image:latest
     ```
- Note: For production use, consider securing your private registry with TLS and authentication mechanisms.
    - What is TLS?
      - TLS (Transport Layer Security) is a cryptographic protocol that provides secure communication over a computer network. It ensures data integrity, confidentiality, and authentication between clients and servers.
- E.g., AWS, Google Cloud, and Azure offer managed container registries that provide additional features like vulnerability scanning, access control, and integration with their cloud services.