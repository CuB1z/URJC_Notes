---
tags: URJC URJC_BD
---

# Tema 4 - Bases de Datos

---

## Tabla de Contenidos

1. [Introducción](#Introducción)
2. [Modelo Entidad-Relación Extendido](#Modelo%20Entidad-Relación%20Extendido)


---

## Introducción

> **📖 Modelado conceptual**
> Se realiza durante la etapa de **análisis**, donde se busca representar de forma simplificada la **información relevante del sistema**, sin preocuparse aún por detalles técnicos.

> ---

> **📖 Análisis y semántica**
> El proceso de análisis requiere **recoger información con alto contenido semántico**, independiente de los modelos de implementación.

> ---

> **📖 Implementación**
> Se desarrolla en la etapa de **diseño**, considerando aspectos de eficiencia y características del sistema gestor de base de datos.

> ---

> **💡 Origen del modelo E/R**
> El modelo **Entidad-Relación** fue propuesto por **Peter P. Chen** en 1976-77, como una herramienta para representar datos de forma abstracta y comprensible.

> ---

> **🎯 Objetivo**
> Proporcionar una **visión global** y **abstracción cercana al usuario** de los datos de una organización, **independiente del sistema o equipo informático** utilizado.

---

## Modelo Entidad-Relación Extendido

> **🧱Entidades**
> Una **entidad** representa un conjunto de objetos concretos del mundo real que comparten características comunes.  
> - Ejemplo: `Empleado`, con instancias como *José Martínez*.  
> - El conjunto actual de instancias se denomina **extensión** de la entidad.
> 
> **🏷️ Tipos de entidades**
> - **Regulares**: Existen por sí mismas.  
> - **Débiles**: Dependientes de una entidad fuerte para su existencia.

> ---

> **🔗 Interrelaciones**
> Son **asociaciones entre dos o más entidades** en las que cada instancia de interrelación se llama **ocurrencia**.
> 
> **🧾 Elementos clave**
> - Nombre  
> - Grado (número de entidades que participan)  
> - Papeles o roles de las entidades  
> - Tipo de correspondencia (cardinalidad)
> 
> **🔁 Tipos de correspondencia**
> - **1:1** $\to$ Un empleado dirige un único departamento  
> - **1:N** $\to$ Un departamento tiene varios empleados  
> - **N:M** $\to$ Un proyecto puede tener múltiples empleados y viceversa

> ---

> **🧮 Dominios y Valores**
> Conjunto de valores válidos para un atributo.  
> - Homogéneo, con nombre definido.  
> - Ejemplos: `Texto`, `Fecha`, `Entero`, listas cerradas.
> 
> **📖 Valor**
> Elemento específico perteneciente a un dominio, asignado a un atributo en una instancia.

---

> **🧬 Atributos**
> Son **características** de una entidad o una interrelación. Cada atributo toma valores de un dominio.
> 
> **📋 Tipos de atributos**
> - 🔑 **Identificador principal**: Distingue de forma única una entidad  
> - 🆔 **Identificadores alternativos**  
> - 🅾️ **Opcional**: Puede contener valores nulos  
> - 🧩 **Compuesto**: Formado por varios atributos (ej. nombre completo)  
> - 🔁 **Multivaluado**: Puede tener varios valores simultáneamente  
> - 🧮 **Derivado**: Se calcula a partir de otros atributos (ej. edad a partir de fecha de nacimiento)

> ---

> **⬆️ Jerarquías: Generalización y Especialización**
> 
> *📖 Generalización*
> Se identifican atributos comunes a varias entidades, agrupándolas en una **entidad de nivel superior**.
> 
> *📖 Especialización*
> Se crean **entidades hijas** a partir de una general, cuando ciertos atributos o comportamientos no aplican a todas las instancias.
> 
> **🔀 Combinaciones posibles**
> - *Parcial y solapada*  
> - *Parcial y exclusiva*  
> - *Total y solapada*  
> - *Total y exclusiva*

> ---

> **🚫 Restricciones de Participación**
> 
> *📖 Exclusividad*
> Un ejemplar **solo puede participar en una interrelación a la vez**.  
> - Ejemplo: Un profesor no puede impartir y recibir el mismo curso simultáneamente.
> 
> *📖 Inclusividad*
> Un ejemplar **debe participar en ambas interrelaciones asociadas**.  
> - Ejemplo: Un profesor que imparte también debe estar vinculado al curso que recibe.
> 
> *📖 Inclusión*
> La **existencia en una interrelación implica obligatoriamente pertenecer a otra**.  
> - Ejemplo: Todo profesor que imparte un curso debe también estar asignado al curso que recibe.

---