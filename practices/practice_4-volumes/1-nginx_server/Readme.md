# Exercise 1: Host Volume with Nginx

In this exercise, you will work with a host volume using the Nginx Alpine image. Follow the steps below to explore the behavior of host volumes and their impact on the Nginx server.

## Steps:

### 1. Create a Container with Host Volume:

Use the following Docker command to create a container with a host volume. Replace **<container_name>**, **<ports_mapping>**, **<host_volume_path>**, and **<nombre_imagen>** with your preferred values.

```bash:
docker run -d --name <container_name> --publish <ports_mapping> -v <host_volume_path>:/usr/share/nginx/html <nombre_imagen>
```

![nginx website](https://github.com/padimaster/Software-Construction-and-Evolution/blob/main/blob/nginx-docker.png?raw=true)

**<container_name>:** Choose a name for your container.

**<ports_mapping>:** Define the port mapping, e.g., 8080:80 to map host port 8080 to container port 80.
**<host_volume_path>:** Specify the path to the folder on your host machine where the HTML content is located. Use **\\** as the directory separator.

### 2. Access Nginx Server:

Visit http://localhost:<ports_mapping> in your web browser. Observe the Nginx server behavior.

### 3. Modify Content:

Download a free HTML template from html5up.net. Unzip the template and place it in the host folder specified in <host_volume_path>.

### 4. Access Nginx Server Again:

Visit http://localhost:<ports_mapping> in your web browser. Observe the changes made to the Nginx server.

![nginx website](https://github.com/padimaster/Software-Construction-and-Evolution/blob/main/blob/nginx-app.png?raw=true)

### 5. Remove the Container:

Run the following command to remove the container:

```bash:
docker rm -f <container_name>
Recreate Container with Host Volume:
```

### 6. Recreate the container using the same command as in step 1. Observe how the changes made to the host folder persist in the Nginx server.

Understand pwd Command:

Learn about the pwd command and how it affects the volume path in the Docker command.

### 7. Host Volume with PWD and PowerShell:

Use the following Docker command to create a container with a host volume using PWD and PowerShell:

```powershell:
docker run -d --name server-nginx --publish published=5000,target=80 -v ${PWD}/html:/usr/share/nginx/html nginx:alpine
```

This command uses PowerShell syntax for PWD.
