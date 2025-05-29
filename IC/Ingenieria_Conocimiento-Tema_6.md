---
tags: URJC URJC_IC
---

# Tema 6 - Ingeniería del Conocimiento

---

## ¿Qué es la búsqueda con espacios estructurados?

> **Búsqueda con Espacios Estructurados**
> Técnica que explora soluciones dentro de un conjunto organizado o jerarquizado de estados, aprovechando su estructura interna para optimizar la búsqueda y reducir la complejidad computacional.

---

## Representaciones "monolíticas" de estados

> **Representación de los conocimientos del agente**
> - _Estado inicial_: Símbolo `s0`.
> - _Estados sucesores_: Función `expandir (s7 |-> {s8, s10, s12})`.
> - _Estados meta_: Función `meta? (s112 |-> true)`.
> - _Coste de operador_: Función (`c (s7, s112) |-> 5`).
> - _Heurísticas_: Función `h⁺ (s7 |-> 235)`.

> **Problema**
> - Complejidad de la representación del conocimiento.
> - Mantenibilidad del conocimiento.

> **Solución**
> - Tomar en cuenta la "estructura" de los estados.
> - Definir un estado no por "un nombre", sino por el conjunto de sus propiedades.

---

## Problemas de Satisfacción de Restricciones (CSPs)

> **Estructura de estados**
> - Un estado está compuesto por un conjunto de n variables que pueden tomar diferentes valores.
> - Un estado es un estado meta si los valores que tienen en sus variables cumplen una serie de restricciones.

> **Problema de satisfacción de restricciones (CSP)**
> Un problema de satisfacción de restricciones, en inglés _Constraint Satisfaction Problem_, es una tripleta (X, D, R), en la que:
> - La _X_ es un conjunto finito de variables.
> - La _D_ es una función total que asigna un dominio a cada variable.
> - La _R_ es un conjunto finito de restricciones tal que R_i es un predicado sobre un subconjunto de las variables de X.

> ---

> **CSP Binario como grafo**
> Los CSPs de restricciones _binarias_ se suelen representar como **grafos**, en los que:
> - Cada variable x_i del CSP es representada por un nodo.
> - Cada restricción binaria R_i(x_j, x_k) se representa por un arco entre los nodos x_j y x_k.

> ---

> **CSP No binario como hipergrafo**
> Los CSPs con restricciones _k-arias (k > 2)_ se representan como **hipergrafos**, en los que:
> - Cada variable x_i del CSP es representada por un nodo.
> - Cada restricción k-área R_i se representa por un hiperarco que conecta k nodos.

---

## Satisfacción de restricciones

> **Búsqueda con asignaciones completas**
> - _Estado_: Asignación completa (valores para todas las variables).
> - _Operador_: Modificar el valor de una variable en la asignación.
> - _Meta?_: Asignación que cumple todas las restricciones.
> - _Coste_: Cero (la longitud de un camino hasta un nodo meta es irrelevante).
> - _Heurística del conflicto mínimo_: Preferir los sucesores que violen el mínimo número de restricciones.

> **Búsqueda con asignaciones parciales**
> - _Estado_: Asignación parcial (valores asignados a algunas variables).
> - _Operador_: Elegir un valor para una variable no asignada.
> - _Meta?_: Solución (asisgnación completa que cumple todas las restricciones).
> - _Coste_: Cero (la longitud de un camino hasta un nodo meta es irrelevante).

> **Notas**
> - En cada camino del árbol de búsqueda, tiene sentido cambiar el valor de cada variable como mucho 1 vez.
> - El árbol de búsqueda tiene profundidad máxima n.
> - A cada una de las n variables se pueden asignar d valores: al nivel 0 hay n×d sucesores, al nivel 1 hay (n-1)×d sucesores, etc.
> - Por tanto, se genera un árbol con hasta `n!×d^n` hojas, pero sólo hay d posibles asignaciones.
> - El orden en el que se cambian los valores de las variables es irrelevante.

---

## Cronological Backtracking

> **Algoritmo**
> ```pascal
> Función VueltaAtrásCronológica(CSP, s)
> 	Si |s| = n entonces
> 		devolver(s)
> 	xi <- ElegirVariableNoAsignada(X, s)
>      dominio <- Dxi
> 	Mientras dominio ≠ {} hacer
>	 	v <- ElegirValor(dominio)
> 		s' <- s U {xi = v}
> 		Si s' pertenece a R entonces
>	 		resultado <- VueltaAtrásCronológica(CSP, s')
>	 		Si resultado ≠ fallo entonces
>	 			devolver(resultado)
> 		dominio <- dominio \ {v}
> 	Fin {Mientras}
>	devolver(fallo)
> Fin {VueltaAtrásCronológica}
> ```

> **Notas**
> La selección de variables (ElegirVariableNoAsignada) y de valores (ElegirValor) no afecta a la completitud (el espacio de búsqueda es finito).
> 
> Sin embargo, sí afecta a la complejidad del algoritmo (el tamaño del árbol de búsqueda).

> **Heurísticas para elección de variables**
> - Hay que asignar todas las variables del CSP.
> - Preferir variables "difíciles" para detectar posibles "callejones sin salida" (_fail first_)
> 	- Preferir la variable de mínimos valores restantes (_MRV_).
> 	- Preferir la variable con mayor número de restricciones (_grado heurístico_).

> **Heurísticas para elección de valores**
> - Es suficiente con asignar uno de los valores en el dominio de una variable.
> - Preferir valores “prometedores” para generar una solución cuanto antes (_fail last_)
> 	- Preferir el valor menos limitante respecto a variables no asignadas.

> ---

> **Problema de Thrashing**
> El _Thrasing_ es un problema del algoritmo de _Cronical Backtracking_ en el que no se toma en cuenta la "causa" de haber llegado a un callejón sin salida. Esto provoca que se genere el mismo error de asignación varias veces.
> 
> Pongamos como ejemplo que `x_i = a` es incompatible con cualquier valor del dominio de `x_k`. Sin embargo, se irían probando los posibles valores para `x_k` (en combinación con `x_i = a`) un número exponencial de veces.

> ---

> **Mejoras al Cronological Backtracking**
> 
>  _Satisfacción de restricciones con salto atrás (backjumping)_
> En lugar de retroceder a la variable más recientemente instanciada que todavía tiene alternativas disponibles, continúa la búsqueda en la primera variable que causó el fallo.
> 
> _Nogoods_
> Recordar las asignaciones parciales que han causado fallo para que no se vuelvan a generar.

---

## Propagación de restricciones

> **Forward Checking**
> Consiste en filtrar los domios después de cada ampliación de la asignación parcial `s`:
> - Para todas las restricciones binarias `R` que involucran una variable `x_i`, asignada en `s` y otra `x_j` no asignada en `s`.
> - Para todo valor `v'` de `D_j`, si `(s(x_i), v')` viola `R(x_i, x_j)` entonces eliminar `v'` de `D_j`.
> 
> Marcha atrás si algún dominio se queda sin valores.
> 
> _Transitividad de Restricciones_
> Hay que ir más allá del _forward checking_ y tomar en cuenta la transitividad de las restricciones para detectar fallos antes.

---

## Consistencia de arco

> **Definición**
> Una variable `x_i`es **arco consistente** con respecto a una restricción binaria `R(x_i, x_j)` si para todo `v` perteneciente a `D_i`, existe un `v'` perteneciente a `D_j` tal que `(v, v')` cumple `R(x_i, x_j)`.
> 
> _Extensión del concepto_:
> - Una variable es **arco consistente**, si lo es con respecto a todas las restricciones binarias `R(x_i, _)` en las que está involucrada.
> - Una restricción binaria `R(x_i, x_j)` es **arco consistente**, si tanto `x_i` como `x_j` son arco consistentes con respecto a ella.
> - Un CSP es **arco consistente**, si todas sus restricciones son arco consistentes.

> ---

> **Notas**
> Si una variable `x_i` **no** es **arco consistente** con respecto a una restricción binaria `R(x_i, x_j)`, entonces existe al menos un valor `v` pertenciente a `D_j` que es incompatible con todos los valores `v'` pertenecientes a `D_j` con respecto a `R(x_i, x_j)`.
> 
> Eliminar estos valores `v` no modifica el conjunto de soluciones de un CSP.

