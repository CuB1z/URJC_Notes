---
tags: URJC URJC_IO
---

# Tema 2 - Investigación Operativa

---

## Tabla de Contenidos

1. [¿Qué es la Optimización Lineal Continua?](#¿Qué%20es%20la%20Optimización%20Lineal%20Continua?)
2. [Asignación de Recursos: Fábrica de Cerveza](#Asignación%20de%20Recursos%20Fábrica%20de%20Cerveza)
3. [Asignación de Recursos: Petroquímica](#Asignación%20de%20Recursos%20Petroquímica)
4. [¿Qué es el Análisis de Sensibilidad?](#¿Qué%20es%20el%20Análisis%20de%20Sensibilidad?)
5. [¿Qué son los Valores Sombra?](#¿Qué%20son%20los%20Valores%20Sombra?)
6. [Tipos de Restricciones](#Tipos%20de%20Restricciones)
7. [Análisis de resultados en Gurobipy](#Análisis%20de%20resultados%20en%20Gurobipy)
8. [Bibliografía](#Bibliografía)

---

## ¿Qué es la Optimización Lineal Continua?

> **Optimización Lineal Continua**
> Método matemático para maximizar o minimizar una función lineal, sujeta a restricciones lineales, donde las variables pueden tomar cualquier valor real dentro de un intervalo continuo.

> **Principales propiedades**
> 
> _Proporcionalidad_
> La contribución al coste y restricciones es proporcional al valor de las variables de decisión.
> 
> _Aditividad_
> El coste y las restricciones se obtienen como suma directa de las contribuciones de las variables.
> 
> _Divisibilidad_
> Las variables pueden tomar valores reales fraccionarios.
> 
> _Determinismo_
> Los coeficientes de las variables son constantes y conocidos.

---

## Asignación de Recursos: Fábrica de Cerveza

> **Caso**
> En una fábrica de cerveza se producen tres tipos distintos: rubia, negra y de baja graduación, y para ello se utilizan dos materias primas: malta y levadura.
> 
> | Materia Prima | Rubia | Negra | Baja | Disponibilidad |
> | --------------- | ------- | ------- | ---- | ---------------- |
> |        Malta       |     1     |     2     |   2   |            30         |
> |     Levadura    |     2     |     1     |   2    |            45          |
> |          PvP        |     7€    |     4€    |   3€  |            ---         |

> **Objetivo**
> Maximizar el beneficio de la producción de tres tipos de cerveza, respetando las limitaciones de malta y levadura.

> ---

> **Variables de decisión**
> $x_1$ $\to$ Producción de cerveza rubia.
> $x_2$ $\to$ Producción de cerveza negra.
> $x_3$ $\to$ Producción de cerveza baja.

> ---

> **Modelo matemático**
> 
> *Función objetivo*
> $\max Z = 7x_1 + 4x_2 + 3x_3$
> 
> *Restricciones*
> $x_1 + 2x_2 + 2x_3 \leq 30$ $\to$ Restricción de malta.
> $2x_1 + x_2 + 2x_3 \leq 45$ $\to$ Restricción de levadura.
> $x₁_1, x_2, x_3 \geq 0$  $\to$ Restricción de no negatividad.

> ---

> **Implementación en Python**
> 
> ```python
> from gurobipy import Model, GRB
>
> # Crear el modelo
> modelo = Model("Asignación de recursos")
> 
> # Definir variables de decisión
> x = modelo.addVar(name="Cerveza_Rubia", lb=0)
> y = modelo.addVar(name="Cerveza_Negra", lb=0)
> z = modelo.addVar(name="Cerveza_Baja", lb=0)
> 
> # Definir la función objetivo
> modelo.setObjective(7 * x + 4 * y + 3 * z, GRB.MAXIMIZE)
> 
> # Agregar restricciones
> modelo.addConstr(x + 2 * y + 2 * z <= 30, name="Restricción_Malta")
> modelo.addConstr(2 * x + y + 2 * z <= 45, name="Restricción_Levadura")
> 
> # Optimizar
> modelo.optimize()
> ```
> 

---

## Asignación de Recursos: Petroquímica

> **Caso**
> Una petroquímica produce dos productos principales: PET-envase y PET-fibra, a partir de dos materias primas: PTA y MEG.
> 
> | Materia Prima | PET-envase | PET-fibra | Disponibilidad |
> | ---------------- | ------------ | ---------- | ---------------- |
> |          PTA         |       0.95      |       0.92   |         280 T       |
> |         MEG        |       0.37       |      0.34    |         170 T      |
> |         PvP         |         32€       |        38€   |          ---          |

> **Objetivo**
> Maximizar el beneficio de la producción de PET-envase y PET-fibra, respetando las limitaciones de PTA y MEG.

> ---

> **Variables de decisión**
> $x$ -> Toneladas de PET-envase a producir.
> $y$ -> Toneladas de PET-envase a producir.

> ---

> **Modelo matemático**
> 
> *Función objetivo*
> $\max Z = 32x + 38y$
> 
> *Restricciones*
> $0.95x + 0.92y \leq 280$ $\to$ Restricción de PTA.
> $0.37x + 0.34y \leq 170$ $\to$ Restricción de MEG.
> $x, y \geq 0$ $\to$  Restricción de no negatividad.

> ---

> **Implementación en Python**
> 
> ```python
> from gurobipy import Model, GRB
>
> # Crear el modelo
> modelo = Model("Producción_PET")
>
> # Variables de decisión
> x = modelo.addVar(name="PET_envase", lb=0)
> y = modelo.addVar(name="PET_fibra", lb=0)
>
> # Función objetivo
> modelo.setObjective(32 * x + 38 * y, GRB.MAXIMIZE)
>
> # Restricciones
> modelo.addConstr(0.95 * x + 0.92 * y <= 280, name="Restricción_PTA")
> modelo.addConstr(0.37 * x + 0.34 * y <= 170, name="Restricción_MEG")
>
> # Optimizar
> modelo.optimize()
> ```

> ---

> **Análisis de los resultados**
> $\text{Consumo\_PTA} = 0.950𝑥 + 0.920𝑦 = 0.950 (0) + 0.920 (304.35) = 280 \space T$
> $\text{Consumo\_MEG} = 0.370𝑥 + 0.340𝑦 = 0.3700 (0) + 0.340 (304.35) = 103.48 \space T$
> 
> Se utiliza toda la disponibilidad de PTA, es decir, $280$ toneladas.
> Se utilizan $103.48$ toneladas de MEG, quedando una disponibilidad restante de $66.52$.
> 
> Hay MEG disponible que no se utiliza, pero la disponibilidad de PTA limita la producción adicional.

> **¿Qué precio tendríamos que poner al PET-envase para que fuera rentable de fabricar?**
> 
> _Paso 1: Entender por qué no se produce PET-envase_ 
> El PET-fibra tiene un mayor beneficio por tonelada y consume menos materias primas por tonelada producida en comparación con el PET-envase.
> Por lo tanto, es más rentable y eficiente producir PET-fibra bajo las condiciones actuales.
> 
> _Paso 2: Calcular el beneficio por unidad de materia prima_
> Para que el PET-envase sea competitivo, su beneficio por unidad de materia prima debe ser al menos igual al del PET-fibra.
> 
> - $\text{Beneficio\_Envase} = 32\space /\space 0.95 \approx 33.68 \text{ euros / tonelada de PTA}$.
> - $\text{Beneficio\_Fibra} = 38\space /\space 0.92 \approx 41.30 \text{ euros / tonelada de PTA}$
> 
> _Paso 3: Determinar el precio necesario para el PET-envase_
> Para que el PET-envase sea tan atractivo como el PET-fibra en términos de beneficio por tonelada de PTA, necesitamos encontrar el nuevo beneficio por tonelada de PET-envase que satisfaga que ${P}\space /\space {0.95} \geq 41.30$.
> 
> Despejando $P$, obtenemos que $P \geq 41.30 \cdot 0.95$ $\approx 39.24 \space \text{euros/tonelada}$.

---

## ¿Qué es el Análisis de Sensibilidad?

> **Análisis de Sensibilidad**
> Técnica que permite evaluar cómo los cambios en los parámetros de un modelo de programación lineal (como los coeficientes de la función objetivo o los recursos disponibles) afectan la solución óptima.

> **Objetivos del análisis de sensibilidad**
> 
> *Evaluar la robustez de la solución óptima*
> Determinar si la solución óptima permanece válida ante pequeños cambios en los parámetros mediante la identificación de los rangos de variación de los coeficientes dentro de los cuales la solución óptima no cambia.
> 
> *Identificar parámetros críticos*
> Detectar qué parámetros tienen mayor impacto en la solución, priorizando la atención en los parámetros más sensibles para una gestión más efectiva.
> 
> *Facilitar la toma de decisiones bajo incertidumbre*
> Preparar planes de contingencia para diferentes escenarios posibles, evaluando el efecto de cambios futuros en el mercado o en la disponibilidad de recursos.

> ---

> **Componentes del Análisis de Sensibilidad**
> 
> *Variación en los coeficientes de la función objetivo*
> Analizar y determinar los rangos de variación para los cuales la solución básica óptima permanece inalterada.
> 
> *Variación en los recursos disponibles*
> Evaluar el impacto de cambios en las restricciones de disponibilidad de recursos y calcular el valor sombra de los recursos, que indica el incremento en el valor de la función objetivo por unidad adicional de recurso.
> 
> *Rango de optimalidad*
> Intervalo en el cual los coeficientes de la función objetivo pueden variar sin cambiar la solución óptima.
> 
> *Rango de factibilidad*
> Intervalo en el cual los recursos pueden variar sin que la solución se vuelva infactible.
> 
> *Informes de sensibilidad del software de optimización*
> Herramientas como **Gurobi**, **CPLEX** o **Excel Solver** proporcionan informes detallados que incluyen valores sombra, rangos de variación y análisis de sensibilidad.

---

## ¿Qué son los Valores Sombra?

> **Valores Sombra**
> Los valores sombra (o precios duales) representan la tasa de cambio del valor óptimo de la función objetivo por unidad adicional de un recurso disponible.
> 
> Indican cuánto aumentaría (o disminuiría) el beneficio total si se incrementa (o reduce) en una unidad el recurso asociado a una restricción activa, manteniendo todo lo demás constante.

> ---

> **Interpretación económica**
> 
> *Valor económico de los recursos escasos*
> Los valores sombra reflejan el valor marginal de un recurso. si un recurso es escaso (la restricción está activa), su valor sombra es positivo, indicando que obtener más de ese recurso aumentaría el beneficio total.
> 
> *Decisiones de inversión*
> Ayudan a decidir si es rentable invertir en obtener más de un recurso limitado. Por ejemplo: contratar más personal o comprar más maquinaria.

> **Cálculo de los Valores Sombra**
> 
> *Mediante el problema dual*
> Cada restricción en el problema primal se corresponde a una variable en el problema dual. Los valores de estas variables duales en la solución óptima son los valores sombra.
> 
> *Utilizando el método Simplex*
> En la última tabla óptima del Simplex, los coeficientes de las variables básicas en las ecuaciones correspondientes a las restricciones proporcionan los valores sombra.

> ---

> **Características de los Valores Sombra**
> 
> *Aplicables a restricciones activas*
> Los valores sombra son generalmente no cero solo para restricciones que están activas (se cumplen con igualdad en la solución óptima).
> 
> *Rangos de validez*
> Los valores sombra son válidos dentro de ciertos rangos de variación del recurso. Fuera de estos rangos, el valor sombra puede variar y la solución óptima puede ser diferente.

---

## Tipos de Restricciones

> **Restricciónes Activas**
> Una restricción activa es aquella que se cumple con igualdad en la solución óptima. Es decir, el recurso asociado está completamente utilizado, y la restricción limita directamente la solución.
> 
> *Identificación de restricciones activas*
> Si en la solución óptima, la restricción se cumple exactamente, es decir, el recurso total disponible es igual al recurso utilizado, entonces es una restricción activa.
> 
> *Importancia de las restricciones activas*
> $\to$ Limitan la solución óptima.
> $\to$ Afectan directamente el valor de la función objetivo.
> $\to$ Asociadas a valores sombra no cero.

> ---

> **Restricciones No Activas**
> Una restricción no activa es aquella que tiene un margen en la solución óptima. Es decir, el recurso asociado no se utiliza en su totalidad y no restringe directamente la solución.
> 
> *Recursos con holgura*
> Indican que hay más recurso disponible de lo que se utiliza en la solución óptima.
> 
> *Valor sombra cero*
> Añadir más de este recurso no mejorará el valor de la función objetivo, ya que no es un recurso limitante.
> 
> *Posibilidad de reasignación*
> Se puede considerar reducir el recurso disponible (si es posible) para ahorrar costes, ya que no afecta la solución óptima.

---

## Análisis de resultados en Gurobipy

```python
from gurobipy import Model, GRB

# Código anterior del modelo ...

# Para acceder al combre de la variable -> (var.VarName)
# Para acceder al nombre de la restricción -> (constr.ConstrName)

# Imprimir los valores sombra de las restricciones (constr.Pi)
print("Valores sombra (dual) de las restricciones:")
for constr in model.getConstrs():
    print(f"{constr.ConstrName}: {constr.Pi:.4f}")

print()

# Imprimir los costes reducidos de las variables (var.RC)
print("Costes reducidos de las variables:")
for var in model.getVars():
    print(f"{var.VarName}: {var.RC:.4f}")

print()
    
# Imprimir las holguras de las restricciones (constr.Slack)
print("Holguras de las restricciones:")
for constr in model.getConstrs():
    print(f"{constr.ConstrName}: {constr.Slack:.4f}")

print()

# Verificar si se encontró una solución óptima
if model.status == GRB.OPTIMAL:
    print("Solución óptima:")

	# Imprimir el valor de las variables (var.X)
    for var in model.getVars():
        print(f"{var.VarName} = {var.X:.2f} unidades")

	# Imprimir el valor de la función objetivo (model.ObjVal)
    print(f"Función Objetivo = ${model.ObjVal:.2f}")

else:
    print("No se encontró una solución óptima.")
    
```

---

## Bibliografía

> 1. Sixto Ríos Insua. *Investigación Operativa. Optimización.*
> 2. Sixto Ríos Insua. *Problemas de Investigación Operativa. Programación Lineal y Extensiones.*
> 3. Paul W. Williams. *Model Building in Mathematical Programming.*  

---