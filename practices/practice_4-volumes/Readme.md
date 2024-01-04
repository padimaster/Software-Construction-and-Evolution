**Author:** Alex Padilla

# Docker Volumes - Practice 4

This repository contains practical exercises focusing on Docker Volumes. Each exercise is designed to help you understand and work with Docker volumes effectively.

## Exercises:

### 1. Build and Run an Nginx Server

In this exercise, you will learn how to build and run an Nginx server using Docker. Follow the instructions to set up and explore the capabilities of the Nginx container.

### 2. Build and Run a Wordpress Server

Explore the process of building and running a Wordpress server using Docker. This exercise provides hands-on experience with setting up a containerized Wordpress environment.

### 3. Operations with Volumes

Learn essential volume operations in Docker. This exercise covers tasks such as mounting volumes, inspecting volume details, and managing data persistence within Docker containers.

#### Create Volume
```bash

```

##### 3.1 Mountpoint of vol-postgres:
After creating the Docker volume with the provided command (docker volume create vol-postgres), the system automatically chooses the Mountpoint location. You can verify it by running the following command:
```bash
docker volume inspect vol-postgres
```
This command will provide detailed information about the volume, including the Mountpoint path.
![docker volume inspect](https://github.com/padimaster/Software-Construction-and-Evolution/blob/main/blob/inspect-vol.png?raw=true)

##### 3.2 Accessing the Mountpoint:
Once you've identified the Mountpoint, you can access it directly from the command line or through a file browser. For example, if the Mountpoint is /var/lib/docker/volumes/vol-postgres/_data, you can use the following command to access it:
```bash
cd /var/lib/docker/volumes/vol-postgres/_data
```
This will take you to the directory where the volume data is stored.

#### 3.3 Creating a network for PostgreSQL:
You can create a Docker network for PostgreSQL using the following command:
```bash
docker network create net-postgres
```
After creating the network, you can use it when running a PostgreSQL container to ensure that related containers are on the same network and can communicate with each other.

When launching the PostgreSQL container, you can specify the network with the following parameter:
```bash
--network=net-postgres
```

This ensures that the PostgreSQL container is on the same network as other containers you may have in that specific network. Make sure to adjust the values according to your needs.

#### 3.4 Postgres server using created volume
Run the following command:
```bash
docker run -d --name server-postgres -e POSTGRES_DB=db_drupal -e POSTGRES_PASSWORD=12345 -e POSTGRES_USER=user_drupal -v vol-postgres:/var/lib/postgresql/data --network net-postgres postgres
```

The Docker command successfully launches a PostgreSQL server named "server-postgres" with specific configurations and attaches a named volume, "vol-postgres," to store persistent data. The use of named volumes enhances data management and allows for seamless communication between containers on the designated Docker network, "net-postgres".

### 4. Anonymous Volume
Docker provides a flexible and efficient way to manage data persistence through volumes. Anonymous volumes, a specific type of volume in Docker, are created automatically by the system when a container is launched with the -v flag and without specifying a named volume. This report delves into the use of anonymous volumes with a practical example involving a Docker container running an Nginx web server.

#### Anonymous Volume Example:
The Docker command:
```bash
docker run -d --name server-nginx -v /usr/share/nginx/html --publish published=9800,target=80 nginx:alpine
```
Launches an Nginx container named "server-nginx" with an anonymous volume mounted at the path /usr/share/nginx/html. This volume is used by Nginx to store its default HTML content. The --publish flag exposes the Nginx container's port 80 to port 9800 on the host.

#### Volume Removal:
To remove both the container and the associated volume, the command:
```bash
docker rm -fv server-nginx
```
is employed. Notably, this command removes the associated anonymous volume if it exists. The use of **-fv** ensures a forceful removal, terminating the running container and removing its associated volume.

> Anonymous volumes offer a convenient way to handle data within Docker containers without the need for explicitly named volumes. This example demonstrates how anonymous volumes can be leveraged in conjunction with a practical use case involving an Nginx web server. Understanding the nuances of anonymous volumes is crucial for effective Docker container management and data persistence strategies.
