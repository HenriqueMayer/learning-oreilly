### Docker Images

- Images are self-contained, read-only template that encapsulates everything needed to run your application.
    - **The base layer**: often a minimal Linux distribution like Alpine, or a more full-fledged one like Ubuntu.
    - **Runtime Environment**: Specific software (e.g., Python, Node.js) required by your application
    - **Libraries & Dependencies**: All the external code your application relies on.
    - **Application code**: Your own source code or compiled binaries.
    - **Configuration**: Settings for your application and its environment.
- A **Docker Image** is like a snapshot of your application and its complete runtime environment, frozen in time and ready to be brought to life as a container. Images can be sourced from multiple locations.
- **Docker Hub**: This is the official Docker Image repository.
- **Private Registries**: For organizations or individuals with proprietary software.