---
tags: URJC URJC_BD
---

# Tema 2 - Bases de Datos

---

## Tabla de Contenidos

1. [Sistemas de Ficheros](#Sistemas%20de%20Ficheros)
2. [Estructuras de un Fichero](#Estructuras%20de%20un%20Fichero)
3. [Operaciones sobre un Fichero](#Operaciones%20sobre%20un%20Fichero)
4. [Organización y Métodos de Acceso](#Organización%20y%20Métodos%20de%20Acceso)
5. [Índices en los Ficheros](#Índices%20en%20los%20Ficheros)
6. [Sistema de Gestión de Bases de Datos (SGBD)](#Sistema%20de%20Gestión%20de%20Bases%20de%20Datos%20(SGBD))
7. [Arquitectura ANSI/X3/SPARC](#Arquitectura%20ANSI/X3/SPARC)
8. [Independencia Física y Lógica](#Independencia%20Física%20y%20Lógica)

---

## Sistemas de Ficheros

> **📄 Fichero**
> Un **fichero** es una colección identificada de datos relacionados de forma lógica, almacenados en memoria no volátil y con una estructura definida.  
> - Está formado por **registros**.  
> - 🏢 *Ejemplo*: Fichero de empleados de una empresa.

> ---

> **📋 Registro**
> Un **registro** contiene información sobre una entidad concreta. Es la unidad básica que procesan las aplicaciones.  
> - Compuesto por **campos** con atributos de la entidad.  
> - 👤 *Ejemplo*: Datos de un empleado (nombre, DNI, etc.).

> ---

> **🔡 Campo**
> Unidad más pequeña de información en un registro. Cada campo tiene un **nombre** y un **tipo de dato**.  
> - 📝 *Ejemplo*: Nombre, dirección, número de empleado, etc.

---

## Estructuras de un Fichero

> **🧠 Estructura lógica**
> Es la forma en que los datos se organizan desde la perspectiva del **usuario**.  
> 🎯 Objetivos:
> - Representación fiel de la realidad  
> - Independencia entre la estructura física y lógica  
> - Facilidad de manipulación  
> - Reducción de redundancia

> ---

> **⚙️ Estructura física**
> Organización de los datos en el **soporte físico** (discos, cintas, etc.).  
> 🔧 Objetivos:
> - Optimización del espacio  
> - Rapidez de respuesta  
> - Reducción del mantenimiento  
> - Eficiencia de recursos

---

## Operaciones sobre un Fichero

> **✍️ Inserción**
> Añadir nuevos registros al fichero. Puede hacerse al final (modo secuencial) o en una posición específica (modo directo), dependiendo de la organización del fichero.

> ---

> **📖 Lectura**
> Recuperar datos de un registro o conjunto de registros. Puede ser secuencial (uno tras otro) o directa (accediendo a un registro específico mediante una clave o posición).

> ---

> **🔁 Actualización**
> Modificar el contenido de uno o más campos de un registro existente, conservando su posición en el fichero.

> ---

> **🗑️ Borrado**
> Eliminar un registro del fichero. Dependiendo de la estructura, puede implicar:
> - Eliminación lógica (marcar el registro como inactivo)
> - Eliminación física (eliminar completamente el registro y reorganizar el fichero)

---

## Organización y Métodos de Acceso

> **📚 Organización de registros**
> Forma en la que se almacenan los registros:
> 
> **Consecutiva**
>   - 🔁 *Seriales*: Sin orden lógico  
>   - 🧮 *Secuenciales*: Ordenados por una clave
> 
> **Direccionada**
>   - 🎯 *Directa*: Relación clave-dirección física  
>   - 🔐 *Dispersa (hashing)*: Dirección calculada con una función

> ---

> **🚪 Métodos de acceso**
> - **Secuencial**: Se accede a los registros siguiendo el orden en que están almacenados.  
> - **Directo**: Acceso directo a un registro específico, sin recorrer los anteriores.

> ---

> **📈 Elección del método**
> Depende de:
> - Si el archivo es **estático o dinámico**  
> - Frecuencia de operaciones (lectura, escritura, actualización)  
> - Elegir el método más eficiente según necesidades

---

## Índices en los Ficheros

> **🔎 Índices**
> Estructuras auxiliares que permiten acceder a los registros a través de campos específicos.  
> - Un fichero puede tener múltiples índices.  
> - Tipos:
>   - 🧾 *Índices simples ordenados*: Como el índice de un libro  
>   - 🌲 *Índices multinivel*: Jerarquías de índices, estructura tipo árbol

---

## Sistema de Gestión de Bases de Datos (SGBD)

> **🧭 Interfaz entre usuario y base de datos**
> El **SGBD** es el software que actúa como puente entre la base de datos y los distintos usuarios o niveles de la organización.

> ---

> **👥 Tipos de usuarios**
> - **Usuarios informáticos**: Programadores, administradores de bases de datos  
> - **Usuarios finales**: Profesionales que consultan y utilizan los datos

> ---

> **🔧 Funciones del SGBD**
> Proporciona datos seguros y consistentes mediante una serie de operaciones:
> - 🔧 *Esenciales*: Definición, manipulación y control de datos  
> - 📦 *Adicionales*: Copias de seguridad, estadísticas, importación de ficheros

---

## Arquitectura ANSI/X3/SPARC

> **📐 Modelo de tres niveles**
> La arquitectura ANSI/X3/SPARC define un modelo estándar para la estructura de las bases de datos, dividiendo su diseño en tres niveles independientes. Su objetivo principal es lograr **independencia entre los datos y los programas de aplicación**.

> ---

> **🔻 Nivel interno (físico)**
> Describe cómo se almacenan físicamente los datos en los dispositivos de almacenamiento.  
> - Se ocupa de estructuras físicas como bloques, índices o páginas.  
> - Optimiza el rendimiento, el uso del espacio y el acceso a los datos.

> ---

> **🔧 Nivel conceptual (lógico)**
> Representa la estructura lógica de toda la base de datos para la organización.  
> - Define entidades, relaciones, restricciones y reglas de integridad.  
> - Es independiente del modo en que los datos están almacenados físicamente.

> ---

> **👁️ Nivel externo (de vistas)**
> Es la capa más cercana a los usuarios.  
> - Cada usuario o aplicación puede tener su propia **vista personalizada** de los datos.  
> - Permite mostrar solo la información relevante para cada caso, ocultando el resto.

> ---

> **🎯 Objetivo clave**
> Separar los distintos niveles para permitir la **independencia lógica y física de los datos**, facilitando el mantenimiento, la evolución y la adaptación de las bases de datos sin afectar a los usuarios o aplicaciones.

---

## Independencia Física y Lógica

> **🎯 Objetivos del diseño de bases de datos**
> El diseño de una base de datos busca desacoplar los distintos niveles de definición y uso de los datos para conseguir:
>
> - 📂 **Independencia entre los datos y su estructura física**, permitiendo que los cambios en el almacenamiento no afecten a las aplicaciones.
> - 👤 **Vistas personalizadas** para diferentes usuarios, según sus necesidades.
> - 🧩 **Separación entre los programas de aplicación y la forma en que se almacenan los datos**, facilitando el mantenimiento y evolución del sistema.

> ---

> **🔍 Independencia de manipulación**
> Permite modificar la forma de acceder a los datos sin alterar los programas que los usan.
> 
> Se logra gracias a la separación entre la lógica de almacenamiento y los programas de aplicación.
> 
> Es influida por el **modelo de datos** adoptado (relacional, orientado a objetos, etc.).

> ---

> **🧾 Independencia de descripción**
> Permite cambiar las descripciones físicas (estructura de almacenamiento) sin afectar a las descripciones lógicas (tablas, vistas).
> 
> Es crucial para que el sistema sea **flexible y adaptable** a cambios tecnológicos sin afectar a la lógica del negocio.

---