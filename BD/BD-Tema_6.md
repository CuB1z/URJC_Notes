---
tags: URJC URJC_BD
---

# Tema 6 - Bases de Datos

---

## Tabla de Contenidos

1. [Definiciones Básicas](#Definiciones%20Básicas)
2. [Estructura del Modelo Relacional](#Estructura%20del%20Modelo%20Relacional)
3. [Representación de una Relación](#Representación%20de%20una%20Relación)
4. [Restricciones Inherentes](#Restricciones%20Inherentes)
5. [Las 12 Reglas de Codd](#Las%2012%20Reglas%20de%20Codd)
6. [Dinámica: Álgebra Relacional](#Dinámica%20Álgebra%20Relacional)

---

## Definiciones Básicas

> El modelo relacional organiza los datos en **relaciones**, también conocidas como **tablas**, que representan entidades o asociaciones del mundo real. Los principales elementos de este modelo son:
>
> *🧩 Relación*
> Estructura fundamental que representa una tabla.
> 
> *🔖 Atributo*
> Columna que define una propiedad de la relación. El número de atributos determina su **grado**.
> 
> *🧪 Dominio*
> Conjunto de valores válidos que puede tomar un atributo.
> 
> *📄 Tupla*
> Fila de una tabla, es decir, una instancia concreta. El número de tuplas indica la **cardinalidad**.
> 
> *📏 Grado*
> Número de atributos o columnas de una relación.
> 
> *🔢 Cardinalidad*
> Número total de tuplas o filas que contiene una relación.

---

## Estructura del Modelo Relacional

> **📘 Intensión**  
> Describe la **estructura lógica** de la relación sin valores concretos. Incluye el nombre de la relación, sus atributos y los dominios de cada uno:
> $$
> R(A1:D1, A2:D2, ..., An:Dn)
> $$
> Se corresponde con la **cabecera** de la tabla: los nombres y tipos de datos de las columnas.

> ---

> **📗 Extensión**  
> Representa el **contenido actual** de la relación: el conjunto de todas las tuplas almacenadas en un momento dado.
> $$
> r(R) = {t1, t2, ..., tn}
> $$
> Cada tupla contiene un valor concreto para cada atributo definido en la intensión. Se corresponde con el **cuerpo** de la tabla.
> 
> 💡 A partir de ahora, los términos *relación*, *tabla* y *entidad* se usarán de manera equivalente para referirse a la intensión de una relación.

---

## Representación de una Relación

> Para representar visualmente las relaciones en un modelo relacional, se siguen estas convenciones:
> - 🔑 **Clave primaria** $\to$ _Subrayado completo_  
> - 🔁 **Clave alternativa** $\to$ **Negrita**  
> - 🔗 **Clave ajena** $\to$ *Cursiva* o _subrayado discontinuo_  
> - ✴️ **Atributo opcional** (admite NULL) $\to$ Acompañado por `*`  
> - 🚫 **Atributo obligatorio** (no admite NULL) $\to$ Se marca con `NN`

> ---

> **🗝️ Tipos de claves**
>
> - **Clave candidata**: Atributo(s) que identifican **únicamente** una tupla, de forma **mínima** y sin redundancia.  
> - **Clave primaria**: La clave candidata **elegida** para identificar tuplas.  
> - **Clave alternativa**: Las demás claves candidatas que **no fueron seleccionadas** como primaria.  
> - **Clave ajena (Foreign Key)**: Atributo que **referencia** la clave primaria de otra relación, permitiendo establecer vínculos entre tablas.

> ---

> **🚯 Política de actualización para claves ajenas**
>
> Al modificar o eliminar una tupla que actúa como clave primaria en otra tabla, se pueden aplicar las siguientes políticas:
>
> - **(R) Restringido**: Se prohíbe la operación si existen dependencias.  
> - **(C) En cascada**: La operación se replica automáticamente en las relaciones dependientes.  
> - **(N) Puesta a NULL**: Los valores de clave ajena se reemplazan por `NULL`.  
> - **(D) Valor por defecto**: Se reemplazan por un valor predeterminado del atributo.

> ---

> **🤖 Restricciones de verificación**
>
> - `CHECK`: Aplica una condición a un atributo de una relación; se verifica en cada operación de escritura.  
> - `ASSERT`: Igual que `CHECK`, pero puede abarcar **varias relaciones**.  
> - `TRIGGER`: Disparador que ejecuta automáticamente una acción cuando se cumple una condición definida.

---

## Restricciones Inherentes

> Las relaciones del modelo relacional presentan propiedades implícitas que deben cumplirse siempre:
> 
> - ❌ No se permiten **tuplas duplicadas**.  
> - 🔀 El **orden** de las tuplas y atributos es **irrelevante**.  
> - 📐 Cada celda debe contener **un único valor** (modelo bidimensional).

> ---

> **📖 Reglas de Integridad**
>
> *🧍 Integridad de entidad*
> Ningún atributo que forme parte de la clave primaria puede contener un valor nulo.
> 
> *🔗 Integridad referencial*
> Toda clave ajena debe referenciar un valor existente en la clave primaria de otra relación.

---

## Las 12 Reglas de Codd

> El creador del modelo relacional, **E. F. Codd**, definió 12 reglas que todo sistema de gestión de bases de datos relacional debe cumplir:
> 
> 0️⃣ Regla fundamental  
> 1️⃣ Representación de la información como valores en tablas  
> 2️⃣ Acceso garantizado a todos los datos  
> 3️⃣ Tratamiento uniforme de los valores nulos  
> 4️⃣ Catálogo relacional accesible por los usuarios  
> 5️⃣ Uso de un sublenguaje completo de datos (como SQL)  
> 6️⃣ Actualización de vistas posibles  
> 7️⃣ Inserciones, actualizaciones y eliminaciones de alto nivel  
> 8️⃣ Independencia física  
> 9️⃣ Independencia lógica  
> 🔟 Integridad gestionada por el sistema  
> 1️⃣1️⃣ Independencia de distribución  
> 1️⃣2️⃣ No subversión del sistema relacional por interfaces externas

---

## Dinámica: Álgebra Relacional

> **ℹ️ Qué es**
> El álgebra relacional define un conjunto de **operaciones formales** que permiten manipular relaciones para obtener nuevas relaciones. Constituye la base teórica para el lenguaje SQL.

> ---

> **📖 Operaciones primitivas**
>
> *Unarias* (una sola tabla):
> - `π` **Proyección**: Selecciona columnas específicas.  
> - `σ` **Selección**: Filtra filas según una condición.
> 
> *Binarias* (dos tablas):
> - `∪` **Unión**: Combina todas las tuplas de ambas relaciones (sin duplicados).  
> - `−` **Diferencia**: Tuplas presentes en la primera pero no en la segunda.  
> - `×` **Producto cartesiano**: Combinación de todas las tuplas entre ambas relaciones.
> 
> 💡 Dos relaciones son **compatibles** si tienen el mismo número y tipo de atributos.

> ---

> **📖 Operaciones derivadas**
>
> - `⨝` **Join (θ, equi, natural)**: Une dos relaciones en base a condiciones comunes.  
> - `∩` **Intersección**: Devuelve las tuplas que existen en ambas relaciones.  
> - `/` **División**: Retorna las tuplas que se relacionan con **todos** los valores de otra relación.  
> - `⊓...GroupBy`: Agrupa por un atributo y permite aplicar funciones agregadas como `SUM`, `AVG`, `COUNT`, etc.

---