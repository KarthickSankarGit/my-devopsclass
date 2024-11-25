# Docker Image PUSH into DockerHub

#### 1. vi Dockerfile

`FROM debian:latest`

`RUN echo "hiiiiii i m java" > myjavafile`

( press-esc , :wq )

ls

#### 2. Build image using Dockerfile


`docker build -t myownimg-1 .`


#### 3. Check your Docker image


`docker images`


#### 4. Push docker image inside Docker-Hub


`docker login`

`docker tag myownimg-1 urdockerhub/myownimg-1:v1`

`docker images`

`docker push urdockerhub/myownimg-1:v1`

( Go to docker-hub and check it )


#### 5. Create container from Docker-hub ,using docker pull ( pushed image )


`docker pull urdockerhub/myownimg-1:v1`

`docker images`

`docker run -itd --name mycontainer-1 urdockerhub/myownimg-1:v1`


#### 6. Check your Docker container

`docker ps -a`


#### 7. To delete docker image

`docker rmi urdockerhub/myownimg-1:v1`


#### 8. To delete docker image forcefully

`docker rmi -f urdockerhub/myownimg-1:v1`


#### 9. To delete multiplpe docker images at once

`docker rmi img1:version img2:version img3:version`
