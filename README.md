# A simple MERN stack application 

This is a simple MERN Stack Application which will follows 3-tier architecture (Presentation Layer for UI, Business Logic for Backend, Database) which you can run in Local and test in Docker Environment with Docker-Compose or just with Docker itself. It is simple employee data related application where we can add employee deatils and later we can edit or delete the same details.
Docker Compose YAML file and Dockerfiles were written already and uploaded in this repo.

## Pre-Requisite:
```
Git
Docker
Docker-Compose
```
## Clone the Project
Clone the repo using Git Clone Command and change the pwd to the root directory of this project.

# Using Docker 

### Create a network for the docker containers

`docker network create demo`

### Build the client 
Building the Client - Frontend Part of the application using Dockerfile

```sh
cd mern/frontend
docker build -t mern-frontend .
```

### Run the client
Creating a FE container with Port mapping and networking.

`docker run --name=frontend --network=demo -d -p 5173:5173 mern-frontend`

### Verify the client is running

Open your browser and type `http://localhost:5173`

### Run the mongodb container
For Database we are using MongoDB. And for this we haven't created any dockerfile. We were taking latest mongodb image directly form dockerhub and doing the port mapping.

`docker run --network=demo --name mongodb -d -p 27017:27017 -v ~/opt/data:/data/db mongodb:latest`

### Build the server
Creating Image for backend service

```sh
cd mern/backend
docker build -t mern-backend .
```

### Run the server
Creating Backend Container along with Port mapping and networking
`docker run --name=backend --network=demo -d -p 5050:5050 mern-backend`

# Using Docker Compose
Instead of doing all the above steps, we can run the Project directly with just one command if we have docker compose installed. 

`docker compose up -d`

This uses [docker-compose.yaml](https://github.com/VarunTej06/MERN-Docker-Compose/blob/main/docker-compose.yaml) to create whole project up and running in the Containers.
It creates all the services like frontend, backend & database inside the conatiners individually and connect them with networking. 

