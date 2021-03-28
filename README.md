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


## Creating Dockerfile

- ***vim Dockerfile***

```
FROM nginx:latest
COPY ./index.html /usr/share/nginx/html/index.html
```

Now we are going to build an image from **Dockerfile**

- ***docker build -t webserver .***


Where, **webserver** is the name of the newly created image.

Now we are going to create a container with the newly created custom image.

- ***docker run -it --rm -d -p 8080:80 --name web webserver***


### THE END


