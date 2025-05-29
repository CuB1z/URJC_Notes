---
tags: URJC URJC_DAS
---

# Tema 2 - Diseño y Arquitectura Software

---

## Tabla de Contenidos

1. [¿Qué es la Ingeniería de Sistemas?](#¿Qué%20es%20la%20Ingeniería%20de%20Sistemas?)
2. [Sistemas de Sistemas (SoS)](#Sistemas%20de%20Sistemas%20(SoS))
3. [Construcción de la Arquitectura Software](#Construcción%20de%20la%20Arquitectura%20Software)
4. [Evolución de la Arquitectura](#Evolución%20de%20la%20Arquitectura)
5. [Evolución de la Arquitectura](#Evolución%20de%20la%20Arquitectura)
6. [Arquitecturas y patrones de Micro-Servicios](#Arquitecturas%20y%20patrones%20de%20Micro-Servicios)
7. [Sistemas en la Industria 4.0](#Sistemas%20en%20la%20Industria%204.0)

---

## ¿Qué es la Ingeniería de Sistemas?

> **🚀 Ingeniería de Sistemas**
> *Systems Engineering (SE)* es una disciplina que involucra diversas sub-disciplinas para la construcción de sistemas intensivos y complejos.
> 
> Algunas subdisciplinas son la gestión de proyectos, gestión de la configuración (SCM), hardware, Ingeniería Software, Verificación, Ingeniería de requisitos, etc.
>
> Se trabaja dentro de un dominio específico para la construcción de productos que involucran HW y SW. La integración de productos HW/SW es uno de los aspectos importantes de la Ingeniería de Sistemas.
> 
> *Dominios específicos:*
> - Sistemas de información complejos (e.g., ATC).
> - Plataformas para trenes, aviónica, civiles (e.g., 112).
> - Infraestructuras civiles y de ingeniería (e.g, presas, energía).
> - Plataformas de transporte.
> 
> La organización que regula los estándares de la Ingeniería de Sistemas es *INCOSE (International Council on Systems Engineering)*, una organización global dedicada a promover la práctica de la ingeniería de sistemas y a proporcionar directrices, estándares y mejores prácticas en este campo.
> 
> [Web Oficial de INCOSE](https://www.incose.org/)

---

## Sistemas de Sistemas (SoS)

> **🔗 Systems of Systems (Sos)**
> Término actual para describir la ingeniería de sistemas complejos compuestos por diversos subsistemas.
> 
> *A SoS is an integration of a finite number of constituent systems which are independent and operable, and which are networked together for a period of time to achieve a certain higher goal.*
> (Jamshidi 2009)
> 
> **🔧 Systems of Systems Engineering (SoSE)**
> De un ámbito superior a SE y acuñado en el ámbito militar, pero expandiéndose al civil. Al igual que en SE, involucra diferentes dominios, disciplinas y expertos.
> 
> Los diferentes subsistemas se integran para proporcionar una funcionalidad de orden superior.

> ---

> **📊 Tipos de SoS basados en la Independencia de sus constituyentes**
> 
> *Dirigidos*
> Orientado a cumplir un propósito específico en el que sus subsistemas constituyentes están subordinados al SoS. Los componentes de los subsistemas pueden operar independientemente, pero subordinados al control central.
> 
> *Reconocidos*
> El SoS tiene objetivos reconocidos pero los constituyentes retienen objetivos independientes respecto a su desarrollo. Los cambios en el sistema se basan en acuerdos.
> 
> *Colaborativos*
> Los componentes del sistema interactúan de manera más o menos voluntaria para cumplir un objetivo. Los actores centrales deciden como permitir o denegar un servicio.
> 
> *Virtuales*
> El SoS carece de una gestión centralizada. Un comportamiento de orden superior suele aparecer de manera no visible como consecuencia de las interacciones entre los constituyentes.

---

## Construcción de la Arquitectura Software

> **🏗️ Pasos para construir una Arquitectura Software**
> 1. Seleccionar cuántas vistas hacen faltan.
> 2. Seleccionar los diagramas apropiados para cada vista.
> 3. Seleccionar el estilo o estilos arquitectónicos:
> 	- Para sistemas con alto grado de interacción el estilo MVC es adecuado.
> 	- Para sistemas críticos, tiempo real y que utilizan sensores, las arquitecturas basadas en eventos son útiles.
> 4. Detallar las clases o los patrones de diseño para cada subsistema.
> 5. Refinar la AS hasta que los requisitos se hayan satisfecho.
> 6. Una vez seleccionados los estilos arquitectónicos, ver si existen patrones de diseño que solucionen problemas concretos.
> 7. Normalmente suele haber una combinación de patrones.
> 8. La arquitectura se diseña en varias iteraciones donde se va refinando el diseño.

---

## Evolución de la Arquitectura

> **🔄 ¿Cómo debe ser la Arquitectura Software?**
> Una buena arquitectura debe mantenerse en el tiempo y ser suficientemente flexible para soportar cambios motivados por obsolescencia tecnológica o nuevos requisitos.
> 
> La evolución de la arquitectura debe reflejar el histórico de los cambios.

> ---

> **🚗 AUTOSAR y sus fases de evolución**
> 
> AUTOSAR es una arquitectura de software abierta y estandarizada para la industria automotriz que busca crear una plataforma común para el desarrollo de software en unidades de control electrónico.
> 
> *Phase I (2004-2006)*
> - Desarrollo inicial de un estándar para sistemas embebidos en la industria automotriz.
> - Introducción de entregas básicas (versiones 1.0 y 2.0).
> - Enfoque en la estandarización para mejorar la interoperabilidad y reducir costos.
> 
> *Phase II (2006-2009)*
> - Extensión del estándar para soportar sistemas multicore, esenciales para vehículos modernos.
> - Entregas avanzadas (versiones 3.0 y 3.1) con soporte para controladores más complejos.
> - Inclusión de soporte para diagnósticos y comunicación entre módulos.
> 
> *Phase III (2009-2013)*
> - Consolidación del estándar con mejoras de mantenimiento y estabilidad.
> - Introducción de entregas 4.0, 4.1 y 4.2, enfocadas en la integración de software de terceros.
> - Mayor énfasis en seguridad funcional (ISO 26262) y sistemas avanzados de asistencia al conductor (ADAS).
> 
> *Post Phase III (2013-2016+)*
> - Expansión hacia tecnologías emergentes como el software adaptable y la conectividad IoT en vehículos.
> - Incorporación de actualizaciones en la entrega 4.3 para admitir nuevos paradigmas, como la conducción autónoma y servicios basados en la nube.

> ---

> **🌐 Contexto y tendencias actuales**
> 
> *Evolución hacia arquitecturas orientadas a servicios (SOA)*
> - Utilizadas para ofrecer flexibilidad en aplicaciones modernas, desde sistemas automotrices hasta IoT.
> - Permiten la integración eficiente de componentes distribuidos y la implementación de actualizaciones continuas.
>  
> *Conducción autónoma y movilidad conectada*
> - Las versiones modernas de AUTOSAR están preparadas para manejar los requisitos de software intensivo en vehículos autónomos.
> - Integración con tecnologías de vanguardia como 5G y sistemas de comunicación vehículo-a-todo (V2X).
>
> *Hacia la estandarización en industrias múltiples*
> - El uso de arquitecturas como IIRA y AUTOSAR influye en sectores más allá del automotriz, como la salud, la manufactura y la logística.

---

## Arquitecturas y Patrones de Micro-Servicios

> **🧩 Arquitecturas de Micro-Servicios**
> Son arquitecturas de servicios web orientadas a aplicaciones débilmente acopladas que facilitan a las organizaciones evolucionar la “pila” tecnológica (capas de tecnología).
> 
> Permiten la descomposicion de capacidades de negocio y existe una colección de patrones para arquitecturas de micro-servicios con el objetivo de  descomponer una arquitectura monolítica en micro-servicios y facilitar la migración de arquitecturas monolíticas.
> 
> Presentan un modelo moderno y eficiente para el desarrollo de aplicaciones complejas. Sin embargo, su implementación requiere una infraestructura adecuada y prácticas sólidas de DevOps para manejar su complejidad inherente.
> 
> [Ejemplo Netflix](https://www.geeksforgeeks.org/system-design-netflix-a-complete-architecture/)

> ---

> **🔄 Transición desde arquitecturas monolíticas**
> 
> *Arquitectura tradicional de aplicaciones web*
> En el modelo monolítico, todos los componentes están integrados en un único contenedor, lo que dificulta el despliegue continuo, genera una sobrecarga en el contenedor web y limita la escalabilidad en diferentes dimensiones.
> 
> *Arquitectura de Micro-Servicios*
> El modelo modular de micro-servicios organiza cada funcionalidad como un servicio independiente, lo que facilita tanto el desarrollo como el despliegue de componentes pequeños y manejables.
> 
> Además, permite que cada servicio se desarrolle de manera autónoma, reduciendo la dependencia tecnológica entre módulos y mejorando la flexibilidad del sistema.

> ---

> **🌟 Ventajas de los Micro-Servicios**
> *1. Desarrollo ágil*
> Los micro-servicios son pequeños, lo que los hace fáciles de desarrollar y mantener. Además, equipos dedicados pueden trabajar en paralelo sobre diferentes servicios, acelerando el proceso de desarrollo.
> 
> *2. Escalabilidad flexible*
> Esta arquitectura permite escalar únicamente los servicios que lo requieren, en lugar de toda la aplicación, lo que optimiza los recursos y reduce los costos de infraestructura y mantenimiento.
> 
> *3. Menor acoplamiento*
> Cada servicio opera de manera autónoma, lo que facilita tanto la actualización como la sustitución de módulos sin afectar el sistema completo.

> ---

> **📚 Patrones de Micro-Servicios**
> 
> | Patrón          | Descripción                                                                           |
> | --------------- | ------------------------------------------------------------------------------------- |
> | Circuit-Breaker | Evita que una aplicación lleve a cabo la ejecución repetida de una operación.         |
> | Retry           | Complementa a circuit-breaker para permitir reintentos en caso de fallo.              |
> | API Gateway     | Permite un único punto de entrada a diferentes clientes que acceden a microservicios. |

> 
> 

---

## Sistemas en la Industria 4.0

> **🏭 ¿Qué es la Industria 4.0?**
> La Industria 4.0 es una nueva revolución industrial de software para gestionar la complejidad de los sistemas software actuales, optimizar la robotización de la Industria 3.0 (logística) y la automatización e intercambio de datos en tecnologías de manufacturas.
> 
> El concepto de “Industrie 4.0” surge en una *feria de Hannover* (Alemania) en *2011* con la idea de automatizar y digitalizar las fábricas alemanas, especialmente las que incluyen más software.
> 
> El concepto de “Industry 4.0 - I4.0” (Europa) e “Industrial Internet of Things - IIoT” (USA) son equivalentes.
> 
> Algunas tecnologías en la Industria 4.0 son:
> - Big data y analítica de datos.
> - Robots autónomos.
> - Simulación.
> - Industrial IoT (IIoT).

> ---

> **📐 Principios y Métodos**
> 
> *Interconexión*
> Capacidad de los sistemas y máquinas, sensores y personas para comunicarse mediante protocolos de "IoT".
> 
> *Transparencia de la información*
> Proporcionan a los operadores de la I4.0 información suficiente para la toma de decisiones descentralizada.
> 
> *Continuous software engineering (CSE) y estrategia DevOps (Development + Operations)*

> ---

> **🗂️ RAMI 4.0**
> Modelo de referencia introducido en 2015, que representa una arquitectura 3D para los sistemas de manufactura inteligentes. Esta estructura organiza los niveles jerárquicos de la industria, asegurando la disponibilidad digital de los datos generados y ubicando la infraestructura de TI a lo largo del eje vertical para una mejor visualización y gestión.
> 
> [Referencia RAMI 4.0](https://blog.tenea.com/rami-4-0-el-modelo-de-arquitectura-de-referencia-para-la-industria-4-0/)

---