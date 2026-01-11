#### CMD vs ENTRYPOINT

- Both `CMD` and `ENTRYPOINT` are instructions used in a Dockerfile to specify the command that should be executed when a container is started from the image.
- The key difference between the two is their intended use and behavior:
    - **CMD**:
        - Provides default arguments for the `ENTRYPOINT` instruction or specifies the command to run when the container starts.
        - Can be overridden by providing a different command when running the container.
        - Example:
            ```Dockerfile
            CMD ["python3", "app.py"]
            ```
    - **ENTRYPOINT**:
        - Configures a container to run as an executable.
        - The command specified in `ENTRYPOINT` will always be executed when the container starts, and any arguments provided when running the container will be passed to the `ENTRYPOINT` command.
        - Example:
            ```Dockerfile
            ENTRYPOINT ["python3", "app.py"]
            ```
- In summary, use `CMD` to provide default commands or arguments that can be overridden, and use `ENTRYPOINT` to define the main command that should always be executed when the container starts.
- You can also combine both instructions in a Dockerfile. In this case, `CMD` provides default arguments to the `ENTRYPOINT` command.
    - Example:
        ```Dockerfile
        ENTRYPOINT ["python3"]
        CMD ["app.py"]
        ```
    - When the container is run without additional arguments, it will execute `python3 app.py`. If you provide an argument when running the container, it will override the `CMD` value but still use the `ENTRYPOINT` command.
        - E.g., `docker run my_image another_script.py` will execute `python3 another_script.py`.
- And we have the `--entrypoint` flag in the `docker run` command to override the `ENTRYPOINT` instruction defined in the Dockerfile.
    - Example:
        ```bash
        docker run --entrypoint /bin/bash my_image
        ```
    - This command will start a container from `my_image` and override the `ENTRYPOINT` to run `/bin/bash` instead of the command specified in the Dockerfile.