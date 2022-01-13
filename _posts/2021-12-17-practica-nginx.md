---
layout: post
categories: 
conToc: true
title: Práctica NGINX
---




# Práctica NGINX


### Instalación NGINX

En esta práctica vamos a instalar un contenedor docker que contendrá un [servidor web](https://es.wikipedia.org/wiki/Servidor_web) de alto rendimiento: [NGINX](https://www.nginx.com/).

Para ello, ingresarás dentro de tu cuenta de [Dockerhub](https://hub.docker.com/) y puedes encontrar la imagen oficial del proyecto.


![](https://raw.githubusercontent.com/savalls/savalls.github.io/main/assets/img/nginx_official_docker_image.png)



Ahora tan facil como dirigirte a  un terminal y teclear lo siguiente:
```bash
$ docker run --rm -d -p 8080:80 --name web nginx
```
Ahora docker se encargará de comprobar si existe la imagen en el sistema, instalará los archivos necesarios, ejecutará el contenedor como demonio (-d) y mapeará el puerto 80 de nuestro huesped en el puerto 8080 de nuestro host. (8080:80)

![](https://raw.githubusercontent.com/savalls/savalls.github.io/main/assets/img/docker_run_nginx_latest.png)


Y éste será el resultado, que has desplegado en menos de cinco minutos
![](https://raw.githubusercontent.com/savalls/savalls.github.io/main/assets/img/nginx_base_localhost.png)



### Agregar HTML personalizado

Ahora crearás una página personalizada, por lo que vincularemos un volumen montado por tí mismo, al directorio en el que NGIX buscará dicho contenido. 

Lo primero es para el contenedor que has creado anteriormente
```bash
$ docker stop web
```
Crea un directorio dentro de _Documents_, nómbralo como __nginx__, y ahora dentro de éste, otro directorio llamado _site-content_.  Por último, agregarás un archivo _index.html_ con el siguiente contenido:

```bash
    <!doctype html>
    <html lang="es">
    <head>
      <meta charset="utf-8">
      <title>Docker NGINX</title>
    </head>
    <body>
      <h2>Hola desde Ciberseguridad</h2>
    </body>
    </html>
```

Ya tienes lista la estructura básica del contenedor, y ahora vincularás esta estructura local al contenedor en ejecución, añadiendo la marca -v, del siguiente modo:

```bash
    docker run --rm -d -p 8080:80 --name web -v ~/Documentos/nginx/site-content:/usr/share/nginx/html nginx
```


![](https://raw.githubusercontent.com/savalls/savalls.github.io/main/assets/img/nginx_hola01.png)



### Crear imagen personalizada

Has visto como adaptar tu contenido local a la imagen del contenedor mediante un comando extenso, y ahora crearás un archivo _Dockerfile_  (dentro del mismo directorio donde has creado la carpeta nginx) donde especificarás esto mismo para que docker construya una imagen.

```bash
FROM nginx:latest
COPY ./site-content/index.html /usr/share/nginx/html/index.html
```

Con esto, sobreescribirá el archivo _index.html_ original que se encuentra en /usr/share/nginx/html/index.html por el nuestro personalizado.

Para construir la imagen personalizada ejecutamos

```bash
$ docker build -t webserver .
```

Con esto, crearemos nuestra imagen en un contenedor que será accesible mediante

```bash
$ docker run --rm -d -p 8080:80 --name web webserver
```



![](https://raw.githubusercontent.com/savalls/savalls.github.io/main/assets/img/docker_run_webserver.png)

