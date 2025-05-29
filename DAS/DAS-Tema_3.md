---
tags: URJC URJC_DAS
---

# Tema 3 - Diseño y Arquitectura Software

---

## Tabla de Contenidos

1. [Introducción](#Introducción)
2. [Estilos arquitectónicos](#Estilos%20arquitectónicos)
3. [Patrones de diseño](#Patrones%20de%20diseño)
4. [Otros patrones](#Otros%20patrones)
5. [Arquitecturas y Diseño UML](#Arquitecturas%20y%20Diseño%20UML)
6. [¿Qué es la Notación C4?](#¿Qué%20es%20la%20Notación%20C4?)

---

## Introducción

> **🏛️ Arquitecturas Software**
> Las arquitecturas de software se construyen mediante la combinación de dos elementos fundamentales: los estilos arquitectónicos y los patrones de diseño.
>    
> Estas arquitecturas son inherentemente heterogéneas, ya que integran diversos estilos y patrones como componentes reutilizables para crear soluciones robustas y eficientes.
> 
> La principal distinción entre estilos arquitectónicos y patrones de diseño radica en su escala y momento de aplicación:
> 
> *Estilos Arquitectónicos*
> Representan decisiones de alto nivel que se toman en las etapas iniciales del diseño. Definen la estructura general y las características fundamentales de la arquitectura.
> 
> *Patrones de Diseño*
> Soluciones más específicas y detalladas que se aplican a problemas recurrentes dentro de la arquitectura. Se implementan generalmente después de haber establecido el estilo arquitectónico general.

---

## Estilos arquitectónicos

> **🔄 Pipes and Filters**
> Un filtro lee flujos de datos de sus entradas y genera flujos de datos a sus salidas. El filtro transforma los datos incrementalmente, mientras que la tubería transmite el flujo de datos.
> 
> [Referencia Pipes and Filters](https://learn.microsoft.com/es-es/azure/architecture/patterns/pipes-and-filters)

> ---

> **📚 Estilos por Capas**
> Un estilo por capas organiza el software en diferentes niveles, donde cada capa se encarga de una responsabilidad específica. Las capas se comunican a través de APIs y deben estar bien definidas para evitar violaciones de los principios de diseño, como el acoplamiento innecesario entre capas.
> 
> Si en un modelo de capas verticales encontramos más capas relacionadas de forma horizontal, podemos entender que estas capas tienen el mismo nivel de responsabilidad.
> 
> [Referencia Estilos por Capas](https://blog.hubspot.es/website/que-es-arquitectura-en-capas)

> ---

> **🖥️ Estilo Cliente-Servidor**
> El estilo cliente-servidor es un modelo utilizado para acceder a datos y aplicaciones en servidores a través de Internet.
> 
> En redes distribuidas (peer-to-peer), los clientes pueden interactuar entre sí directamente, facilitando la distribución de recursos. Las peticiones se realizan de forma asíncrona, y las respuestas se generan en función de eventos específicos.
> 
> [Referencia Cliente Servidor](https://www.redswitches.com/blog/client-server-architecture/)

> ---

> **📊 MVC (Model-View-Controller)**
> El patrón MVC ha sido utilizado en sistemas interactivos desde la década de 1980, permitiendo ofrecer diversas vistas de los mismos datos y facilitando la interacción multimodal.
> 
> *Modelo*
> Responsable de la lógica de negocio, donde se gestionan los datos y las reglas del sistema.
> 
> *Vista*
> Define la presentación de los datos, encargándose de cómo se muestran al usuario.
> 
> *Controlador*
> Maneja las interacciones del usuario, actualizando los datos a través de la modificación del modelo.
> 
> [Referencia MVC](https://www.geeksforgeeks.org/mvc-framework-introduction/)

> ---

> **🌐 REST o RESTful**
> El estilo REST (Representational State Transfer) o Restful es utilizado para manejar el acceso a servicios web y el desarrollo de aplicaciones web.
> 
> Se basa en una arquitectura cliente-servidor sin estado (_stateless_), lo que significa que cada solicitud se trata de manera independiente sin necesidad de mantener el contexto entre ellas.
> 
> Ofrecen una interfaz uniforme, que proporciona una interfaz sencilla y coherente para la interacción entre cliente y servidor. Además, las respuestas de los servidores son cacheables, mejorando la eficiencia en el acceso a recursos repetidos.
> 
> Las principales mejoras que ofrece el estilo REST son:
> 
> *Rendimiento (Performance)*
> Mejora las interacciones entre páginas web y servidores, optimizando la transferencia de datos y reduciendo el tiempo de carga.
> 
> *Escalabilidad (Scalability)*
> Facilita el soporte de un mayor número de componentes y transacciones entre ellos, permitiendo que el sistema crezca de manera eficiente.
> 
> *Simplicidad (Simplicity)*
> La interfaz se simplifica a través de URIs bien definidas, facilitando el acceso y la manipulación de los recursos.
> 
> *Modificabilidad (Modifiability)*
> Permite modificar componentes de manera independiente, favoreciendo la evolución del sistema sin afectar su estructura global.
> 
> *Fiabilidad (Reliability)*
> Aumenta la resistencia del sistema a fallos, al reducir la dependencia entre el servidor y el cliente.
> 
> *Portabilidad (Portability)*
> Mejora la portabilidad de los componentes de código y sus datos, permitiendo su uso en diferentes plataformas y entornos.
> 
> [Referencia REST](https://aws.amazon.com/es/what-is/restful-api/)

> ---

> **🔔 Event-Driven**
> Las arquitecturas Event-Driven (basadas en eventos) se centran en la detección, el consumo y la reacción a eventos. Un evento representa un cambio significativo en el estado de un sistema y puede desencadenar diversas acciones en otros componentes del sistema.
> 
> *Transporte de eventos*
> Los eventos se transmiten entre sistemas poco acoplados mediante mensajes, lo que permite una comunicación eficiente sin dependencias directas entre los emisores y los consumidores de eventos.
> 
> *Componentes de una arquitectura EDA*
> Una **arquitectura EDA** (Event-Driven Architecture) consta de emisores de eventos, consumidores y canales para la transmisión de los eventos. Los emisores no conocen directamente a los consumidores, lo que reduce el acoplamiento entre los diferentes componentes del sistema.
> 
> *Gestión de eventos*
> Existe un módulo dedicado a la gestión de eventos, que monitorea los datos del entorno y analiza los eventos para proporcionar la respuesta más adecuada.
> 
> Las arquitecturas **Event-Driven** emplean el patrón **Publish-Subscribe** para el intercambio de mensajes, lo que permite a los suscriptores recibir los eventos relevantes sin necesidad de interactuar directamente con los emisores.
> 
> **Tipos de eventos en arquitecturas Event-Driven**
> 
> *Eventos simples*
> Representan cambios medibles en una condición, como la modificación de un dato o el cambio de estado de un componente.
> 
> *Eventos en "stream"*
> Se envían en cadena a los suscriptores, permitiendo un procesamiento continuo de los datos a medida que los eventos ocurren.
> 
> *Eventos complejos*
> Resultan de la confluencia de varios eventos y requieren intérpretes de eventos sofisticados para analizar y generar respuestas adecuadas.
> 
> [Referencia Event-Driven](https://www.redhat.com/en/topics/integration/what-is-event-driven-architecture)

---

## Patrones de diseño

> **🛠️ Patrón de Diseño Software**
> Un Patrón de Diseño Software es una solución para problemas recurrentes en un contexto determinado, proporcionando enfoques probados y reutilizables para afrontar desafíos de diseño.
> 
> Se tratan de soluciones de diseño probadas y reutilizables que ayudan a simplificar y estandarizar el desarrollo de software.
> 
> Existen varias categorías de patrones de diseño, incluyendo:
> 
> *Patrones creacionales*
> Se enfocan en la creación de objetos.
> 
> *Patrones de comportamiento*
> Definen la interacción y comunicación entre objetos.
> 
> *Patrones estructurales*
> Se encargan de la composición de clases y objetos.

> ---

> **🏗️ Patrones Creacionales**
> 
> *Builder*
> Abstrae el proceso de creación de un objeto complejo, centralizando dicho proceso en un único punto.
> [Referencia Patrón Builder](https://refactoring.guru/es/design-patterns/builder)
> 
> *Singleton*
> Garantiza la existencia de una única instancia para una clase. Permite restringir la creación de objetos a una clase.
> [Referencia Patrón Singleton](https://refactoring.guru/es/design-patterns/singleton)
> 
> *Abstract Factory*
> Permite trabajar con objetos de familias relacionas y haciendo transparente el tipo de familia que se esté utilizando.
> [Referencia Patrón Abstract Factory](https://refactoring.guru/es/design-patterns/abstract-factory)
> 
> *Factory Method*
> Centraliza en una clase constructora la creación de objetos de un subtipo determinado, ocultando al usuario la diversidad de casos particulares. Tiene como finalidad encapsular un grupo de fábricas individuales bajo un tema común y utiliza interfaces genéricos para crear objetos concretos.
> [Referencia Patrón Factory Method](https://refactoring.guru/es/design-patterns/factory-method)
> 
> *Prototype*
> Permite copiar objetos existentes sin que el código dependa de sus clases.
> [Referencia Patrón Prototype](https://refactoring.guru/es/design-patterns/prototype)

> ---

> **🔧 Patrones Estructurales**
> 
> *Adapter*
> Transforma y adapta interfaces en otras para que puedan ser utilizadas por una clase que de otro modo no podría utilizarla. Es utilizado en programas antiguos para proporcionar front-end moderno.
> [Referencia Patrón Adapter](https://refactoring.guru/es/design-patterns/adapter)
> 
> *Proxy*
> Proporciona un intermediario de un objeto para controlar su uso. Es habitual en sistemas Web para cachear páginas frecuentemente visitadas.
> [Referencia Patrón Proxy](https://refactoring.guru/es/design-patterns/proxy)
> 
> *Facade*
> Proporciona una interfaz simplificada a una librería, un framework o un conjunto de clases complejas. Es una alternativa al abstract factory y similar al Mediator.
> [Referencia Patrón Facade](https://refactoring.guru/es/design-patterns/facade)

> ---

> **🔄 Patrones de Comportamiento**
> 
> *Chain of Responsibility*
> Permite establecer la línea que deben llevar los mensajes para que los objetos realicen la tarea indicada.
> [Referencia Patrón Chain of Responsibility](https://refactoring.guru/es/design-patterns/chain-of-responsibility)
> 
> *Strategy*
> Permite disponer de varios métodos para resolver un problema y elegir cuál utilizar en tiempo de ejecución.
> [Referencia Patrón Strategy](https://refactoring.guru/es/design-patterns/strategy)
> 
> *State*
> Permite que un objeto modifique su comportamiento cada vez que cambie su estado interno.
> [Referencia Patrón State](https://refactoring.guru/es/design-patterns/state)
> 
> *Visitor*
> Define nuevas operaciones sobre una jerarquía de clases sin modificar las clases sobre las que opera.
> [Referencia Patrón Visitor](https://refactoring.guru/es/design-patterns/visitor)
> 
> *Observer*
> Define una dependencia de uno a muchos entre objetos, de forma que cuando un objeto cambie de estado se notifique y actualicen automáticamente todos los objetos que dependen de él.
> [Referencia Patrón Observer](https://refactoring.guru/es/design-patterns/observer)
> 
> *Publish-Subscribe*
> Remitentes envían mensajes no programados a suscriptores. Esto ofrece Scalability y loosely coupling. Entre sus posibles usos está la subscripción a noticias.
> [Referencia Patrón Publish-Subscribe](https://learn.microsoft.com/en-us/azure/architecture/patterns/publisher-subscriber)
> 
> *Mediator*
> Encapsula la comunicación entre objetos a través de un objeto denominado "mediator". Esto permite reducir el acoplamiento entre componentes haciendo que se comuniquen indirectamente a través del elemento "mediator".
> [Referencia Patrón Mediator](https://refactoring.guru/es/design-patterns/mediator)

---

## Otros patrones

> **🔀 Parallel Split**
> Cierto punto de flujo donde un thread individual se divide en varios threads que pueden ejecutarse en paralelo permitiendo la ejecución simultánea de varias actividades.
> 
> Es un patrón básico de control de flujo muy utilizado en reservas de viajes u hoteles vá web para hacer consultas paralelas.
> 

> ---

> **🔄 Inversion of Control**
> El flujo de ejecución tradicional se invierte de manera que se especifican respuestas deseadas a solicitudes concretas, en lugar de que el programador especifique la secuencia de acciones.
> 
> Popularizado con el uso de frameworks, como Spring.

> ---

> **🧩 Micro Servicios**
> - Patrones de descomposición.
> - Patrón de base de datos por servicio.
> - Patrón API Gateway.
> - Patrones de descubrimiento de cliente y de servidor.
> - Patrón de invocación remota de mensajes.
> - Patrón Circuit Breaker.
> - Patrón Access Token.
> - Patrones de observación.
> - Patrones de interfaz de usuario.

---

## Arquitecturas y Diseño UML

> **📄 Vistas y Documentación**
> Las arquitecturas deben documentarse como un conjunto de vistas arquitectónicas. Es importante utilizar solo aquellas vistas necesarias o de interés para los stakeholders.
> 
> Se recomienda el uso de *UML 2.5.x* con herramientas de modelado UML. ¡Evita usar Word ni Visio si estás utilizando UML!
> 
> Es crucial decidir de antemano qué diagramas son necesarios para describir la arquitectura de un sistema complejo.
> 
> Existen más de 9 tipos de diagramas UML que permiten representar distintas vistas arquitectónicas. Sin embargo, no es necesario utilizar todos los diagramas UML para describir una arquitectura de software.

> ---

> **🔍 Vistas Arquitectónicas**
> Permiten describir el sistema y la arquitectura desde diferentes puntos de vista o perspectiva. Cada vista representa los intereses de un grupo de usuarios.
> 
> *Modelo de vistas “4+1”*
> El modelo de vistas "4+1" fue el primer modelo de vistas arquitectónicas propuesto por Kruchten en 1995, en él, cada vista representa la perspectiva de un usuario en la arquitectura del sistema.
> 
> Existen varias vistas que pueden ser representadas:
> 
> *Vista lógica*
> Captura las entidades lógicas (software) de un sistema y cómo se interconectan.
> 
> *Vista física*
> Captura las entidades físicas (hardware) de un sistema y sus interrelaciones.
> 
> *Vista de despliegue*
> Captura cómo las entidades lógicas se reparten en entidades físicas.
> 
> *Vista de comportamiento*
> Captura el comportamiento esperado del sistema o partes de éste.
> 
> *Vista de casos de uso*
> Captura los requisitos funcionales que serán ofrecidos por el sistema de información.

> ---

> **📝 Diseño con UML**
> Notación que incluye diferentes tipos de diagramas para modelar y diseñar sistemas software. Permite modelar vistas arquitectónicas a través de los diferentes diagramas UML.
> 
> Captura la información acerca de la estructura estática y el comportamiento dinámico de un sistema. Además, dispone de un lenguaje de restricciones (OCL) para especificar pre-condiciones y post-condiciones.
> 
> Es generalista, pero para algunos dominios dispone de “perfiles”.
> 
> Para describir la arquitectura de software de un sistema, solo se deben emplear aquellos que sean realmente necesarios mediante la identificación de las vistas arquitectónicas relevantes para cada público.
> 
> [Referencia UML](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/uml-practical-guide/)

---

## ¿Qué es la Notación C4?

> **📐 Notación C4**
> Notación creada para ayudar a los desarrolladores a comunicar la arquitectura y documentar el diseño del código. Trata de reflejar como piensan los arquitectos cuando diseña el software.
> 
> El nombre **C4** proviene de las iniciales de **Context**, **Container**, **Component** y **Code**, que son los cuatro diagramas fundamentales en este enfoque.
> 
> La notación C4 permite crear la estructura estática de un sistema. En este enfoque, un sistema de software se define en términos de *"containers"*, que son aplicaciones y almacenes de datos.
> 
> - Un *"container"* puede contener varios *componentes* (*"components"*).
> - Cada *"component"* se implementa mediante elementos de código, como clases, objetos, funciones, entre otros.
>   
>   [C4 Model Docs](https://c4model.com/)

> ---

> **🌍 System Context Diagram**
> Es el punto de partida para documentar el diseño de un sistema de software.
> 
> Este diagrama no muestra los detalles internos de la arquitectura, sino que se enfoca en los actores (*stakeholders*) involucrados y en las actividades principales que interactúan con el sistema.

> ---

> **📦 Container Diagram**
> Este diagrama muestra los contenedores principales del sistema, como aplicaciones y bases de datos, refinando el diagrama de contexto.
> 
> Puede incluir decisiones tecnológicas importantes sobre las plataformas y estructuras utilizadas.

> ---

> **🔧 Component Diagram**
> Detalla los contenedores al mostrar los componentes del sistema. Los componentes deben reflejar abstracciones reales del sistema, con un enfoque en la organización interna y la interacción entre los mismos.

> ---

> **💻 Code Diagram**
> Este diagrama ofrece detalles a nivel de diseño del código de los componentes individuales, proporcionando una representación detallada del software sin entrar en implementaciones específicas.

---