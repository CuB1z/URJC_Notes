---
tags: URJC URJC_IC
---

# Tema 2 - Ingeniería del Conocimiento

---

## Tabla de Contenidos

1. [¿Qué es la Búsqueda No Informada?](#¿Qué%20es%20la%20Búsqueda%20No%20Informada?)
2. [Espacio de estados](#Espacio%20de%20estados)
3. [Entornos simples](#Entornos%20simples)
4. [Ejemplo de las Torres de Hanoi](#Ejemplo%20de%20las%20Torres%20de%20Hanoi)
    - [Tablas de actuación](#Tablas%20de%20actuación)
    - [Algoritmo](#Algoritmo)
5. [Búsqueda](#Búsqueda)
    - [Ejemplo del Mundo de los Bloques](#Ejemplo%20del%20Mundo%20de%20los%20Bloques)
6. [Búsqueda en espacios de estados](#Búsqueda%20en%20espacios%20de%20estados)
     - [Método de búsqueda](#Método%20de%20búsqueda)
     - [Algoritmo de búsqueda](#Algoritmo%20de%20búsqueda)
7. [Estados repetidos](#Estados%20repetidos)
8. [Clasificación de métodos](#Clasificación%20de%20métodos)
9. [Búsqueda en amplitud (BFS)](#Búsqueda%20en%20amplitud%20(BFS))
    - [Complejidad](#Complejidad)
    - [Requerimientos de tiempo y memoria](#Requerimientos%20de%20tiempo%20y%20memoria)
10. [Búsqueda de coste uniforme](#Búsqueda%20de%20coste%20uniforme)
    - [Características](#Características)

---

## ¿Qué es la Búsqueda No Informada?

> **🔍 ¿Qué es la Búsqueda No Informada?**
> Método que explora todas las posibles soluciones sin usar información adicional o heurísticas, como en la búsqueda en anchura o profundidad.

---

## Espacio de estados

1. Tienen un determinado _objetivo/meta_: "cómo debería ser el mundo".
2. Son capaces de realizar _acciones_ que _modifican_ el mundo.
3. _Buscan_ una secuencia de acciones que modifiquen el mundo para llegar a su objetivo.
4. Mantienen un _modelo simbólico_ del entorno.
5. Anticipan los efectos esperados de sus acciones sobre el modelo.
6. Generan y seleccionan _planes de actuación_ en el modelo previos a ejecutar las acciones.

---

## Entornos simples

Los entornos simples son:

> **🔢 Entornos Discretos**
> Se puede concebir el mundo de estados.
> Hay un conjunto finito de percepciones y acciones en cada estado.

> **🔍 Entornos Accesibles**
> El agente puede acceder a las características relevantes del entorno.
> Se puede determinar el estado actual del mundo.
> Se puede determinar el estado del mundo que se gustaría alcanzar.

> **🕒 Entornos Estático y determinista**
> No hay presión temporal ni incertidumbre.
> El mundo cambia sólo cuando el agente actúa.
> El resultado de cada acción está totalmente definido y previsible.

---

## Ejemplo de las Torres de Hanoi

> **🎯 Objetivo**
> Trasladar los discos de la aguja A a B en el mismo orden.

> **⚠️ Restricción**
> Un disco mayor nunca debe reposar sobre uno de menor tamaño.

### Tablas de actuación

Para cada situación hay una entrada en una tabla de actuación; dicha entrada compila la secuencia de acciones a emprender.

**Estado inicial:** Cuatro discos en A.
> disco 1 de A a C  / disco 2 de A a B  / disco 1 de C a B  / disco 3 de A a C  /
> disco 1 de B a A  / disco 2 de B a C  / disco 1 de A a C  / disco 4 de A a B  /
> disco 1 de C a B  / disco 2 de C a A  / disco 1 de B a A  / disco 3 de C a B  /
> disco 1 de A a C  / disco 2 de A a B  / disco 1 de C a B

- Mejora la flexibilidad aprendiendo nuevas entradas.
- Sin embargo, cabe la posibilidad de que exista un problema de limitaciones de memoria.

### Algoritmo

- El diseñador del agente conoce un método para resolver el problema.
- Codifica este método en un algoritmo particular para el problema.
- Mejora la flexibilidad parametrizando el algoritmo.
- Sin embargo, el diseñador ha de anticipar todos los escenarios posibles.
- Los entornos reales suelen ser demasiado complejos como para anticipar todas las posibilidades.

```pascal
PROCEDURE MoverDiscos(n: integer; origen, destino, auxiliar: char);
{
  Pre: n > 0
  Post: output = [movimientos para pasar n discos de la aguja origen a la destino]
}
BEGIN
    IF n = 0 THEN {Caso base}
        writeln
    ELSE BEGIN
        MoverDiscos(n-1, origen, auxiliar, destino);
        write('Pasar disco', n, 'de', origen, 'a', destino);
        MoverDiscos(n-1, auxiliar, destino, origen);
    END;
END;
```

### Búsqueda

**🧩 Modelo simbólico del problema**
> - "Inicialmente todos los discos reposan en _A_ y su tamaño decrece de abajo hasta arriba".
> - "Queremos que todos los discos estén en _C_ en el mismo orden".
> - "Podemos mover un disco _I_ a la aguja _X_, si no hay otro disco por encima de _I_ y, si actualmente hay discos en _X_, entonces dichos discos han de ser más grandes que _I_".
> - "Cuanto menos movimientos de discos hagamos mejor".

**🤖 Algoritmo de búsqueda genérico**
- Genera una solución a cualquier problema representado mediante el modelo simbólico.

**✨ Mayor flexibilidad**
- EL diseñador no necesita conocer la solución de antemano.
- Es más fácil adaptar el método a nuevas características del problema.

---

## Ejemplo del Mundo de los Bloques

> **🔄 Situaciones**
> n bloques en una mesa de longitud ilimitada

> **⚙️ Acciones**
> - _Apilar(X, Y)_: poner X encima de Y.
>   - Prec: bloques X e Y están libres.
>   - Efecto: bloque X está encima de Y.
>
> - _Quitar(Y)_: poner Y en la mesa.
>   - Prec: bloque Y está libre.
>   - Efecto: bloque Y está en la mesa.

> **🎯 Actitud del agente**
> - Objetivo: cierta configuración de bloques.
> - Sólo la posición vertical es relavante.
> - El coste de cada acción es uno.

---

## Búsqueda en espacios de estados

> **🌍 Espacio de estados**
> Modelo del mundo representado por un grafo.
> 
> | Mundo                 | Modelo         | Representación |
> |-----------------------|----------------|----------------|
> | situación             | estado         | nodo           |
> | situación presente    | estado inicial | nodo inicial   |
> | acción y sus efectos  | operador       | arco           |
> | secuencia de acciones | plan           | camino         |

> **🔍 Problema de búsqueda**
> Espacio de estados + actitud del agente.
> 
> | Actitud               | Representación     |
> |-----------------------|--------------------|
> | estados meta          | conjunto de nodos  |
> | eficiencia de un plan | coste de un camino |

> **🎯 Objetivo**
> Encontrar el plan más eficiente que lleve del estado inicial a un estado meta.

### Método de búsqueda

- Es una estrategia para explorar el espacio de estados.
- En cada paso se expanded un estado.
- Se desarrolla sucesivamente un árbol de búsqueda.

> **🔍 Método general**
> 1. Seleccionar nodo hoja.
> 2. Comprobar si es nodo meta.
> 3. Expandir este nodo hoja.

### Algoritmo de búsqueda

- El árbol se representa en base a un registro del tipo _nodo_.
- `Abierta` es una lista de nodos con las hojas actuales del árbol.
- `Vacía?` determina si una lista es vacía.
- `Primero` quita el primer elemento de una lista.
- `OrdInsertar` añade un nodo a una lista, clasificado según una función de orden.

```pascal
{búsqueda general}
abierta <- S0
Repetir
    Si vacía?(abierta) entonces
        devolver(negativo)
    nodo <- primero(abierta)

    Si meta?(nodo) entonces
        devolver(nodo)
    sucesores <- expandir(nodo)

    Para cada sucesor de sucersores hacer
        n.padre <- nodo
        ordInsertar(n, abierta, <orden>)
Fin {repetir}
```

---

## Estados repetidos

Al ejecutar estos algoritmos, nos surgen estos problemas:
- El mismo estado puede repetirse varias veces en el árbol de búsqueda.
- Puede generarse el mismo subárbol varias veces.

Nos planteamos las siguientes soluciones:
- **Ignorarlo**.
- **Evitar ciclos simples** no añadiendo el padre de un nodo al conjunto de sucesores.
- **Evitar ciclos generales** no añadiendo un antecesor de un nodo al conjunto de sucesores.
- **Evitar todos los estados repetidos** no añadiendo ningún nodo existente en el árbol al conjunto de sucesores.

---

## Clasificación de métodos

> **✨ Características**
> - Completitud: Se encuentra una solución si existe.
> - Optimalidad: Se encuentra la mejor solución si hay varias.
> - Complejidad en tiempo: ¿Cuánto se tarda en encontrar la solución?
> - COmplejidad en espacio: ¿Cuánta memoria se utiliza en la búsqueda?

> **🔍 Tipos de métodos de búsqueda**
> - No informados
>   - Utilizan sólo los conocimientos mínimos (búsqueda en amplitud, búsqueda de coste uniforme, etc).
> - Heurísticos
>   - Además utilizan información aproximada, y específica del problema, para guiar la búsqueda (Algoritmo A* y extensiones, búsqueda multiagente).
> - Con estados estructurados
>   - Se aprovechan de características de los estados para combatir la complejidad (Satisfacción de restricciones, etc).

---

## Búsqueda en amplitud (BFS)

> **🔍 Estrategia**
> - Generar el árbol por niveles de profundidad.
> - Expandir todos los nodos de nivel `i`, antes de expandir nodos de nivel `i+1`.

> **✅ Resultado**
> - Considerar primero todos los caminos de longitud 1, después todos los caminos de longitud 2, etc.
> - Se e cuentra el estado meta de _menor profundidad_.

> **📝 Algoritmo**
> - Usar el algoritmo general de búsqueda.
> - Añadir nuevos sucesores al final de la lista abierta.
> - `Abierta` funciona como cola
> 	- Insercción al final.
> 	- Recuperación desde cabeza.
> 	- Estructura FIFO
> - Siempre expandir primero el nodo más antiguo.
>
> ```pascal
> {búsqueda en amplitud}
> abierta <- S0
> Repetir
>    Si vacía?(abierta) entonces
>        devolver(negativo)
>    nodo <- primero(abierta)
>
 >   Si meta?(nodo) entonces
 >      devolver(nodo)
 >   sucesores <- expandir(nodo)
>
>   Para cada n perteneciente a sucesores hacer
>        n.padre <- nodo
>        ordInsertar(n, abierta, final)
> Fin {repetir}
> ```

### Complejidad

La complejidad es proporcional al número de nodos expandidos.

Suponemos que en el árbol de búsqueda:
- El factor de ramificación es _b_.
- El mejor nodo meta tiene profundidad _d_.

### Requerimientos de tiempo y memoria

| d  | nodos | tiempo   | memoria  |
|----|-------|----------|----------|
| 2  | 110   | 0,11 ms  | 107 KB   |
| 4  | 11110 | 11 ms    | 10,6 MB  |
| 6  | 10⁶   | 1,1 s    | 1 GB     |
| 8  | 10⁸   | 2 min    | 103 GB   |
| 10 | 10¹⁰  | 3 horas  | 10 TB    |
| 12 | 10¹²  | 13 días  | 1000 TB  |
| 14 | 10¹⁴  | 3,5 años | 99 PB    |
| 16 | 10¹⁶  | 350 años | 10000 PB |

---

## Búsqueda de coste uniforme

> **💡 Idea**
> Guiar la búsqueda por el coste de los operadores.

> **🔍 Método**
> - `g(n)`: Coste mínimo para llegar del nodo inicial al nodo _n_.
> - Expandir siempre el nodo de menor coste g primero.

> **📝 Algoritmo**
> - Almacenar cada nodo con su valor g.
> - Insertar los nuevos nodos en `abierta` en orden ascendente según su valor g.

```pascal
{búsqueda en amplitud}
abierta <- S0
Repetir
    Si vacía?(abierta) entonces
        devolver(negativo)
    nodo <- primero(abierta)

    Si meta?(nodo) entonces
        devolver(nodo)
    sucesores <- expandir(nodo)

    Para cada n perteneciente a sucesores hacer
        n.padre <- nodo
        ordInsertar(n, abierta, g)
Fin {repetir}
```

### Características

- La búsqueda de coste uniforme enumera sucesivamente todos los nodos del espacio de estados por costes (valores de g) crecientes.
     - La sucesión de valores g crece de forma monótona en todos los caminos del árbol de búsqueda, ya que el coste de cualquier operador es positivo.
- La búsqueda de coste uniforme es _completa_:
    - Al ser los costes números enteros positivos, la sucesión de valores de g no es acotada.
    - Por tanto, si un nodo meta existe en el espacio de estados, será expandido alguna vez.
- La búsqueda de coste uniforme es _óptima_:
    - Al expandir un nodo cualquiera, todos los nodos de menor valor de g han sido expandidos antes.
    - El primer nodo meta expandido es el nodo meta de menor valor de g.
    - El nodo meta de menor valor de g es el nodo meta de menor coste.

---