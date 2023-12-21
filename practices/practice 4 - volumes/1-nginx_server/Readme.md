# Exercise 1: Host Volume with Nginx

In this exercise, you will work with a host volume using the Nginx Alpine image. Follow the steps below to explore the behavior of host volumes and their impact on the Nginx server.

## Steps:

### 1. Create a Container with Host Volume:

Use the following Docker command to create a container with a host volume. Replace **<nombre_contenedor>**, **<mapeo_de_puertos>**, **<ruta_carpeta_host>**, and **<nombre_imagen>** with your preferred values.

```bash:
docker run -d --name <nombre_contenedor> --publish <mapeo_de_puertos> -v <ruta_carpeta_host>:/usr/share/nginx/html <nombre_imagen>
```

<nombre_contenedor>: Choose a name for your container.
<mapeo_de_puertos>: Define the port mapping, e.g., 8080:80 to map host port 8080 to container port 80.
<ruta_carpeta_host>: Specify the path to the folder on your host machine where the HTML content is located. Use \ as the directory separator.

### 2. Access Nginx Server:

Visit http://localhost:<mapeo_de_puertos> in your web browser. Observe the Nginx server behavior.

### 3. Modify Content:

Download a free HTML template from html5up.net. Unzip the template and place it in the host folder specified in <ruta_carpeta_host>.

### 4. Access Nginx Server Again:

Visit http://localhost:<mapeo_de_puertos> in your web browser. Observe the changes made to the Nginx server.

### 5. Remove the Container:

Run the following command to remove the container:

```bash:
docker rm -f <nombre_contenedor>
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
