---
tags: URJC URJC_SI
---

# Tema 2 - Seguridad Informática

---

## Tabla de Contenidos

1. [Vulnerabilidades](#Vulnerabilidades)
2. [Análisis de Vulnerabilidades](#Análisis%20de%20Vulnerabilidades)
3. [Exploits](#Exploits)
4. [Amenazas](#Amenazas)
5. [Riesgos](#Riesgos)
6. [Metodologías de Análisis de Riesgos](#Metodologías%20de%20Análisis%20de%20Riesgos)
7. [Metodologías de Desarrollo Seguro](#Metodologías%20de%20Desarrollo%20Seguro)
8. [Microsoft SDL](#Microsoft%20SDL)
9. [Respuesta ante Incidentes](#Respuesta%20ante%20Incidentes)

---

## Vulnerabilidades  

> **📖 Definición**  
> Una **vulnerabilidad** es una debilidad, fallo o “agujero de seguridad” en un sistema que permite la materialización de una amenaza.  
>  
> **🔄 Ciclo de vida de una vulnerabilidad**  
> Una vulnerabilidad atraviesa las siguientes fases desde su descubrimiento hasta su resolución:  
>  
> 1. **🕵️ Detección y explotación**
> Identificación de la vulnerabilidad y desarrollo de exploits.
> 
> 2. **🏷️ Registro (CVE-ID)**
> Documentación oficial en bases de datos de seguridad.
> 
> 3. **🛠️Búsqueda de solución**
> Análisis del problema y desarrollo de medidas correctivas.
> 
> 4. **🔄 Generación de parche**
> Implementación y distribución de una actualización o nueva versión del código.

> ---

> **🚨 Top 10 Vulnerabilidades según OWASP**  
> El *Open Web Application Security Project (OWASP)* define las 10 vulnerabilidades más críticas en aplicaciones web:
> 
> 1. 🔑 Brechas en el control de acceso  
> 2. 🔐 Fallos criptográficos  
> 3. 💉 Inyecciones (SQL, NoSQL, OS, LDAP)  
> 4. 🎭 Diseños no seguros  
> 5. ⚙️ Malas configuraciones de seguridad  
> 6. 🏚️ Uso de componentes vulnerables o desactualizados  
> 7. 🆔 Fallos de identificación y autenticación  
> 8. 📊 Fallos en la integridad de los datos y del sistema  
> 9. 📉 Fallos en la monitorización y "logging"  
> 10. 🌐 Server-Side Request Forgery (SSRF)

> ---

> **🔎 CVE-ID (*Common Vulnerabilities and Exposures*)**  
> Estándar de nomenclatura para identificar vulnerabilidades que facilita el intercambio de información entre bases de datos y herramientas de seguridad.
> 
> [Más información en CVE](https://cve.mitre.org/index.html)
>
> **📜 Para registrar una vulnerabilidad se deben superar tres etapas:**
> 
> 1. **🔬 Tratamiento**  
> El *CVE Content Team* analiza, investiga y procesa las solicitudes de registro de nuevas vulnerabilidades.
> 
> 1. **🏷️ Asignación del CVE-ID**  
>    - El CVE-ID puede ser solicitado por cualquier persona.  
>    - Las grandes compañías suelen reservar un “lote” de IDs al año.  
>    - El *CVE Content Team* también puede solicitar el CVE-ID.
>      
> 3. **📤 Publicación**  
> La vulnerabilidad se agrega a la lista, se publica en la web, se mejora la descripción, se añaden nuevas referencias, etc.
>
> **❌ Eliminación de un CVE-ID**  
> Es posible que algún CVE-ID sea eliminado de la lista por los siguientes motivos:  
> - Si una vulnerabilidad ya ha sido registrada con otro CVE-ID.  
> - Si un análisis posterior demuestra que la vulnerabilidad no existe.  
> - Si el informe relacionado con la vulnerabilidad debe ser reformulado.

> ---

> **🌐 NVD (National Vulnerability Database)**  
> La National Vulnerability Database (NVD) es una base de datos mantenida por el gobierno de los Estados Unidos que contiene información sobre vulnerabilidades de software y hardware.
> 
> Está diseñada para proporcionar una única fuente accesible para buscar información sobre vulnerabilidades y ofrecer puntajes CVSS para ayudar a evaluar su gravedad.
> 
> [NVD](https://www.nist.gov/)  

> ---

> **📊 CVSS - Common Vulnerability Scoring System**  
> El Common Vulnerability Scoring System (CVSS) es un sistema estandarizado para medir la gravedad de las vulnerabilidades de seguridad.
> 
> CVSS permite asignar un puntaje a una vulnerabilidad basándose en factores como su facilidad de explotación, el impacto potencial y la posibilidad de mitigación.
> 
> El puntaje se utiliza para priorizar las vulnerabilidades en función del riesgo que representan para las organizaciones.
> 
> [CVSS Calculator](https://nvd.nist.gov/vuln-metrics/cvss/v3-calculator)  

> ---

> **📚 Otras bases de datos**  
> A nivel nacional, también disponemos de una base de datos, o un listado de vulnerabilidades en castellano, desarrollado por *INCIBE*.
> 
> INCIBE, dependiente del Ministerio de Asuntos Económicos y Transformación Digital de España, ofrece servicios de ciberseguridad para ciudadanos, empresas y administraciones públicas.
> 
> [INCIBE: Instituto Nacional de CiberSeguridad](https://www.incibe-cert.es/)  

> ---

> **⚠️ Zero Day**  
> El **Día 0** es el día en que una vulnerabilidad se hace pública.  
> 
> *Ataque de día 0*
> Es el ataque que aprovecha esta vulnerabilidad antes de que se publique una solución oficial. Estos ataques son especialmente peligrosos, ya que las organizaciones no han tenido tiempo de prepararse ni de implementar parches de seguridad.
> 
> *Tiempo de reacción*
> Es el tiempo que transcurre entre el Día 0 y la publicación de una solución a la vulnerabilidad. Un corto tiempo de reacción es crítico para minimizar los daños de un ataque de día 0.

> ---

> **📝 Vulnerabilidades**  
> También tenemos un listado de las debilidades del software desarrollado por la **CWE: Common Weakness Enumeration**.
> 
> CWE es un sistema que clasifica y describe las debilidades de software que podrían ser aprovechadas para ejecutar ataques. Proporciona una referencia útil para desarrolladores y profesionales de seguridad para identificar y corregir debilidades comunes en sus aplicaciones.
> 
> [CWE - Página Oficial](https://cwe.mitre.org/)  

---

## Análisis de Vulnerabilidades

> **🔍 Análisis de Vulnerabilidades**  
> El análisis de vulnerabilidades es un aspecto crítico para la evaluación del riesgo y es fundamental en cualquier **Plan Director de Seguridad** o **iniciativa de fortificación**.
> 
> Este análisis establece un punto de partida para identificar y mitigar posibles amenazas, pero el principal problema es que es una **“carrera” constante**. Existen múltiples metodologías y herramientas disponibles para realizarlo.

> ---

> **🖤 Enfoque de Caja Negra**  
> En este enfoque, el auditor o analista trabaja sin conocimiento previo del sistema objetivo, simulando un ataque real desde una perspectiva externa.
> 
> La principal ventaja de este método es que se pueden identificar síntomas de vulnerabilidades, aunque no las causas.
> 
> Sin embargo, este enfoque puede generar un número significativo de **falsos negativos**, es decir, no detectar como un problema algo que realmente sí lo es.

> ---

> **🤍 Enfoque de Caja Blanca**  
> Este enfoque se basa en un conocimiento completo del sistema objetivo por parte del auditor o analista. Aquí se pueden identificar los orígenes de las vulnerabilidades, lo que permite un análisis más profundo de las debilidades.
> 
> La ventaja de este enfoque es la capacidad de identificar vulnerabilidades de manera detallada, pero puede generar muchos **falsos positivos**, es decir, detectar como un problema algo que realmente no lo es.

> ---

> **🤎 Enfoque de Caja Gris**  
> El enfoque de caja gris combina lo mejor de los dos enfoques anteriores. El auditor o analista no trabaja completamente a ciegas (como en la caja negra), pero tampoco tiene acceso total al sistema (como en la caja blanca).
> 
> Este enfoque intermedio busca equilibrar la detección precisa de vulnerabilidades mientras minimiza la generación de falsos positivos o negativos.

---

## Exploits

> **📖 Definición**  
> Un **exploit** es el acto de explotar o aprovechar una vulnerabilidad de seguridad en un sistema de información para conseguir un comportamiento no deseado.  
>  
> En el ámbito informático, un **exploit** puede ser un fragmento de software creado con el propósito de aprovechar una vulnerabilidad de seguridad para obtener acceso no autorizado o causar efectos no deseados en el sistema.  
>  
> El **exploit** es la técnica base utilizada en los ataques contra aplicaciones vulnerables.  
>  
> **💻 Exploiting** es la capacidad de convertir vulnerabilidades o brechas de seguridad en una entrada real hacia un sistema ajeno.  
>  
> Aunque menos común, los exploits pueden encontrarse en formato **🌐 web** o como **📜 scripts**.


> ---

> **🔍 Tipos de Exploits**
> 
> *🌐 Remotos*
> Se utilizan para atacar sistemas a través de una red, permitiendo la conexión con el sistema de la víctima.
> 
> *💻 Locales*
> El exploit se ejecuta directamente en el propio equipo de la víctima.

> ---

> **💻 ShellCode**  
> Es una cadena de códigos hexadecimales que contiene instrucciones en lenguaje ensamblador.
> 
> Si esta cadena de códigos se introduce en una zona específica de la memoria y redireccionamos el flujo del programa a esa zona, entonces podremos ejecutar dicho **ShellCode**.  
> 
> Se inyecta código ejecutable en espacio de memoria habilitado para guardar datos del usuario, luego se usa un fallo de programación para redireccionar al microprocesador hacia una nueva zona manipulada y se ejecutan las instrucciones recibidas.  
>  
> El código más habitual es el que abre una **💻 shell** o consola, para ejecutar desde ahí los comandos que se requieran.  
>  
> Pero, necesitamos **🔄 redirigir** el flujo de ejecución del programa a la región de memoria donde tenemos ubicado el **ShellCode**.
> Esto se puede hacer de muchas maneras, tal vez, las más conocidas son:  
> - 📈 Stack Overflow
> - 🛠️ Heap Overflow
> - 📦 Buffer Overflow

> ---

> **🛠️ Heap Overflow**  
> El **Heap** es un espacio de memoria destinado al almacenamiento de datos, que a diferencia del **stack**, crece desde las posiciones más bajas a las más altas de la memoria.  
>  
> El **Heap** no se almacena en ningún registro de instrucción o contador de programas.  
>  
> Un **Heap Overflow** se produce cuando un buffer que ha sido reservado por librerías como **malloc**, **calloc** o **realloc**, puede ser desbordado por datos suministrados de forma arbitraria.

> ---

> **📚 Stack Overflow**  
> La **Pila (Stack)** se usa cada vez que se realiza una llamada a una función o procedimiento.  
>  
> Se almacena mucha información, incluyendo:  
> - Las variables internas  
> - Una serie de punteros  
> - La dirección de retorno  
> - Los punteros a los parámetros que se le pasan  
>
> **🎯 Ejemplo de Stack Overflow con código malicioso**  
> El atacante puede aprovechar un stack overflow para modificar la dirección de retorno de una función y redirigir la ejecución del programa a una parte de la memoria donde el código malicioso esté presente. A continuación, te mostramos un ejemplo de cómo se puede hacer esto con un código de ejecución:
> 
> ```c
> #include <stdio.h>
> #include <string.h>
> 
> void funcion_vulnerable() {
>    char buffer[8];
>     printf("Introduce tu nombre: ");
>     gets(buffer);  // Función vulnerable, no verifica los límites
>     printf("Hola, %s\n", buffer);
> }
> 
> int main() {
>    funcion_vulnerable();  // Ejecución de la función vulnerable
>     return 0;
> }
> ```

---

## Amenazas

> **📖 Definición**  
> Una **amenaza** es una acción que podría tener un efecto potencial negativo sobre un activo.  
> Puede afectar a la **confidencialidad**, **integridad** o **disponibilidad** del activo, aunque por sí misma no provoca daño, puesto que es necesario que exista una **vulnerabilidad** en el sistema que permita que se materialice.
> 
> *⚠️ Top amenazas (año 2024)*
> 1. 💻 Ransomware
> 2. 🦠 Malware
> 3. 🔐 Ingeniería social
> 4. 📊 Amenazas frente a datos
> 5. 💥 Amenazas sobre la disponibilidad: Ataques DDoS
> 6. 📰 Desinformación
> 7. 🔗 Ataques en la cadena de suministro

> ---

> **🌐 Los 7 Dominios de Seguridad**  
>  
> *🔒 Dominio de Usuario*
> Este dominio se ve afectado por la falta de conciencia sobre las políticas de seguridad, errores accidentales y actividades maliciosas intencionales, como la ingeniería social.  
>  
> *💻 Dominio de Trabajo (Workstation Domain)*
> Aquí, los problemas incluyen el acceso no autorizado, la introducción de software malicioso y las debilidades en el software instalado en los equipos.  
>  
> *🌐 Dominio de Red*
> Las amenazas en este dominio comprenden el acceso no autorizado a la red, la transmisión de datos sin cifrar y la propagación de malware.  
>  
> *🏢 Dominio de LAN a WAN (LAN-to-WAN Domain)*
> Los riesgos incluyen el acceso externo no autorizado a la red interna, el ingreso de software malicioso y firewalls mal configurados, con puertos abiertos innecesarios.  
>  
> *🌍 Dominio de WAN*
> En este dominio se destacan la transmisión de datos sin cifrar, ataques de denegación de servicio (DoS y DDoS) y la presencia de vulnerabilidades en el software.  
>  
> *🔑 Dominio de Acceso Remoto*
> Los ataques comunes son la fuerza bruta al acceso y la fuga de datos desde el acceso remoto o dispositivos de almacenamiento, además de accesos no autorizados a recursos. 
>  
> *🖥️ Dominio de Sistema*
> Los principales riesgos incluyen el acceso no autorizado, debilidades en el sistema operativo o software de aplicación, y la pérdida de datos debido a errores o desastres.

> ---

> **💥 Tipos de Ataques más Comunes**  
> Existen listas con los patrones de ataque más frecuentes, elaboradas por **CAPEC** (**Common Attack Pattern Enumeration and Classification**).
> 
> Esta lista incluye los ataques más comunes que se utilizan para explotar vulnerabilidades en sistemas de seguridad.

---

## Riesgos

> **📖 Definición**  
> El **riesgo** es la probabilidad de que ocurra un incidente de seguridad, lo cual debe ser evaluado considerando el impacto que tendría en el sistema.  
>  
> La **valoración de riesgos** nos permite ordenarlos, compararlos, priorizarlos.  
>  
> Los riesgos deben ser definidos con criterios claros para permitir su evaluación y aceptación, teniendo en cuenta la posible **pérdida** de alguno (o varios) de los pilares de la seguridad:  
> - 🔒 **Confidencialidad**  
> - 🛡️ **Integridad**  
> - ⚙️ **Disponibilidad**  
>  
> Además, existen tres tipos de riesgos:  
> - 🚨 **Potencial**, **inicial** o **intrínseco**
> 	Antes de aplicar las salvaguardas.  
> - ✅ **Efectivo**
> 	El que se da tras la aplicación de las salvaguardas.  
> - ⚠️ **Residual**
> 	Siempre permanecerá, aunque tengamos todas las salvaguardas aplicadas.  
>  
> Una vez que tenemos identificado un riesgo, tenemos **4 opciones**:
> 
> *✅ Aceptar*
> Si el impacto es muy bajo, o es menor que los costes para evitarlo, o si la probabilidad es muy baja.
> 
> *🚫 Evitar*
> Asegurarse de que el riesgo no tiene probabilidades de ocurrir. Ejemplo: Deshabilitar puertos USB para evitar virus.
> 
> *🔄 Transferir*
> Transferir la responsabilidad de los daños, generalmente mediante un seguro de amenazas.
> 
> *⚖️ Mitigar*
> Tomar medidas para reducir la probabilidad de que suceda o para minimizar el impacto si ocurre.

> ---

> **📖 ISO/IEC 27001**  
> El objetivo de esta norma es proteger la **confidencialidad**, **integridad** y **disponibilidad** de la información en una empresa.  
>  
> **¿Cómo lo hace?**
> 
> *🔍 Evaluando los riesgos*
> Identificando los posibles problemas que podrían afectar a la información.
> 
> *🛡️ Mitigando los riesgos*
> Definiendo las medidas necesarias para evitar que estos problemas se materialicen.
>  
> La **gestión del riesgo** implica identificar los riesgos más significativos que puedan afectar el desempeño de la entidad y priorizar las medidas a tomar para minimizar:  
> - 🚨 La probabilidad de que los riesgos se materialicen.  
> - ⚠️ El impacto en caso de que ocurra.

> ---

> **📖 Mosler**  
> El esquema de matrices en Mosler refleja la frecuencia, magnitud y efecto de un posible ataque, calculando un indicador preciso sobre la probabilidad de materialización de cualquier riesgo que pueda afectar el funcionamiento normal de la empresa.  
>  
> Este proceso consta de 4 fases secuenciales:  
> 1. Definición del riesgo  
> 2. Análisis del riesgo  
> 3. Evaluación del riesgo  
> 4. Cálculo de la clase de riesgo  
>    
> ---
>  
> **🔍 Análisis de cada Riesgo**  
> 
> *Criterio de Función (“F”)*
> Evalúa las consecuencias negativas o daños que afectan la actividad normal de la empresa.
> 
> *Criterio de Sustitución (“S”)*
> Grado de dificultad para sustituir los bienes.
> 
> *Criterio de Profundidad (“P”)*
> Valora la perturbación y efectos psicológicos que pueden afectar la imagen del grupo o la empresa.
> 
> *Criterio de Extensión (“E”)*
> Alcance de los daños o pérdidas causadas.
> 
> *Criterio de Agresión (“A”)*
> Probabilidad de que el riesgo se manifieste.
> 
> *Criterio de Vulnerabilidad (“V”)*
> Probabilidad de que se produzcan daños si el riesgo se materializa.
> 
> ---
>  
> **📊 Evaluación del Riesgo**
> 
> *Cálculo del carácter del Riesgo*
> - Importancia del Suceso: $I = F \times S$  
> - Daños Ocasionados: $D = P \times E$  
> - Carácter del Riesgo: $C = I + D$
>  
> *Cálculo de la Probabilidad*
> - Probabilidad: $PR = A \times V$
> 
> *Cálculo del Riesgo Considerado*
> -  Riesgo Considerado: $ER = C \times PR$

---

## Metodologías de Análisis de Riesgos

> **📖 Magerit**  
> Metodología de Análisis y Gestión de Riesgos de los sistemas de Información en las administraciones públicas.  
> Sigue la norma **ISO 31000** y es conocida como la **Metodología de la UE**, siendo la más utilizada en España.  
> 
> **🔍 Fases de Magerit**
> 
> *1️⃣ Identificación de activos*
> Se determinan los activos clave de la organización, su interrelación y su valor, evaluando el perjuicio (coste) que supondría su degradación.
>  
> *2️⃣ Análisis de amenazas*
> Se identifican los riesgos y amenazas a los que están expuestos los activos.
>  
> *3️⃣ Evaluación de salvaguardas*
> Se analizan las medidas de protección existentes y su eficacia para mitigar los riesgos.
>  
> *4️⃣ Estimación del impacto*
> Se define el daño potencial que sufriría un activo si una amenaza se materializa.
> 
> *5️⃣ Cálculo del riesgo*
> Se pondera el impacto con la tasa de ocurrencia (probabilidad de que suceda) de la amenaza.

> ---

> **📖 CRAMM**  
> Metodología de análisis de riesgos desarrollada por la Agencia Central de Comunicación y Telecomunicación del gobierno británico.  
> Es utilizada en la administración pública británica y en grandes empresas e instituciones.  
> 
> **🔍 Etapas de CRAMM**  
> 
> *1️⃣ Establecimiento de objetivos*  
> Se define el alcance del sistema evaluado e identifica los activos clave:  
> - 📡 Infraestructura: Hardware y redes.  
> - 🖥 Software: Aplicaciones y servicios.  
> - 📂 Datos e información.
>  
> También se valora su impacto económico en caso de:  
> - ❌ Indisponibilidad.  
> - 🔥 Destrucción.  
> - 🔓 Revelación o acceso no autorizado.  
> 
> *2️⃣ Evaluación del riesgo*  
> Se identifican amenazas y se estima su frecuencia:  
> - Impacto 1: Menos de una vez cada 10 años.  
> - Impacto 10: Al menos una vez al mes.  
>  
> Se evalúa la vulnerabilidad del sistema ante estas amenazas:  
> - Vulnerabilidad 1: <10% de probabilidad del peor escenario.  
> - Vulnerabilidad 10: 90-100% de probabilidad del peor escenario.  
>  
> Finalmente, se combina la frecuencia esperada con la vulnerabilidad para cuantificar el riesgo.  
> 
> *3️⃣ Selección de contramedidas*  
> Se priorizan las acciones de mitigación según el nivel de riesgo y se calcula la inversión máxima recomendada para cada amenaza en función del riesgo que mitiguen.  

---

## Metodologías de Desarrollo Seguro

> **📖 Metodología Software**  
> Conjunto de técnicas y métodos organizativos aplicados para diseñar software.  
> 
> **🔍 Tipos de metodologías**  
> - 📏 Cascada
> - 🔄 Espiral
> - 🏗 Prototipado
> - 📈 Incremental
> - ⚡ Agile
> 
> **⚠️ Problema principal**
> Estas metodologías no incluyen tareas enfocadas en la seguridad del sistema.  

> ---

> **🔐 Metodologías de Desarrollo Seguro**  
> En estas metodologías, la seguridad es el eje central del proceso. Algunas de las más utilizadas son:  
> - 🛡 Secure Software Development Life Cycle (SSDLC)
> - 🔍 Comprehensive Lightweight Application Security Process (CLASP) (OWASP)
> - 🏗 Secure Software Development Framework (SSDF) (NIST)  
---

## Microsoft SDL

> **🛡 Microsoft Security Development Lifecycle (SDL)**  
> Es un proceso de control de seguridad enfocado en el desarrollo de software, integrando medidas de seguridad y privacidad a lo largo de su ciclo de vida.  
> 
> **🔍 Beneficios del SDL**  
> - Ayuda a detectar vulnerabilidades en el software.  
> - Desarrolla técnicas y herramientas para mitigar riesgos de seguridad.  
> - Supervisa tendencias y amenazas para mejorar herramientas y procesos.  
> 
> **⚡ Versiones del SDL**  
> 
> *Versión rígida*
> Más adecuada para proyectos con requisitos estables que no cambian durante el desarrollo.
> 
> *Versión ágil*
> Se adapta a desarrollos incrementales, permitiendo ajustes continuos en el producto o sistema.

> ---

> **🔄 Microsoft SDL: Fases del Ciclo de Vida**  
> Microsoft SDL sigue un flujo estructurado para integrar la seguridad en el desarrollo de software:  
>  
> ---  
>  
> **📌 1. Fase de Requisitos**  
> - ✅ Revisión de planes de seguridad.
> - ✅ Integración de la seguridad en el proceso de desarrollo.  
> - ✅ Identificación de objetivos clave de seguridad.  
> - ✅ Análisis de la integración del software y verificación de requisitos.  
>  
> ---  
>  
> **📐 2. Fase de Diseño**  
> - 🏗 Definición de la estructura y arquitectura segura del software.  
> - 🔍 Identificación de componentes críticos y activos gestionados.  
> - ⚠️ Análisis de amenazas potenciales y su probabilidad de ocurrencia.  
> - 🛡 Establecimiento de medidas para reducir el riesgo.  
>  
> ---  
>  
> **💻 3. Fase de Implementación**  
> - 🖥 Codificación, prueba e integración del software.  
> - 📜 Uso de estándares de seguridad para minimizar vulnerabilidades.  
> - 🛠 Análisis estático del código y revisión para detectar errores de seguridad.  
>  
> ---  
>  
> **🛠 4. Fase de Verificación**  
> - 🔎 Revisión exhaustiva del código y ejecución de pruebas en zonas críticas.  
> - 🎯 Aplicación de técnicas como fuzz testing y análisis de código dinámico.  
>  
> ---  
>  
> **🚀 5. Fase de Lanzamiento**  
> - 🏁 Evaluación final de seguridad antes de la entrega.  
> - 🔐 Análisis del nivel de seguridad del producto y su resistencia a ataques.  
>  
> ---  
>  
> **🔎 6. Fase de Respuesta**  
> - 📡 Monitoreo del sistema en producción.  
> - 🆘 Respuesta ante incidentes de seguridad.  
> - 📈 Aprendizaje continuo para futuras mejoras.  

---

## Respuesta ante Incidentes  

> **⚠️ Incidente**  
> Un incidente es la manifestación de una amenaza, ya sea de forma intencionada o accidental.
> 
> Puede implicar accesos no autorizados, interrupciones en los servicios, pérdida de datos, o cualquier otra situación que comprometa la seguridad de la información.  

> ---  

> **💥 Ataque**  
> Un ataque es una acción deliberada que explota vulnerabilidades en un sistema con el fin de comprometer su integridad, disponibilidad o confidencialidad.
> 
> Generalmente, inicia con el uso de *exploits* o técnicas de intrusión y su objetivo puede ser obtener acceso no autorizado, robar información, alterar sistemas o causar daños.
> 
> Finaliza cuando se obtiene un resultado concreto, como la ejecución de código malicioso, la exfiltración de datos o la denegación de servicio (*DoS*).

> ---  

> **📊 Evento de Seguridad**  
> Un evento de seguridad es cualquier actividad que puede indicar un intento de ataque o una vulnerabilidad en el sistema.
>   
> Se trata de una acción específica sobre un objetivo o víctima (*target*) y queda registrado en los archivos de log, lo que permite su análisis posterior.
> 
> Puede ser clave para la detección temprana de ataques y la mitigación de riesgos antes de que se conviertan en incidentes críticos.

> ---

> **🛡️ CSIRT - Computer Security Incident Response Team**  
> El CSIRT se encarga de:  
> - 🔍 Mantenerse al día con vulnerabilidades y ataques.  
> - 📝 Realizar auditorías de sistemas y redes.  
> - ⚙️ Desarrollar soluciones para mitigar vulnerabilidades.  
> - 📚 Actualizar procedimientos y guías.  
> - 📡 Ser el punto de contacto para incidentes de seguridad.  
> - 🗂️ Documentar y catalogar incidentes.

> ---

> **🚨 Plan de Respuesta a Incidentes**  
> El plan se divide en 4 fases clave:
> 1. *🛑 Acción Inmediata*: Detener o minimizar el incidente.  
> 2. *🔍 Investigación*: Analizar el incidente.  
> 3. *🔄 Restauración*: Recuperar los recursos afectados.  
> 4. *📢 Reporte*: Informar a los canales adecuados.
> 
> **Puntos clave**
> - ⚡ Respuesta rápida y decisiva para minimizar el impacto.  
> - 🧑‍⚖️ Estrategia legal revisada y aprobada.  
> - 💰 Soporte financiero y ejecutivo de la compañía.  
> - 📝 Plan de acción factible y recursos adecuados.

---