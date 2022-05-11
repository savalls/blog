---
layout: post
categories: 
conToc: true
title: Tarea SQL Injection - Laboratorios
---



# Tarea SQL Injection - Laboratorios




### Lab 1.  [Vulnerabilidad de inyección SQL en la cláusula WHERE que permite la recuperación de datos ocultos](https://portswigger.net/web-security/sql-injection/lab-retrieve-hidden-data)


Añadimos 'OR+1=1– al final de la secuencia.   Se puede añadir directamente, o bien mediante el uso de burpsuite, que tiene la comodidad que introduce el formato adecuado. 

![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/lab_01.png?raw=true)





### Lab 2.  [Vulnerabilidad de inyección SQL que permite eludir el inicio de sesión](https://portswigger.net/web-security/sql-injection/lab-login-bypass)


En este caso, vamos a probar algunos nombres de usuario para validarnos.  Introducimos en la caja de texto el nombre junto con el comentario, y una secuencia aleatoria en la caja de texto de la contraseña.    ___administrator'-- : asdfas___

![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/lab_02A.png?raw=true)




![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/lab_02B.png?raw=true)



### Lab 3.  [Ataque UNION de inyección SQL, determinando el número de columnas devueltas por la consulta](https://portswigger.net/web-security/sql-injection/union-attacks/lab-determine-number-of-columns)


Para averiguar el número de columnas hay que añadir la secuéncia '+UNION+SELECT+ seguida de tantos NULL, como columnas tenga la tabla.  No olvides incluir el comentario – tras el último NULL.     ___+UNION+SELECT+NULL,NULL,NULL--___


![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/lab_03.png?raw=true)



### Lab 4.  [Averigua la versión de la base de datos mediante un ataque de UNION](https://portswigger.net/web-security/sql-injection/examining-the-database/lab-querying-database-version-oracle)

En este laboratorio, hay que ir probando qué secuencia es la que reconoce el servidor y devuelve un código de respuesta 200.

![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/lab_04A.png?raw=true)

Para ello, elige antes una categoría de la página web e inyecta el código a continuación junto al comentario final.

___+UNION+SELECT+BANNER,+NULL+FROM+v$version___


![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/lab_04B.png?raw=true)
