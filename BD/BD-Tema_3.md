---
tags: URJC URJC_BD
---

# Tema 3 - Bases de Datos

---

## Tabla de Contenidos

1. [Modelo vs. Esquema](#Modelo%20vs.%20Esquema)
2. [Clasificación de los Modelos de Datos](#Clasificación%20de%20los%20Modelos%20de%20Datos)
3. [Propiedades de un Modelo de Datos](#Propiedades%20de%20un%20Modelo%20de%20Datos)
4. [Los Modelos de Datos en el Diseño de BD](#Los%20Modelos%20de%20Datos%20en%20el%20Diseño%20de%20BD)

---

## Modelo vs. Esquema

> **🧩 Modelo de Datos**
> Representación **técnica y detallada** de cómo se organizan los datos en una base de datos.  
> - Define tablas, campos, claves, relaciones y **restricciones de integridad**.  
> - Guía la **implementación real** de la base de datos.
> 
> 🎯 **Propósito del Modelo**
> - Diseñar y construir la BD de manera precisa  
> - Garantizar reglas y requisitos correctos en el almacenamiento de los datos

> ---

> **🗺️ Esquema de Datos**
> Visión **abstracta y general** de la estructura de una base de datos o sistema de información.  
> - Describe cómo los datos están **organizados**, **relacionados** y **accedidos**.
> 
> 🎯 **Propósito del Esquema**
> - Proporcionar una representación de alto nivel de la base de datos  
> - Describir **tablas, relaciones, tipos de datos y restricciones**

---

## Clasificación de los Modelos de Datos

> **📖 Tipos de modelos de datos según el nivel**
> - **🔹 Externo**: Vistas específicas para distintos usuarios o aplicaciones  
> - **🔸 Global**: Representación lógica única de toda la base de datos  
> - **🔻 Interno**: Descripción física del almacenamiento en disco

> ---

> **1️⃣ Modelos de Datos Conceptuales**
> - Representan el mundo real **sin considerar su implementación técnica**.  
> - Alto nivel de **abstracción** y **capacidad semántica**.  
> - Son ideales para el diseño lógico inicial y para facilitar la comunicación entre usuarios e informáticos.
> 
> 📌 *Ejemplos*:  
> - E/R (Entidad-Relación)  
> - UML  
> - KL-One

> ---

> **2️⃣ Modelos de Datos Convencionales o Lógicos**
> - Son **implementables** en SGBD comerciales.  
> - Poseen menor capacidad semántica y están centrados en la **estructura técnica**.  
> - Actúan como puente entre el diseño conceptual y el sistema físico.
> 
> 📌 *Ejemplos*:  
> - Modelo **Jerárquico**  
> - Modelo **Codasyl**  
> - Modelo **Relacional**

---

## Propiedades de un Modelo de Datos

> **📖 Propiedades Estáticas**
> Describen **qué elementos** pueden formar parte del modelo y cómo se relacionan:
> - 🔹 **Objetos** (tablas, entidades)  
> - 🔗 **Asociaciones** (relaciones)  
> - 📐 **Características** de los objetos  
> - 🌐 **Dominios** (tipos de datos válidos)  
> - 🚫 Elementos prohibidos y restricciones  
> - ✅ Restricciones de integridad (únicas, referenciales, semánticas)

> ---

> **⚙️ Propiedades Dinámicas**
> Se refieren al **comportamiento del modelo** frente a la manipulación de datos:
>
> *📍 Localización*
> Capacidad de identificar un registro o conjunto dentro del sistema.
> 
> *🛠️ Acción*
> Operaciones permitidas sobre dichos registros (modificación, consulta, eliminación).

---

## Los Modelos de Datos en el Diseño de BD

> **🧠 Rol clave en el proceso de diseño**
> Los modelos de datos son esenciales para:
>
> - Comprender y reflejar la **estructura lógica** del sistema  
> - Permitir una **implementación eficiente y precisa**  
> - Asegurar **consistencia**, **integridad** y **escalabilidad** de los datos  
> - Servir como puente entre la lógica del negocio y el diseño técnico
> 
> 🧩 El uso de diferentes modelos en diferentes fases del diseño (conceptual, lógico, físico) permite un desarrollo más ordenado y una base de datos más robusta y adaptable.

---