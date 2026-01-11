### Docker Run

- **TAG**: `docker run [OPTIONS] IMAGE [COMMAND] [ARG...]`, E.g. `docker run redis:4.0` (4.0 is the tag here)
- **STDIN**: `-i` Keep STDIN open even if not attached (interactive). The `-it` option is commonly used to run containers interactively.
- **PORT mapping**: `-p` Map a container's port to a host port. E.g. `-p 8080:80` maps port 80 in the container to port 8080 on the host.
- **VOLUME mapping**: `-v` Bind mount a volume. E.g. `-v /host/path:/container/path` mounts the host directory to the container directory.
- **ISPECT**: `docker inspect [OPTIONS] NAME|ID [NAME|ID...]`, E.g. `docker inspect my_container` to get detailed information about a container.
- **Container Naming**: `--name` Assign a name to the container. E.g. `--name my_container` names the container "my_container".
- **Container Logging**: `docker logs [OPTIONS] CONTAINER`, E.g. `docker logs my_container` to view the logs of a container.