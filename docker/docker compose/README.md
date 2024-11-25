## What is a Docker Compose ?

Docker Compose is a tool for defining and running multi-container Docker applications. 

It allows you to use a YAML file to configure your application’s services, making it easy to start and stop all services at once, and manage complex environments.

Docker Compose is a powerful tool for managing multi-container Docker applications and simplifies the process of development, testing, and deployment.


### 1. Install Docker Compose on Ubuntu :-

```sh
apt update
apt install docker.io -y
apt install docker-compose -y
docker --version
docker-compose --version
```

### 2. Define Your Services :-

vi docker-compose.yml

```sh
version: '3'
services:
  web:
    image: nginx:latest
    ports:
      - "80:80"
  db:
    image: mysql:latest
    environment:
      MYSQL_ROOT_PASSWORD: example

```

:wq ( save )


#### In this example:

Two services are defined: web and db.

The web service uses the nginx image and maps port 80 on the host to port 80 in the container.

The db service uses the mysql image and sets an environment variable for the MySQL root password.

### 3. Start Your Application :-

Run  your docker-compose.yml file.

```sh
docker-compose up
```

Add the -d flag to run the containers in the background (detached mode)

```sh
docker-compose up -d
```

### 4. Manage Your Application :-

List the running containers.

```sh
docker-compose ps
```

Stop the running containers without removing them.

```sh
docker-compose stop
```

Stop and remove the containers, networks, and volumes created by up.

```sh
docker-compose down
```

You can scale services using the --scale flag

```sh
docker-compose up --scale web=3 -d
```




## Host webpage by docker compose
--------------------------------------

#### Step 1 : Set Up Project Directory

```sh
mkdir my_webpage
cd my_webpage
```

#### Step 2 : Create HTML File

```sh
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>India Tour</title>
</head>
<body>
    <h1>Welcome to INDIA !</h1>
    <p>India is a beautifull country.</p>
</body>
</html>

```

#### Step 3 : Create Docker Compose File

Create a docker-compose.yml file inside the my_webpage directory with the following content

```sh
version: '3'

services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
    volumes:
      - ./index.html:/usr/share/nginx/html/index.html

```
:wq

#### Step 4 : Start Docker Compose

```sh
docker-compose up -d
```

#### Step 5 : Access the Webpage

Open your web browser and go to http://localhost:8080
