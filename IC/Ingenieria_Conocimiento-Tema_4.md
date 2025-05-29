---
tags: URJC URJC_IC
---

# Tema 4 - Ingeniería del Conocimiento

---

## ¿Qué es la búsqueda heurística avanzada?

> **Búsqueda Heurística Avanzada**
> Utiliza estrategias y reglas específicas para encontrar soluciones eficientes a problemas complejos, reduciendo el espacio de búsqueda mediante aproximaciones o atajos.

---

## Aprendizaje de funciones heurísticas

> **Idea**
> Generar información heurística "sobre la marcha", es decir, realizar varias búsquedas (ligeramente diferentes) en el mismo dominio. Por ejemplo, siempre a Bucares, pero desde diferentes ciudades iniciales.
> 
> En cada paso de una búsqueda, usar el coste real de un paso para mejorar el valor de h⁺, y, en la próxima búsqueda se utilizarán los valores de h⁺ actualizados.

> **Método**
> - Inicialmente, se realiza una búsqueda con `h⁺(n) = 0`para todos los nodos n.
> - En cada paso de `ni` a `nj`: `h⁺(ni) <- min [h⁺(nj) + c(ni, nj)]`.
> - Extensión (opcional):
> 	- Al aprender un nuevo valor `h⁺(n)` para un estado `n`, en caso de que hubieran otras copias de `n` como hojas en el árbol de búsqueda generado por A⁺, actualizar sus valores de f⁺.

> **Problema**
> Hay que almacenar los valores de h⁺ de todos los nodos en una tabla (memoria).

---

## Diseño de funciones heurísticas

> **Opciones**
> - Intuición del diseñador (por ejemplo, la similitud con heurísticas para dominios parecidos).
> - Método sistemático de diseño (a partir de las características de un estado s).

> **Problemas relajados**
> Problema relajado P' con respecto a un problema original P:
> - Igual en P y en P': conjunto de estados S, estado inicial `s0`, estados meta.
> - En P' se pueden realizar las mismas acciones que en P, y algunas más.
> - Para las acciones compartidas, el coste c es el mismo en P y en P'.
>
> _Ejemplo_: Red regular 2D - estado meta: (x, y) - coste por acción: 1.
> - `hP ((u,v)) = | u – x | + | v – y |`.
> - `hP’ ((u,v)) = max(| u – x |, | v – y |)`.
> - `hP⁺((u,v)) = max(| u – x |, | v – y |)`.
> - Idea:
> 	- Por construcción, `hP’(n) <= hP(n)` para todo estado s perteneciente a S.
> 	- Si hP’ se puede computar fácilmente, constituye una función heurística optimista hP⁺ efectiva para P.

> **¿Cómo encontrar problemas relajados P' ?**
> Relajar las precondiciones para poder aplicar una acción a en un estado s en el problema original P

---

## Problema del 8-puzzle

> **Estados**
> Posición de cada una de las piezas.
> 
> _Estado inicial_: [(2, 7, 3), (1, 8, 4), (6, \_, 5)]
> 
> _Estado meta_: [(1, 2, 3), (8, \_, 4), (7, 6, 5)]

> **Operadores**
> Mover pieza adyacente a la posición del "hueco".
> - De 2 a 4 operadores aplicables, según el estado.

> **Coste**
> La aplicación de cada operador vale una unidad.

> ---

> **Precodiciones para acciones en P**
> Se puede mover una ficha de X a Y en s si:
> - `C1`: Y está vacío en s y `C2`: X es adyacente a Y.

> **Precodiciones para acciones en diferentes P'**
> Se puede mover una ficha de X a Y en s si:
> - `Pa'`: Siempre (se pide ninguna de las precondiciones).
> - `Pb'`: Si Y está vacío (se pide sólo `C1`).
> - `Pc'`: Si X es adyacente a Y (se pide sólo `C2`).

> **Funciones heurísticas para P**
> - `ha⁺(s)` = número de piezas descolocadas en s.
> 	- Ejemplo: `ha⁺(s0)` = 5.
> - `hb⁺(s)` = suma de saltos necesarios en s.
> 	- Ejemplo: `ha⁺(s0)` = 5.
> - `hc⁺(s)` = suma de las distancias de Manhattan en s.
> 	- Ejemplo: `hc(s0)` = 1 + 1 + 1 + 3 + 1 = 7

---

## Calidad de funciones heurísticas

> **Definición**
> Sean `h1⁺` y `h2⁺` dos funciones heurísticas optimistas,
> `h1⁺` es más informada que `h2⁺`, si para todo nodo `n` se cumple que:
> `h1⁺(n) >= h2⁺(n)`.

> **Teorema 3**
> Sean `h1⁺` y `h2⁺` dos funciones heurísticas optimistas. Si `h1⁺` es más informada que `h2⁺`, entonces `A⁺(h2⁺)` expande al menos tantos nodos como `A⁺(h1⁺)`.
> 
> Es decir, que se verifica lo siguiente: `A⁺(h1⁺) <= A⁺(h2⁺)`.
> 
> Si `h1⁺`es más informada que `h2⁺`, entonces todo nodo que es expandido por A⁺ con la "buena" función heurística `h1⁺` (la más informada) también es expandido por la "mala" función heurística `h2⁺`.
> 
> Sin embargo, pueden existir nodos que son expandidos por la "mala" función heurística `h2⁺`, y no son expandidos por la "buena" función heurística `h1⁺`.

> **Nota**
> - La calidad de la función heurística _influye en el número de nodos que se expanden_.
> - La calidad de la función heurística _no influye en la calidad de la solución_.

> **Conclusión Práctica**
> - Preferir valores grandes de h⁺, siempre que se mantenga optimista.
> - Si hay dos funciones heurísticas optimistas `h1⁺` y `h2⁺`, y `h1⁺` es más informada que `h2⁺`, entonces podemos prescindir de `h2⁺` en el proceso de búsqueda A⁺.
> - Si hay varias funciones heurísticas optimistas `h1⁺, ..., hm⁺`, sin que ninguna de ellas sea  más informada que otra, entonces:
> 	- Si todas las funciones son "fáciles" de evaluar, se puede definir una nueva función heurística a partir de ellas: `h⁺(n) = max[h1⁺(n), ..., hm⁺(n)]`.
> 	- Por construcción, `h⁺` es más informado que cualquiera de las funciones `h1⁺, ..., hm⁺`.

---

## Complejidad de A⁺

El número de nodos expandidos por A⁺ depende de la precisión de `h⁺`:
1. Si `h⁺(n) = h(n)` para todos los nodos n:
	- Información completa: Complejidad lineal (sin contar la complejidad de computar h⁺!).
	- Calcular `h⁺(n)` suele equivaler a resolver el problema completo.
2. Si `h⁺(n) = 0` para todos los nodos n:
	- A⁺ degenera a la búsqueda de coste uniforme.
3. Resultados generales
	- En el _pero caso_, A⁺ es lineal sólo si para todos los nodos n, `|h(n) - h⁺(n)| <= O(c)`.
	- En el _peor caso_, A⁺ es polinominal sólo si para todos los nodos n, `|h(n) - h⁺(n)| <= O(log h(n))`.
	- En _escenarios reales_, el error heurístico `|h(n) - h⁺(n)|` crece, al menos, de forma lineal con el coste `h(n)`. Aún así, suele haber una mejora notable en comparación con métodos no informados.

---

## Mejoras de A⁺

### Heurísticas débiles

> **Mejoras respetando la optimalidad**
> Consiste en atacar el problema de la complejidad en memoria de A⁺ mediante la expansión repetida de algunos nodos, lo que reduce la cantidad de nodos almacenados en memoria.

> **IDA⁺ (Iterative Deepening ⁺A)**
> _Korf (1985)_

> **SMA⁺ (Simplified Memory-bounded A⁺)**
> _Russell (1992)_

> **RBFS (Recursive Best First Search)**
> _Korf (1992)_

### Heurísticas fuertes

> **Mejoras usando heurísticas fuertes**
> La idea principal consiste en acotar el espacio de búsqueda con información heurística.
> Un ejemplo sería la _Búsqueda Guiada por Subobjetivos (Island-Driven Search)_.
> Sin embargo, debemos saber que la _búsqueda por subobjetivos no es óptima_.

> **Búsqueda Jerárquica**
> Se puede concebir como una extensión de la búsqueda por subobjetivos.
> - _Idea_: Generar los estados intermedios de forma dinámica.
> - Método:
> 	- Se define un espacio de estados a un “meta-nivel”.
> 	- Macro-operadores representan acciones complejas.
> 	- Realizar búsqueda A* a meta-nivel con macro-operadores.
> 	- Refinar la solución anterior en base a la búsqueda guiada por subobjetivos

### Búsqueda en Línea

> **Búsqueda en Línea (Online Search)**
> 1. Se percibe el estado actual del mundo s.
> 2. Se aplica un método de búsqueda online para decidir la siguiente acción a.
> 3. Se ejecuta la acción a en el mundo real, dando lugar al nuevo estado s'.
> 
> Es indicado cuando:
> - El espacio de búsqueda es demasiado grande para buscar hasta la solución.
> - No es realista usar un modelo determinista de los efectos de acciones.
>
> 
>
> Medida de eficiencia:
> - No se puede asegurar optimalidad ni completitud.
> - El índice competitivo puede ser infinito, particularmente cuando hay acciones que no son reversibles.

---

## Búsqueda con horizonte (Limited-Horizon Search)

> **Método**
> Buscar k acciones hacia adelante, luego decidir la siguiente acción y ejecutarla.
> - Generar el conjunto `Hk` de estados a los que se puede llegar con k acciones.

> **Algoritmo**
> - Repetir hasta que el agente se encuentre en un estado meta:
> 	- Percibir el estado actual `s`.
> 	- Aplicar búsqueda en profundidad limitada por el nivel `k`.
> 	- En cada nodo hoja `n` de nivel `k`, actualizar un valor `a` que representa el mínimo valor de `f⁺` encontrado en nodos de nivel `k` hasta el momento:
> 		- Inicializar `a` <- `+∞`.
> 	- En el nodo `n` (de nivel `k`) realizar: `a` <- `min(a , f⁺(n))`.
> 	- Si en la búsqueda en profundidad limitada se ha encontrado un nodo meta, sea `n⁺` este nodo. De lo contrario, sea `n⁺` el primer nodo hoja (de nivel `k`) con `f⁺(n⁺) = α.
> 	- Ejecutar la primera acción `a⁺` en el camino que lleva de `s` a `n⁺`.
>
> - Optimización mediante podas α (para h* consistente)
> 	- Si `h⁺` es consistente, para cualquier nodo interior `n'` del árbol de búsqueda, los sucesores de `n'` tendrán valor de `f⁺` mayor o igual a `f⁺(n')` \[Lema 1].
> 	- Por tanto, durante el proceso de búsqueda en profundidad limitada, se puede abandonar cualquier rama a partir de un nodo `n'` con `f⁺(n') ≥ a`.

---