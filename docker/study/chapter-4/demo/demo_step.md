#### Demo

- **Manually**:
1. Open your terminal.
2. `docker run -it ubuntu:latest bash`: This command runs a Docker container using the latest Ubuntu image and opens an interactive bash shell inside the container.
3. Inside the container:
    1. `apt update`: This command updates the package lists for upgrades and new package installations.
    2. `apt install -y python3`: This command installs Python 3 inside the container.
    3. `python3 --version`: This command checks the installed version of Python
    4. `apt-get install -y python3-pip`: This command installs pip, the package installer for Python.
    5. `pip3 install flask`: This command installs the Flask web framework using pip.
    6. `cat > /opt/app.py`, then paste the source code.
    7. `FLASK_APP=/opt/app.py flask run --host=0.0.0.0`: This command sets the Flask application environment variable and runs the Flask development server, making it accessible from outside the container.
    
- **Containerize with Dockerfile**:
1. Create a new directory for your project and navigate into it.
2. Create a file named `Dockerfile` and add the following content:
    ```Dockerfile
    FROM ubuntu:latest

    RUN apt-get update
    RUN apt-get install -y python3 python3-pip
    RUN pip3 install --break-system-packages flask

    COPY app.py /opt/app.py

    ENV FLASK_APP=/opt/app.py
    ENTRYPOINT ["flask", "run", "--host=0.0.0.0"]
    ```
3. Create a file named `app.py` in the same directory.
4. Run `docker build -t my-flask-app .` to build the Docker image.
5. Run the container with `docker run -d -p 5000:5000 my-flask-app`.
6. Open your web browser and navigate to `http://localhost:5000` to see the Flask application running inside the Docker container.

#### Push Image to Docker Hub

1. Create an account on Docker Hub if you don't have one.
2. Log in to Docker Hub from your terminal using `docker login`.
3. Tag your image with your Docker Hub username: `docker tag my-flask-app your_dockerhub_username/my-flask-app:latest`.
4. Push the image to Docker Hub using `docker push your_dockerhub_username/my-flask-app:latest`.
5. Verify that the image is available on your Docker Hub repository.
