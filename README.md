# Docker nginx custom image setup

To setup nginx using docker custom image

## Installing docker

The easiest way of installing docker in Centos/RHEL Operating systems:

- $ yum install docker -y

After installation we need to start the docker service

- $ service docker start

Now we are going to pull nginx image from docker hub and create a container named *web*  
where **8080** is the host port and **80** is the container port  

- $ docker run -it --rm -d -p 8080:80 --name web nginx

###Options used

1. d -> Used to run the container in detach mode.

2. p -> Used to assign ports.

3. it -> Used to run docker interactively.

4. rm -> Used to remove container automatically when it exits.

5. name -> Used to assign a name to the container.

## View docker images

- $ docker image ls

## View containers

- $ docker container ls

## Stop container

- $ docker stop web

where *web* is the name of the container

#Creating docker custom images

We are now creating a sample website **index.html** inside a directory **site-content**

- mkdir site-content
- cd site-content/
- vim index.html

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



