# spring-boot-docker
Dockerization of spring boot

# Install docker on mac os
https://docs.docker.com/docker-for-mac/install/

# Dockerfile to be added into spring boot project
FROM openjdk:8 <br/>
EXPOSE 8080 <br/>
ADD target/spring-boot-docker.jar spring-boot-docker.jar <br/>
ENTRYPOINT ["java","-jar","/spring-boot-docker.jar"]

# Build docker image
docker build -f Dockerfile -t docker-spring-boot .

# To list docker image
docker image ls

# To push to docker hub - login first and authorize
docker login

# Create a tag to push to docker hub
docker tag docker-spring-boot docker-user-name/docker-spring-boot

# Push docker image to docker hub
docker push docker-user-name/docker-spring-boot

# Pull from docker hub
docker pull docker-user-name/docker-spring-boot

# Run docker image mapping to port
docker run -p 9090:8080 docker-user-name/docker-spring-boot
