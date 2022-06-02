---
layout: post
categories: 
conToc: true
title: Tarea DIVA
---



# Tarea DIVA





En esta tarea crackearemos una App vulnerable de android.  En este link podrás descargar un ejemplo de apk llamada [DIVA](http://www.payatu.com/wp-content/uploads/2016/01/diva-beta.tar.gz) .  Para ello, instalaremos en nuestro pc el programa [android studio](https://developer.android.com/studio?hl=es) desde su página web, después de haber aceptado la licencia de uso.

Iremos siguiendo los pasos descritos en los contenidos del curso relativos a la [Ingeniería inversa en Android](https://victorponz.github.io/Ciberseguridad-PePS/tema6/seguridad/m%C3%B3vil/2022/03/01/Ingenieria-inversa.html) 


Ejecutamos la aplicación modificada por nosotros en AndroidStudio.



![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_001.png?raw=true)

Y con la actividad del movil en el mulador, iremos desgranando los 13 retos descritos en [Cracking Damn Insecur and Vulnerable App (DIVA)](https://resources.infosecinstitute.com/topic/cracking-damn-insecure-and-vulnerable-app-diva-part-5/)

### Challenge 1

Ejecutamos en la pantalla el punto 1 INSECURE LOGGING
Después en una consola de texto en nuestro equipo ejecutamos
```bash
$ adb logcat
```

Cuando cliquemos cualquier numero en la pantalla del movil, lo podremos ver en la información que aparece en nuestra consola.

![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_002.png?raw=true)


Observamos la secuencia introducida en la pantalla..
![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_003.png?raw=true)


Si vamos a revisar la clase _LogActivity.class_ correspondiente con el programa jd-gui (java-decompiler) veremos la sentencia que lo permite.
![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_004.png?raw=true)


### Challenge 2

Escribiremos lo que queremos en la caja de texto del movil

![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_005.png?raw=true)

Ahora vamos a ver la clase _HardcodeActivity.class_ 

![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_006.png?raw=true)

Vemos el resultado de lo que hemos escrito en pantalla.


### Challenge 3

![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_007.png?raw=true)


Ahora conectaremos nuestra consola mediante __adb root__  y vamos buscando el directorio donde está la aplicación
```bash
$ adb root shell
generic_x86:/ # cd /data/data
generic_x86:/data/data # ls -l | grep 'diva'
drwxr-x--x  6 u0_a122        u0_a122        4096 2022-05-24 17:36 jakhar.aseem.diva
generic_x86:/data/data #
```

Y entramos en la app diva y navegamos hasta el directorio donde está shared_prefs
```bash
generic_x86:/data/data # cd jakhar.aseem.diva/ 
generic_x86:/data/data/jakhar.aseem.diva # 

generic_x86:/data/data/jakhar.aseem.diva # ls
cache  code_cache  databases  lib  shared_prefs
generic_x86:/data/data/jakhar.aseem.diva # cache
/system/bin/sh: cache: inaccessible or not found
127|generic_x86:/data/data/jakhar.aseem.diva # ls
cache  code_cache  databases  lib  shared_prefs
generic_x86:/data/data/jakhar.aseem.diva # cd shared_prefs/                                                                            
generic_x86:/data/data/jakhar.aseem.diva/shared_prefs # ls
jakhar.aseem.diva_preferences.xml
generic_x86:/data/data/jakhar.aseem.diva/shared_prefs #
```
Ahora hacemos cat sobre jakhar.aseem.dive_preferences.xml

![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_009.png?raw=true)


### Challenge 4

Introducimos credenciales en la caja de texto y gravamos.

![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_010.png?raw=true)


Nos dirigimos a ver la clase __InsecureDataStorage2Activity.class__ mediante JD-GUI

![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_011.png?raw=true)


Ahora vamos a la consola con ___adb___  y realizamos un "___adb pull___" sobre las bases de datos que estan en /data/data/jakhar.aseem.diva/databases/ids2
```bash
$ adb pull /data/data/jakhar.aseem.diva/databases/ids2
```

![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_012.png?raw=true)

```bash
$ file ids2 
ids2: SQLite 3.x database, last written using SQLite version 3028000
```

Y abrimos con sqlite3

![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_013png.png?raw=true)




### Challenge 5




![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_014.png?raw=true)




Realizamos un adb root shell
```bash

$ adb shell
generic_x86:/ # cd data/data/jakhar.aseem.diva     
generic_x86:/data/data/jakhar.aseem.diva # ls
cache  code_cache  databases  lib  shared_prefs  uinfo3206885863351116265tmp
generic_x86:/data/data/jakhar.aseem.diva #
```

Observamos que hay un archivo  _uinfo3206885863351116265tmp_

Hacemos un cat sobre el, y veremos las credenciales guardadas en texto plano…

![](https://raw.githubusercontent.com/savalls/savalls.github.io/main/assets/img/2022-05-31_diva_015.png)




### Challenge 6

![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_016.png?raw=true)


Si abrimos la clase _InsecureDataStorage4Activity.class_ con JD-GUI, observamos que hay un archivo .uinfo.txt

![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_017.png?raw=true)


Ahora con adb root nos dirigiremos a /mnt/sdcard y lo veremos con un cat…

```bash
$ adb shell
\# cd /mnt/sdcard
\# cat .uinfo.txt
```
Y aquí tenemos el texto

usuario6:passw6



### Challenge 7




![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_018.png?raw=true)

Buscaremos un usuario sin conocer la tabla de usuarios..

escribiremos en la caja de texto ___1'or'1'!='2'___ para comprobar si existe una vulnerabilidad, e intentaremos un inyección de código SQL



![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_019.png?raw=true)



### Challenge 8


Abriremos un navegador en el teléfono e intentaremos abrir un archivo que se encuentre en su almacenamiento interno.


![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_20.png?raw=true)




Podemos introducir una cadena de búsqueda mediante adb shell

```bash
adb shell input text file:///data/data/jakhar.aseem.diva/shared_prefs/jakhar.aseem.diva_preferences.xml


```

![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_21.png?raw=true)

y aceptamos en la terminal

|  ![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_22.png?raw=true) | ![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_23.png?raw=true)  |











### Challenge 9





|   ![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_24.png?raw=true)  |  ![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_25.png?raw=true)  |


Ahora vamos a acceder a las credenciales, pero sin accionar el botón, y lo haremos mediante la terminal

```bash
$ adb shell am start jakhar.aseem.diva/.APICredsActivity
```
![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_26.png?raw=true)



![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_27.png?raw=true)


### Challenge 10


![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_28.png?raw=true)


Mediante la shell introduciremos una secuencia para acceder a las credenciales



![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_29.png?raw=true)

Entonces se abre la pantalla para introducir

![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_30.png?raw=true)


Muestra la pantalla como si huibiera enviado un pin, por lo que ahora revisaremos parte del codigo de ___strigs.xml___ y buscaremos el parámetro _chk_pin_ 
El archivo ___strings.xml___ se encuentra en /[app](https://github.com/payatu/diva-android/tree/master/app)/[src](https://github.com/payatu/diva-android/tree/master/app/src)/[main](https://github.com/payatu/diva-android/tree/master/app/src/main)/[res](https://github.com/payatu/diva-android/tree/master/app/src/main/res)/[values](https://github.com/payatu/diva-android/tree/master/app/src/main/res/values)/strings.xml

Después, en la clase ___AccessControl2Activity.java___ verificaremos el valor de _check_pin_ (V | F) para comprobar que el usuario se encuentra registrado o no..

```bash
$ adb shell am start -n jakhar.aseem.diva/.APICreds2Activity -a jakhar.aseem.diva.action.VIEW_CREDS2
```

![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-05-31_diva_31.png?raw=true)


*El challenge 10 y 11 de momento los damos por concluidos… seguimos con el 12

### Challenge 12


En este reto encontraremos el proveedor de la llave y remitirlo..

Para ello, desde jd-gui, entraremos en la clase _Hardcode2Activity.class_ y encontramos que se está intentado crear una instancia del objeto ___DivaJni()___

![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-06-02_diva_32.png?raw=true)


Descomprimimos la aplicación ___diva-beta.apk___ y examinamos sus archivos
```bash
$ unzip diva-beta.apk
```

![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-06-02_diva_33.png?raw=true)


Nos movemos a la carpeta ___lib___ y después dentro de la arquitectura de tu máquina, que en nuestro caso es ___x86_64___ listamos el contenido.  De entre todos los archivos se encuentra ___libdivajni.so___ por lo que lo examinaremos con el comando _strings_
```bash
$ unzip divaModificada.apk > divaModificada
cd divaModificada/lib/x86_64
$ ls
$ libdivajni.so
$ strings libdivajni.so
```


![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-06-02_diva_34.png?raw=true)


![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-06-02_diva_35.png?raw=true)


### Challenge 13

![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-06-02_diva_36.png?raw=true)

Si pulsamos una combinación incorrecta, deniega el acceso, hasta que pulsamos 20A seguidas, que cerrará la aplicación..

Exploramos el logcat, ejecutando _adb logcat_ en una consola  de texto

Si accedemos al código fuente del componente [divajni.c ](https://github.com/payatu/diva-android/blob/master/app/src/main/jni/divajni.c) observaremos que el límite de longitud establecido está en 20 caracteres.


![](https://github.com/savalls/savalls.github.io/blob/main/assets/img/2022-06-02_diva_37.png?raw=true)
