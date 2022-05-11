---
layout: post
categories: 
conToc: true
title: Tarea ASVS
---



# Tarea ASVS




Instalaremos un container con la imagen de OWASP [ASVS](https://github.com/Santandersecurityresearch/asvs)  instalada en ella, y con la que testaremos la web de nuestro proyecto de empresa.

Realiza un git clone del código proporcionado y muevete a su interior.


```bash
$ git clone https://github.com/Santandersecurityresearch/asvs.git
```
** Por circunstancias, hay que instalar la versión 3.6.1 de Reportlab, por lo que modificaremos la imagen para su ejecución, por lo que debes modificar el archivo _requirements.txt_ para que conste de la siguiente manera.
```bash
django
django-crispy-forms
reportlab==3.6.1
django_otp
djangorestframework-jsonapi
pyyaml
ua-parser
user-agents
requirements-parser
psycopg2-binar
```

A continuación construye la imagen y ejecútala.
```bash
$ docker build -t asvs .  
$ docker run -d -p 8000:8000 asvs
```




Nuestro proyecto de empresa se refiere a..    que concede acceso a la intranet desde la cual realizaremos las gestiones necesarias para…