> ---

> **Método para alcanzar arco consistencia en un CSP**
> Para todas las variables `x` y restricciones `R(x, _)` en las que x está involucrada, hacer `x` arco consistente con respecto a `R(x, _)`.
> 
> Al eliminar un valor del dominio `D_i` de una variable `x_i` involucrada en la restricción `R_y(x_i, x_j)`, se puede “estropear” la arco consistencia de otra variable `x_k` con respecto a la restricción `R_z(x_i, x_k)`.
> 
> Es decir, aunque ya se haya alcanzado arco consistencia para `x_k` con respecto a la restricción `R_z(x_i, x_k)`, es posible pueda ser necesario “propagar” valores varias veces por la misma restricción.

---

## Algoritmo de arco consistencia

> **Algoritmo**
> ```pascal
> Función ConsistenciaDeArcos(CSP)
> 	abierta <- R
> 	Mientras no es vacio?(abierta) hacer
>		R_y(x_i, x_j) <- primero(abierta)
> 		Si BorrarValoresInconsistentes(R_y(x_i, x_j)) entonces
>			Para cada x_k en vecinos(x_i) hacer
>		 	abierta <- abierta U {R_z(x_i, x_k)}
>	Fin {Mientras}
> Fin {ConsistenciaDeArcos}
> ```
>
> ```pascal
> Función BorrarValoresInconsistentes(R_y(x_i, x_j))
> 	borrado <- no
> 	Para cada v en D_i hacer
>		Si no existe un v' en a D_j : (v, v') en R_y(x_i, x_j) entonces
>			D_i <- D_i \ {v}
>			borrado <- si
>	devolver(borrado)
> Fin {BorrarValoresInconsistentes}
> ```

> ---

> **Resultado**
> El algoritmo de consistencia de arco reduce un CSP en un **CSP’ equivalente**.
> 
> Si al aplicar el algoritmo, el _dominio de una variable se queda vacío_, el CSP es _inconsistente_, es decir, no tiene solución.

> **Complejidad**
> Un grafo que representa el CSP binario tiene como mucho `n·(n-1)` arcos dirigidos. Además, cada uno de estos arcos puede insertarse en "abierta" a lo sumo `d` veces.
> 
> El borrado de valores que no son arco consistentes se realiza en `O(d²)` pasos.
> 
> Por lo tanto, la complejidad en tiempo en el peor de los casos es `O(n²·d³)`.

> **Análisis**
> - No se puede garantizar que el algoritmo de arco consistencia detecte cualquier CSP inconsistente.
> - _k consitencia_
> Para cualquier asignación consistente `s_k-1` a `k-1` variables, y para cualquier variable restante, existe un valor en el dominio de esta k-ésima variable que es consistente con `s_k-1`.
>
> - Arco consistencia se conoce tambié como "2-consistencia".
> 
> - Se puede asegurar que un CSP con `n` variables tiene solución si es **fuertemente n-consistente**.

---

## Algoritmo MAC

> **MAC**
> En inglés, _Maintaining Arc Consistency_, consiste en intercalar satisfacción y propagación de restricciones.
> 
> Primero se realiza una búsqueda con vuelta atrás cronológica. Y después de aumentar una asignación, se construye un CSP equivalente que sea arco consistente. 
> 
> El algoritmo MAC es de los algoritmos básicos más conocidos para CSPs.
> 

> **Algoritmo**
> ```pascal
> Función MAC(CSP, s)
> 	Si |s| = n entonces
> 		devolver(s)
> 	xi <- ElegirVariableNoAsignada(X, s)
>      dominio <- Dxi
> 	Mientras dominio ≠ {} hacer
>		v <- ElegirValor(dominio)
> 		s' <- s U {xi = v}
> 		Si s' pertenece a R entonces
> 			CSP' <- ConsistenciaDeArcos(s'(CSP))
>		 	resultado <- VueltaAtrásCronológica(CSP, s')
>		 	Si resultado ≠ fallo entonces
>			 	devolver(resultado)
> 		dominio <- dominio \ {v}
> 	Fin {Mientras}
>	devolver(fallo)
> Fin {MAC}
> ```