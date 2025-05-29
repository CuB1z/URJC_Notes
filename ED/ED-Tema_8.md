---
tags: URJC URJC_ED
---

# Tema 8 - Estructuras de Datos

---

## Tabla de Contenidos

1. [Definiciones](#Definiciones)
2. [Tipos de Árboles](#Tipos%20de%20Árboles)
3. [Recorridos](#Recorridos)
4. [Especificaciones](#Especificaciones)
5. [Implementación](#Implementación)
6. [Árboles AVL](#Árboles%20AVL)

---

## Definiciones

> **🔍 ¿Qué es un árbol?**
> Un árbol es una estructura de datos no lineal y jerárquica compuesta por nodos. Cada nodo tiene un nodo padre y puede tener varios nodos hijos.
> 
> La **raíz** es el nodo inicial, y las **hojas** son los nodos terminales, sin descendientes.
> 
> Un árbol es recursivo, es decir, cualquier subparte del árbol es también un árbol.

> ---

> **🌿 Elementos de un Árbol**
> - **Nodo raíz**: Es el nodo principal del árbol, desde donde comienza la jerarquía.
> - **Hijos**: Los nodos que dependen de un nodo padre. Cada nodo puede tener varios hijos.
> - **Hoja**: Un nodo que no tiene hijos, es el nodo terminal.
> - **Rama**: La conexión entre un nodo y sus hijos.

> ---

> **🌱 Tipos de árboles en relación a sus estructuras**
> - **Árboles completos**: Cada nodo tiene el máximo número de hijos posibles.
> - **Árboles binarios**: Tienen a lo sumo dos hijos por nodo.

---

## Tipos de Árboles

> **🌳 Árboles Generales**
> Un árbol general no tiene límite en el número de hijos por nodo. Se representa mediante un nodo raíz que puede tener varios descendientes y subárboles.
> 
> Para su implementación se utiliza un manejador, que es un puntero al nodo raíz, y una estructura de nodo con enlaces a sus hijos.

> ---

> **🌳 Árboles Binarios**
> En los **árboles binarios**, cada nodo tiene como máximo dos hijos: izquierdo y derecho.
> 
> Los nodos hijos izquierdo y derecho son subárboles binarios, y las operaciones sobre el árbol se realizan de manera recursiva.

> ---

> **🌲 Árboles Binarios de Búsqueda (BST)**
> En los árboles binarios de búsqueda, para cada nodo, los valores de su subárbol izquierdo son menores que el nodo, y los valores del subárbol derecho son mayores. Esto permite realizar búsquedas rápidas y eficientes.

> ---

> **🔑 Características de los Árboles Binarios**
> - Cada nodo tiene 2 hijos como máximo.
> - Los árboles binarios son útiles para representar jerarquías de decisiones o estructuras de datos como tablas hash y listas enlazadas.

---

## Recorridos

> **🔄 Recorridos de un árbol**
> Los recorridos en árboles binarios son técnicas para visitar todos los nodos de manera ordenada. Existen dos tipos principales:
> - **Recorrido en profundidad**:  
>   1. **Pre-orden**: Raíz, subárbol izquierdo, subárbol derecho.
>   2. **In-orden**: Subárbol izquierdo, raíz, subárbol derecho.
>   3. **Post-orden**: Subárbol izquierdo, subárbol derecho, raíz.
> - **Recorrido en anchura**: Visita los nodos horizontalmente, de la raíz a todos sus hijos, luego a los hijos de los hijos, y así sucesivamente.

> ---

> **🌐 Recorrido en profundidad (Pre-orden)**  
> 1. Visita la raíz.  
> 2. Recurre al subárbol izquierdo.  
> 3. Recurre al subárbol derecho.

> ---

> **🌐 Recorrido en profundidad (In-orden)**  
> 4. Recorre el subárbol izquierdo.  
> 5. Visita la raíz.  
> 6. Recorre el subárbol derecho.

> ---

> **🌐 Recorrido en profundidad (Post-orden)**  
> 7. Recorre el subárbol izquierdo.  
> 8. Recorre el subárbol derecho.  
> 9. Visita la raíz.

---

## Especificaciones

> **📝 TAD Árbol Binario**
> El TAD Árbol Binario se define con las siguientes operaciones:
> - `add`: Añadir un elemento.
> - `remove`: Eliminar un elemento.
> - `is_empty`: Comprobar si el árbol está vacío.
> - `in`: Verificar si un elemento está en el árbol.
> - `initialize`: Inicializar el árbol.
> 
> **Otras posibles operaciones**:
> - **find**: Buscar un elemento específico.
> - **height**: Calcular la altura del árbol.
> - **balance_factor**: Calcular el factor de balance en árboles AVL.

> ---

> **Operaciones en Árboles Binarios de Búsqueda**
> - **insert**: Insertar un nodo en el árbol binario.
> - **delete**: Eliminar un nodo del árbol binario.

---

## Implementación

> **⚙️ Implementación de un Árbol Binario de Búsqueda (BST)**
> El **árbol binario de búsqueda** sigue las reglas de que los datos del subárbol izquierdo son menores que el nodo raíz, y los datos del subárbol derecho son mayores.
> 
> Para implementar el TAD, se pueden usar punteros a los nodos del árbol. Aquí hay un ejemplo de cómo se implementa la estructura:
> 
> ```pascal
> type
>   tBinarySearchTree = ^tnode;
>   tnode = record
>     info: integer;
>     hi, hd: tBinarySearchTree;
>   end;
> 
> procedure initialize(var a: tBinarySearchTree);
> function is_empty(a: tBinarySearchTree): boolean;
> procedure add(var a: tBinarySearchTree; x: integer);
> function in_tree(a: tBinarySearchTree; x: integer): boolean;
> procedure remove(var a: tBinarySearchTree; x: integer);
> ```

> ---

> **🔄 Método Recursivo en BST**
> El método `add` se realiza de manera recursiva:
> 1. Si el valor a insertar es menor que el nodo actual, se mueve al subárbol izquierdo.
> 2. Si es mayor, se mueve al subárbol derecho.
> 3. Si el nodo es vacío, se crea el nuevo nodo.

---

## Árboles AVL

> **🌳 Árboles AVL**
> Un **árbol AVL** es un tipo especial de árbol binario de búsqueda que es **auto-balanceable**. Esto significa que después de cada operación de inserción o eliminación, el árbol se ajusta para mantener un equilibrio en su estructura.
> 
> El factor de equilibrio de un nodo se calcula como la diferencia entre la altura de su subárbol derecho y su subárbol izquierdo. Este factor debe estar entre -1 y 1.

> ---

> **🔄 Rotaciones**
> Para mantener el árbol equilibrado, se realizan rotaciones:
> - **Rotación simple**: a izquierda o a derecha.
> - **Rotación doble**: combina dos rotaciones simples para reequilibrar.

> ---

> **🛠 Ejemplo de inserción en un árbol AVL**
> Cuando un nodo es insertado y desequilibra el árbol, se debe realizar una rotación para restaurar el equilibrio. Existen cuatro casos básicos de rotación:
> - **LL**: Rotación simple a la derecha.
> - **RR**: Rotación simple a la izquierda.
> - **LR**: Rotación doble a la izquierda, luego a la derecha.
> - **RL**: Rotación doble a la derecha, luego a la izquierda.

---