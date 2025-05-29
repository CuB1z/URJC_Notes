---
tags: URJC URJC_DAS
---

# Tema 5 - Diseño y Arquitectura Software

---

## Tabla de Contenidos

1. [Introducción](#Introducción)
2. [¿Qué son los Atributos de Calidad?](#¿Qué%20son%20los%20Atributos%20de%20Calidad?)
3. [¿Qué es un escenario?](#¿Qué%20es%20un%20escenario?)
4. [Evaluación de Arquitecturas](#Evaluación%20de%20Arquitecturas)
5. [¿Qué es ATAM?](#¿Qué%20es%20ATAM?)
6. [Pasos del método ATAM](#Pasos%20del%20método%20ATAM)

---

## Introducción

> **📘 Introducción**  
> Las arquitecturas de software no son solo el resultado de los Requisitos Funcionales (RF), sino que los Requisitos No Funcionales (RNF) o Atributos de Calidad (QAs) tienen un impacto directo en la arquitectura final.
> 
> Los RNF afectan varias partes de la arquitectura y son esenciales para construir un sistema de calidad, mientras que un RF solo afecta una parte específica de la arquitectura.  

> ---

> **🛠️ Evaluación de soluciones de diseño**  
> Es necesario evaluar las soluciones de diseño cuando existen varias candidatas.
> 
> La evaluación se realiza a través de los atributos de calidad (QAs) y ADD (Architecture Driven Design) ayuda a integrarlos desde las fases tempranas del diseño.
> 
> Evaluar es difícil porque se evalúa un diseño, no un programa ejecutado.

---

## ¿Qué son los Atributos de Calidad?

> **📊 Atributo de Calidad**  
> Es un requisito no funcional que mide la calidad de una parte del sistema. Representa los objetivos de negocio y aspectos de calidad de los diferentes actores involucrados en el producto de software.  
> 
> Es fundamental especificar y priorizar los atributos de calidad más importantes para el diseño. La arquitectura no será definitiva hasta satisfacer todos los RF y RNF definidos al inicio, aunque algunos QA pueden no ser alcanzables.
> 
> [Modelo de calidad ISO 25010](https://iso25000.com/index.php/normas-iso-25000/iso-25010)

> ---

> **📏 Valores cuantitativos de QA**  
> Son valores numéricos o rangos asignados a los QA para evaluarlos.
> 
> Por ejemplo, "Prestación de CPU < 3 ms". Sin valores medibles, no es posible evaluar la calidad. Un ejemplo sería: "Encriptar 1GB de datos con AES de 256 bits toma alrededor de 6 segundos".

> ---

> **📂 Tipos de Atributos de Calidad**
> *Runtime*
> Functionality, Performance, Security, Availability, Interoperability, etc.
> 
> *Non Runtime*
> Portability, Reusability, Modifiability, Maintainability, etc. 
> 
> *Business*
> Cost, Time to market.

> ---

> **🌳 Utility Tree**
> Organiza y clasifica los atributos de calidad en forma de árbol. Por ejemplo, el QA maintainability, tendría la siguiente forma:
> 
> *QA: Maintainability*
>   - Sub-QA nivel 1: Complexity  
>   - Sub-QA nivel 1: Size  
>   - Sub-QA nivel 1: Modularity  

---

## ¿Qué es un escenario?

> **🎭 Escenario**
> Situación posible en la que un usuario interactúa con el sistema y suele ir asociado a la evaluación de atributos de calidad.
> 
> *Escenarios generales*
> Independientes del sistema.
> 
> *Escenarios concretos*
> Específicos de un sistema particular.
> 
> Los escenarios concretos es la única manera que tenemos de cuantificar de forma medible los atributos de calidad de un sistema.

> ---

> **📋 Formato de un escenario**
> 
> *“when 100 users initiate ‘complete payment’ transition, the payment component, under normal circumstances, will process the requests with an average latency of three seconds.”*
> 
> | Parte                  | Descripción             |
> | ---------------------- | ----------------------- |
> | Estímulo               | Iniciar transacción     |
> | Fuente del estímulo    | Usuarios                |
> | Entorno                | Circunstancias normales |
> | Elemento afectado      | Componente de pago      |
> | Efecto o respuesta     | Transacción completada  |
> | Medida de la respuesta | Latencia en segundos    |

---

## Evaluación de Arquitecturas

> **🔍 ¿En qué consiste?**  
> El objetivo es evaluar una o varias soluciones de diseño para verificar si cumplen con los atributos de calidad definidos.
> 
> Es crucial establecer un equilibrio (QA trade-off) entre atributos que son dependientes entre sí.  

> ---

> **🛠️ Construcción y evaluación del Utility Tree**  
> 1. Definir los QA basados en los deseos de calidad y los RNF.  
> 2. Construir el Utility Tree descomponiendo los QA en sub-atributos y usando clasificaciones de atributos aceptadas.  
> 3. Definir escenarios de uso para cada atributo y parte del sistema, incluyendo valores medibles.  
> 4. Priorizar y ordenar los escenarios (ranking).  
> 5. Evaluar los escenarios para cada QA mediante simulaciones o fórmulas.  
> 6. Utilizar tácticas (no obligatorias, pero deseables).  
> 7. Seleccionar los escenarios más adecuados.  
> 8. Seleccionar las soluciones de diseño basadas en los resultados de la evaluación.

> ---

> **📊 Métodos para Evaluar Arquitecturas**  
> 
> | Método | Significado                                 |
> | ------ | ------------------------------------------- |
> | ATAM   | Architecture Trade-off Evaluation Method    |
> | SAAM   | Software Architecture Evaluation Method     |
> | ARID   | Active Reviews for Intermediate Design      |
> | SARA   | Software Architecture Review and Assessment |
> | CBAM   | Cost Benefit Analysis Method                |

---

## ¿Qué es ATAM?

> **🏛️ ATAM (Architecture Tradeoff Analysis Method)**
> Es un enfoque estructurado para evaluar y analizar arquitecturas de software, ayudando a tomar decisiones sobre qué diseño arquitectónico es el más adecuado para satisfacer los requisitos de un sistema.
> 
> Se centra en identificar y comprender los trade-offs (compromisos) entre diferentes cualidades del sistema, como el rendimiento, la seguridad, la escalabilidad, y la mantenibilidad, entre otras.
>
> El método ATAM se utiliza para:
>
> *1. Evaluar arquitecturas*
> Analizar si una arquitectura propuesta puede cumplir con los requisitos técnicos y no funcionales del sistema.
> 
> *2. Identificar riesgos*
> Detectar posibles problemas o áreas de incertidumbre que puedan comprometer la efectividad de la arquitectura.
> 
> *3. Tomar decisiones informadas*
> Ayudar a los arquitectos y otros stakeholders a tomar decisiones basadas en una evaluación detallada de las opciones arquitectónicas.
>
> ATAM es un proceso colaborativo que involucra a varios actores del proyecto (como arquitectos de software, diseñadores, clientes y otros stakeholders) para obtener una visión completa y precisa de los compromisos implicados en las decisiones de diseño.

> ---

> **⚠️ Descubrimiento de riesgos**
> ATAM ayuda a identificar riesgos potenciales que podrían crear problemas en el sistema.
> 
> Un ejemplo de riesgo sería: Si falla el módulo de pago seleccionado, el sistema no permite compras on-line.
>
> **🔍 Descubrimiento de puntos sensibles**
> ATAM también permite identificar puntos sensibles ("sensitivity points") en los que un pequeño cambio puede causar una diferencia significativa en una cualidad del sistema (QA).
> 
> Un ejemplo de punto sensible sería: El Sistema de Comunicaciones es clave en la arquitectura del sistema.
>
> **⚖️ Descubrimiento de tensiones entre QAs**
> Finalmente, ATAM permite descubrir tensiones ("trade-offs") entre diferentes cualidades del sistema que pueden afectar a más de un atributo.
> 
> Un ejemplo de trade-off sería: Si aumentamos las prestaciones de la base de datos, se incrementa el coste.

> ---

> **👥 Roles en ATAM**
> En el proceso de ATAM, diferentes roles son asignados a los participantes para garantizar una evaluación efectiva de la arquitectura. A continuación, se describen los principales roles involucrados:
>
> *Clientes*
> Deben presentar los objetivos de calidad del sistema y negocio.
> 
> *Equipo ATAM*
> Es el grupo que lidera y facilita la evaluación de la arquitectura utilizando el método ATAM.
> 
> *Moderador*
> Supervisa y modera las discusiones largas para asegurar que el proceso se mantenga dentro del tiempo estimado (2 a 3 días).
> 
> *Redactor*
> Parte del equipo ATAM que redacta los posibles escenarios durante la evaluación.
> 
> *Controlador de tiempo*
> Controla el tiempo de discusión de los escenarios para asegurar que las sesiones se mantengan eficientes y dentro de los plazos.
> 
> *Monitor/Observador del proceso*
> Observa que se cumplan todos los pasos del proceso ATAM y sugiere mejoras en el proceso en tiempo real.
> 
> *Entrevistador*
> Lanza preguntas y problemas a los usuarios para determinar qué aspectos de calidad son más importantes y relevantes para el sistema.

---

## Pasos del método ATAM

> **📝 Paso 1. Presentación de ATAM**
> 
> El equipo ATAM explica el método al cliente, quien puede hacer preguntas sobre el proceso.
> 
> Se detallan las fases, la duración (2-3 días) y se identifican los stakeholders y sus roles.

> ---

> **🎯 Paso 2. Objetivos de Negocio**
> 
> Se describen el contexto de negocio, los requisitos funcionales y de calidad de alto nivel.
> 
> El cliente indica deseos de calidad razonables y su impacto en la arquitectura.

> ---

> **🏗️ Paso 3. Presentar la Arquitectura**
> 
> Se describe la arquitectura existente, sus partes principales, restricciones técnicas, middleware, sistemas con los que interactúa y los estilos arquitectónicos utilizados para aspectos de calidad.
> 
> Se presenta visualmente.

> ---

> **🔍 Paso 4. Identificar Aproximaciones Arquitectónicas**
> 
> Se identifican las partes de la arquitectura susceptibles de ser medidas con atributos de calidad y se proponen al menos dos aproximaciones arquitectónicas para cada deseo de calidad.

> ---

> **🌳 Paso 5. Construir el Utility Tree**
> 
> Se identifican, priorizan y seleccionan los QAs más relevantes. Luego, se describen los escenarios para cada fila del utility tree y se numeran. Finalmente, se asigna una combinación de importancia y dificultad (H, M, L) a cada escenario.

> ---

> **🔍 Paso 6. Analizar Aproximaciones Arquitectónicas**
> 
> El equipo ATAM evalúa las aproximaciones para:
> 
> - Identificar riesgos, puntos críticos y trade-offs.
> - Presentar arquitecturas alternativas que afecten a un QA específico.
> - Identificar elementos clave relacionados con los QAs de mayor prioridad.

> ---

> **📊 Paso 7. Selección y Priorización de Escenarios**
> 
> El equipo ATAM discute los escenarios basados en los resultados del Paso 6, seleccionando los elegidos (marcando en verde los seleccionados y en rojo los descartados).
> 
> Se pueden seleccionar varios escenarios por QA y parte del sistema. Si no hay acuerdo, se vota.
> 
> Los escenarios seleccionados se listan y explican.

> ---

> **🔄 Paso 8. Volver a Analizar Aproximaciones Arquitectónicas**
> 
> Se pueden incluir nuevos escenarios no considerados previamente y regresar al Paso 5 para ajustar el análisis.

> ---

> **📄 Paso 9. Presentar Resultados**
> 
> Se documentan todos los pasos de ATAM. Se describe y explica la nueva arquitectura modificada del Paso 3, indicando claramente los elementos añadidos, eliminados o modificados que afectan la estructura del diseño.

---