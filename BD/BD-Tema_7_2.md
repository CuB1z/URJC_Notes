---
tags: URJC URJC_BD
---

# Tema 7.2 - Bases de Datos

---

## Tabla de Contenidos

1. [Introducción](#Introducción)
2. [Dependencias Funcionales](#Dependencias%20Funcionales)
3. [Axiomas de Armstrong](#Axiomas%20de%20Armstrong)
4. [Claves y Recubrimiento Mínimo](#Claves%20y%20Recubrimiento%20Mínimo)
5. [Formas Normales](#Formas%20Normales)
6. [Resumen de Formas Normales](#Resumen%20de%20Formas%20Normales)

---

## Introducción

> **🎯 Propósito de la normalización**
>
> La normalización es un proceso sistemático utilizado para organizar datos en una base de datos relacional, con los siguientes objetivos:
>
> - Eliminar redundancias y datos innecesarios.
> - Evitar anomalías durante las operaciones de inserción, modificación y eliminación.
> - Garantizar la integridad de los datos mediante estructuras coherentes y eficientes.
>
> Si una relación presenta errores estructurales, será necesario **descomponerla** en relaciones más pequeñas y correctas sin que se pierda información.

> ---

> **📢 Fundamento teórico**
>
> El proceso de normalización se basa en el análisis de las **dependencias funcionales**, que definen cómo un conjunto de atributos determina a otros dentro de una relación.

> ---

> **💀 Anomalías comunes**
>
> - **Inserción**: No podemos almacenar un hecho hasta que tengamos toda la información relacionada.
> - **Eliminación**: Al borrar un dato, se pueden eliminar otros datos relacionados sin querer.
> - **Modificación**: Cambios inconsistentes entre tuplas que deberían compartir valores.

---

## Dependencias Funcionales

> **📖 Definición**
>
> Una **dependencia funcional** entre dos conjuntos de atributos, `X → Y`, implica que si dos tuplas comparten el mismo valor en `X`, también deben compartir el valor en `Y`.
>
> - Representan **restricciones semánticas** impuestas por el usuario.
> - Son válidas para **todas las extensiones posibles** de una relación.
>
> 📌 Estas dependencias permiten inferir estructura lógica desde el significado de los datos.

> ---

> **🔍 Tipos de dependencias**
>
> - **Trivial**: Cuando el implicado ya está contenido en el implicante (`X → Y`, con `Y ⊆ X`).
> - **Plena**: Todos los atributos del implicante son necesarios para determinar al implicado.
> - **Parcial**: Si se puede eliminar un atributo del implicante y la dependencia sigue cumpliéndose.
> - **Transitiva**: Si `X → Y` y `Y → Z`, entonces `X → Z`.
> - **Equivalencia**: Si `X → Y` y `Y → X`.

> ---

> **🧠 Cierre de un conjunto de atributos**
>
> El **cierre** de un conjunto de atributos `X`, denotado como `X⁺`, es el conjunto de todos los atributos que pueden ser derivados de `X` mediante las dependencias funcionales del esquema.
>
> Se utiliza para:
> - Verificar si `X` es clave candidata.
> - Determinar si `X → Y` es válida (`Y ⊆ X⁺`).

---

## Axiomas de Armstrong

> **📖 Conjunto de reglas que permiten deducir dependencias funcionales**
>
> - **Reflexividad**: Si `Y ⊆ X`, entonces `X → Y`
> - **Aumento**: Si `X → Y`, entonces `XZ → YZ`
> - **Transitividad**: Si `X → Y` y `Y → Z`, entonces `X → Z`

> ---

> **🧮 Axiomas derivados**
>
> - **Proyección**: De `X → Y`, se deduce `X → Y'` si `Y' ⊆ Y`
> - **Unión**: Si `X → Y` y `X → Z`, entonces `X → YZ`
> - **Pseudotransitividad**: Si `X → Y` y `YW → Z`, entonces `XW → Z`

---

## Claves y Recubrimiento Mínimo

> **📔 Claves candidatas**
>
> Son subconjuntos mínimos de atributos que **identifican unívocamente** las tuplas de una relación.
>
> - **Clave primaria**: Una de las claves candidatas elegida como identificador principal.
> - **Clave alternativa**: Las demás claves candidatas no elegidas.

> ---

> **📐 Recubrimiento mínimo**
>
> Un **recubrimiento mínimo** o **irredundante** de un conjunto de dependencias funcionales es aquel que cumple:
>
> 1. Cada dependencia tiene un solo atributo en el lado derecho.
> 2. No existen atributos innecesarios en los lados izquierdos.
> 3. No existen dependencias redundantes.

> ---

> **🧮 Algoritmo para obtener claves candidatas**
>
> 4. Eliminar dependencias triviales.
> 5. Calcular cierres para verificar implicaciones.
> 6. Identificar atributos que aparecen solo como implicantes.
> 7. Añadir atributos hasta que el cierre cubra todos los atributos.
> 8. Añadir equivalencias y recuperar claves alternativas.

---

## Formas Normales

> **📖 ¿Qué es una forma normal?**
>
> Una **forma normal** representa un conjunto de reglas que una relación debe cumplir para evitar redundancias, inconsistencias y anomalías durante las operaciones CRUD (Create, Read, Update, Delete).
> 
> A medida que se avanza hacia formas normales más elevadas, el modelo se vuelve más limpio, modular y fácil de mantener.

> ---

> **🧱 1FN - Primera Forma Normal**
> Una relación está en 1FN si **todos los atributos contienen valores atómicos**, es decir, indivisibles.
> 
> **No se permiten** atributos que contengan listas, conjuntos, registros o estructuras jerárquicas dentro de una celda.
> 
> Esto implica la **eliminación de multivalores** y la **expansión de atributos compuestos**.
>
> ✅ Todas las relaciones en un modelo relacional bien diseñado **deben cumplir como mínimo esta forma**.
>
> 📘 *Ejemplo no válido*
> 
> | Código | Nombre | Teléfonos        |  
> |--------|--------|------------------|  
> | E1     | Juan   | 111, 222          |
>
> 📗 *Ejemplo en 1FN*
>   
> | Código | Nombre | Teléfono          |  
> |--------|--------|-------------------|  
> | E1     | Juan   | 111               |  
> | E1     | Juan   | 222               |

> ---

> **🧮 2FN - Segunda Forma Normal**
> Se alcanza cuando:
> - La relación cumple con los requisitos de la **1FN**, y  
> - **Cada atributo no clave** depende de manera **completa** de la clave primaria, no solo de una parte de ella.
> 
> Esta forma normal cobra especial importancia en relaciones con **claves compuestas**, ya que evita que atributos dependan solo de un subconjunto de la clave.
> 
> Aplicar la 2FN permite eliminar **redundancias parciales** y contribuye a un diseño más limpio y eficiente, asegurando que cada atributo aporte información relacionada con la totalidad de la clave.
> 
> 📘 *Ejemplo típico*
> Una tabla `Estudiante_Beca` con clave compuesta `{Cod_Est, Cod_Beca}` y un atributo `Nombre_Est`.
> 
> Si `Nombre_Est` depende solo de `Cod_Est`, se debe separar en otra relación `Estudiante`.

> ---

> **🔗 3FN - Tercera Forma Normal**
>
> - Una relación se encuentra en **3FN** si:
>   - Ya cumple con los requisitos de la **2FN**, y  
>   - No existen **dependencias transitivas** entre atributos no clave y la clave primaria.
> 
> - Es decir, **ningún atributo no clave debe depender de otro atributo no clave**. Todas las dependencias deben ir directamente desde la clave hacia los atributos dependientes.
> 
> - Esta forma normal **elimina redundancias lógicas** que pueden provocar errores al actualizar, insertar o eliminar datos, mejorando así la **consistencia e integridad** del diseño.
> 
> 📘 *Ejemplo típico*
> En la relación `Estudiante(Cod_Est, Cod_Proy, Nom_Proy)`:
> - Si se cumple que `Cod_Proy → Nom_Proy`  
> - Y también que `Cod_Est → Cod_Proy`  
> 
> Entonces se da una **dependencia transitiva**: `Cod_Est → Cod_Proy → Nom_Proy`, es decir, `Cod_Est → Nom_Proy`, lo cual **viola la 3FN**.

> ---

> **🛡️FNBC - Forma Normal de Boyce-Codd**
> Es una **versión más estricta** que la 3FN, diseñada para resolver situaciones en las que la 3FN no garantiza completamente la eliminación de anomalías.
> 
> Una relación está en **FNBC** si, para cada **dependencia funcional** `X → Y`, el conjunto `X` es una **superclave** de la relación.
> 
> Se aplica principalmente en relaciones con **múltiples claves candidatas** que se **solapan**, donde pueden persistir dependencias no deseadas incluso cumpliendo la 3FN.
> 
> 🔧 Aunque esta forma puede llevar a la **pérdida de algunas dependencias funcionales** tras la descomposición, **maximiza la integridad y consistencia estructural** del esquema.
> 
> 📘 *Ejemplo*
> Considera la relación `Clase(Cod_Est, Cod_Prof, Materia)` con las siguientes dependencias:
> - `(Cod_Est, Materia) → Cod_Prof`  
> - `Cod_Prof → Materia`  
> 
> Aquí las claves `{Cod_Est, Cod_Prof}` y `{Cod_Est, Materia}` **se solapan**, lo que **viola la FNBC** a pesar de que pueda cumplirse la 3FN.

---

## Resumen de Formas Normales

> **🔹 1FN – Primera Forma Normal**
>
> ✅ Los atributos deben contener **valores atómicos**, sin listas ni estructuras internas.  
> 📌 Cada celda debe almacenar **un único dato** por atributo y tupla.  
> 🧹 Elimina duplicidad estructural o anidamiento.

---

> **🔸 2FN – Segunda Forma Normal**
>
> ✅ Cumple con 1FN.  
> 🔗 Todos los atributos **no clave** deben depender de **toda la clave primaria**, no solo de una parte.  
> 🚫 Evita **dependencias parciales** que provocan redundancia.

---

> **🔺 3FN – Tercera Forma Normal**
>
> ✅ Cumple con 2FN.  
> 🔍 No debe haber **dependencias transitivas**: un atributo no clave **no puede depender de otro atributo no clave**.  
> 🔒 Mejora la **integridad y coherencia** del modelo.

---

> **🔰 FNBC – Forma Normal de Boyce-Codd**
>
> ✅ Cumple con 3FN.  
> 🧠 Toda **dependencia funcional** debe tener como determinante una **superclave**.  
> 🔄 Elimina **anomalías residuales** aún presentes en 3FN, especialmente en esquemas con claves solapadas.  
> ⚠️ Puede implicar pérdida de algunas dependencias, a cambio de una **estructura más robusta**.

---