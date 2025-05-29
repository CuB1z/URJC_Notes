---
tags: URJC URJC_ED
---

# Tema 9 - Grafos

---

## Tabla de Contenidos

1. [Introducción](#Introducción)
2. [Tipos de grafos](#Tipos%20de%20grafos)
3. [Conceptos básicos](#Conceptos%20básicos)
4. [TAD Grafo: especificación](#TAD%20Grafo%20especificación)
5. [Representación](#Representación)
6. [Implementación](#Implementación)
7. [Recorridos](#Recorridos)

---

## Introducción

> **🔍 ¿Qué es un grafo?**
> Un grafo es una estructura de datos abstracta, no lineal, compuesta por un conjunto de vértices o nodos y un conjunto de aristas o arcos que los conectan.
> 
> Formalmente se define como un par $(G = (V, A))$, donde $(V)$ es el conjunto de vértices y $(A)$ es el conjunto de arcos. Un arco es un par $((v_1, v_2))$ de vértices de $(V)$.
> 
> Los grafos se utilizan para modelar numerosos dominios tales como mapas, transporte o redes de todo tipo (de ordenadores, de comunicación, sociales, biológicas, etc.).

---
  
## Tipos de grafos

> **🌳 Grafos Dirigidos vs No Dirigidos**
> 
> *📍 Grafo Dirigido (Digrafo)*
> Las aristas son pares ordenados, es decir, tienen un **origen** y un **destino** definidos, lo que implica que las relaciones tienen una dirección específica.
> 
> *🔄 Grafo No Dirigido*
> Las aristas no tienen un sentido definido; la relación entre los vértices es **bidireccional**, es decir, puede ir en ambas direcciones.

> ---

> **🌳 Grafos Binarios vs Grafos Ponderados**
> 
> *⚪ Grafo Binario*
> Las aristas simplemente indican la existencia o no existencia de una relación entre dos vértices, sin un valor adicional que cuantifique la relación.
> 
> *💰 Grafo Ponderado*
> Las aristas tienen un **peso** o **valor** asociado que representa, por ejemplo, la distancia, costo o capacidad de la conexión entre los vértices.

> ---

> **🌳 Otras Clasificaciones de Grafos**
> 
> *🔗 Conexo vs No Conexo*
> Un grafo **conexo** tiene un camino entre cualquier par de vértices, mientras que en un grafo **no conexo** existen vértices sin conexión directa entre sí.
> 
> *🔢 Unicapa vs Multicapa (Múltiplex)*
> Los grafos **unicapa** tienen una sola arista entre los mismos vértices, mientras que los **multicapa** permiten múltiples aristas entre un par de vértices, representando diferentes tipos de relaciones.
> 
> *⚪ Grafo Simple vs Multigrafo*
> En un **multigrafo**, se permite más de una arista entre los mismos vértices, lo que no es posible en un **grafo simple**, donde solo se permite una arista entre cada par de vértices.
> 
> *⏳ Estáticos vs Dinámicos*
> Los grafos **estáticos** tienen una estructura fija, mientras que los **dinámicos** pueden cambiar con el tiempo, ya sea modificando los vértices o las aristas (por ejemplo, en redes sociales o de comunicación en tiempo real).


---

## Conceptos básicos

> **📍 Grado de un vértice**
> El grado de un vértice es el número de aristas incidentes en él.
> 
> - **Grado saliente** (out-degree) en grafos dirigidos: Número de aristas que salen de un vértice.
> - **Grado entrante** (in-degree) en grafos dirigidos: Número de aristas que llegan a un vértice.

> ---

> **📍 Camino**
> - **Camino Simple**: Un camino en el que todos sus vértices son distintos.
> - **Longitud**: El número de aristas de un camino.
> - **Camino Cerrado**: Un camino en el que el primer y último vértice son el mismo (bucle).
> - **Camino Mínimo**: El camino más corto entre dos vértices.

> ---

> **📍 Adyacencia y Bucle**
> - **Adyacencia**: Dos vértices se consideran adyacentes si están conectados por una arista.
> - **Bucle**: Un camino simple cerrado de longitud \( k \).

---

## TAD Grafo: especificación

> **📝 Operaciones del TAD Grafo**
> El TAD Grafo se define con las siguientes operaciones:
> - `insert_node()`: Insertar un nodo.
> - `insert_edge()`: Insertar una arista.
> - `delete_node()`: Eliminar un nodo.
> - `delete_edge()`: Eliminar una arista.
> - `is_empty(graph)`: Comprobar si el grafo está vacío.
> - `in_graph(node)` / `in_graph(arc)`: Verificar si un nodo o una arista está en el grafo.
> - `degree(node)` / `indegree(node)` / `outdegree(node)`: Obtener el grado de un nodo.
> - `adjacent(node1, node2)`: Comprobar si dos nodos son adyacentes.

> ---

> **📍 Otras Operaciones**
> En grafos utilizados en análisis de redes sociales, por ejemplo, se calculan métricas como:
> - Diámetro
> - Coeficiente de clustering
> - Betweenness, closeness, eigenvector centrality
> - Densidad

---

## Representación

> **🔧 Representación de Grafos**
> Los grafos son estructuras complejas que requieren representaciones apropiadas. Existen dos tipos principales:
> - **Representaciones Estáticas**: Como matrices de adyacencia y vectores de nodos.
> - **Representaciones Dinámicas**: Como listas de adyacencia y listas de arcos.

> ---

> **🌐 Matriz de Adyacencia**
> En una matriz de adyacencia, se usa una tabla de \( n \times n \) (siendo \( n \) el número de vértices). Las celdas representan las relaciones entre los vértices:
> - En grafos ponderados, las celdas contienen valores numéricos (pesos).
> - En grafos no dirigidos, las relaciones se reflejan en ambos sentidos.

> ---

> **🌐 Lista de Adyacencia**
> La lista de adyacencia es una representación más eficiente para grafos dispersos, donde cada vértice tiene una lista de sus nodos vecinos. Esta lista puede estar ponderada o no.

---

## Implementación

> **⚙️ Implementación de un Grafo Dirigido**
> La implementación de un grafo dirigido puede realizarse con una matriz de adyacencia o una lista de adyacencia. La elección depende de la densidad del grafo y la frecuencia de las operaciones.

---

## Recorridos

> **🔄 Recorridos de Grafos**
> Recorrer un grafo implica visitar todos los nodos alcanzables desde un nodo dado sin repetir ningún nodo. Los dos tipos principales de recorrido son:
> - **En Anchura (BFS, Breadth-first)**: Utiliza una cola auxiliar.
> - **En Profundidad (DFS, Depth-first)**: Utiliza una pila auxiliar.

> ---

> **🌍 Recorrido en Anchura (BFS)**
> El algoritmo de recorrido en anchura visita primero los nodos adyacentes al nodo inicial y luego explora los nodos de nivel 1, nivel 2, etc. Utiliza una **cola** para almacenar los nodos por visitar.

> ---

> **🌍 Recorrido en Profundidad (DFS)**
> El algoritmo de recorrido en profundidad explora lo más profundo posible antes de retroceder. Utiliza una **pila** para almacenar los nodos por visitar.

---