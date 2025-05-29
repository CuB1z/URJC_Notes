---
tags: URJC URJC_BD
---

# Tema 8 - Bases de Datos

---

## Tabla de Contenidos

1. [Introducción al Lenguaje SQL](#Introducción%20al%20Lenguaje%20SQL)
2. [Tipos de Sentencias SQL](#Tipos%20de%20Sentencias%20SQL)
3. [Tipos de Datos](#Tipos%20de%20Datos)
4. [Dominios](#Dominios)
5. [Opciones de Borrado y Modificación](#Opciones%20de%20Borrado%20y%20Modificación)
6. [Aserciones y Checks](#Aserciones%20y%20Checks)

---

## Introducción al Lenguaje SQL

> **📖 ¿Qué es SQL?**  
> SQL (Structured Query Language) es el lenguaje estándar para trabajar con bases de datos relacionales.  
> Es un lenguaje **declarativo**: se indica **qué** se desea obtener, no **cómo** hacerlo.
>
> - Permite operar con **conjuntos de registros**.
> - Trabaja sobre el modelo **relacional**.
> - Se divide en tres bloques funcionales principales.

---

## Tipos de Sentencias SQL

> **📘 Lenguaje de Definición de Datos (LDD)**  
> Permite definir o modificar la **estructura** de las bases de datos:
>
> - `CREATE`, `DROP`, `ALTER`, `ASSERTION`, etc.
>
> 🧪 *Ejemplos*
> ```sql
> CREATE TABLE empleados (...);
> DROP TABLE pedidos;
> ```

> ---

> **🧩 Lenguaje de Manipulación de Datos (LMD)**  
> Permite **modificar o consultar los datos** almacenados:
>
> - `INSERT`, `DELETE`, `UPDATE`, `SELECT`.
>
> 🧪 *Ejemplos*
> ```sql
> SELECT * FROM clientes;
> UPDATE productos SET precio = precio * 1.10;
> ```

> ---

> **🔐 Lenguaje de Control de Datos (LCD)**  
> Gestiona **permisos** de usuarios y el **control de transacciones**:
>
> - `GRANT`, `REVOKE`, `COMMIT`, `ROLLBACK`.
>
> 🧪 *Ejemplos*
> ```sql
> GRANT SELECT ON ventas TO usuario1;
> ROLLBACK;
> ```

---

## Tipos de Datos

> **🔢 Equivalencias ANSI SQL vs Oracle**
>
> | ANSI SQL                                               | Oracle                        |
> |--------------------------------------------------------|-------------------------------|
> | `CHARACTER(n)` / `CHAR(n)`                             | `CHAR(n)`                     |
> | `CHARACTER VARYING(n)` / `VARCHAR(n)`                  | `VARCHAR2(n)`                 |
> | `NATIONAL CHARACTER(n)` / `NATIONAL CHAR(n)`           | `NCHAR(n)`                    |
> | `NATIONAL CHAR VARYING(n)` / `NCHAR VARYING(n)`        | `NVARCHAR2(n)`                |
> | `INTEGER`, `INT`, `SMALLINT`                           | `NUMBER(digs, decs)`          |
> | `DECIMAL(digs, decs)`, `NUMERIC(digs, decs)`           | `NUMBER(digs, decs)`          |
> | `FLOAT`, `REAL`, `DOUBLE PRECISION`                    | `FLOAT(126)` / `FLOAT(63)`    |
> | `DATE`, `TIME`, `TIMESTAMP`, `INTERVAL`                | `DATE`, `TIMESTAMP`, `INTERVAL` |

---

## Dominios

> **⛳ Definición de Dominios**
>
> - Los **dominios** permiten definir un tipo de dato con restricciones asociadas.
> - Se usan en ANSI SQL para crear **tipos reutilizables**.
>
> 🧪 *Ejemplo*
> ```sql
> CREATE DOMAIN EdadPositiva AS INTEGER CHECK (VALUE > 0);
> ```
>
> ⚠️ En **Oracle**, los dominios **no están soportados** directamente. Para restricciones similares, se deben usar `CHECK`.

---

## Opciones de Borrado y Modificación

> **🗑️ Integridad Referencial**
>
> - Se define dentro de las **claves ajenas**.
> - Controlan cómo reacciona una tabla ante cambios en las tablas relacionadas.
>
> 🔧 *Opciones comunes*
> - `ON DELETE CASCADE`: Borra en cascada.
> - `ON DELETE SET NULL`: Asigna `NULL`.
> - `ON DELETE SET DEFAULT`: Valor por defecto.
> - `ON DELETE RESTRICT` / `NO ACTION`: Previene cambios si hay dependencias.
> 
> 🧪 *Ejemplo*
> ```sql
> CONSTRAINT fk_libro_editorial
> FOREIGN KEY (editorial_id)
> REFERENCES editorial(id)
> ON DELETE SET NULL
> ```

---

## Aserciones y Checks

> **☑️ Validación de Datos**
>
> - `CHECK`: Restringe valores dentro de la **misma tupla**.
> - `ASSERTION`: Permite restricciones **entre múltiples tablas**.
>
> 🧪 *Ejemplo con CHECK*
> ```sql
> CREATE TABLE empleado (
>   nombre VARCHAR2(50),
>   salario NUMBER CHECK (salario > 0)
> );
> ```
>
> ⚠️ Oracle **no permite ASSERTIONS**, por lo que restricciones entre tablas deben implementarse con **triggers** o en la lógica de aplicación.

---