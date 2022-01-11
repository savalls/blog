---
layout: post
categories: 
conToc: true
title: Practica Dockerhub
---




# Práctica Dockerhub

En esta práctica aprenderás a crear imágenes de tus containers y a subirlos a un repositorio para que las tengas siempre disponibles.

El primer paso será crear una cuenta en [Dockerhub](https://hub.docker.com/), y posteriormente te logueas en

![2021-12-15_dockerhub_portada.png](../assets/img/2021-12-15_dockerhub_portada.png)


Ahora desde una consola de texto te logueas dentro de la cuenta que acabas de crear
```bash
$ docker login
```

Seguídamente tendrás que preparar la nomenclatura de la imagen que vas a subir, de la siguiente manera **nombre\_de\_usuario/nombre\_del\_repositorio:etiqueta** y generas un tag de la imagen referida para nombrarla.

```bash
docker tag counterx savalls/counterx:v1
```