---
layout: post
categories: 
conToc: true
title: Práctica Wordpress
---




# Práctica Wordpress


### Docker Compose

Docker puede construir más de una imagen y trabajar con diversos contenedores interactuando entre ellos.  Para ello haremos uso de la utilidad _docker compose_

El proceso consta de tres pasos:

    1. Definir el entorno de tu aplicación mediante un _Dockerfile_
    2. Definir los servicios que componen la aplicación mediante un archivo _docker-compose.yml_
    3. Ejecutar _docker-compose up_ con lo que se inicia la aplicación.


### Instalación Wordpress

Wordpress requiere el uso de una base datos, que ahora correrá en un contenedor alternativo al del propio Wordpress.

Crea un directorio para albergar el proyecto, dentro de la carpeta Documentos por ejemplo,  e ingresa dentro desde una consola de texto. Una vez dentro crearemos un archivo _docker-compose.yml_

```bash
$ mkdir my_wordpress
$ cd my_wordpress
$ nano docker-compose.yml
```

y copiaremos lo siguiente:
```bash
version: '3.3'
       
services:
   db:
     image: mysql:5.7
     volumes:
       - db_data:/var/lib/mysql
     restart: always
     environment:
       MYSQL_ROOT_PASSWORD: somewordpress
       MYSQL_DATABASE: wordpress
       MYSQL_USER: wordpress
       MYSQL_PASSWORD: wordpress
       
   wordpress:
     depends_on:
       - db
     image: wordpress:latest
     ports:
       - "8000:80"
     restart: always
     environment:
       WORDPRESS_DB_HOST: db:3306
       WORDPRESS_DB_USER: wordpress
       WORDPRESS_DB_PASSWORD: wordpress
       WORDPRESS_DB_NAME: wordpress
volumes:
    db_data: {}
```

Si ananlizas el código verás que antes de proceder a instalar Wordpress como tal, necesita que esté creada la base de datos mysql para alojar los archivos de configuración. 

### Construir el proyecto

Ejecutaremos _docker-compose up -d_ que se encargará de extraer las imágenes necesarias e iniciar los contenedores de base de datos y Wordpress.

![](https://raw.githubusercontent.com/savalls/savalls.github.io/main/assets/img/docker_compose_up_d.png)

 
 
 Y para acceder a la instalación de Wordpress accedes, mediante un navegador, a tu dirección local en el puerto 8000. 
 
![](https://raw.githubusercontent.com/savalls/savalls.github.io/main/assets/img/wordpress_instalacion.png)

 