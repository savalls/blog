---
layout: post
categories: 
conToc: true
title: Tarea MASVS
---



# Tarea MASVS



 El Estándar de Verificación de Seguridad en Aplicaciones Móviles [M[ASVS](https://owasp.org/www-project-application-security-verification-standard/)](https://github.com/OWASP/owasp-masvs/releases) por sus siglas en inglés), de [OWASP](https://owasp.org/),  es una lista de requisitos o pruebas de seguridad en aplicaciones móviles que puede ser utilizado por arquitectos, desarrolladores,  probadores, profesionales de la seguridad,   proveedores de herramientas y consumidores para definir,  construir, probar y verificar aplicaciones seguras.
  
 MASVS és el homólogo de ASVS (para aplicaciones web), pero para aplicaciones móviles y define también tres niveles de verificación para la seguridad, incrementando su profundidad en cada nivel. 

* __Nivel 1__ es para todo el software.
*  __Nivel 2__ es para las aplicaciones conteniendo datos sensibles, los cuales requieren protección.
*  __Nivel 3__ es para las aplicaciones más críticas, aplicaciones realizando transacciones de alto valor, conteniendo datos médicos sensibles, o cualquier aplicación el cual requiera un alto nivel de confianza.

Nuestra empresa ficticia se refiere a un fabricante de envases, embalajes y derivados del cartón ondulado que permite compras mediante la aplicación para teléfonos móviles y realizan gestiones necesarias en cuanto a diseños de productos, estado de pedidos, etc.. a los clientes de la empresa.

El nivel asociado al proyecto es de grado 2.

Apunta alguna de las medidas de cada apartado general que te parezcan más importantes para el cumplimiento de las normas de [ASVS](https://owasp.org/www-project-application-security-verification-standard/).

---
# [V1: Requisitos de Arquitectura, Diseño y Modelado de Amenazas](https://github.com/OWASP/owasp-masvs/blob/master/Document-es/0x06-V1-Architecture_design_and_threat_modelling_requireme.md#v1-requisitos-de-arquitectura-dise%C3%B1o-y-modelado-de-amenazas)

En un mundo perfecto, la seguridad sería considerada en todas las fases del desarrollo. Sin embargo, en la realidad, la seguridad es a menudo sólo considerada en una etapa tardía del desarrollo del software. Además de los controles técnicos, el MASVS requiere que existan procesos que garanticen que la seguridad se ha abordado explícitamente al planificar la arquitectura de la aplicación móvil, y que se conocen los roles funcionales y de seguridad de todos los componentes. Dado que la mayoría de las aplicaciones móviles actúan como clientes de los servicios remotos, debe garantizarse que también se apliquen las medidas de seguridad adecuadas a dichos servicios, no basta con probar la aplicación móvil de forma aislada.

La categoría V1 lista los requerimientos pertinentes a la arquitectura y al diseño de la aplicación. Debido a esto es la única categoría que no se corresponde con casos de test de la Guía de Pruebas Móviles de OWASP. Para cubrir temas tales como el modelado de amenazas, SDLC seguro, gestión de claves, los usuarios del MASVS deben consultar los respectivos proyectos de OWASP y/u otros estándares como los que se encuentran enlazados a debajo.


  | #       | MSTG-ID     | Descripción                                                                                                                      | L1 | L2 |
|---------|-------------|----------------------------------------------------------------------------------------------------------------------------------|----|----|
| **1.3** | MSTG-ARCH-3 | Se definió una arquitectura de alto nivel para la aplicación y los servicios y se incluyeron controles de seguridad en la misma. | x  | x  |
| **1.4** | MSTG-ARCH-4 | Se identificó claramente la información considerada sensible en el contexto de la aplicación móvil.                              | x  | x  |



—
# [V2: Requerimientos de Almacenamiento de datos y Privacidad](https://github.com/OWASP/owasp-masvs/blob/master/Document-es/0x07-V2-Data_Storage_and_Privacy_requirements.md)

La protección de datos sensibles, como las credenciales del usuario y la información privada, es un aspecto clave de la seguridad móvil. En primer lugar, los datos confidenciales pueden exponerse involuntariamente a otras aplicaciones que se ejecutan en el mismo dispositivo si se utilizan de forma inadecuada mecanismos de comunicación entre procesos del sistema operativo. Los datos también pueden filtrarse involuntariamente en el almacenamiento en la nube, las copias de seguridad o la caché del teclado. Además, los dispositivos móviles pueden perderse o robarse más fácilmente que otros tipos de dispositivos, por lo que un adversario que obtiene acceso físico al mismo es un escenario más probable. En ese caso, se pueden implementar protecciones adicionales para dificultar la recuperación de los datos sensibles.

El MASVS se centra en las aplicaciones y por esto no cubre políticas para el dispositivo como Mobile Device Managment (MDM) ([https://gsuite.google.com/products/admin/mobile/](https://gsuite.google.com/products/admin/mobile/)) o Enter (EDM). Igualmente se recomienda utilizar estas soluciones en contextos empresariales.


| #       | MSTG-ID        | Descripción                                                                                  | L1 | L2 |
|---------|----------------|----------------------------------------------------------------------------------------------|----|----|
| **2.5** | MSTG-STORAGE-5 | Se desactiva la caché del teclado en los campos de texto que contienen información sensible. | x  | x  |
| **2.6** | MSTG-STORAGE-6 | No se expone información sensible mediante mecanismos de comunicación entre procesos (IPC).  | x  | x  |

---
# [V3: Requerimientos de Criptografía](https://github.com/OWASP/owasp-masvs/blob/master/Document-es/0x08-V3-Cryptography_Verification_Requirements.md)

La criptografía es un componente esencial a la hora de proteger los datos almacenados en un dispositivo móvil. También es una categoría en la que las cosas pueden ir terriblemente mal, especialmente cuando no se siguen las convenciones estándar. El propósito de estos controles es asegurarse de que la aplicación utiliza criptografía siguiendo las mejores prácticas de la industria, incluyendo:

* Uso de librerías criptográficas reconocidas y probadas;
* Configuración y elección apropiada de primitivas criptográficas;
* Uso de generadores de números aleatorios suficientemente seguros.

| #       | MSTG-ID       | Descripción                                                                                                                            | L1 | L2 |
|---------|---------------|----------------------------------------------------------------------------------------------------------------------------------------|----|----|
| **3.1** | MSTG-CRYPTO-1 | La aplicación no depende únicamente de criptografía simétrica cuyas claves se encuentran directamente en el código fuente de la misma. | x  | x  |
| **3.2** | MSTG-CRYPTO-2 | La aplicación utiliza implementaciones de criptografía probadas.                                                                       | x  | x  |



---
# [V4: Requerimientos de Autenticación y Manejo de Sesiones](https://github.com/OWASP/owasp-masvs/blob/master/Document-es/0x09-V4-Authentication_and_Session_Management_Requirements.md)

En la mayoría de los casos, una parte esencial de la arquitectura global de aplicaciones móviles es que los usuarios deben inician sesión en un servicio remoto. Aunque la mayor parte de la lógica ocurre en el servidor, MASVS define algunos requerimientos básicos sobre como manejar las cuentas y sesiones del usuario.

| #       | MSTG-ID     | Descripción                                                                                                            | L1 | L2 |
|---------|-------------|------------------------------------------------------------------------------------------------------------------------|----|----|
| **4.6** | MSTG-AUTH-6 | El servidor implementa mecanismos, cuando credenciales de autenticación son ingresadas una cantidad excesiva de veces. | x  | x  |
| **4.7** | MSTG-AUTH-7 | Las sesiones y los tokens de acceso expiran luego de un tiempo predefinido de inactividad.                             | x  | x  |


---
# [V5: Requerimientos de Comunicación a través de la red](https://github.com/OWASP/owasp-masvs/blob/master/Document-es/0x10-V5-Network_communication_requirements.md)

Los controles enumerados en esta categoría tienen por objetivo asegurar la confidencialidad e integridad de la información intercambiada entre la aplicación móvil y los servicios del servidor. Como mínimo se deben utilizar canales seguros y cifrados utilizando el protocolo TLS con las configuraciones apropiadas. En el nivel 2 se establecen medidas en profundidad como fijación de certificados SSL.

| #       | MSTG-ID        | Descripción                                                                                                                                                                                                 | L1 | L2 |
|---------|----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----|----|
| **5.1** | MSTG-NETWORK-1 | La información es enviada cifrada utilizando TLS. El canal seguro es usado consistentemente en la aplicación.                                                                                               | x  | x  |
| **5.2** | MSTG-NETWORK-2 | Las configuraciones del protocolo TLS siguen las mejores prácticas de la industria, o lo hacen lo mejor posible en caso de que el sistema operativo del dispositivo no soporte los estándares recomendados. | x  | x  |



---
# [V6: Requerimientos de Interacción con la Plataforma](https://github.com/OWASP/owasp-masvs/blob/master/Document-es/0x11-V6-Interaction_with_the_environment.md)

Estos controles revisan que se utilicen las APIs de la plataforma y componentes estándar de una manera segura. Además, se cubre la comunicación entre aplicaciones (IPC).

| #       | MSTG-ID         | Descripción                                                                                                                                                      | L1 | L2 |
|---------|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|----|----|
| **6.6** | MSTG-PLATFORM-6 | Las WebViews se configuran para permitir el mínimo de los esquemas (idealmente, sólo https). Esquemas peligrosos como file, tel y app-id están deshabilitados.   | x  | x  |
| **6.7** | MSTG-PLATFORM-7 | Si objetos nativos son expuestos en WebViews, debe verificarse que cualquier componente JavaScript se carga exclusivamente desde el contenedor de la aplicación. | x  | x  |



---
# [V7: Requerimientos de Calidad de Código y Configuración del Compilador](https://github.com/OWASP/owasp-masvs/blob/master/Document-es/0x12-V7-Code_quality_and_build_setting_requirements.md)

Estos controles buscan asegurar que se siguieron las prácticas de seguridad básicas en el desarrollo de la aplicación. Y que se activaron las funcionalidades "gratuitas" ofrecidas por el compilador.

| #       | MSTG-ID     | Descripción                                                                                                       | L1 | L2 |
|---------|-------------|-------------------------------------------------------------------------------------------------------------------|----|----|
| **7.5** | MSTG-CODE-5 | Todos los componentes de terceros se encuentran identificados y revisados en cuanto a vulnerabilidades conocidas. | x  | x  |
| **7.6** | MSTG-CODE-6 | La aplicación captura y gestiona debidamente las posibles excepciones.                                            | x  | x  |



---
# [V8: Requerimientos de Resistencia ante la Ingeniería Inversa](https://github.com/OWASP/owasp-masvs/blob/master/Document-es/0x15-V8-Resiliency_Against_Reverse_Engineering_Requirements.md)

En esta sección se cubren protecciones recomendadas para aplicaciones que maneja o brindan acceso a información o funcionalidades sensibles. La falta de estos controles no generan vulnerabilidades - sino que, están pensados para incrementar la resistencia contra la ingeniería inversa de la aplicación, dificultándole al adversario el acceso a los datos o el entendimiento del modo de ejecución de la aplicación.

Los controles de esta sección deben aplicarse según sea necesario, basándose en una evaluación de los riesgos causados por la manipulación no autorizada de la aplicación y/o la ingeniería inversa del código. Sugerimos consultar el documento de OWASP "Ingeniería Inversa - Amenazas de la Ingeniería Inversa de OWASP" (vea las referencias a continuación) para obtener una lista de los riesgos del negocio, así como las amenazas técnicas asociadas.

Para que cualquiera de los controles de la lista siguiente sea eficaz, la aplicación debe cumplir al menos todos los requerimientos del nivel MASVS-L1 (es decir, deben existir sólidos controles de seguridad), así como todos los requerimientos de números más bajos en V8. Por ejemplo, los controles de ofuscación listados en la sección "impedir la comprensión" deben combinarse con el "impedir el análisis dinámico y la manipulación" y la "atadura al dispositivo".

**Tenga en cuenta que los controles de software nunca deben utilizarse como reemplazo de los controles de seguridad. Los controles listados en MASVR-R buscan añadir controles de protección adicionales y específicos contra las amenazas a las aplicaciones que también cumplen con los requerimientos de seguridad del MASVS.**

Se aplican las siguientes consideraciones:

1.  Debe definirse un modelo de amenaza que defienda claramente las amenazas del lado del cliente. Además, debe especificarse el grado de protección que debe proporcionar el sistema. Por ejemplo, un objetivo podría ser obligar a los autores de malware dirigido que quieren usar la aplicación a que tengan que invertir importantes esfuerzos para realizar la ingeniería inversa.
    
2.  El modelo de amenaza debe ser sensato. Por ejemplo, ocultar una clave criptográfica en una implementación de caja blanca es un problema si el atacante puede simplemente utilizar la aplicación como un todo.
    
3.  La eficiencia de la protección siempre debe ser verificada por un experto con experiencia en el testeo de tipos particulares de anti-manipulación y ofuscación utilizados (ver también los capítulos "ingeniería inversa" y "evaluación de protecciones del software" en la Guía de Pruebas de Seguridad Móvil).

### Impedir el Análisis Dinámico y la Manipulación

| #       | MSTG-ID           | Descripción                                                                                                                                                                           | R |
|---------|-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|
| **8.7** | MSTG-RESILIENCE-7 | La aplicación implementa múltiples mecanismos de detección para los puntos del 8.1 al 8.6. Nótese que, a mayor cantidad y diversidad de mecanismos usados, mayor será la resistencia. | x |
| **8.8** | MSTG-RESILIENCE-8 | Los mecanismos de detección provocan distintos tipos de respuestas, incluyendo respuestas retardadas y silenciosas.                                                                   | x |
| **8.9** | MSTG-RESILIENCE-9 | La ofuscación se aplica a las defensas del programa, lo que a su vez impide la desofuscación mediante análisis dinámico.                                                              | x |

### Asociación del Dispositivo

| #   | MSTG-ID | Descripción | R   |
| --- | --- | --- | --- |
| **8.10** | MSTG-RESILIENCE-10 | La aplicación implementa un “enlace al dispositivo” utilizando una huella del dispositivo derivado de varias propiedades únicas al mismo. | x   |

### Impedir la Comprensión

| #   | MSTG-ID | Descripción | R   |
| --- | --- | --- | --- |
| **8.11** | MSTG-RESILIENCE-11 | Todos los archivos ejecutables y bibliotecas correspondientes a la aplicación se encuentran cifrados, o bien los segmentos importantes de código se encuentran cifrados o "empaquetados" (packed). De este modo cualquier análisis estático trivial no revelará código o datos importantes. | x   |
| **8.12** | MSTG-RESILIENCE-12 | Si el objetivo de la ofuscación es proteger código propietario, debe utilizarse un esquema de ofuscación apropiado para la tarea particular y robusto contra métodos de desofuscación manual y automatizada, considerando la investigación actual publicada. La eficacia del esquema de ofuscación debe verificarse mediante pruebas manuales. Nótese que, siempre que sea posible, las características de aislamiento basadas en hardware son preferibles a la ofuscación. | x   |

### Impedir el Eavesdropping

| #   | MSTG-ID | Descripción | R   |
| --- | --- | --- | --- |
| **8.13** | MSTG-RESILIENCE-13 | A modo de defensa en profundidad, además de incluir un refuerzo (hardening) sólido de la comunicación, puede implementarse el cifrado de datos (payloads) a nivel de aplicación como medida adicional contra ataques de eavesdropping. | x   |




[Fuente](https://github.com/OWASP/owasp-masvs/tree/master/Document-es)

