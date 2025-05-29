---
tags: URJC URJC_ED
---

# Tema 6 - Estructuras de Datos

---

## Tabla de Contenidos

1. [Definiciones](#Definiciones)
2. [El TAD Lista](#El%20TAD%20Lista)
3. [Implementación](#Implementación)
4. [Lista Enlazada Simple](#Lista%20Enlazada%20Simple)
5. [Lista Circular](#Lista%20Circular)
6. [Lista Doblemente Enlazada](#Lista%20Doblemente%20Enlazada)
7. [Listas y Genericidad](#Listas%20y%20Genericidad)
8. [Listas como Base para Otras Estructuras](#Listas%20como%20Base%20para%20Otras%20Estructuras)

---

## Definiciones

> **📖 ¿Qué es una Lista?**  
> Una **lista** es una estructura de datos lineal y dinámica que representa una secuencia de elementos, a menudo del mismo tipo.  
> Cada elemento se conecta al siguiente mediante un "enlace", formando una cadena de nodos.

---

## El TAD Lista

> **🔧 Operaciones Básicas de una Lista**  
> Un TAD Lista puede incluir las siguientes operaciones básicas:
> - `insert`: Insertar un elemento.
> - `delete`: Eliminar un elemento.
> - `is_empty`: Consultar si la lista está vacía.
> - `first`: Obtener el primer elemento.
> - `last`: Obtener el último elemento.
> - `in_list`: Verificar si un elemento está presente.

> --- 

> **💡 Especificación de la Lista**  
> Algunas operaciones comunes incluyen:
> - `insert_at_end`, `insert_at_begin`, `delete_at_end`, `delete_at_begin`, `is_empty`, `first`, `last`, etc.
>  
> Dependiendo de la implementación, estas operaciones pueden variar.

---

## Implementación

> **🔨 Tipos de Implementación de Listas**  
> Las listas se pueden implementar utilizando diferentes tipos:
> - **Lista enlazada simple**: Un nodo apuntando al siguiente.
> - **Lista circular**: El último nodo apunta de nuevo al primero.
> - **Lista doblemente enlazada**: Cada nodo tiene enlaces tanto al siguiente como al anterior.

---

## Lista Enlazada Simple

> **🔲 Implementación con Memoria Dinámica**  
> La implementación de una lista enlazada simple requiere el uso de punteros para gestionar los nodos. Cada nodo contiene la información y un puntero al siguiente nodo.  
> Se necesita una estructura con dos punteros: uno al primer nodo (`first`) y otro al último nodo (`last`).

> ---

> **📑 Ejemplo de Implementación en Pascal**  
> ```pascal
> type
>   nodo = record
>     info: integer;
>     sig: ^nodo;
>   end;
> 
> tListaSimple = record
>   first, last: ^nodo;
> end;
> ```

> ---

> **📌 Operaciones Básicas de la Lista Enlazada Simple**  
> - `initialize`: Inicializa la lista.
> - `is_empty`: Verifica si la lista está vacía.
> - `insert_at_end`: Inserta un elemento al final.
> - `insert_at_begin`: Inserta un elemento al principio.
> - `delete_at_end`: Elimina un elemento del final.
> - `delete_at_begin`: Elimina un elemento del principio.
> - `to_string`: Representa la lista como una cadena.
> - `clear`: Elimina todos los elementos.

---

## Lista Circular

> **🔄 Implementación de Lista Circular**  
> En una lista circular, el último nodo apunta de nuevo al primero, lo que significa que no hay un `nil` al final de la lista.  
> La lista se gestiona con un solo manejador que apunta al último nodo.

> ---

> **📑 Ejemplo de Implementación en Pascal**  
> ```pascal
> type
>   nodo = record
>     info: integer;
>     sig: ^nodo;
>   end;
> 
> tListaCircular = record
>   last: ^nodo;
> end;
> ```

> ---

> **📌 Operaciones Básicas de la Lista Circular**  
> - `initialize`: Inicializa la lista.
> - `is_empty`: Verifica si la lista está vacía.
> - `insert_at_end`: Inserta un elemento al final.
> - `insert_at_begin`: Inserta un elemento al principio.
> - `delete`: Elimina un elemento por valor.
> - `to_string`: Representa la lista como una cadena.

---

## Lista Doblemente Enlazada

> **🔁 Implementación de Lista Doblemente Enlazada**  
> En una lista doblemente enlazada, cada nodo contiene dos punteros: uno al siguiente nodo y otro al anterior.  
> Esto facilita las inserciones y eliminaciones en ambos extremos de la lista.

> ---

> **📑 Ejemplo de Implementación en Pascal**  
> ```pascal
> type
>   nodo = record
>     info: integer;
>     sig: ^nodo;
>     ant: ^nodo;
>   end;
> 
> tListaDoble = record
>   first, last: ^nodo;
> end;
> ```

> ---

> **📌 Operaciones Básicas de la Lista Doblemente Enlazada**  
> - `initialize`: Inicializa la lista.
> - `is_empty`: Verifica si la lista está vacía.
> - `insert_at_end`: Inserta un elemento al final.
> - `insert_at_begin`: Inserta un elemento al principio.
> - `delete_at_end`: Elimina un elemento del final.
> - `delete_at_begin`: Elimina un elemento del principio.
> - `to_string`: Representa la lista como una cadena.

---

## Listas y Genericidad

> **🧩 Listas Genéricas**  
> Las listas pueden ser programadas de manera genérica para trabajar con cualquier tipo de dato, similar a las pilas o colas genéricas.  
> Esto permite que las listas se adapten a diferentes tipos de elementos, proporcionando una mayor flexibilidad en su uso.

---

## Listas como Base para Otras Estructuras

> **🔧 Uso de Listas para Otras Estructuras**  
> Las listas pueden servir como base para implementar estructuras más complejas, tales como:
> - **Listas ordenadas**.
> - **Colas de prioridades**.
> - **Deques (colas doblemente terminadas)**.
> - **Mapas o Diccionarios**.
> - **Grafos**.

> --- 

> **💡 Ejemplos de Estructuras Basadas en Listas**  
> - **Lista ordenada**: Mantiene los elementos siempre en orden.
> - **Cola de prioridades**: Mantiene los elementos ordenados por prioridad.
> - **Deque**: Permite inserciones y eliminaciones en ambos extremos.

---

