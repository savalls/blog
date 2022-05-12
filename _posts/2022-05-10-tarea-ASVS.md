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

[x]

#### V1 Arquitectura, Diseño y Modelado de Amenazas


##### V1.1 Ciclo de Vida de Desarrollo de Software Seguro

|  | #     | Descripción                                                                                                                                                                                                                                          | L1 | L2  | L3  | CWE  |
|--|-------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----|-----|-----|------|
|  | 1.1.1 | Verifique el uso de un ciclo de vida de desarrollo de software seguro queaborde la seguridad en todas las etapas del desarrollo.                                                                                                                     |    | [x] | [x] |      |
|  | 1.1.2 | Verifique el uso del modelado de amenazas para cada cambio de diseño oplanificación de sprint para identificar amenazas, planificar contramedidas,facilitar respuestas de riesgo adecuadas y guiar las pruebas de seguridad.                         |    | [x] | [x] | 1053 |
|  | 1.1.3 | Verifique que todas las historias y características de usuario contienen restricciones de seguridad funcionales, como por ejemplo: "Como usuario, debería poder ver y editar mi perfil. No debería ser capaz de ver o editar el perfil de nadie más" |    | [x] | [x] | 1110 |
|  | 1.1.4 | Verifique la documentación y la justificación de todos los límites de confianza,componentes y flujos de datos significativos de la aplicación                                                                                                        |    | [x] | [x] | 1059 |
|  | 1.1.5 | Verifique la definición y el análisis de seguridad de la arquitectura de altonivel de la aplicación y todos los servicios remotos conectados.                                                                                                        |    | [x] | [x] | 1059 |
|  | 1.1.6 | Verifique la implementación de controles de seguridad centralizados, simples(economía del diseño), comprobados, seguros y reutilizables para evitarcontroles duplicados, faltantes, ineficaces o inseguros.                                          |    | [x] | [x] | 637  |
|  | 1.1.7 | Verifique la disponibilidad de una lista de comprobación de codificaciónsegura, requisitos de seguridad, directriz o directiva para todos losdesarrolladores y evaluadores.                                                                          |    | [x] | [x] |      |


##### V1.2 Arquitectura de Autenticación


|  | #     | Descripción                                                                                                                                                                                                                                         | L1 | L2 | L3 | CWE |
|--|-------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----|----|----|-----|
|  | 1.2.1 | Verifique el uso de cuentas de sistema operativo únicas o especiales conprivilegios bajos para todos los componentes, servicios y servidores de laaplicación.                                                                                       |    |    |    |     |
|  | 1.2.2 | Verifique que las comunicaciones entre los componentes de la aplicación,incluidas las API, el middleware y las capas de datos, se autentican. Loscomponentes deben tener los mínimos privilegios necesarios.                                        |    |    |    |     |
|  | 1.2.3 | Verifique que la aplicación utiliza un único mecanismo de autenticacióncomprobado que se sabe que es seguro, se puede ampliar para incluir unaautenticación segura y tiene suficiente logging y supervisión para detectarabuso de cuenta o brechas. |    |    |    |     |
|  |       | Verifique que todas las vías de autenticación y las API de administración deidentidades implementan una fortaleza coherente del control de seguridad deautenticación, de modo que no haya alternativas más débiles por el riesgo dela aplicación    |    |    |    |     |

##### V1.3 Arquitectura de Gestión de Sesiones


|  |  |
|--|--|


##### V1.4 Arquitectura de Control de Acceso


|  | #     | Descripción                                                                                                                                                                                                                                                  | L1 | L2 | L3 | CWE |
|--|-------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----|----|----|-----|
|  | 1.4.1 | Verifique que los puntos de cumplimiento de confianza, tales como puertasde enlace de control de acceso, servidores y funciones serverless, exijancontroles de acceso. Nunca aplique controles de acceso en el cliente.                                      |    |    |    |     |
|  | 1.4.2 | ELIMINADO                                                                                                                                                                                                                                                    |    |    |    |     |
|  | 1.4.3 | ELIMINADO                                                                                                                                                                                                                                                    |    |    |    |     |
|  | 1.4.4 | Verifique que la aplicación utilice un mecanismo de control de acceso único ybien comprobado para acceder a datos y recursos protegidos. Todas lassolicitudes deben pasar por este único mecanismo para evitar copiar y pegar orutas alternativas inseguras. |    |    |    |     |
|  |       | Verifique que se utiliza el control de acceso basado en atributos o entidadesmediante el cual el código comprueba la autorización del usuario para unelemento de característica o datos en lugar de solo su rol. Los permisos debenasignarse mediante roles  |    |    |    |     |

