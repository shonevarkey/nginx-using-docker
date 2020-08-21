# Docker nginx custom image setup

To setup nginx using docker custom image

## Installing docker

The easiest way of installing docker in Centos/RHEL Operating systems:

- ***$ yum install docker -y***

After installation we need to start the docker service

- ***$ service docker start***

Now we are going to pull nginx image from docker hub and create a container **web**  
Where, **8080** is the host port and **80** is the container port  

- ***$ docker run -it --rm -d -p 8080:80 --name web nginx***

### Options used

1. ***d -> Used to run the container in detach mode.***

2. ***p -> Used to assign ports.***

3. ***it -> Used to run docker interactively.***

4. ***rm -> Used to remove container automatically when it exits.***

5. ***name -> Used to assign a name to the container.***

## View docker images

- ***$ docker image ls***

## View containers

- ***$ docker container ls***

## Stop container

- ***$ docker stop web***

Where, **web** is the name of the container

# Creating docker custom images

We are now creating a sample webpage **index.html** inside a directory **site-content**

- ***mkdir site-content***
- ***cd site-content/***
- ***vim index.html***

```
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Docker Nginx</title>
</head>
<body>
  <h2>Hello from Nginx container</h2>
</body>
</html>
```
A container is created with the sample webpage mounted into  it.

- ***docker run -it --rm -d -p 8080:80 --name web -v /root/site-content/:/usr/share/nginx/html nginx***

1. ***v -> Used to bind mount a file/directory from host machine to the container***

## Creating Dockerfile

- ***vim Dockerfile***

```
FROM nginx:latest
COPY ./index.html /usr/share/nginx/html/index.html
```

1. **FROM** ***-> Used to set the Base Image for subsequent instructions***
2. **COPY** ***-> Used to copy files from source to destination***

Now we are going to build an image from **Dockerfile**

- ***docker build -t webserver .***

1. ***build -t -> builds an image from a Dockerfile in the current directory and tags the image***

Where, **webserver** is the name of the newly created image.

Now we are going to create a container with the newly created custom image.

- ***docker run -it --rm -d -p 8080:80 --name web webserver***


### THE END


