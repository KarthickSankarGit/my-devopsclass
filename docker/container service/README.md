# 1. How to create container :- FROM IMAGE (USING DOCKER PULL)

#### ex-1 :-

Suppose if you want to create debian based container , then go to docker-hub & search `debian`

```sh
sudo docker pull debian
```

To check images


```sh
sudo docker images
```


To create container from `debian image`


```sh
sudo docker run -d -it --name container-1 debian /bin/bash
```

To check only Running container status


```sh
sudo docker ps
```


To stop container


```sh
sudo docker stop container-1
```

To check all container ( both stop and running ) status


```sh
sudo docker ps -a
```


To start a stopped container


```sh
sudo docker start container-1
```

To Remove container from your system

```sh
sudo docker stop container-1
sudo docker rm container-1
```

# 2. How to create container :- FROM IMAGE (USING DOCKER FILE)

#### ex-1 :-

To create a dockerfile

`vi Dockerfile`

( press-i )


```sh
FROM debian
RUN echo "hi all" > myfile
```

( Press - esc , :wq )


Now Create image from dockerfile


```sh
sudo docker build -t myownimg1 .
```


To check image (dockerfile)


```sh
sudo docker images
```


To create container from `myownimg1`


```sh
sudo docker run -d -it --name container-2 myownimg1 /bin/bash
```

To check container status


```sh
sudo docker ps -a
```

Go inside Container

```sh
sudo docker exec -it <container-id-no> /bin/bash
```

To verify `myfile` & its Data present inside container or not

```sh
ls
```

```sh
cat myfile
```

To Go outside from container

```sh
exit
```




## TO HOST A WEBSITE USING DOCKERFILE

#### 1. Create a html file

`vi index.html`

( press-i )

```sh
<html>
<head>
<body>
<title> India-visit </title>
<h1> WELCOME TO INDIA </h1>
<p1> MY INDIA ! MY COUNTRY </p1>
</body>
</head>
</html>
```

( Press - esc , :wq )


#### 2. To create a dockerfile

`vi Dockerfile`

( press-i )


```sh
# Use an existing Nginx image from Docker Hub as the base image
FROM nginx:alpine

# Copy the HTML file into the Nginx default document root directory
COPY index.html /usr/share/nginx/html/

# Expose port 80 to allow communication to/from the container
EXPOSE 80
```

( Press - esc , :wq )


Now Create image from dockerfile


```sh
sudo docker build -t mywebsiteimg1 .
```


To check image (dockerfile)


```sh
sudo docker images
```


To create container from `mywebsiteimg1`


```sh
sudo docker run -d -it -p 8080:80 --name container-3 mywebsiteimg1 /bin/bash
```

To check container status


```sh
sudo docker ps -a
```




# 3. How to create container image


`docker commit container-name newimagename`

`docker images`
