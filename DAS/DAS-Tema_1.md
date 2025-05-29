---
tags: URJC URJC_DAS
---

# Tema 1 - Diseño y Arquitectura Software

---

## Tabla de Contenidos

1. [¿Qué es una Arquitectura Software?](#¿Qué%20es%20una%20Arquitectura%20Software?)
2. [¿Qué es un Arquitecto Software?](#¿Qué%20es%20un%20Arquitecto%20Software?)
3. [Otras Arquitecturas](#Otras%20Arquitecturas)
4. [Principios de Diseño Software](#Principios%20de%20Diseño%20Software)
5. [Patrones de Diseño Software](#Patrones%20de%20Diseño%20Software)
6. [Estilos Arquitectónicos Software](#Estilos%20Arquitectónicos%20Software)
7. [Estándar ISO 42010](#Estándar%20ISO%2042010)

---

## ¿Qué es una Arquitectura Software?

> **🏛️ Arquitectura Software (AS)**
> Representa la versión moderna del diseño de un sistema software complejo desde distintos puntos de vista, según los intereses de diversos usuarios (*"Stakeholders"*).
> 
> *Según Perry & Wolf, 1991*
> $AS = \text{componentes, forma, lógica}$
> 
> Una arquitectura software es una tripleta de elementos arquitectónicos como clases y paquetes UML que se conectan con una determinada forma.
> 
> Diferentes arquitecturas pueden presentar formas diferentes (formas de organizar dichos componentes). La lógica hace referencia a las decisiones que se toman para seleccionar un determinado componente o un patrón de diseño.

> **📝 Notas**
> - Las arquitecturas software deben estar siempre alineadas con el código o implementación existente para evitar lo que se conoce como *“architectural mismatch”*.
> - Las arquitecturas software se “erosionan” o degradan durante las fases de evolución del sistema.
> - Las arquitecturas software pueden diseñarse con distintos niveles de detalle.

---

## ¿Qué es un Arquitecto Software?

> **👷 Arquitecto Software**
> Diseñador que tiene como misión identificar los requisitos funcionales y no funcionales que permitan construir el diseño software de un sistema.
> 
> *Son la piedra angular de toda fase de diseño software*.

---

## Otras Arquitecturas

> **🏗️ Arquitecturas de Referencia**
> Diseños software de alto nivel que describen las partes fundamentales de un conjunto de sistemas en un dominio particular.
> 
> Por ejemplo, Partes estándar de un compilador, Modelo OSI TCP / IP, etc.

> ---

> **🛠️ Arquitecturas de Producto Software**
> Personalización / derivación de una arquitectura software para un producto determinado que refleja sus características.
> 
> Se basa en la personalización de partes variables (*“software variability”*) y el empleo de partes comunes reutilizables, es decir, la arquitectura de un producto no se construye generalmente desde cero.

---

## Principios de Diseño Software

_1._ Separación de responsabilidades (_“separation of concerns”_).

_2._ Hacer explícita la comunicación entre niveles.

_3._ Realizar abstracciones para diseñar niveles con bajo grado de acoplamiento (_“loose coupling”_).

_4._ Modularizar el diseño y descomponer en subsistemas y módulos.

_5._ Las arquitecturas se rigen por un conjunto de principios que no se deben violar.

_6._ Cohesión y acoplamiento son principios de diseño básico en todo sistema software.

_7._ Acoplamiento (_“Coupling”_).

_8._ Cohesión (_“Cohesion”_).

_9._ No duplicar la funcionalidad de componentes.

_10._ No sobrecargar (_“overload”_) la funcionalidad de componentes (anti-patrón God Class).

_11._ Modularizar el diseño software y separación de responsabilidades en paquetes UML.

_12._ Un componente no tiene porqué conocer los detalles internos de otro (_“information hiding”_).

_13._ Alta cohesión implica bajo acoplamiento.

_14._ El bajo acoplamiento se consigue mediante la abstracción, separación de responsabilidades y ocultamiento de la información.

_15._ Evitar dependencias circulares.

_16._ Principio de Hollywood _“Don’t call us, we call you”_.

_17._ Un módulo define una interfaz que otros módulos la realizan. Los módulos superiores no dependen de los módulos en niveles inferiores (_"Dependency Inversion of Control"_).

_18._ Transfiere la responsabilidad de creación y enlace de módulos de software a un framework externo configurable (_"Dependency Injection"_).

---

## Patrones de Diseño Software

> **🧩 Patrón de Diseño Software**
> Solución de diseño para un problema recurrente en un contexto determinado. Se tratan de soluciones de diseño reutlizables ya probadas en otras situaciones similares.
> 
> También nombrados como *"design patterns"*.

> ---

> **📜 Cronología e historia de los patrones software**
> 
> *The Timeless Way of Building*, C. Alexander.  
> 1979  
> 
> *Lenguajes de patrones para programas OO*, Cunningham y Beck.  
> 1987  
> 
> *Patrones de diseño*, Gamma et al.  
> 1995
> 
> *Estilos arquitectónicos*, Buschmann et al.  
> 1996-2000  
> 
> *Patrones de arquitecturas de aplicaciones empresariales*, M. Fowler.  
> 2002  
> 
> *Patrones actuales centrados en tecnologías y plataformas*.
> 2010 - actualidad

> ---

> **📂 Categorías Básicas de Patrones**
> 
| **Categoría**                               | **Patrones**                                         |
| ------------------------------------ | ------------------------------------------ |
| Creacionales                               | Abstract Factory, Builder, Singleton…   |
| Estructurales                               | Adapter, Facade, Proxy                         |
| Comportamiento                        | Mediator, Observer…                            |
| Concurrencia                              | Scheduler, Lock, Thread Pool                |
| Interacción                                  | ---                                                          |
| Workflow y Process Automation | ---                                                          |
| Microservicios                             | ---                                                          |

---

## Estilos Arquitectónicos Software

> **🏛️ Estilos Arquitectónicos**
> Un estilo arquitectónico se diferencia de un patrón de diseño en el tamaño. Los estilos involucran subsistemas mientras que los patrones son un conjunto reducido de clases.
> 
> Evitan reinventar soluciones de diseño ya probadas.
> 
> *En diseño software, se debe seleccionar primero el estilo o estilos (si hubiera más de 1) y luego los patrones*.
> 
> **Algunos estilos arquitectónicos son:**
> - Modelo-Vista-Controlador (MVC)
> - Capas (Layers, Tiers)
> - Filtros y Tuberías (Pipe & Filter)
> - Cliente / Servidor (Client/Server)
> - Pizarra (Blackboard)
> - Máquina virtual
> - Basados en componentes
> - Message bus
> - Peer-to-Peer
> - SOA y Micro-servicios

---

## Estándar ISO 42010

> **📜 ¿Qué es el estándar ISO 42010?**
> Nuevo estándar ISO/IEC 42010 (2009) en sustitución del IEEE 1471-2000, como práctica recomendada para la descripción de sistemas intensivos software.
> - Mantiene el modelo de vistas arquitectónicas.
> - Incluye como novedad soporte para lógica y decisiones de diseño.
> - Alineación con otros estándares como RM-ODP y Enterprise Architecture (EA).

> ---

> **📚 Conceptos y Terminología**
> 
> *Architecture*
> Fundamental conception of a system in its environment embodied in elements, their relationships to each other and to the environment, and principles guiding system design and evolution.
> 
> *Architecting*
> Activities of conceiving, defining, describing, documenting, certifying proper implementation of, maintaining and improving an architecture throughout a system’s life cycle.
> 
> *Architecture decision*
> Choice made from among possible options that addresses one or more architecture-related concerns.
> 
> *Architecture rationale*
> Explanation or justification for an architecture decision.
> 
> *Architecture view*
> Work product representing a system from the perspective of architecture-related concerns.
> 
> *Architecture viewpoint*
> Work product establishing the conventions for the construction, interpretation and use of architecture views and associated architecture models.

---