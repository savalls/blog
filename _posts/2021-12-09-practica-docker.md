---
layout: post
categories: 
conToc: true
title: Practica Docker
---




# Práctica Docker

Para ejecutar ésta práctica, clonaremos el directorio remoto   [https://github.com/victorponz/docker/tree/master/P1](https://github.com/victorponz/docker/tree/master/P1)  a una carpeta de nuestro equipo y podremos examinar los diferentes archivos _.sh_ que se compone, y que determinarán la ejecución de la misma.

Antes de esto, nos aseguraremos que tenenos instalado _docker.io_ en nuestro equipo, por lo que instalaremos _docker_

```bash
$ sudo apt install docker.io -y
```

Una vez instalado,  nuestro usuario debe pertenecer al grupo _docker_ para poder ejecutar comandos sin recurrir al usuario root, dado que podría suponer un problema de vulnerabilidad grave, por lo que que añades a tu _usuario_ en el grupo __docker__.

```bash
$ sudo adduser usuario docker
```

 
- [ ] Ahora ya es hora de volver al directorio donde has alojado el directorio _P1_.  Si observas el _Dockerfile_ comprobarás que partirá de una imagen de _debian_, que construirá la imagen si no encuentra la imagen previamente.
```bash
# we will inherit from  the Debian image on DockerHub
FROM debian
```

- [ ] En el siguiente paso, configurará la zona horaria que le hemos indicado, _Europe/Madrid_.
 ```bash
# set timezone so files' timestamps are correct
ENV TZ=Europe/Madrid     
```    

- [ ] Actualizará los repositorios e instalará Apache y PHP 7.4
```bash
# install apache and php 7.4
# we include procps and telnet so you can use these with shell.sh prompt
RUN apt-get update -qq >/dev/null && apt-get install -y -qq procps telnet apache2 php7.4 -qq >/dev/null
```

- [ ] Creará la infraestructura de archivos necesaria para alojar los contenidos de la web " . " en _/var/www/html_ y escribirá su estado en _/data_.  Para ello, estableceremos los permisos necesarios a _www-data_.
```bash
# HTML server directory
WORKDIR /var/www/html
COPY . /var/www/html/


# The PHP app is going to save its state in /data so we make a /data inside the container
RUN mkdir /data && chown -R www-data /data && chmod 755 /data & chmod 775 -R /var/www/html/

# we need custom php configuration file to enable userdirs
COPY php.conf /etc/apache2/mods-available/php7.4.conf

```

- [ ] Finalmente, se registrará el _virtualhost_, y saldrá a una consola de texto.
```bash
# enable userdir and php
RUN a2enmod php7.4

# we run a script to stat the server; the array syntax makes it so ^C will work as we want
CMD  ["./entrypoint.sh"]
```

