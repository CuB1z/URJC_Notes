---
tags: URJC URJC_DAS
---

# Tema 4 - Diseño y Arquitectura Software

---

## Tabla de Contenidos

1. [¿Qué son las Decisiones de Diseño Arquitectónico?](#¿Qué%20son%20las%20Decisiones%20de%20Diseño%20Arquitectónico?)
2. [Caracterización de Decisiones](#caracterizacion-de-decisiones)
3. [Vista y Procesos](#vista-y-procesos)
4. [Dependencias y Evolución](#dependencias-y-evolucion)
5. [Herramientas de AKM](#herramientas-de-akm)
6. [Formato MADR](#Formato%20MADR)
7. [Reflection](#reflection)
8. [Conclusiones](#conclusiones)

---

## ¿Qué son las Decisiones de Diseño Arquitectónico?

> **🏛️ Decisiones de Diseño Arquitectónico** 
> Una Arquitectura Software debe considerarse como el resultado de un conjunto de decisiones de diseño (ADD - Architectural Design Decisions) en lugar de un conjunto de componentes y conectores, *(Bosch, 2004)*.
> 
> Las decisiones de diseño permiten:
> - Comprender las alternativas evaluadas.
> - Documentar motivos subyacentes.
> - Facilitar la evolución de la arquitectura.
> 
> Son necesarias para comprender las alternativas evaluadas durante el proceso de diseño. Además, son un conocimiento implícito, subyacente y tácito que reside en la mente de los arquitectos software y que es necesario hacer explícito para que pueda ser reutilizable y transferible.
> 
> Las ADD cubren el hueco entre requisitos y diseño, facilitan que el conocimiento experto no se evapore, son reproducibles y permiten comprender el motivo de decisiones buenas  malas.

---

## Caracterización de Decisiones

> **📝 Caracterización de Decisiones**
> El primer paso para capturar conocimiento de ADD es caracterizarlo, utilizando:
> 
> *Plantillas de texto*
> (Tyree & Akerman, Capilla, Babar)
> 
> *Ontologías*
> (Kruchten)
> 
> *Anotaciones en código*
> (Zimmermann)

> ---

> **📄 Plantillas de texto**
> Las plantillas de texto definen un conjunto de atributos que capturan el conocimiento de las decisiones y su motivación.
> 
> Las plantillas deben ser flexibles en cuanto a número de ítems o atributos a capturar.

> ---

> **📋 Atributos para describir una decisión**
> 
> | Atributo    | Descripción                           |
> | ----------- | ------------------------------------- |
> | Nombre      | Asignar un nombre corto a la decisión |
> | Descripción | Descripción corta pero explicativa    |
> | Estatus     | "pendiente / aprobada / rechazada"        |
> | Categoría   | ---                                   |
> | Lógica      | Motivo de tomar dicha decisión        |
> | Responsable | ---                                   |
> | Fecha       | ---                                   |
> | Pros/Cons   | ---                                   | 

> ---

> **🛠️ PAKME (2006)**  
> PAKME es una herramienta diseñada para la captura, mantenimiento, recuperación y presentación del conocimiento aplicado (AK).
> 
> Está basada en la plantilla de Tyree y se enfoca en la relación con los atributos de calidad (QA). Además, permite la compartición de conocimiento y la captura de patrones de diseño, facilitando la descripción de escenarios.
> 
> *Funciones clave*
> - Captura y mantenimiento de conocimiento aplicado (AK).
> - Recuperación y presentación de información relevante.
> - Relación directa con atributos de calidad (QA).
> - Soporte para compartir conocimiento entre los usuarios.
> - Captura de patrones de diseño y descripción de escenarios.

---

## Vista y Procesos

> **🔍 Decisiones de Diseño**
> Las decisiones de diseño son elementos de primera clase definidos en el estándar $ISO/IEC/IEEE \space 42010:2022$.
> 
> Representan un nuevo punto de vista frente a vistas tradicionales (Kruchten, Rozanski). Se capturan y documentan junto con las arquitecturas software.
> 
> **📑 Captura y Gestión de Decisiones Arquitectónicas**  
> El primer paso es capturar y documentar las Decisiones de Diseño Arquitectónico (ADD) junto con su arquitectura.
> 
> Es esencial establecer trazabilidad con requisitos y arquitecturas, y compartir las decisiones con stakeholders a través de documentos y RSS (“knowledge sharing”). Además, se debe mantener y evolucionar un histórico de decisiones (“Decision History”).
> 
> *Pasos clave*
> - Captura y documentación de las decisiones de diseño y arquitectura.
> - Establecimiento de trazabilidad con requisitos y arquitecturas.
> - Compartición de decisiones con stakeholders.
> - Mantenimiento de un histórico de decisiones.

---

## Dependencias y Evolución

> **🔗 Dependencias de Decisiones**  
> Las herramientas de AKM permiten establecer dependencias explícitas entre decisiones, requisitos y arquitecturas, facilitando la trazabilidad completa.
> 
> Esto posibilita:
> 
> *Backward traceability*
> Rastrear las causas y orígenes de los cambios en el diseño.
> 
> *Forward traceability*
> Estimar el impacto de cambios en los requisitos sobre el diseño.
> 
> Las dependencias entre decisiones de diseño constituyen una trazabilidad interna para conocer el impacto en una decisión cuando otra se modifica. Si la granularidad de las decisiones es fina, la red de dependencias entre decisiones puede crecer enormemente.
> 
> Se deben limitar decisiones a nivel de clase en la arquitectura.

> ---

> **🔄 Evolución de Decisiones**  
> Un campo de versión en las decisiones permite gestionar un histórico de las decisiones para: 
> 
> - Conocer la historia de las decisiones tomadas.
> - Revertir cambios si es necesario.
> - Conocer la historia de la arquitectura y sus cambios.  
> 
> El histórico de decisiones debe mantenerse separado de la red de decisiones actual.
> 
> Además, el histórico de decisiones ofrece las siguientes posibilidades:
> 
> - Recrear decisiones pasadas.
> - Revertir decisiones si es necesario.
> - Conocer las alternativas consideradas, su lógica y utilizarlas para entender cómo se diseñó un sistema.
> - Enseñar y asesorar a arquitectos de software con menos experiencia.
> 
> *Meta-Modelo con Soporte para Evolución*
> Los metamodelos ayudan a describir de manera lógica los ítems necesarios para describir las decisiones e implementarlo en herramientas.

---

## Herramientas de AKM

> **🛠️ Herramientas de AKM**  
> Desde 2005, se han creado diversas herramientas de investigación prototipo para la captura y compartición de decisiones de diseño.
> 
> Estas herramientas buscan mejorar la toma de decisiones en el diseño de software al permitir una gestión más eficiente y transparente del conocimiento arquitectónico.
> 
> Algunas de las principales herramientas son:
> 
> *PAKME*
> Herramienta Web para la captura de decisiones basada en la plantilla de Tyree & Akerman (2005) con soporte para atributos de calidad (Babar et al).
> 
> *Archium*
> Herramienta de modelado que permite la captura de decisiones de diseño (DD) con avisos sobre decisiones incompatibles.
> 
> *AREL/eAREL*
> Herramienta de modelado UML que permite incluir decisiones de diseño (DD) en los modelos de clases. Soporta dependencias e histórico de decisiones.
> 
> *ADDSS*
> Herramienta Web para la captura de conocimiento. Soporta personalización de atributos, evolución de arquitecturas y dependencias. Las últimas versiones incorporan mecanismos de compartición.
> 
> *The Knowledge Architect*
> Herramienta plug-in para Word que permite marcar las decisiones de diseño con otros elementos del documento Word.
> 
> *EAGLE*
> Herramienta Web para compartir conocimiento, que incluye RSS y gestión de usuarios. Basada en la plataforma Hipergate.
> 
> *AdWiki*
> Herramienta Web similar a EAGLE, que almacena más de 400 decisiones SOA.
> 
> *ADvISE (Architectural Design Decision Support Framework)*
> Soporta la captura y representación de decisiones arquitectónicas mediante el método QOC (“Question-Option-Criteria”).
> 
> Permite crear decisiones reutilizables con un cierto grado de incertidumbre y generar preguntas basadas en las decisiones tomadas.
> 
> *VbMF (View-based Modeling Framework)*
> Junto con ADvISE, proporciona una vista de componentes y conectores (C&C) de la arquitectura, enlazando arquitecturas y decisiones.

---

## Formato MADR

> **📄 Formato de captura MADR**  
> MADR (Markdown Architectural Decision Records) es un formato libre para capturar decisiones arquitectónicas.  
> 
> Proporciona ficheros markdown en texto plano para capturar la información de las decisiones, además de permitir enlazar decisiones por su ID.
> 
> No todos los ítems de captura son obligatorios y permite su conexión con GitHub.
> 
> [Documentación del formato MADR](https://adr.github.io/madr/) 


---

## Reflection

> **💭 Reflection**  
> La toma de decisiones en diseño arquitectónico debe ser reflexiva y libre de sesgos, asegurando que se cuente con toda la información relevante. Reflexionar antes de decidir mejora la calidad de las decisiones.
> 
> *Consideraciones clave*
> - Evitar decisiones sesgadas.
> - Contar con toda la información contextual y de otras fuentes.
> - Hacerse preguntas antes de decidir.
> - No tomar decisiones con información incompleta.
> - Las decisiones sesgadas pueden llevar a malas interpretaciones.
> - El pensamiento reflexivo desafía las decisiones, mejorando su calidad.

> ---

> **🧠 Modelo Mind1 / Mind2**
> El modelo describe cómo las decisiones (Mind1) son desafiadas por otras perspectivas (Mind2) para obtener decisiones de mayor calidad.
> 
> *Mind 1 (Toma de decisiones)*
> 
> | Tarea                             | Descripción                                                |
> | --------------------------------- | ---------------------------------------------------------- |
> | Identificar contexto y requisitos | Recoger información relevante sobre el problema.           |
> | Formular problemas de diseño      | El arquitecto plantea los principales problemas de diseño. |
> | Plantear soluciones               | Las soluciones deben coevolucionar con los problemas.      |
> | Seleccionar una solución          | Elección lógica tras analizar opciones.                    |
> 
> *Mind 2 (Reflexión crítica)*
> 
> | Tarea                             | Descripción                                                |
> | --------------------------------- | ---------------------------------------------------------- |
> | Reflexionar sobre contexto y requisitos | Asegurarse de que sean completos y precisos.               |
> | Reflexionar sobre problemas de diseño  | Evaluar y desafiar problemas mal articulados.             |
> | Reflexionar sobre soluciones     | Asegurarse de que resuelvan requisitos y estén bien fundamentadas. |
> | Reflexionar sobre decisiones     | Evaluar la validez de las decisiones, considerando pros, contras y riesgos. |

---