##### V1.5 Arquitectura de Entradas y Salidas


|  | #     | Descripción                                                                                                                                                                                                                                                                                                       | L1 | L2 | L3 | CWE |
|--|-------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----|----|----|-----|
|  | 1.5.1 | Verifique que los requisitos de entrada y salida definan claramente cómomanejar y procesar datos en función del tipo, contenido y las leyes,regulaciones y otras leyes aplicables, reglamentos y otras normas decumplimiento de políticas                                                                         |    |    |    |     |
|  | 1.5.2 | Verifique que no se usa serialización al comunicarse con clientes que no sonde confianza. Si esto no es posible, asegúrese de que se apliquen controles deintegridad adecuados (y posiblemente cifrado si se envían datosconfidenciales) para evitar ataques de deserialización, incluida la inyección deobjetos. |    |    |    |     |
|  | 1.5.3 | Verifique que la validación de datos de entrada (input) se aplica en una capade servicio de confianza.                                                                                                                                                                                                            |    |    |    |     |
|  |       | Verifique que la codificación de salida (output encode) se produce cerca o enel intérprete para el que está destinada.                                                                                                                                                                                            |    |    |    |     |

##### V1.6 Arquitectura Criptográfica


|  | #     | Descripción                                                                                                                                                                                               | L1 | L2 | L3 | CWE |
|--|-------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----|----|----|-----|
|  | 1.6.1 | Verifique que existe una política explícita para la administración de clavescriptográficas y que un ciclo de vida de clave criptográfica sigue un estándarde administración de claves como NIST SP 800-57 |    |    |    |     |
|  | 1.6.2 | Verifique que los consumidores de servicios criptográficos protegen elmaterial clave y otros secretos mediante el uso de almacenes de claves oalternativas basadas en API                                 |    |    |    |     |
|  | 1.6.3 | Verifique que todas las claves y contraseñas son reemplazables y formanparte de un proceso bien definido para volver a cifrar los datos confidenciales.                                                   |    |    |    |     |
|  |       | Verifique que la arquitectura trata los secretos del lado cliente (como clavessimétricas, contraseñas o tokens de API) como inseguros y nunca los usa paraproteger o acceder a datos confidenciales       |    |    |    |     |

##### V1.7 Arquitectura de Errores, Logging y Auditoría


