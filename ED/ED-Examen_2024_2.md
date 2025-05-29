---
tags: URJC URJC_ED
---

# Examen 2024 - Estructura de Datos

---

## Tabla de Contenidos

1. [Ejercicio 1](#Ejercicio%201)
2. [Ejercicio 2](#Ejercicio%202)
3. [Ejercicio 3](#Ejercicio%203)
4. [Ejercicio 4](#Ejercicio%204)
5. [Ejercicio 5](#Ejercicio%205)
6. [Ejercicio 6](#Ejercicio%206)
7. [Ejercicio 7](#Ejercicio%207)
8. [Ejercicio 8](#Ejercicio%208)
9. [Ejercicio 9](#Ejercicio%209)
10. [Ejercicio 10](#Ejercicio%2010)
11. [Ejercicio 11](#Ejercicio%2011)
12. [Ejercicio 12](#Ejercicio%2012)
13. [Ejercicio 13](#Ejercicio%2013)
14. [Ejercicio 14](#Ejercicio%2014)

---

## Ejercicio 1

> **📄 Enunciado**
> El siguiente árbol binario de búsqueda fue creado insertando los números de una lista en secuencia. ¿Cuál de las siguientes secuencias **NUNCA** hubiera dado lugar a este árbol?
> 
> ```pseudo
>         5
>        / \
>       3   9
>        \  / \
>        4 7 12
>          /     \
>         6      20
>           \
>            8
> ```
> 
> _✅ Respuesta correcta_
> **E. 5 9 3 6 7 8 4 12 20**
> 
> En esta secuencia, el número **6** se inserta **antes** que el 7 y el 12, pero para que quede como **hijo izquierdo de 7**, como en el árbol final, el 7 debe existir antes.  
> 
> Además, el 4 aparece **después** del 6, lo cual rompe la posición que tiene como hijo derecho de 3.  
> 
> Por lo tanto, esta secuencia **no puede producir** la estructura mostrada.

---

## Ejercicio 2

> **📄 Enunciado**
> Nos piden utilizar un árbol AVL para mostrar ordenados por pantalla una secuencia de elementos que proceden de un generador aleatorio. ¿Es posible hacer algo así?
> 
> De ser posible, indica cómo lo harías y qué complejidad tendría tu solución.
> 
> No se pide implementar, solo responder razonadamente a las preguntas planteadas.
> 
> _✅ Respuesta correcta_
> 
> Sí, es posible.
> 
> Insertamos los elementos en un **árbol AVL**, que se mantiene **balanceado** automáticamente con cada inserción.
> 
> Luego, para obtener los elementos en orden creciente, realizamos un **recorrido inorden (inorder traversal)**, que visita los nodos en el siguiente orden:
> - Hijo izquierdo
> - Raíz
> - Hijo derecho
> 
> Este recorrido garantiza que los elementos se impriman de menor a mayor.
> 
> _🧮 Complejidad_
> - **Inserción** de N elementos en un AVL: **O(log N)** por elemento $\to$ total **O(N log N)**
> - **Recorrido inorden**: **O(N)**
> 
> **Complejidad total:** **O(N log N)**

---

## Ejercicio 3

> **📄 Enunciado**
> Desarrolla un subprograma que calcule la profundidad máxima de un árbol binario, medida como el número de niveles del camino más largo que parte de la raíz y llega a un nodo hoja.
> 
> Nota: Puedes utilizar la fución `max` de la biblioteca `Math` que calcula el máximo de dos números que recibe como argumentos.
> 
> _✅ Respuesta correcta_
> ```pascal
> function profundidad_maxima(a: TArbol): integer;
> begin
> 	if a = nil then profundidad_maxima := 0
> 	else begin
> 		profundidad_maxima := 1 + max(
> 			profundidad_maxima(a^.hi),
> 			profundidad_maxima(a^.hd)
> 		);
> 	end;
> end;
> ```

---

## Ejercicio 4

> **📄 Enunciado**
> Desarrolla un subprograma que realice una copia en profundidad de un subárbol que recibe como parámetro.
> 
> _✅ Respuesta correcta_
> ```pascal
> procedure copy(a: TArbol; var res: TArbol);
> begin
> 	if a <> nil then begin
> 		add(res, a^.info);
> 		copy(a^.hi, res);
> 		copy(a^.hd, res);
> 	end;
> end;
> ```

---

## Ejercicio 5

> **📄 Enunciado**
> Escribe la especificación de TAD Conjunto_de_dias que se utiliza para saber si un empleado trabaja un cierto día del mes o no.
> 
> Especifica todas las funciones que consideres necesarias para dicho TAD pero implementa solo las siguientes 2 funciones utilizando internamente un array de booleanos.
> - `inicializar(mes: Conjunto_de_dias, n: integer)`
> - `trabaja(mes: Conjunto_de_dias, dia: integer)`
> 
> _✅ Respuesta correcta_
> **TBD**

---

## Ejercicio 6

> **📄 Enunciado**
> Para representar un grafo, ponderado como el de la figura, hay 2 posibilidades. Indica cuáles y dibuja cómo quedaría representado el grafo en cada una de ellas:
> 
> _✅ Respuesta correcta_
> 1. Mediante una matriz de adyacencia 3 x 3.
> ```pseudo
> | M | A | B | C |
> | A | - | - | 5 |
> | B | 2 | - | 1 | 
> | C | - | 2 | - |
> ```
> 
> 2. Mediante una lista de listas de adyacencias.
> ```pseudo
> Lista de Adyacencia
> - [A] -> [(C, 5)]
> - [B] -> [(A, 2), (C, 1)]
> - [C] -> [(B, 2)]
> ```

---

## Ejercicio 7

> **📄 Enunciado**
> Si tenemos el siguiente grafo y queremos hacer un recorrido en anchura a partir del nodo 4. ¿Qué nodo jamás visitaríamos en primer lugar? ¿Y si el recorrido fuese en profundidad?
> 
> _✅ Respuesta correcta_
> Independientemente del tipo de recorrido, serían los nodos: `[2, 6, 9]`.

---

## Ejercicio 8

> **📄 Enunciado**
> Si recorremos el siguiente árbol binario en pre-orden y a medida que recorremos los nodos los vamos insertando en una cola... ¿Puedes representar gráficamente la cola y los contenidos de esta?
> 
> ```pseudo
>          45
>        /    \
>      23     65
>     /  \    /  \
>    2   38  52   96
>     \     /  \
>      7   48  52
> ```
> 
> _✅ Respuesta correcta_
> `[45, 23, 2, 7, 38, 65, 52, 48, 96]`

---

## Ejercicio 9

> **📄 Enunciado**
> Un software de control de acceso ha ido almacenando en un archivo todas las entradas de los empleados de una empresa a un edificio gracias a la lectura de su tarjerta en los tornos de entrada.
> 
> Se desea producir un listado de los identificadores de empleado almacenados sin duplicados.
> 
> **a)** Si el identificador de empleado es un entero entre 1 y 100, ¿cuál sería la opción de implementación más eficiente?
> 
> _✅ Respuesta correcta_
> Se podría implementar mediante un conjunto primitivo en Pascal. Por otra parte, podría implementarse mediante un Array de 100 posiciones de valores booleanos.
> 
> **b)** ¿Y si se usase el DNI (es decir, un string de 9 caracteres)? Razona tu respuesta.
> 
> _✅ Respuesta correcta_
> Mediante un árbol binario de búsqueda e implementado un método comparador que permita determinar si el DNI es mayor o menor.
> 
> Otra aleternativa sería una tabla hash, aunque podría tener problemas de conflictos.

---

## Ejercicio 10

> **📄 Enunciado**
> Indica a qué tipo de recorrido corresponde el siguiente algoritmo e indica qué nodos y en qué orde se visitarían en el grafo de la figura si se toma como nodo inicial el **2**.
> 
> _✅ Respuesta correcta_
> Se corresponde al recorrido en **profundidad**.
> Tiene como resultado: `[2, 5, 3, 0, 1]`.

---

## Ejercicio 11

> **📄 Enunciado**
> ¿Qué recorrido de los siguientes no podría haberse dado nunca utilizando un algoritmo de reocrrido en profunidad (DFS) que comenzase por el nodo 4?
> 
> _✅ Respuesta correcta_
> - **d** `[4, 0, 1, 2, 6, 9, 8, 5, 3, 7]`.
> - **e** `[4, 7, 3, 0, 1, 5, 8, 2, 6, 9]`.

---

## Ejercicio 12

> **📄 Enunciado**
> Describe el proceso de inserción en un árbol AVL de la siguiente secuencia de nodos: `12, 10, 23, 35, 28, 6, 3, 11, 15`.
> 
> Se deberán mostrar todos los pasos intermedios, indicando u describiendo las acciones que se deban ir tomando.
> 
> _✅ Respuesta correcta_
> 1. Inserción del nodo `12`.
> 2. Inserción del nodo `10`.
> 3. Inserción del nodo `23`.
> 4. Inserción del nodo `35`.
> 5. Inserción del nodo `28`. Balanceo del nodo `23`.
> 6. Inserción del nodo `6`. 
> 7. Inserción del nodo `3`. Balanceo del nodo `10`.
> 8. Inserción del nodo `11`. 
> 9. Inserción del nodo `15`.
> 
> ```pseudo
>      12
>     /  \
>    6    28
>   / \   /  \
>  3  10 23  35
>       \   /
>       11 15
> ```
 
---

## Ejercicio 13

> **📄 Enunciado**
> En un árbol AVL inicialmente vacío se insertan, por este orden, los valores `25, 26, 27, 19, 21, 23, 19, 30`.
> 
> Muestra el árbol al final del proceso, llevando a cabo recalibraciones.
> 
> _✅ Respuesta correcta_
> 1. Inserción del nodo `25`.
> 2. Inserción del nodo `26`.
> 3. Inserción del nodo `27`. Balanceo del nodo `25`.
> 4. Inserción del nodo `19`.
> 5. Inserción del nodo `21`. Balanceo del nodo `25`.
> 6. Inserción del nodo `23`. Balanceo del nodo `26`.
> 7. Inserción del nodo `30`. Balanceo del nodo `26`.
> 
> ```pseudo
>      25
>     /  \
>    21    27
>   / \   /  \
>  19  23 26  30
> ```    

---

## Ejercicio 14

> **📄 Enunciado**
> Dado el siguiente subprograma, indica qué hace.
> 
> ```pascal
> procedure misterio(a: tArbol, var l: tLIsta);
> var
> 	r: integer;
> begin
> 	if not is_empty(a) then
> 	begin
> 		if is_empty(a^.hi) and is_empty(a.^hd) then
> 			insert(l, a^.info);
> 		else begin
> 			misterio(a^.hi, l);
> 			misterio(a^.hd, l);
> 		end;
> 	end;
> end;
> ```
> 
> _✅ Respuesta correcta_
> La función `misterio` inserta en una lista todos los nodos hojas del árbol binario de búsqueda siguiendo el recorrido **preorden**.

---