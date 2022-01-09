---
typora-copy-images-to: ../assets/img/DIRECTORIO
typora-root-url: ../
layout: post
categories: 
conToc: true
title: Probando el Fork
---

# Probando el Fork 

Una ramificación es una copia de un repositorio. Bifurcar un repositorio te permite experimentar libremente con cambios sin afectar el proyecto  original.

## Acerca de las bifurcaciones

Casi siempre las bifurcaciones se usan para proponer cambios al  proyecto de otra persona o para usar el proyecto de otra persona como  inicio de tu propia idea. Puedes bifurcar un repositorio para crear una  copia del mismo y hacer cambios sin afectar al repositorio ascendente.  Para obtener más información, consulta la sección "[Trabajar con las bifurcaciones](https://docs.github.com/es/github/collaborating-with-issues-and-pull-requests/working-with-forks)".

### 

### Proponer cambios para el proyecto de otra persona

Por ejemplo, puedes utilizar ramificaciones para proponer cambios  relacionados con arreglar un error. En lugar de registrar una propuesta  para un error que has encontrado, puedes hacer lo siguiente:

- Bifurcar el repositorio.
- Solucionar el problema.
- Emitir solicitudes de cambios al propietario del proyecto.

### 

### Usar el proyecto de otra persona como inicio de tu propia idea

El software de código abierto se basa en la idea de que, si  compartimos el código, podemos crear software más confiable y mejor.  Para obtener más información, consulta la sección "[Acerca de la Iniciativa de Código Abierto](http://opensource.org/about)" en la Iniciativa de Código Abierto.

Para obtener más información acerca de aplicar los principios de  código abierto al trabajo de desarrollo de tu organización en  GitHub.com, consulta la documentación técnica de GitHub "[Introducción al innersource](https://resources.github.com/whitepapers/introduction-to-innersource/)".

Cuando creas tu repositorio público desde una ramificación del  proyecto de alguien más, asegúrate de incluir el archivo de licencia que determine cómo quieres que se comparta tu proyecto con los demás. Para  obtener más información, consulta la sección "[Elegir una licencia de código abierto](https://choosealicense.com/)" en choosealicense.com.

Para obtener más información acerca del código abierto,  específicamente sobre cómo crear y hacer crecer un proyecto de código  abierto, hemos creado las [Guías de Código Abierto](https://opensource.guide/) que te ayudarán fomentar una comunidad saludable mediante la  recomendación de mejores prácticas para crear y mantener repositorios  para tus proyectos de código abierto.También puedes tomar un curso  gratuito de [Laboratorio de aprendizaje de GitHub](https://lab.github.com/) sobre cómo mantener comunidades de código abierto.



Puedes ramificar un proyecto para proponer cambios en los  repositorios precedentes u originales. En este caso, es una buena  práctica sincronizar tu bifurcación periódicamente con el repositorio  ascendente. Para hacerlo, deberás usar Git en la línea de comando.  Puedes practicar cómo configurar el repositorio precedente utilizando el mismo repositorio [octocat/Spoon-Knife](https://github.com/octocat/Spoon-Knife) que acabas de ramificar.

1. On GitHub.com, navigate to the [octocat/Spoon-Knife](https://github.com/octocat/Spoon-Knife) repository.
2. En el ángulo superior derecho de la página, haz clic en **Bifurcar**. ![Botón Bifurcar](https://docs.github.com/assets/images/help/repository/fork_button.jpg "Botón Bifurcar")

## 

## Clonar tu repositorio bifurcado

Ahora mismo, tienes una bifurcación del repositorio Spoon-Knife, pero no tienes los archivos de ese repositorio localmente en tu computadora.

​    [Web browser](https://docs.github.com/es/get-started/quickstart/fork-a-repo#)    [GitHub CLI](https://docs.github.com/es/get-started/quickstart/fork-a-repo#)        [Desktop](https://docs.github.com/es/get-started/quickstart/fork-a-repo#)          

1. On GitHub.com, navigate to **your fork** of the Spoon-Knife repository.
2. Sobre la lista de archivos, da clic en 

 **Código**. ![Botón de "Código"](https://docs.github.com/assets/images/help/repository/code-button.png)

Para clonar el repositorio utilizando HTTPS, debajo de "Clonar con HTTPS", da clic en

. To clone the repository using an SSH key, including a certificate  issued by your organization's SSH certificate authority, click **Use SSH**, then click . To clone a repository using CLI de GitHub, click **Use CLI de GitHub**, then click 

. ![El icono de portapapeles para copiar la URL para clonar un repositorio](https://docs.github.com/assets/images/help/repository/https-url-clone.png)

  ![El icono del portapapeles para copiar la URL para clonar un repositorio con el CLI de GitHub](https://docs.github.com/assets/images/help/repository/https-url-clone-cli.png)

Abre la Terminal.

Cambia el directorio de trabajo actual a la ubicación en donde quieres clonar el directorio.

Escribe `git clone`, y luego pega la URL que copiaste antes. Se verá así, con tu nombre de usuario de GitHub en lugar de `YOUR-USERNAME`:

```shell
$ git clone https://github.com/YOUR-USERNAME/Spoon-Knife
```

Presiona **Enter** (Intro). Se creará tu clon local.

```shell
$ git clone https://github.com/YOUR-USERNAME/Spoon-Knife
> Cloning into `Spoon-Knife`...
> remote: Counting objects: 10, done.
> remote: Compressing objects: 100% (8/8), done.
> remove: Total 10 (delta 1), reused 10 (delta 1)
> Unpacking objects: 100% (10/10), done.
```

