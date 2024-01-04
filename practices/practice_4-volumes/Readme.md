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
docker run -d --name server-postgres -e POSTGRES_DB=db_drupal -e POSTGRES_PASSWORD=12345 -e POSTGRES_USER=user_drupal -v vol-postgres:/var/lib/postgresql/data --network net-postgres postgres
```

##### 3.1 Mountpoint of vol-postgres:
After creating the Docker volume with the provided command (docker volume create vol-postgres), the system automatically chooses the Mountpoint location. You can verify it by running the following command:
```bash
docker volume inspect vol-postgres
```
This command will provide detailed information about the volume, including the Mountpoint path.
![docker volume inspect](https://github.com/padimaster/Software-Construction-and-Evolution/blob/main/inspect-vol.png?raw=true)

##### 3.2 Accessing the Mountpoint:
/var/lib/docker/volumes/vol-postgres/_data


### 4. Anonymous Volume

Dive into the concept of anonymous volumes in Docker. Understand how to create and utilize anonymous volumes for temporary data storage within containers.

## Getting Started

Follow these general steps to get started with the exercises: