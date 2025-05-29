---
tags: URJC URJC_IO
---

# Tema 3 - Investigación Operativa

---

## Tabla de Contenidos

1. [¿Qué es la Optimización Entera?](#¿Qué%20es%20la%20Optimización%20Entera?)
2. [Relación de la Programación Entera con la Lineal](#Relación%20de%20la%20Programación%20Entera%20con%20la%20Lineal)
3. [Problema de la Mochila](#Problema%20de%20la%20Mochila)
4. [Problema de Selección de Inversiones](#Problema%20de%20Selección%20de%20Inversiones)
5. [Problema del Viajante de Comercio (TSP)](#Problema%20del%20Viajante%20de%20Comercio%20(TSP))
6. [Planificación de Producción: PCIngredients](#Planificación%20de%20Producción%20PCIngredients)
7. [Bibliografía](#Bibliografía)

---

## ¿Qué es la Optimización Entera?

> **Optimización Entera**
> Extensión de los modelos lineales donde algunas variables toman valores enteros, frecuentemente $0$ o $1$. Permite representar sistemas más complejos a cambio de mayor dificultad computacional.

> **Clasificación de problemas**
> 
> *Clase P*
> Resolubles en tiempo polinomial.
> 
> *Clase NP*
> Soluciones verificables en tiempo polinomial.
> 
> *NP-completo*
> Problemas más difíciles en NP, incluyendo problemas como SAT o clique.
> 
> *NP-duro*
> Tan difícil como cualquier problema en NP, pero no necesariamente verificable en tiempo polinomial.

> ---

> **Ventajas de la Optimización Entera**
> 
> *Precisión*
> Los modelos enteros permiten capturar decisiones binarias o de conteo, ajustándose a escenarios reales como "hacer o no hacer" y "asignar unidades discretas".
> 
> *Flexibilidad*
> Admite modelado de condiciones complejas como exclusiones mutuas, dependencias lógicas y umbrales mínimos o máximos.
> 
> **Desventajas de la Optimización Entera**
> *Complejidad Computacional*
> Resolver modelos enteros es significativamente más complejo que los modelos lineales continuos, especialmente a gran escala.
> 
> *Limitación de Escalabilidad*
> El tiempo de cálculo puede crecer exponencialmente con el número de variables.

> ---

> **Aplicaciones de la Optimización Entera**
> 
> *Gestión de Recursos*
> Asignación de personal, vehículos y maquinaria.
> 
> *Planificación de Producción*
> Determinación de lotes de fabricación y combinación de productos.
> 
> *Logística*
> Diseño de rutas, almacenamiento y distribución.
> 
> *Inversiones*
> Selección óptima de carteras bajo restricciones presupuestarias.

---

## Relación de la Programación Entera con la Lineal

> Los modelos de programación entera comparten la estructura de la programación lineal, pero añaden restricciones que imponen valores enteros a ciertas variables. Esto se logra utilizando métodos especializados como:
> 
> *Branch and Bound*
> Divide el problema en subproblemas más simples.
> 
> *Branch and Cut*
> Combina la división de problemas con cortes para reducir el espacio de soluciones.
> 
> *Método del Plano de Cortes*
> Introduce restricciones adicionales para excluir soluciones no enteras.

---

## Problema de la Mochila

> **Caso**
> Se dispone de N objetos, cada uno con las siguientes características:
> - Un valor asociado $v_i$​.
> - Un peso asociado $w_i$.
> 
> Además, se cuenta con una mochila que tiene una capacidad máxima de peso $W$. El objetivo es determinar una combinación óptima de objetos que maximice el valor total​, cumpliendo las siguientes condiciones:
> 
> 1. El peso total de los objetos seleccionados no debe superar la capacidad máxima de la mochila $W$.
> 2. Cada objeto puede ser seleccionado o no (decisión binaria).
> 3. No se permiten fracciones de objetos, es decir, cada objeto debe ser incluido completamente o no incluido en absoluto.
> 
> | Objeto | Valor (€) | Peso (kg) |
> | ------- | --------- | ----------- |
> |    1      |    60        |     10        |
> |    2      |   100       |     20        |
> |    3      |   120       |     30        |
> 
> Capacidad máxima: $50 \space kg$.

> **Objetivo**
> Seleccionar objetos con peso y valor conocidos para maximizar el valor total sin exceder la capacidad máxima de peso de una mochila.

> ---

> **Modelo matemático**
> 
> *Función objetivo*
> $\max Z = \sum_i^N{v_i \cdot x_i}$
> 
> *Restricciones*
> $\sum_i^N{w_i \cdot x_i} ≤ W$ $\to$ Límite de la mochila.
> $x_i \in \{0, 1\}$ $\to$  Decisión binaria sobre incluir el objeto $i$.

> ---

> **Implementación en Python**
> 
> ```python
> from gurobipy import Model, GRB
>
> # Datos del problema
> objetos = [1, 2, 3]
> valores = {1: 60, 2: 100, 3: 120}
> pesos = {1: 10, 2: 20, 3: 30}
> capacidad = 50
>
> # Crear modelo
> modelo = Model("Mochila_0_1")
>
> # Variables de decisión
> x = {}
> for i in objetos:
> 	x[i] = modelo.addVar(vtype=GRB.BINARY, name=f"x_{i}")
> 	
> # Restricción de capacidad
> modelo.addConstr(
> 	sum(pesos[i] * x[i] for i in objetos) <= capacidad,
> 	name="Capacidad"
> )
>
> # Función objetivo
> modelo.setObjective(
> 	sum(valores[i] * x[i] for i in objetos),
> 	GRB.MAXIMIZE
> )
>
> # Optimizar el modelo
> modelo.optimize()
>
> # Resultados
> if modelo.status == GRB.OPTIMAL:
>     print(f"Valor óptimo: {modelo.ObjVal}")
>     print("Objetos seleccionados:")
>     for i in objetos:
>         if x[i].X > 0.5:
>             print(f" - Objeto {i}: Valor = {valores[i]}, Peso = {pesos[i]}")
> else:
> 	print("No se ha encontrado una solución")
> ```

---

## Problema de Selección de Inversiones

> **Caso**
> Una empresa considera cuatro inversiones, cada una con un beneficio y costo asociados. Con un presupuesto limitado, se busca maximizar el beneficio.
> 
> | Inversión | Beneficio (€) | Costo (€) |
> |-----------|---------------|-----------|
> |     1         |    16,000        |  5,000     |
> |     2         |    22,000        |  7,000     |
> |     3         |    12,000        |  4,000     |
> |     4         |     8,000         |  3,000     |
> 
> Presupuesto máximo: $14,000 \space \text{€}$.

> **Objetivo**
> Maximizar el beneficio de la empresa basado en los datos proporcionados.

> ---

> **Modelo matemático**
> 
> *Función objetivo*
> $\max Z = \sum_i^N{b_i \cdot x_i}$
> 
> *Restricciones*
> $\sum_i^N{c_i \cdot x_i} ≤ \text{Presupuesto}$ $\to$ Restricción de presupuesto.
> $x_i \in \{0, 1\}$ $\to$ Decisión binaria sobre realizar la inversión $i$.

> ---

> **Implementación en Python**
> 
> ```python
> from gurobipy import Model, GRB
>
> # Datos del problema
> inversiones = [1, 2, 3, 4]
> beneficios = {1: 16000, 2: 22000, 3: 12000, 4: 8000}
> costos = {1: 5000, 2: 7000, 3: 4000, 4: 3000}
> presupuesto = 14000
>
> # Crear modelo
> modelo = Model("Seleccion_Inversiones")
>
> # Variables de decisión
> x = {}
> for i in inversiones:
> 	x[i] = modelo.addVar(vtype=GRB.BINARY, name=f"x_{i}")
> 
> # Restricción de presupuesto
> modelo.addConstr(
> 	sum(costos[i] * x[i] for i in inversiones) <= presupuesto,
> 	"Presupuesto"
> )
> 
> # Función objetivo
> modelo.setObjective(
> 	sum(beneficios[i] * x[i] for i in inversiones),
> 	GRB.MAXIMIZE
> )
>
> # Optimizar
> modelo.optimize()
>
> # Resultados
> if modelo.status == GRB.OPTIMAL:
>     print(f"Beneficio óptimo: {modelo.ObjVal}")
>     print("Inversiones seleccionadas:")
>     for i in inversiones:
>         if x[i].X > 0.5:
>             print(f" - Inversión {i}: Beneficio = {beneficios[i]}, Costo = {costos[i]}")
> else:
> 	print("No se ha encontrado una solución")
> ```

---

## Problema del Viajante de Comercio (TSP)

> **Caso**
> Un viajante debe recorrer un conjunto de ciudades, visitando cada una exactamente una vez y regresando al punto de partida. El objetivo es minimizar el costo total del recorrido, es decir, la distancia total recorrida, respetando que no se repiten ciudades.
>
> | Ciudad | Coordenadas (X, Y) |
> | -------- | --------------------- |
> |       1     |          (0, 0)              |
> |       2     |          (1, 2)              |
> |       3     |          (4, 5)              |
> |       4     |          (7, 8)              |
>
> Distancia máxima entre ciudades: $\infty$.

> **Objetivo**
> Minimizar la distancia total recorrida por el viajante visitando todas las ciudades una vez y regresando a la ciudad inicial.

> ---

> **Modelo matemático**
> 
> *Función objetivo*
> $\min Z = \sum_i^N{c_{ij} \cdot x_{ij}}$
> 
> Donde ( $c_{ij}$ ) es la distancia entre la ciudad ( $i$ ) y la ciudad ( $j$ ), y ( $x_{ij}$ ) es una variable binaria que indica si el viajante va de la ciudad ( $i$ ) a la ciudad ( $j$ ).
> 
> *Restricciones*
> $\sum_{i, j}^N{x_{ij}} = 1$ $\to$ Cada ciudad sea visitada exactamente una vez.
> $\sum_{i, j}^N{x_{ji}} = 1$ $\to$ Cada ciudad sea salida exactamente una vez.
> $u[i] - u[j] + n \cdot x_{ij} \leq n - 1$ $\to$ Evitar ciclos en el recorrido.

> ---

> **Implementación en Python**
> 
> ```python
> from gurobipy import Model, GRB
> import math
>
> # Datos del problema
> ciudades = [1, 2, 3, 4]
> coordenadas = {1: (0, 0), 2: (1, 2), 3: (4, 5), 4: (7, 8)}
> n = len(ciudades)
> distancias = {}
> for i in ciudades:
>     for j in ciudades:
>         if i != j:
>             distancias[(i, j)] = math.sqrt((coordenadas[i][0] - coordenadas[j][0]) ** 2 +
>                                            (coordenadas[i][1] - coordenadas[j][1]) ** 2)
>
> # Crear modelo
> modelo = Model("Viajante_de_Comercio")
>
> # Variables de decisión
> x = {}
> for i in ciudades:
>     for j in ciudades:
>         if i != j:
>             x[i, j] = modelo.addVar(vtype=GRB.BINARY, name=f"x_{i}\_{j}")
> 
> u = {}
> for i in ciudades:
>     u[i] = modelo.addVar(vtype=GRB.CONTINUOUS, name=f"u_{i}")
> 
> # Restricciones
> for i in ciudades:
>     if i != 1:
>         modelo.addConstr(sum(x[i, j] for j in ciudades if j != i) == 1, f"Salida_{i}")
>         modelo.addConstr(sum(x[j, i] for j in ciudades if j != i) == 1, f"Llegada_{i}")
> for i in ciudades:
>     for j in ciudades:
>         if i != j and i != 1 and j != 1:
>             modelo.addConstr(u[i] - u[j] + n * x[i, j] <= n - 1, f"No_Ciclos_{i}\_{j}")
>
> # Función objetivo
> modelo.setObjective(
>     sum(distancias[i, j] * x[i, j] for i in ciudades for j in ciudades if i != j),
>     GRB.MINIMIZE
> )
>
> # Optimizar
> modelo.optimize()
>
> # Resultados
> if modelo.status == GRB.OPTIMAL:
>     print(f"Distancia óptima: {modelo.ObjVal}")
>     print("Ruta seleccionada:")
>     ruta = []
>     for i in ciudades:
>         for j in ciudades:
>             if i != j and x[i, j].X > 0.5:
>                 ruta.append((i, j))
>     print(ruta)
> else:
>     print("No se ha encontrado una solución")
> ```

---

## Planificación de Producción: PCIngredients

> **Caso**
> La empresa PCIngredients produce tres tipos de ordenadores: de mesa (A), portátil normal (B) y portátil de lujo (C). El beneficio neto por la venta un ordenador es 350, 470 y 610 euros, respectivamente.
> 
> Los ordenadores pasan un control de calidad de una hora y la empresa dispone de 120 horas para realizar los controles de los ordenadores A y B y 48 para los C.
> 
> El resto de las operaciones de montaje requieren 10, 15 y 20 horas, respectivamente, y la empresa dispone de 2000 horas a la semana.

> **Objetivo**  
> Maximizar el beneficio total de la producción de tres tipos de ordenadores, respetando las limitaciones de tiempo de control de calidad, horas de montaje y capacidad de producción interna y externa.

> **Variables de decisión**
> $x_1$ $\to$ Cantidad de ordenadores A (de mesa) producidos.
> $x_2$ $\to$ Cantidad de ordenadores B (portátil normal) producidos.
> $x_3$ $\to$ Cantidad de ordenadores C (portátil de lujo) producidos.

> **Modelo matemático**  
> 
> *Función objetivo*  
> $\max Z = 350 \cdot x_1 + 470 \cdot x_2 + 610 \cdot x_3$
> 
> *Restricciones*  
> $10 * x_1 + 15 \cdot x_2 + 20 \cdot x_3 \leq 2000$ $\to$ Restricción de horas de montaje.
> $x_1 + x_2 \leq 120$ $\to$ Restricción de horas de calidad para los productos A y B.
> $x_3 \leq 48$ $\to$ Restricción de horas de calidad para el producto C.
> $x_1, x_2, x_3 \geq 0$ $\to$ Restricción de no negatividad.

> ---

> **Implementación en Python**
> ```python
> from gurobipy import Model, GRB
> 
> # Crear el modelo
> modelo = Model("Producción de Ordenadores")
> 
> # Definir variables de decisión
> x1 = modelo.addVar(name="Ordenador_A", lb=0)
> x2 = modelo.addVar(name="Ordenador_B", lb=0)
> x3 = modelo.addVar(name="Ordenador_C", lb=0)
> 
> # Definir la función objetivo
> modelo.setObjective(350 * x1 + 470 * x2 + 610 * x3, GRB.MAXIMIZE)
> 
> # Agregar restricciones
> modelo.addConstr(10 * x1 + 15 * x2 + 20 * x3 <= 2000, name="Restricción_Montaje")
> modelo.addConstr(x1 + x2 <= 120, name="Restricción_Quality_AB")
> modelo.addConstr(x3 <= 48, name="Restricción_Quality_C")
> 
> # Optimizar
> modelo.optimize()
> 
> # Imprimir los resultados
> if modelo.status == GRB.OPTIMAL:
> 	print("Solución óptima encontrada:")
> 	print(f"Ordenadores A (de mesa) producidos: {x1.x}")
> 	print(f"Ordenadores B (portátil normal) producidos: {x2.x}")
> 	print(f"Ordenadores C (portátil de lujo) producidos: {x3.x}")
> 	print(f"Beneficio total: {modelo.objVal} euros")
> else:
> 	print("No se ha encontrado una solución óptima.")
> ```

---

## Bibliografía

> 1. Sixto Ríos Insua. _Investigación Operativa. Optimización._
> 2. Sixto Ríos Insua. *Problemas de Investigación Operativa. Programación Lineal y Extensiones.*
> 3. Paul W. Williams. *Model Building in Mathematical Programming.*

---