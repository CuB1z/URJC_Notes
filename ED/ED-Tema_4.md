---
tags: URJC URJC_ED
---

# Tema 4 - Estructuras de Datos

---

## Tabla de Contenidos

1. [Definición de Pila](#Definición%20de%20Pila)
2. [El TAD Pila: Operaciones Básicas](#El%20TAD%20Pila%20Operaciones%20Básicas)
3. [Implementación de la Pila](#Implementación%20de%20la%20Pila)
4. [Implementación con un Array](#Implementación%20con%20un%20Array)
5. [Ejemplos de Aplicación](#Ejemplos%20de%20Aplicación)
6. [Pilas y Genericidad](#Pilas%20y%20Genericidad)

---

## Definición de Pila

> **📚 ¿Qué es una Pila?**  
> Una **pila** es una estructura de datos lineal, dinámica, que da soporte al concepto **LIFO**: **Last In, First Out** (Último en entrar, primero en salir).

---

## El TAD Pila: Operaciones Básicas

> **🔧 Operaciones Básicas de una Pila**  
> Independientemente de su implementación, una pila debe proporcionar al menos estas 4 operaciones básicas:
> - `push`: Meter un elemento en la pila.
> - `pop`: Sacar un elemento de la pila.
> - `is_empty`: Consultar si la pila está vacía.
> - `peek/top`: Conocer el elemento en la cima de la pila.
> - `initialize/crear`: Inicializar la pila.

---

## Implementación de la Pila

> **🔨 Formas de Implementación**  
> Existen dos formas comunes de implementar una pila:  
> - **Con un array**: Tiene limitaciones de espacio, pero es sencilla de implementar.  
> - **Con memoria dinámica y punteros**: No tiene límite de almacenamiento (teóricamente), pero su implementación es más compleja.

---

## Implementación con un Array

> **🔲 Implementación con Array**  
> Necesitaremos una variable entera que indicará la posición de la cima y un array del tipo base para almacenar los elementos.  
> La implementación será eficiente (O(1)) para las operaciones de inserción y eliminación.

> ---

> **📑 Ejemplo en Pascal**  
> ```pascal
> unit uPilaEnteros;
> 
> interface
> 
> const MAX_ELEMENTOS = 100;
> 
> type
>   tPilaEnteros = record
>     cima: integer;
>     stack: array[1..MAX_ELEMENTOS] of integer;
>   end;
> 
> procedure initialize(var p: tPilaEnteros);
> procedure push(var p: tPilaEnteros; x: integer);
> procedure pop(var p: tPilaEnteros);
> function peek(p: tPilaEnteros): integer;
> function isEmpty(p: tPilaEnteros): boolean;
> ```

> ---

> **📌 Funciones**
> ```pascal
> procedure initialize(var p: tPilaEnteros);
> begin
>   p.cima := 0;
> end;
> 
> function isEmpty(p: tPilaEnteros): boolean;
> begin
>   isEmpty := p.cima = 0;
> end;
> 
> procedure push(var p: tPilaEnteros; x: integer);
> begin
>   if p.cima < MAX_ELEMENTOS then
>   begin
>     p.cima := p.cima + 1;
>     p.stack[p.cima] := x;
>   end;
> end;
> 
> procedure pop(var p: tPilaEnteros);
> begin
>   if not isEmpty(p) then
>     p.cima := p.cima - 1;
> end;
> 
> function peek(p: tPilaEnteros): integer;
> begin
>   if not isEmpty(p) then
>     peek := p.stack[p.cima];
> end;
> 
> ```

---

## Ejemplos de Aplicación

> **💻 Aplicaciones Comunes de las Pilas**  
> Las pilas son muy utilizadas en diversas áreas de la computación, tales como:
> - Evaluación de expresiones.
> - Llamadas a subprogramas (stack frames).
> - Funcionalidad de deshacer/rehacer en editores.
> - Navegadores web (funcionalidad de atrás/adelante).
> - Algoritmos de **Backtracking** (por ejemplo, resolver el problema de las 9 reinas o búsqueda en laberintos).
> - Gestión de memoria.
> - Y mucho más.

---

## Pilas y Genericidad

> **🧩 Genericidad en Pilas**  
> Las pilas pueden ser programadas de manera **genérica** para trabajar con cualquier tipo de dato, no solo con enteros.  
> En lenguajes como Pascal, no hay soporte para plantillas (templates), pero podemos simularlo mediante el uso de unidades específicas.

> ---

> **📑 Ejemplo de Pila Genérica en Pascal**  
> ```pascal
> unit uPilaGenerica;
> 
> interface
> 
> uses uTElemento;
> 
> const MAX_ELEMENTOS = 100;
> 
> type
>   tPilaTElemento = record
>     cima: integer;
>     stack: array[1..MAX_ELEMENTOS] of TElemento;
>   end;
> 
> procedure initialize(var p: tPilaTElemento);
> procedure push(var p: tPilaTElemento; x: TElemento);
> procedure pop(var p: tPilaTElemento);
> function peek(p: tPilaTElemento): TElemento;
> function isEmpty(p: tPilaTElemento): boolean;
> ```

---