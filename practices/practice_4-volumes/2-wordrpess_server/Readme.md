# Exercise 2: Wordpress with Docker Networks and Volumes

In this exercise, you'll delve into deploying a Wordpress application using Docker containers, emphasizing the use of networks and volumes for efficient data management.

## Instructions:

### 1. Create a Docker Network:

To facilitate communication between containers, establish a Docker network named net-wp.

``` bash:
docker network create net-wp
```
![docker volume inspect](https://github.com/padimaster/Software-Construction-and-Evolution/blob/main/blob/wp-net.png?raw=true)

### 2. MySQL Container:

Set up a MySQL container connected to the net-wp network. Ensure persistent data storage by specifying a host folder for MySQL data.

```bash:
docker run -d --name mysql-container --network net-wp -v <host_volume_path>:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=<your_password> mysql:latest
```

- **<host_volume_path>:** Define the path to the host folder (db in this case) for MySQL data persistence.
- **<your_password>:** Set a secure password for the MySQL root user.


### 3. Wordpress Container:

Deploy a Wordpress container connected to the net-wp network. Specify a host folder for persistent Wordpress data.

```bash:
docker run -d --name wordpress-container --network net-wp -v <host_volume_path>:/var/www/html -e WORDPRESS_DB_HOST=mysql-container -e WORDPRESS_DB_USER=root -e WORDPRESS_DB_PASSWORD=<your_password> -p <host_port>:80 wordpress:latest
```

<host_volume_path>: Indicate the path to the host folder (www in this case) for Wordpress data persistence.
<your_password>: Utilize the same MySQL root password as configured earlier.
<host_port>: Map a host port to the container's port (e.g., 8080:80).
Customize Wordpress:

![docker volume inspect](https://github.com/padimaster/Software-Construction-and-Evolution/blob/main/blob/wp-containers.png?raw=true)

Access the Wordpress site at http://localhost:<host_port> in your web browser. Customize the appearance and add an entry.

![docker volume inspect](https://github.com/padimaster/Software-Construction-and-Evolution/blob/main/blob/wp-set-up.png?raw=true)

### 4. Remove and Recreate Container:

Experiment with container removal and recreation:

```bash
docker rm -f wp-site
```

Recreate the container using the same command as in step 3. Observe the behavior and data persistence.
![docker volume inspect](https://github.com/padimaster/Software-Construction-and-Evolution/blob/main/blob/wp-site.png?raw=true)

## Summary:
Explore the seamless interaction between Docker containers, networks, and volumes in deploying and managing a Wordpress application. Understand how persistent data storage enhances the reliability and consistency of your Dockerized applications. Feel free to experiment and contribute improvements to this exercise. 

***Happy Dockerizing!***