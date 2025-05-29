---
tags: URJC URJC_ED
---

# Tema 3 - Estructuras de Datos

---

## Tabla de Contenidos

1. [[Definición](#Definición)
2. [Medidas de Complejidad](#Medidas%20de%20Complejidad)
3. [Notación O Grande](#Notación%20O%20Grande)
4. [Cálculo de Complejidades](#Cálculo%20de%20Complejidades)
5. [Cálculo de Complejidades: Bucles](#Cálculo%20de%20Complejidades%20Bucles)
6. [Cálculo de Complejidades: Recursividad](#Cálculo%20de%20Complejidades%20Recursividad)
7. [Ejercicios Propuestos](#Ejercicios%20Propuestos)

---

## Definición

> **❓ ¿Qué es la complejidad?**  
> La complejidad de un algoritmo mide qué tan eficiente es para resolver el problema para el que fue diseñado.
> 
> Mide cuánto tiempo y espacio (memoria) necesita para producir una solución.
> 
> Estas medidas no son absolutas (en segundos, bytes…), sino relativas al tamaño del problema y son independientes de la máquina, la plataforma y el lenguaje utilizado.

---

## Medidas de Complejidad

> **⏱️ Complejidad temporal**  
> Consiste en contar el número de operaciones básicas (como sumas o multiplicaciones) que realiza el algoritmo.

> ---

> **💾 Complejidad espacial**  
> Consiste en determinar la cantidad de memoria (en bytes o bits) que utiliza el algoritmo al ejecutarse.

---

## Notación O Grande

> **🔍 ¿Qué es la notación O grande?**  
> La notación O grande se utiliza para comparar la complejidad de diferentes algoritmos.
> 
> Define la complejidad temporal de un algoritmo en función del tamaño de la entrada (n) y establece una cota superior asintótica para la función "número de operaciones del algoritmo".

> ---

> **📊 Comparativa de complejidades**  
> 
> | Complejidad      | Descripción             |
> |------------------|-------------------------|
> | $O(1)$           | Constante (la mejor)    |
> | $O(\log n)$      | Buena                   |
> | $O(n)$           | No está mal             |
> | $O(n \cdot \log n)$ | Mala                   |
> | $O(n^2)$, $O(2^n)$, $O(n!)$ | Muy mala          |


---

## Cálculo de Complejidades

> **📏 Regla de la Suma**  
> Si ejecutamos dos fragmentos de código secuenciales, la complejidad total será la del fragmento más lento:  
> O(max(A + B))

> ---

> **🔀 Regla del Producto**  
> Si un algoritmo se ejecuta como parte de otro, la complejidad final es el producto de las complejidades:  
> O(A·B)

> ---

> **⚖️ Regla del producto por constante**  
> Si dos fragmentos de código tienen complejidades O(N) y O(kN) para alguna constante k, en complejidad asintótica, el valor es el mismo: O(kN) = O(N).

> ---

> **📝 Asignaciones y expresiones simples**  
> Las asignaciones y expresiones simples, accesos a elementos de arrays, y lecturas o escrituras de datos simples tienen una complejidad O(1).

> ---

> **🔢 Complejidad lineal**  
> En un bucle que recorre todos los elementos de un arreglo:  
> O(1) + n·O(1) → O(n).

---

## Cálculo de Complejidades: Bucles

> **🔁 Bucles con número fijo de iteraciones**  
> Cuando el número de iteraciones es constante, la complejidad es O(1):  
> `for i:= 1 to K do sentencia_simple → K * O(1) = O(1)`
> 
> **🔁 Bucles lineales**  
> Cuando el número de iteraciones depende de n, la complejidad es O(n):  
> `for i:= 1 to n do sentencia_simple → n * O(1) = O(n)`
> 
> **🔁 Bucles anidados**  
> Si hay bucles anidados, la complejidad aumenta cuadráticamente:  
> `for i:= 1 to n do for j:= 1 to n do sentencia_simple → O(n²)`
> 
> **🔁 Bucles anidados no estrictamente n**  
> Si los bucles anidados no recorren todos los elementos, el número de iteraciones total puede ser diferente, pero sigue siendo cuadrático en muchos casos:  
> `for i:= 1 to n do for j:= 1 to i do for k:= j to n do → O(n²)`

---

## Cálculo de Complejidades: Recursividad

> **📜 Recursividad**  
> En algoritmos recursivos, la complejidad se calcula expandiendo las recurrencias y estudiando el caso base y general.  
> Ejemplo:  
> `Factorial(n) = n * Factorial(n-1) → O(n)`.

---

## Ejercicios Propuestos

> **1. Algoritmo iterativo para hallar el factorial de un número natural n:**  
> ```pascal
> fact := 1;
> for i:= 1 to n do
>    fact := fact * i;
> ```
> 
> **2. Algoritmo para buscar secuencialmente un elemento en un vector v con n elementos:**  
> ```pascal
> function Buscar(v: TipoVecor; buscado: integer): boolean;  
> i := 1;
> while (i <= n) and (v[i] <> buscado) do  
>    i := i + 1;  
> Buscar := i <= n;
> ```
> 
> **3. Bucle anidado:**  
> ```pascal
> x := 0;
> for i:= 1 to n do
>    for j:= 1 to n do
>       for k:= 1 to n do
>          x := x + 1;
> ```
> 
> **4. Bucle anidado:**  
> ```pascal
> x := 0;
> for i:= 1 to n do
>    for j:= 1 to i do
>       for k:= j to n do
>          x := x + 1;
> ```

---