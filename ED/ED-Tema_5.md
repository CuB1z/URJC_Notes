---
tags: URJC URJC_ED
---

# Tema 5 - Estructuras de Datos

---

## Tabla de Contenidos

1. [Definición de Cola](#Definición%20de%20Cola)
2. [El TAD Cola: Operaciones Básicas](#El%20TAD%20Cola%20Operaciones%20Básicas)
3. [Implementación](#Implementación)
4. [Implementación mediante Arrays](#Implementación%20mediante%20Arrays)
5. [Implementación con Memoria Dinámica](#Implementación%20con%20Memoria%20Dinámica)
6. [Funcionalidades Adicionales](#Funcionalidades%20Adicionales)
7. [Aplicaciones](#Aplicaciones)
8. [Colas y Genericidad](#Colas%20y%20Genericidad)

---

## Definición de Cola

> **📚 ¿Qué es una Cola?**  
> Una **cola** es una estructura de datos lineal y dinámica que sigue el principio **FIFO**: **First In, First Out** (El primer elemento en entrar es el primero en salir).

---

## El TAD Cola: Operaciones Básicas

> **🔧 Operaciones Básicas de una Cola**  
> Las operaciones básicas que debe soportar una cola incluyen:
> - `enqueue`: Insertar un elemento al final de la cola.
> - `dequeue`: Eliminar el primer elemento de la cola.
> - `empty_queue`: Verificar si la cola está vacía.
> - `first`: Consultar el primer elemento.
> - `last`: Consultar el último elemento.
> - `initialize/crear`: Inicializar la cola.

---

## Implementación

> **🔨 Formas de Implementación**  
> Las colas pueden implementarse de dos formas principales:
> - **Con un array**: Limitaciones de espacio, pero implementación sencilla.
> - **Con memoria dinámica y punteros**: No tiene límite de almacenamiento (teóricamente), pero es más compleja de implementar.

---

## Implementación mediante Arrays

> **🔲 Implementación con Array Lineal**  
> Utilizando arrays para implementar una cola, podemos emplear una estructura con dos índices para `first` y `last` que apuntan a los elementos en la cola. A continuación, se puede ver una implementación sencilla con eliminación simple.
>  
> - **Eliminación simple**: Se elimina el primer elemento desplazando el índice `first` hacia el siguiente elemento.  
> - **Reorganización**: Al sacar un elemento, se reorganizan los elementos de la cola para que los vacíos sean minimizados.  
>  
> Sin embargo, este tipo de implementación presenta algunos inconvenientes como la limitación de espacio y la necesidad de reorganizar el array.

> ---

> **📑 Ejemplo de Implementación en Pascal**  
> ```pascal
> unit uColaEnteros;
> 
> interface
> 
> const MAX_ELEMENTOS = 100;
> 
> type
>   tColaEnteros = record
>     primero, ultimo: integer;
>     cola: array[1..MAX_ELEMENTOS] of integer;
>   end;
> 
> procedure initialize(var c: tColaEnteros);
> procedure enqueue(var c: tColaEnteros; x: integer);
> procedure dequeue(var c: tColaEnteros);
> function first(c: tColaEnteros): integer;
> function last(c: tColaEnteros): integer;
> function empty_queue(c: tColaEnteros): boolean;
> ```

---

## Implementación con Memoria Dinámica

> **💡 Implementación con Memoria Dinámica**  
> La implementación mediante memoria dinámica permite gestionar una cola sin la necesidad de definir un tamaño máximo. Utiliza punteros `first` y `last` para indicar los extremos de la cola.
>  
> Las operaciones `enqueue` y `dequeue` tienen una complejidad de O(1), ya que la inserción y eliminación de elementos son muy eficientes.

> ---

> **📑 Ejemplo de Implementación en Pascal**  
> ```pascal
> unit uColaDinamica;
> 
> interface
> 
> type
>   nodo = record
>     info: integer;
>     sig: ^nodo;
>   end;
> 
>   tCola = record
>     first, last: ^nodo;
>   end;
> 
> procedure initialize_queue(var c: tCola);
> procedure enqueue(var c: tCola; x: integer);
> procedure dequeue(var c: tCola);
> function first(c: tCola): integer;
> function last(c: tCola): integer;
> function empty_queue(c: tCola): boolean;
> ```

> ---

> **🔄 Funciones para Manipulación de la Cola**  
> ```pascal
> procedure initialize_queue(var c: tCola);
> begin
>   c.first := nil; 
>   c.last := nil;
> end;
> 
> function empty_queue(c: tCola): boolean;
> begin
>   empty_queue := c.first = nil;
> end;
> 
> procedure enqueue(var c: tCola; x: integer);
> var
>   nuevo: ^nodo;
> begin
>   new(nuevo); 
>   nuevo^.info := x; 
>   nuevo^.sig := nil;
>   if empty_queue(c) then
>     c.first := nuevo
>   else
>     c.last^.sig := nuevo; 
>   c.last := nuevo;
> end;
> 
> procedure dequeue(var c: tCola);
> var
>   aux: ^nodo;
> begin
>   if not empty_queue(c) then
>   begin
>     aux := c.first; 
>     c.first := c.first^.sig; 
>     if c.first = nil then
>       c.last := nil;
>     dispose(aux);  
>   end;
> end;
> ```

---

## Funcionalidades Adicionales

> **🛠 Funcionalidades Extra para la Cola**  
> Es posible añadir funcionalidades adicionales a las colas, como:
> - `clear()`: Vaciar la cola.
> - `toString()`: Obtener una representación en cadena de la cola.
> - `num_elems()`: Contar el número de elementos en la cola.
> - `copy()`: Crear una copia de la cola.

> ---

> **📑 Ejemplo en Pascal para Funciones Adicionales**  
> ```pascal
> procedure clear(var c: tCola);
> begin
>   while not empty_queue(c) do
>     dequeue(c);
> end;
> 
> function toString(c: tCola): string;
> var
>   aux: ^nodo;
>   s: string;
> begin
>   aux := c.first;
>   s := '[';
>   while aux <> nil do
>   begin
>     s := s + IntToStr(aux^.info); 
>     aux := aux^.sig; 
>     if aux <> nil then s := s + ', ';
>   end;
>   s := s + ']';
>   toString := s;
> end;
> ```

---

## Aplicaciones

> **💻 Aplicaciones de las Colas**  
> Las colas son ampliamente utilizadas en computación para manejar tareas como:
> - Gestión de tareas de la CPU.
> - Organización de trabajos de impresión.
> - Gestión de recursos compartidos.
> - Almacenamiento en búfer.
> - Centros de llamadas.
> - Y más.

---

## Colas y Genericidad

> **🧩 Genericidad en Colas**  
> Al igual que con las pilas, podemos crear colas genéricas para trabajar con cualquier tipo de dato, como enteros, cadenas, etc.  
> Se debe implementar un tipo de elemento que soporte operaciones como `assign`, `lessThan` y `equalTo` para garantizar su funcionalidad genérica.

---

