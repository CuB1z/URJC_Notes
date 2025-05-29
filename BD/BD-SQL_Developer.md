---
tags: URJC URJC_BD
---

# SQL Developer

---

## Tabla de Contenidos

1. [¿Qué es SQL Developer?](#¿Qué%20es%20SQL%20Developer?)
2. [Atributos](#Atributos)
3. [Relaciones](#Relaciones)

---

## ¿Qué es SQL Developer?

> **📘 Descripción general**
> **Oracle SQL Developer** es una herramienta gráfica gratuita proporcionada por Oracle que facilita el desarrollo y gestión de bases de datos. Permite ejecutar consultas SQL, modelar datos, crear y modificar estructuras de base de datos, y administrar objetos de forma intuitiva.

> ---

> **🧩 Módulo Data Modeler**
> **SQL Developer Data Modeler** es un componente integrado que permite diseñar modelos entidad-relación (ER), generar scripts DDL y visualizar de forma gráfica las relaciones y estructuras de una base de datos. Es especialmente útil para el diseño conceptual, lógico y físico de sistemas de información.

---

## Atributos

> **#️⃣ Clave primaria**
> El símbolo `#` al inicio del atributo indica que es una **clave primaria**, utilizada para identificar de forma única cada registro de una tabla.

> ---

> **❗ Atributo obligatorio**
> El símbolo `*` representa que el atributo **no puede ser nulo**, es decir, su valor es **obligatorio** en todos los registros.

> ---

> **⭕ Atributo opcional**
> El símbolo `o` indica que el atributo **puede ser nulo**, por lo tanto, su inclusión en el registro es **opcional**.

> ---

> **🔐 Atributo único**
> La letra `U` señala que el atributo debe tener un **valor único** en cada fila, aunque **no sea clave primaria**.

---

## Relaciones

> **📎 Cardinalidad mínima**
> Se determina **mirando el lado de la entidad**. La simbología utilizada es:
>
> - `Línea discontinua` → **Mínimo = 0**
> - `Línea continua` → **Mínimo = 1**

> ---

> **🔁 Cardinalidad máxima**
> Se analiza **observando el lado opuesto de la entidad**. Las representaciones son:
>
> - `Línea continua` → **Máximo = 1**
> - `Pata de gallo` → **Máximo = N** (muchos)

---