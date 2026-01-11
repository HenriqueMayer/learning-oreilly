### Demo

1. `docker run centos:centos7.9.2009`  
   This command will download the CentOS image and create a container. However, since CentOS is an operating system, the container will exit immediately after starting because there is no long-running process.
    - `docker run centos:centos7.9.2009 sleep 60` can be used to keep the container running for 60 seconds for demonstration purposes.
2. `docker ps -a`  
   This command lists all containers, including the one we just created. You will see the CentOS container with an "Exited" status.
3. `docker run -it centos:centos7.9.2009 /bin/bash`  
   This command runs the CentOS container interactively with a terminal and starts a bash shell inside the container.
4. Inside the container, run `cat /etc/centos-release`  
   This command displays the CentOS version information.
5. Exit the container by typing `exit` or pressing `Ctrl+D`.
6. `docker rm [container_id]`  
   Replace `[container_id]` with the actual ID of the exited CentOS container to remove it.
7. `docker images`  
   This command lists all Docker images on the local machine, including the CentOS image we pulled earlier.
8. `docker rmi centos:centos7.9.2009`  
   This command removes the CentOS image from the local machine.