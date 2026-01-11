#### Demo - Docker Voting App
- Link: https://github.com/dockersamples/example-voting-app

![Docker Voting App](images/architecture.excalidraw.png)

- The Docker Voting App is a simple web application that demonstrates how to use Docker containers to build and deploy a multi-service application. It consists of a voting service, a result service, and a Redis database.
- The voting service allows users to vote for their favorite option, while the result service displays the current voting results. The Redis database is used to store the votes.
- The application is built using Docker Compose, which allows you to define and run multi-container Docker applications. The `docker-compose.yml` file defines the services, networks, and volumes needed for the application.
