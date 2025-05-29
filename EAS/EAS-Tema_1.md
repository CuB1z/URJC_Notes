---
tags: URJC URJC_EAS
---

# Tema 1 - Evolución y Adaptación Software

---

## Tabla de Contenidos

1. [Definiciones](#Definiciones)
2. [Importancia del Mantenimiento](#Importancia%20del%20Mantenimiento)
3. [WordPress](#WordPress)
4. [Procesos Diferenciados vs Único Proceso](#Procesos%20Diferenciados%20vs%20Único%20Proceso)
5. [Procesos de Evolución](#Procesos%20de%20Evolución)
6. [Mantenimiento y su Clasificación](#Mantenimiento%20y%20su%20Clasificación)
7. [Legacy Systems](#Legacy%20Systems)
8. [Evaluación de los Sistemas Heredados](#Evaluación%20de%20los%20Sistemas%20Heredados)

---

## Definiciones

> **🛠️ Mantenimiento del Software**  
> Es la primera forma de evolución de los sistemas. Muchas empresas con software desarrollado hace 25 años requieren estas actividades si la aplicación sigue siendo útil.  
>   
> *ANSI/IEEE*  
> Modificaciones al software tras su entrega para corregir errores, mejorar rendimiento o adaptarlo a nuevos entornos.  
>   
> *ISO/IEC*  
> Cambios en el código y documentación para solucionar problemas o mejorar el software, manteniendo su integridad.  
>   
> *Mantenimiento*
> Proceso de mejora y optimización del software después de su entrega al usuario final, así como la corrección y prevención de defectos.  

> ---  

> **🔄 Evolución del Software**  
> La evolución del software es la dinámica de crecimiento del software.  
>   
> *Meir M. Lehman y Juan F. Ramil*  
> Incluye todas las actividades de programación orientadas a generar una nueva versión de un software a partir de una versión anterior operativa.  
>   
> *Chapin, N. et al. (2001)*  
> Es la aplicación de actividades y procesos de mantenimiento que generan una nueva versión operativa con funcionalidades o propiedades cambiadas, junto con procesos de garantía de calidad y gestión.  
>   
> De estas definiciones se desprende que la evolución cubre el ajuste a funcionalidades adicionales.  
>   
> La guía *SWEBOK* indica que el mantenimiento surge tanto por la necesidad de cambios como de evolución en el software.  
>   
> *Evolución*
> Todas las actividades de generación de software que se orientan a generar una nueva versión a partir de una versión anterior operativa. Incluye cambios en los requisitos.
> 
> Más información: [http://www.computer.org/portal/web/swebok](http://www.computer.org/portal/web/swebok).

> ---  

> **🛡️ Conservación del Software**  
> Aplicación de medidas especiales para mantener en funcionamiento un sistema antiguo.  
>   
> Los requisitos evolucionan durante el desarrollo y los grandes sistemas cambian con el tiempo.

---

## Importancia del Mantenimiento

> **🔄 Ciclo de Vida del Software**  
> Los sistemas grandes y complejos tienen un *largo período de vida*.  
> Es necesario realizar *cambios* en el software para *corregir errores* en los *requisitos iniciales* y para implementar *nuevos requisitos* que surgen.  

> ---

> **💰 Cuestiones de Coste en la Evolución del Software**  
> Los cambios en el software deben evaluarse desde una perspectiva *técnica* y de *negocio*, asegurando que aporten *valor* a la organización, no solo mejoras aisladas.  
>   
> Dado que los *subsistemas* están interconectados, un cambio en uno puede afectar a otros, requiriendo *ajustes adicionales*.  
>   
> Además, la falta de *documentación* sobre las decisiones de diseño obliga a los responsables de mantenimiento a investigar el motivo detrás de las implementaciones originales.  
>   
> Con el tiempo, la *estructura* del software se degrada, aumentando los *costos de mantenimiento* y la *complejidad de los cambios*.  

> ---

> **💸 Coste del Mantenimiento**  
> Entre el 80% y el 90% del *presupuesto* de muchas empresas de informática se destina a mantenimiento.  
> - El mantenimiento de una *aplicación grande* puede consumir entre 2 y 4 veces más *recursos* que su *desarrollo inicial*.  
> - Estimar los *costes de mantenimiento* es una tarea *compleja*.  
> 
> [¿Porqué pagar un mantenimiento software?](https://www.mundoerp.com/blog/porque-pagar-mantenimiento-software-erp-crm-bi/)

> ---

> **🔮 Predicción del Mantenimiento**
> La aceptación o no de un cambio en un software/sistema depende de la mantenibilidad de los componentes afectados por dicho cambio.
> 
> *Aspectos a considerar*
>   - Mantenimiento previsto  
>   - Costes previstos de mantenimiento  
>   - Cambios previstos del sistema  
> - La implementación de los cambios del sistema tiende a degradar la estructura de dicho sistema y, por lo tanto, reduce su mantenibilidad.  
> 
> *Nº de peticiones de cambio*
> Para predecir cuántos cambios se solicitarán, es esencial entender la relación del sistema con su entorno.
> 
> | Factor                 | Descripción                                                                       |
> |------------------------|-----------------------------------------------------------------------------------|
> | Interfaces del sistema | A mayor cantidad y complejidad, mayor probabilidad de recibir peticiones de cambio. |
> | Requisitos volátiles   | Los requisitos relacionados con políticas y procedimientos tienden a cambiar más.  |
> | Procesos de negocio    | La evolución de estos procesos genera más solicitudes de cambio.                   |
> 
> *Mantenibilidad*
> La predicción de la mantenibilidad de un sistema se relaciona con el número y los tipos de relaciones entre sus componentes. Cuanto más complejo es un sistema o componente, mayor es el coste de mantenerlo.
> 
> Existen estudios sobre los diferentes tipos de complejidad (McCabe, 1976) y sobre la relación entre complejidad y mantenibilidad (Kafura y Reddy, 1987).
> 
> Reducir los costes de mantenimiento implica, en parte, reemplazar los componentes complejos.

---

## WordPress

> **🌐 ¿Qué es WordPress?**  
> WordPress es un sistema de gestión de contenido (CMS) de código abierto basado en PHP y MySQL. Permite a los usuarios crear y gestionar sitios web de manera sencilla.  
>   
> La versión 2 introdujo mejoras clave en flexibilidad y funcionalidades, consolidándose como uno de los CMS más populares.  
>   
> Con el *Proyecto Calypso*, WordPress dio un salto hacia una arquitectura moderna, mejorando la experiencia de usuario y permitiendo la administración de sitios a través de una interfaz basada en JavaScript desde cualquier lugar.
> 
> [Página Oficial de WordPress](https://wordpress.com/es/)

> ---

> **☁️ Implementación junto a AWS**  
> Implementar WordPress en AWS permite crear sitios web escalables y flexibles, aprovechando la infraestructura de nube de Amazon.  
>   
> Servicios como Amazon EC2 para alojamiento, Amazon RDS para bases de datos gestionadas y Amazon S3 para almacenamiento permiten construir una arquitectura robusta y altamente disponible.  
>   
> La integración con AWS incluye características avanzadas como autoescalado, balanceo de carga y seguridad.  

> ---

> **📐 WordPress AWS Reference Architecture**  
> La *WordPress AWS Reference Architecture* proporciona una guía recomendada para implementar WordPress en la nube de AWS, optimizando la escalabilidad, disponibilidad y seguridad.  
>   
> Esta arquitectura utiliza diversos servicios de AWS para crear un entorno eficiente con soporte para el tráfico variable y capacidades de recuperación ante desastres.  
>   
> La configuración recomendada incluye balanceo de carga (ELB), servidores EC2, bases de datos RDS y almacenamiento en S3 para garantizar un rendimiento superior y alta disponibilidad.

---

## Procesos Diferenciados vs Único Proceso

> **⚙️ Procesos Diferenciados**  
> Históricamente, ha existido una diferenciación entre el proceso de desarrollo y el proceso de evolución (o mantenimiento) del software. El proceso de desarrollo siempre se ha considerado más atractivo por ser creativo y por involucrar la creación de algo nuevo. Por el contrario, el mantenimiento solía verse como una tarea monótona y menos interesante.  
> 
> Sin embargo, en la actualidad, esta diferencia entre desarrollo y mantenimiento tiende a ser irrelevante. Gran parte del desarrollo actual se enfoca en adaptar el software existente o en hacer evolucionar los sistemas.  
> Esto se debe a que, en el pasado, se hicieron grandes inversiones en desarrollos desde cero, y ahora es más rentable modificar y evolucionar esos sistemas que crear nuevos desde el inicio.  
> 
> Si bien el costo del mantenimiento a veces es mayor que el del desarrollo inicial, el proceso de desarrollo desde cero conlleva muchos más desafíos y problemas que el mantenimiento.

---

> **🔄 Proceso Único de Evolución**  
> Hoy en día, se ve el desarrollo y el mantenimiento como un proceso único y continuo de evolución. Este enfoque integra tanto actividades de desarrollo como de mantenimiento, asegurando que el sistema evolucione de manera continua a lo largo de su ciclo de vida.  
> 
> De esta forma, el ciclo de vida del software se apoya en un proceso continuo de evolución, con pasos que incluyen:
> 
> - **🔑 Definir los requisitos del sistema**
> - **📊 Valorar los sistemas existentes**
> - **🔧 Proponer cambios en el sistema**
> - **🛠️ Modificar el sistema**
> - **🔄 Nuevo sistema / Sistemas existentes**

---

> **📈 Comprensión del Proceso Evolutivo**  
> Es fundamental entender que los cambios y modificaciones en el software son inevitables para mantener la utilidad y relevancia del sistema. El desarrollo y la evolución pueden integrarse en un único modelo continuo, como el **modelo en espiral**.  
> 
> Además, es importante conocer los diferentes tipos de mantenimiento del software y los factores que influyen en los costos asociados.  
> 
> Algunos puntos clave a tener en cuenta son:
> 
> - **⚙️ Conocimiento de los procesos involucrados**: Comprender cómo se lleva a cabo la evolución del software en cada etapa.
> - **🗂️ Evaluación de sistemas heredados**: Evaluar si los sistemas heredados deben desecharse, mantenerse, re-desarrollarse o reemplazarse, considerando sus beneficios y costos.

---

## Procesos de Evolución

> **🎯 Objetivos Docentes**  
> Los procesos de evolución del software son fundamentales para adaptarse a las necesidades cambiantes de las organizaciones. Los objetivos docentes deben centrarse en lo siguiente:
> 
> - **🏢 Dependencia de la organización**:  
>   Los procesos de evolución dependen de cada organización, considerando el software a mantener, el proceso de desarrollo utilizado y el personal involucrado (formal e informal).
> 
> - **🔄 Peticiones de cambio**:  
>   Las peticiones de cambio son los principales conductores de los procesos de evolución del software en todas las organizaciones. Son esenciales para adaptar el sistema a las necesidades cambiantes.
> 
> - **💡 Tipos de propuestas de cambio**:
>   - 🔄 *Requisitos ya existentes no integrados aún*.
>   - 🆕 *Peticiones de nuevos requisitos*.
>   - ⚠️ *Reparaciones de errores*.
>   - ✨ *Ideas nuevas y mejoras indicadas por el equipo de desarrollo*.
> 
> Los procesos de identificación de cambios y evolución del sistema son cíclicos y continúan durante toda la vida del sistema. Esto asegura que el sistema se mantenga alineado con los objetivos organizacionales.

> ---

> **📅 Ciclo de Implementación de Cambios**
> El ciclo de implementación de cambios es crucial para garantizar que el sistema se mantenga alineado con las necesidades del negocio y con los cambios tecnológicos. Las fases del ciclo incluyen:
> 
> - **📋 Análisis de requisitos**
> - **💡 Cambios propuestos**
> - **🔄 Actualización de requisitos**
> - **🛠️ Desarrollo de software**
> 
> *🔄 Cambio del software y entregas sucesivas del sistema.*
> 
> **📂 Gestión de Configuraciones**: Aseguramiento de versiones correctas en cada entrega para garantizar la coherencia del sistema.

---

## Mantenimiento y su Clasificación

> **🔧 Tipos de Mantenimiento**
> 
> *🛠️ Mantenimiento perfectivo*  
> Actividades para mejorar o añadir nuevas funcionalidades requeridas por el usuario.
> 
> *🔄 Mantenimiento adaptativo*  
> Actividades para adaptar el sistema a cambios en su entorno tecnológico (hardware o software).
> 
> *⚠️ Mantenimiento correctivo*  
> Actividades para corregir defectos en el hardware o en el software detectados por los usuarios durante la explotación del sistema.
> 
> *🔒 Mantenimiento preventivo*  
> Actividades para facilitar el mantenimiento futuro del sistema.

---

## Legacy Systems

> **🏚️ Sistemas Socio-Técnicos**
> Un sistema es una colección de componentes interrelacionados que trabajan conjuntamente para cumplir un objetivo (lavadora, sistema de control del tráfico aéreo, semáforo de circulación, bicicleta…).
> 
> Los sistemas que incluyen software son de dos tipos:
> 
> *💻 Sistemas técnico-informáticos*  
> Son sistemas que incluyen hardware y software pero no procesos ni procedimientos, como los móviles, procesadores de texto, lavadoras, etc. Los individuos usan estos sistemas para algún fin, pero ese fin no es parte del sistema.
> 
> *🌐 Sistemas socio-técnicos*  
> Son sistemas que comprenden uno o más sistemas técnicos pero que además incluyen el conocimiento de cómo debe usarse el sistema para alcanzar algún objetivo más amplio.
> 
> Tienen definidos procesos operativos, incluyen personas como parte inherente del sistema, están gobernados por políticas y reglas organizacionales y pueden verse aceptados por restricciones externas como leyes nacionales y políticas reguladoras.

> ---

> **🌐 Características de los Sistemas Socio-Técnicos**
> 
> *✨ Propiedades emergentes*  
> Las propiedades de los componentes individuales más las relaciones entre ellos. Por ello, no pueden probarse hasta que no esté el sistema completo.
> 
> *🔄 No deterministas*  
> El comportamiento del sistema depende de operadores humanos, por lo que no siempre se obtiene la misma salida ante una entrada determinada.
> 
> *🎯 Grado de apoyo a los objetivos organizacionales*  
> El grado de apoyo a los objetivos no solo depende del sistema, sino también de la estabilidad de los objetivos, las relaciones y cómo las personas interpretan esos objetivos. Una nueva dirección en la organización puede reinterpretar los objetivos y transformar un sistema exitoso en un fracaso.

> ---

> **🔄 Evolución en los Sistemas Heredados**  
> Un sistema heredado es un sistema socio-técnico que sigue siendo útil o fundamental para una organización, pero que ha sido desarrollado utilizando tecnología o métodos obsoletos.
> 
> Estos sistemas, aunque obsoletos, siguen realizando funciones críticas para el negocio, por lo que deben ser mantenidos.
> 
> Las grandes organizaciones suelen tener sistemas heredados que deben ser extendidos para adaptarse a las nuevas prácticas de negocio (como comercio electrónico, sistemas bancarios, control aéreo, distribución de productos, etc.).  
> 
> Sin embargo, el mantenimiento y actualización de estos sistemas suele requerir presupuestos limitados, por lo que es necesario evaluar realísticamente cuál es la estrategia de evolución más adecuada.

> ---

> **🛠️ Estrategias de Evolución (I)**
> 
> *❌ Desechar completamente el sistema*
>   Cuando el sistema ya no constituye una contribución efectiva a los procesos de negocio.
> 
> *🔄 Dejar el sistema sin cambios y continuar con un mantenimiento regular*
>   Esta opción es útil cuando el sistema sigue siendo necesario y muy estable, y solo se requieren pequeños cambios.

> ---

> **🔄 Estrategias de Evolución (II)**
> 
> *🔧 Reemplazar todo o parte del sistema con un nuevo sistema*
> Esta opción es adecuada cuando factores como el nuevo hardware hacen que el sistema antiguo ya no pueda seguir funcionando.
> 
> *🔨 Reingeniería del sistema para mejorar su mantenibilidad*
> Cuando un sistema ha sido modificado continuamente, su calidad puede haberse degradado, por lo que es necesario hacer cambios para restaurar su mantenimiento.

---

## Evaluación de los Sistemas Heredados

> **🔍 Perspectiva técnica y de negocio**
> La evaluación de un sistema heredado no solo implica aspectos técnicos, sino también de negocio. Un análisis detallado de su calidad y su valor dentro de la organización ayudará a tomar decisiones informadas sobre su mantenimiento o reemplazo.

> ---

> **📉 Cuatro posibles categorías**
> 
> **1. Baja calidad y bajo valor de negocio**
> *Caro mantenimiento* y *beneficios pequeños*. El sistema no contribuye de manera significativa a los procesos de negocio y no justifica el costo de su mantenimiento.
> - **Acción**: Desechar el sistema.
>   
> **2. Baja calidad y alto valor de negocio**  
> *Caro mantenimiento* pero *grandes beneficios*. El sistema es esencial para el negocio, aunque su mantenimiento es costoso.
> - **Acción**: Mejorar o reemplazar el sistema, ya que su valor para el negocio es alto.
>   
> **3. Alta calidad y bajo valor de negocio**  
> *Barato mantenimiento* pero *beneficios pequeños*. El sistema tiene un buen rendimiento, pero su impacto en el negocio es limitado.
> - **Acción**: Si los cambios son costosos, desechar el sistema.
>   
> **4. Alta calidad y alto valor de negocio**  
> *Barato mantenimiento* y *grandes beneficios*. El sistema es crucial para el negocio y su mantenimiento es económico.
> - **Acción**: Continuar con el mantenimiento y optimización.

> ---

> **📊 Evaluación del valor de negocio**  
> Es fundamental evaluar qué tan valioso es el sistema para la organización. Aquí algunos criterios clave a considerar:
> 
> *📉 Uso del sistema*  
> Si el uso del sistema es bajo, el valor del negocio también lo será.
> 
> *🔄 Procesos de negocio soportados*  
> Si el sistema no puede soportar nuevos procesos de negocio o adaptarse a cambios, su valor de negocio será bajo.
> 
> *⚠️ Confiabilidad del sistema*  
> Si el sistema no es confiable y puede afectar a los clientes o operaciones del negocio, afectará directamente al valor del negocio.
> 
> *🎯 Salidas del sistema*  
> Si las salidas del sistema son críticas y contribuyen al éxito del negocio, el valor será alto. Si estas salidas no se usan regularmente o pueden ser obtenidas de otra manera, el valor de negocio será bajo.

> ---

> **⚙️ Evaluación de la perspectiva técnica (I)**  
> La evaluación técnica se enfoca en la aplicación misma del sistema y su entorno, incluyendo tanto el software como el hardware de soporte. Algunos aspectos clave de la evaluación técnica son:
> 
> *📝 Comprensión del código fuente*  
> ¿El código es comprensible? ¿Está bien estructurado y documentado?  
> 
> *📚 Documentación*  
> ¿Existe documentación del sistema? ¿Está completa y actualizada?
> 
> *💾 Modelo de datos*  
> ¿Existe un modelo de datos del sistema? ¿Se gestionan los datos adecuadamente o están duplicados?  
> ¿Son los datos consistentes y actuales?
> 
> *🚀 Rendimiento*  
> ¿El sistema tiene un rendimiento adecuado?  
> ¿Repercute negativamente en la experiencia del usuario?
> 
> *💻 Lenguajes de programación*  
> ¿Se utilizan lenguajes de programación modernos o obsoletos?  
> ¿Son compatibles con las herramientas y tecnologías actuales?
> 
> *🔧 Gestión de configuraciones*  
> ¿Están gestionadas todas las versiones del sistema?  
> ¿Existen descripciones de las versiones de los componentes del sistema actual?
> 
> *🧪 Datos de prueba*  
> ¿Existen conjuntos de datos de prueba adecuados para el sistema?  
> ¿Se realiza el seguimiento de las pruebas de regresión?
> 
> *👨‍💻 Habilidades del personal*  
> ¿El personal tiene las capacidades necesarias para mantener y gestionar el sistema?  
> ¿Cuántas personas comprenden completamente el sistema?

> ---

> **⚙️ Evaluación de la perspectiva técnica (II)**  
> Además de los aspectos técnicos de la aplicación, se debe evaluar el entorno en el que el sistema opera. Esto incluye el hardware, el software de soporte, la estabilidad del proveedor y otros factores clave que impactan su sostenibilidad:
> 
> *🏢 Estabilidad del proveedor*  
> ¿El proveedor del sistema sigue ofreciendo soporte?  
> ¿Existen garantías de continuidad o proveedores alternativos disponibles?
> 
> *⚠️ Tasas de fallos de ejecución*  
> ¿El hardware falla con frecuencia?  
> ¿El software de soporte es confiable o presenta errores frecuentes?
> 
> *⏳ Edad del sistema*  
> ¿Cuánto tiempo lleva en funcionamiento el sistema?  
> ¿Es el hardware o el software obsoleto?  
> 
> *🚀 Rendimiento del sistema*  
> ¿El sistema sigue siendo eficiente y cumple con los requisitos de rendimiento?  
> ¿Impacta el rendimiento en los usuarios?
> 
> *💸 Costes de mantenimiento*  
> ¿El mantenimiento del hardware o las licencias de software son caros?  
> 
> *🔌 Interoperabilidad*  
> ¿El sistema tiene problemas de interfaz con otros sistemas?  
> ¿Es difícil integrar el software de aplicación con otros sistemas de soporte?

---