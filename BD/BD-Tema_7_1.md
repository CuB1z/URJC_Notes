---
tags: URJC URJC_BD
---

# Tema 7.1 - Bases de Datos

---

## Tabla de Contenidos

1. [Glosario de equivalencias](#Glosario%20de%20equivalencias)
2. [Reglas de Transformación](#Reglas%20de%20Transformación)
3. [Reglas Básicas](#Reglas%20Básicas)
4. [Interrelaciones N:M](#Interrelaciones%20N%20M)
5. [Interrelaciones 1:N](#Interrelaciones%201%20N)
6. [Interrelaciones 1:1](#Interrelaciones%201%201)
7. [Transformación de Atributos y Claves](#Transformación%20de%20Atributos%20y%20Claves)
8. [Restricciones de Interrelación](#Restricciones%20de%20Interrelación)
9. [Transformación de Generalizaciones](#Transformación%20de%20Generalizaciones)

---

## Glosario de equivalencias

> En el proceso de transformación del **modelo Entidad-Relación (E/R)** al **modelo relacional**, utilizamos terminología equivalente que facilita la comprensión entre ambos enfoques. Aunque conceptualmente distintos, estos términos se corresponden de la siguiente manera:
>
> *🔁 Relación $\equiv$ Tabla, entidad o interrelación*
> En el modelo relacional, toda entidad o interrelación se convierte en una **relación**, que se representa como una **tabla**.  
>
> *📄 Atributo $\equiv$ Columna*
> Cada propiedad o característica de una entidad o relación se representa como un **atributo**, que se convierte en una **columna** en la tabla correspondiente.
>
> *📊 Tupla $\equiv$ Fila o elemento*
> Una **tupla** es una instancia concreta de una entidad, y corresponde a una **fila** dentro de la tabla que representa esa relación.

---

## Reglas de Transformación

> Transformar un modelo E/R a modelo relacional implica una serie de reglas sistemáticas que permiten representar toda la estructura lógica del sistema en forma de tablas. Este proceso, aunque robusto, conlleva ciertas limitaciones.
> 
> **⚠️ Pérdida de semántica**
>
> A diferencia del modelo E/R, el modelo relacional **no distingue explícitamente** entre **entidades** e **interrelaciones**.
> 
> En transformaciones de relaciones **1:N** o **1:1**, se puede **perder el nombre o el significado** de la interrelación, ya que esta suele integrarse como un atributo o clave ajena.
> 
> Este fenómeno genera una **pérdida semántica**, es decir, se pierde parte del contexto y la riqueza del modelo original al simplificarlo en términos puramente estructurales.

---

## Reglas Básicas

> Estas reglas fundamentales permiten establecer una correspondencia directa entre los elementos del modelo E/R y las estructuras del modelo relacional.
> 
> - Toda **entidad** se transforma en una **relación** o **tabla**.  
> - Los **atributos** de la entidad pasan a formar parte de dicha tabla como **columnas**.  
> - Si la entidad tiene una **clave primaria**, esta se traslada como tal al modelo relacional.  
> - Las **relaciones de generalización**, **atributos multivaluados** o **interrelaciones** requieren transformaciones más específicas (que se verán en secciones siguientes).

---

## Interrelaciones N:M

> Las interrelaciones con cardinalidad **muchos a muchos (N:M)** no pueden representarse directamente mediante claves ajenas, por lo que requieren una transformación especial.
> 
> **📖 Transformación**
>
> - Se crea una **nueva tabla** que representa la interrelación como una entidad independiente.
> - Esta tabla se conoce como una **tabla puente** o **intermedia**.
> 
> **🖌️ Representación**
>
> - Las **columnas** de esta tabla incluyen:
>   - Las **claves primarias** de las dos entidades que participan en la relación. Estas claves actúan también como **claves ajenas** hacia las tablas originales.
>   - Cualquier **atributo adicional** que la interrelación pueda tener.
>
> - La **clave primaria** de la tabla será **compuesta**, formada por las dos claves primarias de las entidades relacionadas.
>
> ✅ Esta técnica asegura la integridad de la relación N:M y conserva todos los datos relevantes de forma explícita.

---

## Interrelaciones 1:N

> **📖 Transformación**
> Las interrelaciones con cardinalidad **uno a muchos (1:N)** pueden representarse de dos formas en el modelo relacional, dependiendo de las necesidades semánticas del diseño:
>
> - ✅ **Propagación de clave ajena** dentro de una de las tablas existentes.  
> - 🗂️ **Creación de una tabla intermedia**, similar a las usadas para N:M, cuando se necesita mayor flexibilidad o se desea mantener semántica adicional.

> ---

> **🖌️ Propagación de clave**
> - Consiste en **añadir una clave ajena** en la tabla del lado N de la relación (es decir, donde puede haber múltiples instancias).
> - Esta clave ajena hace referencia a la clave primaria de la entidad del lado 1.
> 
> 📘 *Ejemplo*: Una relación 1:N entre `Editorial` y `Libro`:
> - Se añade una columna `editorial_id` en la tabla `Libro` que apunta a la clave primaria de `Editorial`.
> 
> ⚠️ Esta técnica es sencilla, pero puede suponer **una pérdida de semántica**, ya que no garantiza, por ejemplo, que cada editorial tenga al menos un libro asociado.

> ---

> **ℹ️ Condiciones según cardinalidad mínima**
> La **cardinalidad mínima** de la relación define si el nuevo atributo será:
> - `0` → **Opcional** (puede ser nulo): se marca con `*`  
> - `1` → **Obligatorio** (no puede ser nulo): se marca con `NN`

> ---

> **🖌️ Creación de una nueva tabla**
> En lugar de propagar la clave, se puede crear una tabla independiente que represente la interrelación.
> Esta opción es más recomendable cuando:
> - Se desea mantener explícitamente la **semántica de la relación**  
> - La interrelación incluye **múltiples atributos** propios  
> - Se quiere una estructura más modular y clara

---

## Interrelaciones 1:1

> **📖 Transformación**
> Las interrelaciones de tipo **uno a uno (1:1)** se tratan de manera similar a las 1:N, pero con una restricción adicional:
> - El atributo propagado debe ser **único** (`UNIQUE`), ya que una sola tupla del lado 1 debe relacionarse con una única tupla del otro lado.
> 
> 💡 En caso de duda, se recomienda **propagar la clave hacia el lado de la cardinalidad mínima 1**, para minimizar la pérdida de semántica.

---

## Transformación de Atributos y Claves

> **📖 Claves candidatas**
> - Todas las **claves candidatas** deben indicarse en el modelo relacional con la restricción **`UNIQUE`**, aunque solo una se elija como clave primaria.

> ---

> **📖 Atributos multivaluados**
> Los atributos que pueden tener **más de un valor** (como "teléfonos") no pueden almacenarse directamente en una sola columna.  
> Se transforman mediante la creación de una **nueva tabla** con la siguiente estructura:
> - Una columna con la **clave primaria** de la entidad original  
> - Una columna con los **valores individuales** del atributo multivaluado
> 
> 🔐 La clave primaria de esta nueva tabla será **compuesta** por ambas columnas.
> 
> 💡 Si se desea evitar que se repita el mismo valor entre diferentes entidades, se puede aplicar `UNIQUE` sobre la columna del valor.

> ---

> **📖 Atributos compuestos**
> - Se **descomponen** en atributos simples.  
> - Por ejemplo, un atributo `Dirección` se convierte en `Calle`, `Ciudad`, `Código Postal`, etc.

> ---

> **♻️ Reglas de borrado/modificación**
> - Cuando hay una **dependencia en la existencia o identificación**, se aplican restricciones `ON DELETE CASCADE` y `ON UPDATE CASCADE`.  
> - ⚠️ No se permite `SET NULL` en claves primarias, ya que estas **no pueden contener valores nulos**.

---

## Restricciones de Interrelación

> **📖 Exclusión e inclusión**
> Algunas restricciones propias del modelo E/R no se representan directamente en el modelo relacional. Para mantenerlas, es necesario:
>
> - Utilizar **`CHECK`**: Verifica condiciones sobre una única tabla  
> - Utilizar **`ASSERT`**: Permite definir restricciones sobre **varias tablas**, aunque no todos los SGBD lo implementan

---

## Transformación de Generalizaciones

> **📖 Objetivo**
> Representar adecuadamente la relación entre **supertipo** y **subtipos** en el modelo relacional, eligiendo la estrategia más adecuada según el caso.

> ---

> **🅰️ Opción A: Una sola tabla**
> - Se crea **una única tabla** que incluye:
>   - Todos los atributos del supertipo  
>   - Todos los atributos de cada subtipo  
>   - Un **atributo discriminante** que indica a qué subtipo pertenece cada tupla  
> - Esta opción puede generar **muchos valores nulos** si hay subtipos muy diferentes.

> ---

> **🅱️ Opción B: N tablas (solo subtipos)**
> - Se crea **una tabla por cada subtipo**, **sin crear tabla para el supertipo**.  
> - Cada tabla incluye los atributos comunes (del supertipo) y los propios.  
> - Permite independencia, pero puede redundar la información.

> ---

> **🆎 Opción C: N + 1 tablas**
> - Se crean:
>   - Una tabla para el **supertipo** (con su clave primaria)  
>   - Una tabla para **cada subtipo**, que incluye:
>     - Su clave primaria como **clave ajena** al supertipo  
>     - Sus atributos propios  
> - Esta es la opción más **modular** y fiel al modelo E/R.
> 
> ℹ️ En esta opción, si la generalización es **abierta**, se permite que el **atributo discriminante** sea nulo.

---