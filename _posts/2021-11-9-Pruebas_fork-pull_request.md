---
typora-copy-images-to: ../assets/img
typora-root-url: ../../
layout: post
categories: 
conToc: true
title: Pruebas Fork - pull request
---

# Pruebas Fork - pull request



## Fork de un proyecto

Como sabes, en Git se trabaja siempre en local, con la copia del  repositorio en nuestro ordenador. Fíjate que el repositorio que tienes  en local no debe ser un clon de aquel con el que deseas contribuir, sino un fork propio. 



Puedes hacer un Fork desde la propia página de GitHub, entrando en un  repositorio y pulsando el botón "Fork", arriba a la derecha.  Inmediatamente se creará en tu cuenta de GitHub un nuevo repositorio, el fork, que es la copia de estado actual del repositorio original. Podrás ver la información del repositorio, identificando que es un fork, en un área arriba de la página.



Hola Santi que tal estas ? <!--  -->

El github funciona.



En tu fork se supone que habrás realizado diversos cambios en el código, en uno o más ficheros. Tendrás entonces que hacer el commit para  enviarlos a tu copia del repositorio en local.

Nota: Ya debes conocer la operación commit, si no, mira en el artículo [Primer commit](https://desarrolloweb.com/articulos/iniciar-repositorio-git-primer-commit.html) del Manual de Git.

Luego tendrás que enviar esos cambios a tu propio repositorio, el fork,  publicado en GitHub. Eso lo consigues con el comando git push, indicando el repo al que quieres enviar los cambios y la rama donde enviarlos.

