---
tags: URJC URJC_BD
---

# Tema 5 - Bases de Datos

---

## Tabla de Contenidos

1. [Etapas en el Modelado Conceptual](#Etapas%20en%20el%20Modelado%20Conceptual)
2. [Técnicas y Principios del Modelado Conceptual](#Técnicas%20y%20Principios%20del%20Modelado%20Conceptual)

---

## Etapas en el Modelado Conceptual

> **📖 Fases del proceso de modelado**
> El **modelado conceptual** consiste en representar de forma estructurada y comprensible los requerimientos del sistema mediante el **Modelo Entidad-Relación (E/R)**.  
> Este proceso se lleva a cabo en varias etapas claramente definidas:

> ---

> **🔍 1. Recogida de requerimientos**
> Se recopila información clave a partir de entrevistas, documentos y observación.  
> El objetivo es entender las necesidades de los usuarios y del sistema.

> ---

> **🧱 2. Identificación de elementos del modelo**
> A partir del lenguaje natural utilizado en los requerimientos, se identifican:
> - **Entidades**  
> - **Atributos**  
> - **Relaciones**  
> - **Restricciones**

> ---

> **🗺️ 3. Representación gráfica**
> Se construye el **diagrama E/R (extendido)** para visualizar la estructura de los datos y sus relaciones.  
> Este modelo actúa como puente entre el análisis y el diseño lógico.

> ---

> **🔎 4. Revisión y validación**
> Se valida el modelo con los usuarios y expertos para asegurar:
> - Coherencia  
> - Completitud  
> - Correcta interpretación de los requisitos del sistema



---

## Técnicas y Principios del Modelado Conceptual

> **📖 1. Frases en LN >>> Elementos E/R**
> El modelado conceptual **parte del lenguaje natural (LN)** usado en descripciones y requisitos, para traducirse en un modelo **Entidad-Relación (E/R)**.  
> - Se identifican entidades, atributos y relaciones desde frases lingüísticas.

> ---

> **📖 2. Enfoque Lingüístico de Chen**
> Según el enfoque de **Peter Chen**, se pueden interpretar frases naturales de la siguiente manera:
> - 🟩 **Sustantivos** → Entidades  
> - 🟦 **Nombres propios** → Instancias de entidades  
> - 🟧 **Verbos transitivos/frases verbales** → Relaciones entre entidades  
> - 🟨 **Preposiciones/frases preposicionales** → Asociaciones o vínculos con atributos

> ---

> **📖 3. Modelo E/R Extendido**
> Se utiliza el **Modelo Entidad-Relación Extendido**, que añade elementos como:
> - Jerarquías de generalización/especialización  
> - Atributos compuestos, multivaluados, derivados  
> - Entidades débiles y restricciones avanzadas

> ---

> **📖 4. Interpretación de verbos “Ser” y “Tener”**
> - **"ES UN"** → Usado para representar **generalización** (una entidad es un subtipo de otra)  
> - **"TIENE"** → Puede implicar una **relación entre entidades** o una **asociación con atributos**  
> - Contextualizar su uso es clave para un modelado correcto

> ---

> **📖 5. Número de Entidades y Cardinalidad**
> La **cantidad y tipo de entidades** mencionadas en una frase puede indicar la **cardinalidad** de la relación.  
> 🧾 Ejemplo:  
> - “Un empleado puede participar en varios proyectos y un proyecto puede tener varios empleados”  
> - Implica una **relación N:M** con **grado 2**

> ---

> **📖 6. Entidad vs. Atributo**
> A veces conviene modelar un dato como **entidad** en lugar de **atributo**, especialmente cuando:
> - Tiene **atributos propios**  
> - Se relaciona con **otras entidades**  
> ✔️ Esto permite representar mejor su rol y dependencias

> ---

> **📖 7. Unicidad de los Atributos**
> Un mismo atributo **no debe aparecer duplicado** en distintas entidades.  
> - Si ocurre, puede indicar la existencia de una **interrelación no modelada correctamente**  
> - Es preferible **revisar el diseño** para identificar relaciones implícitas

---