|  | #     | Descripción                                                                                                                                            | L1 | L2 | L3 | CWE |
|--|-------|--------------------------------------------------------------------------------------------------------------------------------------------------------|----|----|----|-----|
|  | 1.7.1 | Verifique que se utilice un formato común y un enfoque de logging en todo elsistema. (                                                                 |    |    |    |     |
|  |       | Verifique que los registros de log se transmitan de forma segura a un sistemapreferentemente remoto para análisis, detección, alertas y escalamiento.  |    |    |    |     |

##### V1.8 Arquitectura de Protección de Datos y Privacidad


|  | #     | Descripción                                                                                                                                                                                                                                                                      | L1 | L2 | L3 | CWE |
|--|-------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----|----|----|-----|
|  | 1.8.1 | Verifique que todos los datos confidenciales se identifiquen y clasifiquen enniveles de protección                                                                                                                                                                               |    |    |    |     |
|  |       | Verifique que todos los niveles de protección tienen un conjunto asociado derequisitos de protección, como los requisitos de cifrado, los requisitos deintegridad, la retención, la privacidad y otros requisitos de confidencialidad, yque estos se aplican en la arquitectura. |    |    |    |     |

##### V1.9 Arquitectura de Comunicaciones


|  | #     | Descripción                                                                                                                                                                                                                                             | L1 | L2 | L3 | CWE |
|--|-------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----|----|----|-----|
|  | 1.9.1 | Verifique que la aplicación cifra las comunicaciones entre componentes,especialmente cuando estos componentes se encuentran en contenedores,sistemas, sitios o proveedores de nube diferentes.                                                          |    |    |    |     |
|  |       | Verifique que los componentes de la aplicación verifiquen la autenticidad decada lado en un vínculo de comunicación para evitar ataques de "persona enel medio". Por ejemplo, los componentes de la aplicación deben validarcertificados y cadenas TLS. |    |    |    |     |

##### V1.10 Arquitectura de Software Malicioso


|  | #      | Descripción                                                                                                                                                                                                                                                                                                                     | L1 | L2  | L3 | CWE |
|--|--------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----|-----|----|-----|
|  | 1.10.1 | Verifique que un sistema de control de código fuente está en uso, conprocedimientos para garantizar que los check-ins están respaldados ticketsde issues o solicitudes de cambio. El sistema de control de código fuentedebe tener control de acceso y usuarios identificables para permitir latrazabilidad de cualquier cambio |    | [x] |    | 284 |

##### V1.11 Arquitectura de la Lógica de Negocio


|  | #      | Descripción                                                                                                                                                                                                                                                           | L1 | L2 | L3 | CWE |
|--|--------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----|----|----|-----|
|  | 1.11.1 | Verifique la definición y documentación de todos los componentes de laaplicación en términos de las funciones de negocio o de seguridad queproporcionan.                                                                                                              |    |    |    |     |
|  | 1.11.2 | Verifique que todos los flujos de lógica de negocio de alto valor, incluida laautenticación, la administración de sesiones y el control de acceso, nocompartan estados no sincronizados.                                                                              |    |    |    |     |
|  |        | Verifique que todos los flujos de lógica de negocio de alto valor, incluida laautenticación, la administración de sesiones y el control de acceso, seanseguros para subprocesos y resistentes a condiciones de carrera time-of-check y time-of-use (race conditions). |    |    |    |     |

##### V1.12 Arquitectura de Carga Segura   de Archivos


|  | #      | Descripción                                                                                                                                                                                                                                                                                                                                                                                               | L1 | L2 | L3 | CWE |
|--|--------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----|----|----|-----|
|  | 1.12.1 | ELIMINADO                                                                                                                                                                                                                                                                                                                                                                                                 |    |    |    |     |
|  |        | Verifique que los archivos subidos por el usuario, -si es necesario que semuestren o descarguen desde la aplicación-, se hace mediante descargas desecuencias de octetos o desde un dominio no relacionado, como unalmacenamiento de archivos en la nube. Implemente una directiva deseguridad de contenido (CSP) adecuada para reducir el riesgo de vectoresXSS u otros ataques desde el archivo cargado |    |    |    |     |

##### V1.13 Arquitectura de API


|  |  |
|--|--|

##### V1.14 Arquitectura de Configuración


|  | #      | Descripción                                                                                                                                                                                                                                                                  | L1 | L2 | L3 | CWE |
|--|--------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----|----|----|-----|
|  | 1.14.1 | Verifique la segregación de componentes de diferentes niveles de confianzaa través de controles de seguridad bien definidos, reglas de corta fuego,pasarelas de API, proxies reversos, grupos de seguridad basados en nube, omecanismos similares.                           |    |    |    |     |
|  | 1.14.2 | Verifique que las firmas binarias, las conexiones de confianza y los puntos deconexión verificados se usan para el despliegue de archivos binarios adispositivos remotos.                                                                                                    |    |    |    |     |
|  | 1.14.3 | Verifique que el canal de compilación advierte de componentes obsoletos oinseguros y realiza las acciones adecuadas.                                                                                                                                                         |    |    |    |     |
|  | 1.14.4 | Verifique que el canal de compilación contiene un paso para compilar ycomprobar automáticamente el despliegue seguro de la aplicación,especialmente si la infraestructura de la aplicación está definida porsoftware, como los scripts de compilación del entorno en la nube |    |    |    |     |
|  | 1.14.5 | Verifique que los despliegues de aplicaciones sean en sandbox,contenedores y/o aislados a nivel de red para retrasar e impedir que losatacantes vulneren otras aplicaciones, especialmente cuando realizanacciones sensibles o peligrosas, como la deserialización.          |    |    |    |     |
|  |        | Verifique que la aplicación no utiliza tecnologías del lado cliente nocompatibles, inseguras o en desuso, como NSAPI plugins, Flash, Shockwave,ActiveX, Silverlight, NACL o client-side java applets                                                                         |    |    |    |     |

