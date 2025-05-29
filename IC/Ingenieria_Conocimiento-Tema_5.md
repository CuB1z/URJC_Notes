---
tags: URJC URJC_IC
---

# Tema 5 - Ingeniería del Conocimiento

---

## ¿Qué es la búsqueda multiagente?

> **Búsqueda Multiagente**
> Técnica de resolución de problemas en entornos con múltiples agentes que interactúan.
> Cada agente puede tener objetivos propios o comunes, y su comportamiento afecta el de los demás.

---

## Agentes especializados

> **Situación**
> - Múltiples agentes de resolución de problemas actúan en el mismo entorno.
> - Las acciones de los agentes influyen en los demás agentes.
> - Ningún agente puede controlar las acciones de los demás agentes.
> - Un agente puede "predecir" las acciones de los demás hasta cierto punto.

> **Tipos de problemas multiagente**
> - Escenarios cooperativos (metas compartidas).
> - Escenarios parcialmente cooperativos (algunas metas compartidas).
> - Escenarios antagónicos (metas opuestas).

---

## Escenarios antagónicos

> **Juegos**
> El ejemplo clásico de escenarios antagónicos son los _juegos de suma nula_.
> En estos juegos el escenario está totalmente definido por las reglas del juego, y los agentes jugadores los conocen completamente.

> **Tipos de juegos**
> - Número de jugadores: Bipersonales / Múltiples jugadores.
> - Elementos de azar: Con elementos / Sin elementos.
> - Información: Info perfecta / info incompleta.

---

## Árboles de juego

> **Definición**
> Sea N un conjunto de nodos {max, min}, y G = {N, E, L} un árbol etiquetado. G es un árbol de juego si
> - G no es vacío.
> - La raíz está etiquetada max
> - Todos los sucesores de max son etiquetados min.
> - Todos los sucesores de min son etiquetados max.

> **Observaciones**
> - Cada nivel del árbol de juego representa un _"ply"_ (media jugada)
> - Las hojas de un árbol de juego (completamente desarrollado) representan las posiciones terminales del juego.

---

## Modelo de juegos bipersonales

> **Nota**
> La función expandir codifica las jugadas permitidas en una posición s. Además, implícitamente supone que los jugadores se alternan en realizar las jugadas.
> 
> La función de utilidad está definida sólo en los estados terminales s de los juegos de suma nula, en los que max gana si y sólo si min pierde. La función de utilidad sería la siguiente: 
> - Gana max: `U(s) = +∞`.
> - Gana min: `U(s) = -∞`.
> - Empate: `U(s) = 0`.

---

## Estrategias

> **¿Cómo determina max su mejor jugada?**
> Max podría aplicar métodos de búsqueda estándar, usando las posiciones en las que él gana como estados meta, pero min no querría realizar las acciones que el plan de max prevé para él.

> **Estrategia**
> Define las jugadas de max en todos los estados alcanzables del juego, es decir, da una respuesta a todas las jugadas posibles de min.
> 
> Por lo tanto, la estrategia está basada en crear un subárbol del árbol de juego.

> **Estrategia óptima (o racional)**
> La estrategia óptima será la que implica el mejor resultado _garantizado_ para max.
> 
> Se debe tener en cuenta que los escenarios son totalmente antagónicos con agentes racionales, lo que implica que max puede asumir que min hará lo mejor para sí mismo, lo cual es lo peor para max.
> 
> En definitiva, la estrategia óptima para max es la estrategia minimax, es decir, maximizar la utilidad mínima en cada jugada.

---

## Método Minimax

> **Método**
> 1. Generar el árbol de juego completo.
> 2. Aplicar la función de utilidad en cada nodo terminal.
> 3. Propagar las utilidades hacia arriba.
> 	1. En los nodos max, usar la utilidad máxima de los sucesores.
> 	2. En los nodos min, usar la utilidad mínima de los sucesores.
> 4. Eventualmente los valores de utilidad llegan al nodo raíz (max).
> 5. La jugada óptima de max es la que lleva al sucesor de utilidad máxima.

