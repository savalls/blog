---
layout: post
categories: 
conToc: true
title: Tarea ASVS
---



# Tarea ASVS



 El Estándar de Verificación de Seguridad en Aplicaciones ([ASVS](https://owasp.org/www-project-application-security-verification-standard/) por sus siglas en inglés), de [OWASP](https://owasp.org/),  es una lista de requisitos o pruebas de seguridad en aplicaciones que puede ser utilizado por arquitectos, desarrolladores,  probadores, profesionales de la seguridad,   proveedores de herramientas y consumidores para definir,  construir, probar y verificar aplicaciones seguras.
  
 ASVS define tres niveles de verificación para la seguridad, incrementando su profundidad en cada nivel. 

* __Nivel 1__ es para todo el software.
*  __Nivel 2__ es para las aplicaciones conteniendo datos sensibles, los cuales requieren protección.
*  __Nivel 3__ es para las aplicaciones más críticas, aplicaciones realizando transacciones de alto valor, conteniendo datos médicos sensibles, o cualquier aplicación el cual requiera un alto nivel de confianza.

Nuestra empresa ficticia se refiere a un fabricante de envases, embalajes y derivados del cartón ondulado que concede acceso a intranet, mediante zona de clientes, y  desde la cual se realizan gestiones necesarias en cuanto a diseños de productos, estado de pedidos, etc..

El nivel asociado al proyecto es de grado 2.

Apunta alguna de las medidas de cada apartado general que te parezcan más importantes para el cumplimiento de las normas de [ASVS](https://owasp.org/www-project-application-security-verification-standard/).


# V1 Arquitectura, Diseño y Modelado de Amenazas

|     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- |
| **1.14.6** | Verifique que la aplicación no utiliza tecnologías del lado cliente no compatibles, inseguras o en desuso, como NSAPI plugins, Flash, Shockwave, ActiveX, Silverlight, NACL o client-side java applets. |     | ✓   | ✓   | 477 |


# V2 Autenticación

| **2.2.1** | Verifique que los controles anti-automatización son efectivos para mitigar las pruebas de credenciales filtradas, fuerza bruta y ataques de bloqueo de cuentas. Estos controles incluyen el bloqueo de las contraseñas filtradas más comunes, bloqueos suaves, limitación de velocidad, CAPTCHA, retrasos cada vez mayores entre intentos, restricciones de direcciones IP o restricciones basadas en riesgos, como la ubicación, el primer inicio de sesión en un dispositivo, los intentos recientes de desbloquear la cuenta o similares. Verifique que no sea posible realizar más de 100 intentos fallidos por hora en una sola cuenta. | ✓ | ✓ | ✓ | 307 | 5.2.2 / 5.1.1.2 / 5.1.4.2 / 5.1.5.2 |
|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|---|---|-----|-------------------------------------|


# V3 Gestión de sesiones

|           |                                                                                                                                                                                                                                                                                                                                                     |  |   |   |     |  |
|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--|---|---|-----|--|
| **3.3.3** | Verifique que la aplicación ofrece la opción de terminar todas las demás sesiones activas después de un cambio de contraseña correcto (incluido el cambio mediante el restablecimiento/recuperación de contraseña), y que esto es efectivo en toda la aplicación, el inicio de sesión federado (si está presente) y cualquier usuario de confianza. |  | ✓ | ✓ | 613 |  |


# V4 Control de Acceso

|     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- |
| **4.2.1** | Verifique que los datos confidenciales y las API están protegidos contra ataques de referencia insegura directa de objetos (IDOR; por sus siglas en inglés) dirigidos a la creación, lectura, actualización y eliminación de registros, como la creación o actualización del registro de otra persona, la visualización de los registros de todos o la eliminación de todos los registros. | ✓   | ✓   | ✓   | 639 |


# V5 Validación, Desinfección y Codificación

|     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- |
| **5.1.5** | Verifique que las redirecciones y reenvíos de URL solo permiten destinos que aparecen en una lista de permitidos, o muestra una advertencia al redirigir a contenido potencialmente no confiable. | ✓   | ✓   | ✓   | 601 |


# V6 Criptografía almacenada

|     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- |
| **6.2.8** | Verifique que todas las operaciones criptográficas son de tiempo constante, sin operaciones de "cortocircuito" en comparaciones, cálculos o devoluciones, para evitar fugas de información. |     |     | ✓   | 385 |


# V7 Manejo y Registro de Errores

| **7.2.2** | Verifique que se pueden registrar todas las decisiones de control de acceso y que se registran todas las decisiones erróneas. Esto debe incluir solicitudes con los metadatos pertinentes necesarios para las investigaciones de seguridad. |  | ✓ | ✓ | 285 |
|-----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--|---|---|-----|


# V8 Protección de Datos

|     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- |
| **8.1.5** | Verifique que se realizan copias de seguridad periódicas de datos importantes y que se realizan pruebas de la restauración de datos. |     |     | ✓   | 19  |


# V9 Comunicación

|     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- |
| **9.2.1** | Verifique que las conexiones hacia y desde el servidor utilizan certificados TLS de confianza. Cuando se utilizan certificados generados internamente o autofirmados, el servidor debe configurarse para que solo confíe en las CA internas específicas y en los certificados autofirmados específicos. Todos los demás deben ser rechazados. |     | ✓   | ✓   | 295 |


# V10 Código Malicioso

|     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- |
| **10.1.1** | Verifique que se está utilizando una herramienta de análisis de código que puede detectar código potencialmente malintencionado, como funciones de tiempo, operaciones de archivos no seguras y conexiones de red. |     |     | ✓   | 749 |


# V11 Lógica de Negocio

|     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- |
| **11.1.1** | Verificar que la aplicación solo procesará flujos de la lógica de negocio para el mismo usuario en orden de pasos secuenciales y sin omitir pasos. | ✓   | ✓   | ✓   | 841 |


# V12 Archivos y Recursos

|     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- |
| **12.1.2** | Verifique que la aplicación compruebe los archivos comprimidos (p. ej. zip, gz, docx, odt) contra el tamaño máximo sin comprimir permitido y con el número máximo de archivos antes de descomprimir el archivo. |     | ✓   | ✓   | 409 |


# V13 API y Servicios Web

|     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- |
| **13.1.3** | Verifique que las direcciones URL de la API no exponen información confidencial, como API keys, los tokens de sesión, etc. | ✓   | ✓   | ✓   | 598 |


## V14.1 Compilación y Despliegue

|     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- |
| **14.1.3** | Verifique que la configuración del servidor está hardenizada según las recomendaciones del servidor de aplicaciones y los framewors en uso. |     | ✓   | ✓   | 16  |


[Fuente](https://github.com/OWASP/ASVS/tree/v4.0.3/4.0/es)
