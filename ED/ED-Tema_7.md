---
tags: URJC URJC_ED
---

# Tema 7 - Estructuras de Datos

---

## Tabla de Contenidos

1. [Definición](#Definición)
2. [Los TADs Conjunto y Bolsa](#Los%20TADs%20Conjunto%20y%20Bolsa)
3. [Implementación](#Implementación)
4. [Conjuntos en Pascal](#Conjuntos%20en%20Pascal)
5. [Implementación mediante Arrays, Listas y Tablas Hash](#Implementación%20mediante%20Arrays,%20Listas%20y%20Tablas%20Hash)

---

## Definición

> **🔍 Definición**
> Los **conjuntos** y **bolsas** son estructuras de datos no lineales que representan colecciones de elementos.
> 
> - Un **conjunto** (set) es una estructura en la que no se permiten duplicados. Es una colección no ordenada de elementos.
> - Una **bolsa** (multiset) es una estructura similar al conjunto, pero permite duplicados. En otras palabras, un elemento puede aparecer múltiples veces.

> ---
  
## Los TADs Conjunto y Bolsa

> **💼 TAD Conjunto**
> Un conjunto permite realizar varias operaciones:
> - **add**: Añadir un elemento al conjunto.
> - **remove**: Eliminar un elemento del conjunto.
> - **in**: Verificar si un elemento pertenece al conjunto.
> - **size**: Consultar el tamaño del conjunto.
> Además, los conjuntos soportan operaciones como:
> - Unión, intersección, diferencia, y extracción de subconjuntos.

> ---
  
> **💼 TAD Bolsa**
> Una bolsa proporciona operaciones adicionales como:
> - **remove_all**: Eliminar todas las ocurrencias de un elemento.
> - **multiplicity**: Consultar cuántas veces un elemento aparece en la bolsa.
> - **add** y **remove**: Añadir o eliminar un elemento, pero manteniendo la cantidad de veces que aparece.

> ---
  
> **Ejemplo de operaciones en el TAD Conjunto:**
> - **Unión**: Unión de dos conjuntos, los elementos de ambos se combinan sin duplicados.
> - **Intersección**: Elementos que están en ambos conjuntos.
> - **Diferencia**: Elementos del primer conjunto que no están en el segundo.
> - **Complemento**: Elementos que no están en un conjunto.

> ---
  
## Implementación

> **⚙️ Implementación de Conjuntos y Bolsas**
> Los conjuntos y bolsas se pueden implementar utilizando varias estructuras de datos:
> - **Arrays**: Estructura de datos estática, donde los índices representan los elementos del conjunto.
> - **Listas Enlazadas**: Más flexibles, permiten añadir o eliminar elementos de forma eficiente.
> - **Árboles de Búsqueda Binarios**: Permiten realizar operaciones en tiempo logarítmico, pero son más complejos de implementar.
> - **Tablas Hash**: Ofrecen acceso eficiente mediante una función hash, aunque pueden producir colisiones que se gestionan mediante listas enlazadas.

> ---

> **🧩 Implementación mediante Arrays**
> - En esta implementación, los índices del array representan los valores del conjunto.
> - Esta es la técnica utilizada en el tipo **Set** de Pascal.

> ---

> **🔧 Implementación mediante Listas Enlazadas**
> - Utiliza una lista para almacenar los elementos del conjunto. En el caso de una bolsa, la lista tiene un campo adicional para la multiplicidad.

> ---

> **🔨 Implementación mediante Tablas Hash**
> - Utiliza una función hash para acceder rápidamente a los elementos.
> - Las tablas hash pueden manejar colisiones usando listas enlazadas.

---
  
## Conjuntos en Pascal

> **💻 Conjuntos en Pascal**
> Pascal incluye una implementación simple de conjuntos, pero limitada a un máximo de 256 elementos.
> - El tipo **Set** en Pascal permite trabajar con conjuntos homogéneos donde el tipo base es cualquier **ordinal** (enteros, caracteres o enumeraciones).

> ---
  
> **Operaciones en Pascal**:
> - Unión: `+`
> - Intersección: `*`
> - Diferencia: `-`
> - Diferencia simétrica: `><`
> - Igualdad: `=`
> - Desigualdad: `<>`
> - Inclusión: `<=`, `>=`
> - Pertenencia: `in`
> - Añadir y eliminar elementos: `include`, `exclude`

> ---

> **Ejemplo de código en Pascal**:
> ```pascal
> type
>     language = (solidity, java, python, C++, ruby, go);
>     languages = set of language;
> var
>     programmer_skills: languages;
> begin
>     programmer_skills := [java, python];
>     if solidity in programmer_skills then
>         writeLn('The guy is a blockchain developer!');
> end.
> ```

---
  
## Implementación mediante Arrays, Listas y Tablas Hash

> **🧱 Implementación mediante Arrays**
> - Un array tiene índices que corresponden a los elementos posibles en el conjunto. 
> - Este enfoque es eficiente para conjuntos pequeños y cuando el tipo de los elementos es un valor ordinal (como enteros).

> ---

> **🔗 Implementación mediante Listas Enlazadas**
> - Una lista enlazada mantiene los elementos del conjunto de manera ordenada (o desordenada).
> - En el caso de bolsas, se debe almacenar la **multiplicidad** de los elementos, es decir, cuántas veces aparece un elemento.

> ---

> **🔒 Implementación mediante Tablas Hash**
> - Una tabla hash utiliza una **función hash** para distribuir los elementos en diferentes "celdas" de una tabla.
> - Las colisiones se manejan mediante **listas enlazadas** en cada celda. 
> - Esto permite un acceso muy rápido a los elementos, especialmente cuando la tabla tiene un buen tamaño y las colisiones son mínimas.

> ---

> **Ejemplo de implementación en Pascal con tablas hash**:
> ```pascal
> unit uHashTable;
> interface
> uses SysUtils, uListaEnlazadaSimple;
> const
> HASHTABLESIZE = 10;
> type
> tHashTable = array[0..HashTableSize-1] of tListaSimple;
> procedure initialize(var table: tHashTable);
> procedure add(var table: tHashTable; key: string);
> procedure remove(var table: tHashTable; key: string);
> function contains(table: tHashTable; key: string): boolean;
> procedure show_table_state(table: tHashTable);
> function hash_function(key: string): integer;
> ```

---