> **Algoritmo**
> - Funciones mutuamente recursivas.
> - α: máximo de la utilidad de los sucesores de un nodo max.
>   
> ````pascal
> { MaxValor en el Minimax básico }
> Función MaxValor(estado)
> 	Si terminal?(estado) entonces
> 		devolver(U(estado))
> 	sucesores <- expandir(max, estado)
> 	α <- -∞
> 	Para cada s en sucesores hacer
> 		α <- max(α, MinValor(s))
> 	devolver(a)
> 	Fin { MaxValor }
> ```

> **Complejidad**
> El algoritmo minimax genera el árbol de juego completo, en profundidad primero, hasta los nodos (o: el nivel de) suspensión. Lo que lleva a que su complejidad sea de `O(b^d)` (factor de ramificación b; número de plys explorados d).

---

## Decisiones imperfectas

> **Problema**
> _Crecimiento exponencial del árbol de juego_.
> Incluso en juegos muy simples, es imposible desarrollar el árbol de juego completo hasta todos sus nodos terminales.

> **Solución**
> _Heurísticas_.
> Sustituir la prueba terminal por una prueba suspensión que detiene la búsqueda aún sin llegar a una posición terminal: límite de profundidad fijo, posiciones "en resposo", etc.
> 
> Aplicar una función `evaluación e`, que estime la utilidad esperada del juego correspondiente a una posición s determinada.
> - La función `e` debe coincidir con la función de utilidad u en los nodos terminales.
> - Suele ser función lineal ponderada: `e(s) = w1 f1(s) + w2 f2(s) + ... + wn fn(s)`.
> - Ajedrez: `e(s) = “suma de los valores materiales en s”`.
> 
> Aplicar heurísticas fuertes, aunque esto implique que las jugadas del Minimax ya no serán óptimas, pero dependerán de la calidad de las heurísticas.

> **Algoritmo Minimax con suspensión**
> 
> ````pascal
> { MaxValor: Minimax con suspensión }
> Función MaxValor(estado)
> 	Si suspensión?(estado) entonces
> 		devolver(e(estado))
> 	sucesores <- expandir(max, estado)
> 	α <- -∞
> 	Para cada s en sucesores hacer
> 		α <- max(α, MinValor(s))
> 	devolver(a)
> 	Fin { MaxValor }
> ```

---

## Poda α-β

> **Poda α**
> _α_: Evaluación más alta encontrada (de momento) en un nodo max.
> _β_: Evaluación más baja encontrada (de momento) en su sucesor directo min.
> 
> **Condición de poda: α >= β**
> Si α >= β, el valor (exacto) de U_max no depende de U_min, por lo que no es necesario explorar los sucesores restantes de min.

> **Poda β**
> _β_: Evaluación más baja encontrada (de momento) en un nodo min.
> _α_: Evaluación más alta encontrada (de momento) en su sucesor directo max.
> 
> **Condición de poda: β <= α**
> Si β <= α, el valor (exacto) de U_min no depende de U_max, por lo que no es necesario explorar los sucesores restantes de max.

---

## Minimax con poda α-β

> **Algoritmo**
> - Funciones mutuamente recursivas.
> - α es el mejor valor de evaluación para max en el camino hasta estado.
>   
> ````pascal
> { MaxValor: Minimax con poda α-β }
> Función MaxValor(estado, α, β)
> 	Si supensión?(estado) entonces
> 		devolver(e(estado))
> 	sucesores <- expandir(max, estado)
> 	Para cada s en sucesores hacer
> 		α <- max(α, MinValor(s, α, β))
> 		Si α >= β entonces devolver(α)
> 	devolver(a)
> 	Fin { MaxValor }
> ```

> **Análisis**
> El algoritmo Minimax con poda α-β siempre produce el mismo resultado que sin la poda. Además, la eficiencia de Minimax con poda α-β depende del orden en el que se exploran los nodos.

---

## Algoritmo ExpectMinimax

> **Idea**
> - Utilizar el algoritmo Minimax.
> - Añadir un nuevo jugador "azar", que se incluye en el árbol siempre que haya un nuevo evento independiente de los jugadores y cuyo resultado es aleatorio.
> - Los sucesores de un nodo "azar" son las posibles situaciones que podrían ser el resultado de este elemento de azar.
> - Cada uno de los sucesores de un nodo "azar" tiene asociado la probabilidad de que este resultado ocurra.

> **Funciones de evaluación / utilidad**
> - La escala de los valores si importa (no como en el algoritmo Minimax).
> - las funciones no deben devolver +∞ o -∞.
> - La función de evaluación e debe estimar la probabilidad de ganar.

> **Complejidad**
> La complejidad es proporcional al número de nodos en el árbol.