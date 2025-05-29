---
tags: URJC URJC_IC
---

# Tema 3 - Ingeniería del Conocimiento

---

## Tabla de Contenidos

1. [¿Qué es la búsqueda heurística?](#¿Qué%20es%20la%20búsqueda%20heurística?)
2. [Heurísticas](#Heurísticas)
3. [Funciones Heurísticas](#Funciones%20Heurísticas)
4. [Aproximación naíf](#Aproximación%20naíf)
5. [Búsqueda A⁺](#Búsqueda%20A⁺)
6. [El algoritmo A⁺](#El%20algoritmo%20A⁺)
7. [Búsqueda A⁺: valores de f⁺](#Búsqueda%20A⁺%20valores%20de%20f⁺)
8. [Funciones heurísticas consistentes](#Funciones%20heurísticas%20consistentes)
9. [Monotonía de f⁺ con función heurística consistente](#Monotonía%20de%20f⁺%20con%20función%20heurística%20consistente)
10. [La estrategia de A⁺ con función heurística consistente](#La%20estrategia%20de%20A⁺%20con%20función%20heurística%20consistente)
11. [Cota de f⁺ con función heurística optimista](#Cota%20de%20f⁺%20con%20función%20heurística%20optimista)
12. [Valores de f⁺ en árboles de búsqueda A⁺](#Valores%20de%20f⁺%20en%20árboles%20de%20búsqueda%20A⁺)

---

## ¿Qué es la búsqueda heurística?

> **🔍 Búsqueda Heurística**
> Enfoque basado en reglas o atajos para encontrar soluciones eficientes a problemas complejos, sacrificando exhaustividad a cambio de velocidad y practicidad.

---

## Heurísticas

> **🔍 Heurística**
> Del griego _"heuriskein"_: **"encontrar"**, **"descubrir"**.

> **🤖 Inteligencia Artificial**
> Compila conocimiento _"empírico"_ sobre un problema / un entorno.

> **💡 Interpretación "fuerte"**
> - Una heurística suele facilitar la resolución de un problema, pero no garantiza que se resuelva.
> - Una heurística es una _"regla de tres"_ para un problema.
> - **Búsqueda:** Optimalidad o incluso completitud no garantizados.

> **💡 Interpretación "débil"**
> - Método riguroso + información heurística.
> - Información heurística puede mejorar el rendimiento medio de un método de resolución de problemas, pero no garantiza una mejora en el peor caso.
> - **Búsqueda:** Mejora de complejidad no garantizada.

---

## Funciones Heurísticas

> **🔍 Funciones heurísticas**
> - Estiman la adecuación de un nodo para ser expandido.
> - Métodos de búsqueda _"el mejor primero"_ eligen el nodo más prometedor para expandir.

> **📏 Heurística usual**
> - Distancia hacia la meta.
> - `h:N -> M` mide el coste _real_ desde el nodo n hasta el nodo meta más cercano.
> - `h⁺:N -> M` es una **función heurística** que estima el valor de h(n).
> - Una función heurística h⁺ es **optimista**, si h⁺(n) <= h(n) para todo nodo n.
>   - Nota: En algunas fuentes, estas funciones se denominan **"admisibles"**.

> **📊 Ejemplos de funciones optimistas**
> - Mundo de los bloques: Número de bloques descolocados.
> - Encontrar rutas: Distancia en línea recta hasta un nodo meta.

---

## Aproximación naíf

> **🔍 Búsqueda avara**
> - Entre las hojas del árbol de búsqueda, elegir el nodo de valor h⁺ mínimo.
> - Es decir, el nodo hoja del que pensamos que más cerca esté de la meta.

> **⚠️ Problema**
> - La búsqueda avara **no es óptima**.
> - No solo hay que tomar en cuenta cómo de cerca está un nodo de la meta, sino también cuánto ha costado llegar hasta él desde el estado inicial.

---

## Búsqueda A⁺

> **💡 Idea**
> - Minimizar el coste estimado total de un camino en el árbol de búsqueda.
> - Combinar:
>   - El coste para llegar al nodo n (se conoce exactamente: g).
>   - El coste aproximado para llegar a un nodo meta desde el nodo n (estimado por la función heurística h⁺).

> **🔍 Función heurística de A⁺**
> - `f(n) = g(n) + h(n)`: Coste real del plan de mínimo coste que pasa por n.
> - `f⁺(n) = g(n) + h⁺(n)`: Estimación de f.

> **📊 Estrategia A⁺**
> - Entre las hojas del árbol de búsqueda, elegir el nodo de valor f⁺ mínimo.

---

## El algoritmo A⁺

> **💻 Algoritmo A⁺**
> - Se basa en la búsqueda general.
> - Almacenar el valor de g de cada nodo expandido.
> - Mantener la lista abierta ordenada por valores crecientes de f⁺.
> - Insertar nuevos nodos en abierta según sus valores f⁺.

```pascal
{A⁺}
abierta <- S0
Repetir
    Si vacía?(abierta) entonces
        devolver(negativo)
    nodo <- primero(abierta)

    Si meta?(nodo) entonces
        devolver(nodo)
    sucesores <- expandir(nodo)

    Para cada sucesor de sucesores hacer
        n.padre <- nodo
        ordInsertar(n, abierta, f⁺)
Fin {repetir}
```

---

## Búsqueda A⁺: valores de f⁺

- En la búsqueda de coste uniforme, los valores de g crecen a lo largo de todos los caminos del árbol de búsqueda, porque cada paso se suma el coste de un operador (que es un número natural positivo).

- Los valores de f⁺ crecen a lo largo de todos los caminos del árbol de búsqueda, pero no siempre es así:
    -  En un camino del árbol de búsqueda, sea `nk` un sucesor (no necesariamente directo) de `ni`, entonces el valor de f⁺(`ni`) contiene una _estimación_ del coste de llegar de `ni` a `nk`, y f⁺(`nk`) el coste _real_.

---

## Funciones heurísticas consistentes

> **📏 Definición**
> Si para todo `ni` y todo sucesor directo de `nj` de `ni` se cumple que
> `h⁺(ni) - h⁺(nj) <= c(ni, nj)`
> entonces h⁺ es _consistente_.

> **💡 Interpretación intuitiva**
> - h⁺ estima también implícitamente el coste de cada operador.
> - h⁺ es consistente si subestima el coste de todos los operadoes.

> **📝 Nota**
> - Si h⁺ es _consistente_, entonces también es optimista.
> - Sin embargo, existen funciones heurísticas h⁺ _optimistas_ que no son consistentes.

---

## Monotonía de f⁺ con función heurística consistente

> **📏 Lema 1**
> Si h⁺ es consistente, entonces f⁺ crece de forma débilmente monótona en todos los caminos del árbol de búsqueda, es decir:
> 
> Si `nj` es sucesor directo de `ni`, entonces `f⁺(ni) <= f⁺(nj)`.

> **📊 Corolario 1**
> Sea `nm` el mejor nodo meta. Si h⁺ es _consistente_, entonces el algoritmo A⁺ expande todos los nodos `ni` tal que `f⁺(ni) <= f⁺(nm)`.

---

## La estrategia de A⁺ con función heurística consistente

> **💡 Idea**
> - _Si nos alejamos de la meta_: g crece y h⁺ crece, por lo que f⁺ crece "mucho".
> - _Si nos acercamos a la meta_: g crece y h⁺ disminuye, por lo que f⁺ crece "poco".

---

## Cota de f⁺ con función heurística optimista

> **📏 Lema 2**
> Sea camino `a(nm)` el conjunto de nodos en el camino desde la raíz a un nodo meta `nm` cualquiera.
> 
> Si h⁺ es optimista, entonces para todos los nodos `nj` perteneciente al camino `a(nm)` se verifica que `f⁺(nj) <= f⁺(nm)`.

---

## Valores de f⁺ en árboles de búsqueda A⁺

> **📊 Corolario 2**
> Sea `nm` el mejor nodo meta, y camino `a(ni)` el conjunto de nodos `nj` en el camino desde la raíz a un nodo `ni` cualquiera (`ni` incluido).
> 
> Si h⁺ es optimista, entonces el algoritmo A⁺ expande todos los nodos `ni` tal que para todo `nj` perteneciente al camino `a(ni) * f⁺(nj) <= f⁺(nm)`.

---