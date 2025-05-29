---
tags: URJC URJC_IO
---

# Tema 5 - Investigación Operativa

---

## Tabla de Contenidos

1. [¿Qué es una simulación?](#¿Qué%20es%20una%20simulación?)
2. [Tipos de simulaciones](#Tipos%20de%20simulaciones)
3. [Características de sistemas con sucesos discretos](#Características%20de%20sistemas%20con%20sucesos%20discretos)
4. [Modelado de sistemas con sucesos discretos](#Modelado%20de%20sistemas%20con%20sucesos%20discretos)
5. [Eventos y procesos de eventos](#Eventos%20y%20procesos%20de%20eventos)
6. [Generación de números y variables aleatorias](#Generación%20de%20números%20y%20variables%20aleatorias)
7. [Generación de números y variables aleatorias discretas](#Generación%20de%20números%20y%20variables%20aleatorias%20discretas)
8. [Generación de números y variables aleatorias continuas](#Generación%20de%20números%20y%20variables%20aleatorias%20continuas)
9. [Validación de números pseudoaleatorios](#Validación%20de%20números%20pseudoaleatorios)
10. [Simulación de Monte Carlo](#Simulación%20de%20Monte%20Carlo)
11. [Aplicaciones de la simulación de Monte Carlo](#Aplicaciones%20de%20la%20simulación%20de%20Monte%20Carlo)
12. [Bibliografía](#Bibliografía)

---

## ¿Qué es una simulación?

> **Simulación**
> Proceso de crear un modelo abstracto de un sistema real para estudiar su comportamiento bajo diferentes condiciones.
> 
> Este modelo reproduce de manera temporal y lógica las operaciones y dinámicas del sistema, permitiendo experimentar y analizar su desempeño sin afectar el sistema real.
> 
> Las simulaciones son importantes porque nos permiten:
> - Reducir costes y riesgos.
> - Analizar sistemas complejos.
> - Optimizar procesos.
> - Predecir comportamientos.
> - Ayudar en la toma de decisiones.
> 
> **Tipos de modelos de simulación**
> 
> *Modelos deterministas*
> Donde las salidas son completamente determinadas por las entradas, sin incertidumbre.
> 
> *Modelos estocásticos*
> Incorporan elementos de aleatoriedad y variabilidad.

> ---

> **Conceptos Clave**
> 
> *Modelado abstracto*
> Representación simplificada de un sistema real, enfocándose en aspectos relevantes para el análisis.
> 
> *Interactividad*
> Permite la modificación de variables y parámetros para observar diferentes resultados.
> 
> *Temporalidad*
> Captura la evolución del sistema a lo largo del tiempo, observando cómo cambia bajo distintas condiciones.
> 
> *Repetibilidad*
> Posibilidad de ejecutar múltiples simulaciones con diferentes configuraciones para obtener resultados estadísticamente significativos.

---

## Tipos de simulaciones

> **Simulación Continua**
> Modela sistemas donde las variables cambian de manera continua a lo largo del tiempo y utiliza ecuaciones diferenciales para describir el comportamiento del sistema.
> 
> Adecuada para sistemas físicos y naturales, como el flujo de fluidos, dinámicas de poblaciones, y sistemas mecánicos.

> ---

> **Simulación Discreta**
> Modela sistemas donde los cambios en las variables ocurren en momentos específicos y discretos, generalmente como resultado de eventos.
> 
> Utiliza lógica secuencial para manejar la ocurrencia y efecto de eventos.

> ---

> **Simulación Estática**
> Modela sistemas en un estado específico en un momento determinado, sin considerar la evolución temporal.
> 
> Está enfocada en un análisis puntual del sistema y no incorpora la dimensión del tiempo ni la evolución del estado del sistema.

> ---

> **Simulación Dinámica**
> Modela sistemas considerando la evolución y cambios a lo largo del tiempo e incorpora la dimensión temporal, permitiendo observar cómo el sistema responde a cambios y eventos.
> 
> Puede ser continua o basada en eventos discretos.

| Característica            | Simulación Continua          | Simulación Discreta             |
| ------------------------- | ---------------------------- | ------------------------------- |
| Tiempo                    | Fluido y continuo            | Discreto y basado en eventos    |
| Método de modelado        | Ecuaciones diferenciales     | Lógica secuencial y eventos     |
| Aplicaciones              | Sistemas físicos y naturales | SSOO, colas, redes …            |
| Complejidad computacional | Alta                         | Varía según el eventos y manejo |

| Característica          | Simulación Estática                   | Simulación Dinámica                      |
| ----------------------- | ------------------------------------- | ---------------------------------------- |
| Consideración de tiempo | No considera                          | Considera cambios y evolución            |
| Propósito principal     | Análisis puntual del sistema          | Análisis de comportamientos y respuestas |
| Complejidad del modelo  | Generalmente menor                    | Generalmente mayor                       |
| Aplicaciones            | Evaluación de capacidades, equilibrio | Flujos, planificación estratégica        |

---

## Características de sistemas con sucesos discretos

> **Eventos discretos**
> Un evento es una ocurrencia instantánea que cambia el estado del sistema.
> 
> Puede ser la llegada de un cliente, el inicio o fin de un servicio, el fallo de un componente, entre otros.

> ---

> **Estados del sistema**
> El estado del sistema en un momento dado está definido por todas las variables relevantes que describen la situación actual del sistema, como el número de clientes en cola, el estado de los servidores, el inventario disponible, etc.
> 
> Dinámica del estado: El estado del sistema cambia únicamente en los instantes en que ocurren eventos.

> ---

> **Tiempo de simulación**
> Es una variable continua que representa el progreso del tiempo dentro del modelo de simulación. En sistemas de sucesos discretos, el tiempo avanza de un evento a otro.
> 
> *Escalabilidad del tiempo*
> Permite simular el comportamiento del sistema a lo largo de períodos extensos sin necesidad de observar cada unidad de tiempo real.

> ---

> **Discretización**
> En sistemas de sucesos discretos, el tiempo se discretiza en instantes específicos cuando ocurren eventos, a diferencia de sistemas continuos donde las variables cambian constantemente.
> 
> *Ventajas de la discretización*
> - Simplificación del modelo.
> - Reducción de la complejidad computacional al enfocarse únicamente en los momentos de cambio.
> - Mayor precisión en la representación de sistemas con interacciones event-driven.

> ---

> **Interacciones y dependencias**
> Las interacciones entre componentes en un sistema pueden generar dependencias complejas, ya que un evento puede afectar a múltiples partes del sistema, lo que requiere una gestión adecuada de esas interdependencias.
> 
> Además, existen dependencias temporales, donde la ocurrencia de un evento depende de eventos previos, lo que establece una secuencia lógica dentro del sistema que debe ser cuidadosamente controlada.

---

## Modelado de sistemas con sucesos discretos

> **Introducción**
> El modelado de sistemas de sucesos discretos implica la creación de una representación abstracta del sistema real, capturando sus elementos clave y las interacciones entre ellos.
> 
> Este modelo sirve como base para la simulación, permitiendo experimentar y analizar diferentes escenarios sin afectar el sistema real.

> ---

> **Componentes principales**
>
> | **Componente**                 | **Descripción**                                                          |
> |--------------------------------|--------------------------------------------------------------------------|
> | Entidades                      | Objetos que se mueven y experimentan cambios en el sistema.              |
> | Atributos de entidades         | Características que definen a las entidades y su comportamiento.         |
> | Recursos                       | Componentes que proporcionan servicios a las entidades.                  |
> | Colas                          | Espacios donde las entidades esperan para recibir servicio.              |
> | Eventos                        | Ocurrencias instantáneas que cambian el estado del sistema.              |
> | Registros y estadísticas       | Herramientas para recopilar y analizar datos durante la simulación.      |
> | Inicialización y condiciones de inicio | Establecen el estado inicial del sistema.                        |
> | Condiciones de terminación     | Criterios para finalizar la simulación.                                  |
> | Agenda de eventos              | Lista ordenada de eventos futuros programados para ocurrir.              |
> | Algoritmo de simulación        | Conjunto de pasos lógicos para procesar eventos y actualizar el sistema. |
> | Validación y verificación      | Procesos para asegurar la precisión y adecuación del modelo.             |

> ---

> **Métodos para validar**
>
> *Comparación con datos reales*
> Verificar que el modelo reproduce comportamientos observados.
> 
> *Pruebas de sensibilidad*
> Evaluar cómo cambios en los parámetros afectan los resultados.
> 
> *Revisión de consistencia lógica*
> Asegurar que las reglas y políticas definidas son coherentes con el sistema real.

---

## Eventos y procesos de eventos

> **¿Qué es el proceso de eventos?**
> El proceso de eventos describe cómo y cuándo ocurren los eventos dentro del sistema.
> 
> En simulación, este proceso se gestiona mediante una *agenda de eventos*, que es una estructura de datos que mantiene una lista ordenada de eventos futuros.

> ---

> **Eventos y procesos de eventos**
> El proceso de eventos describe cómo y cuándo ocurren los eventos dentro del sistema. En simulación, este proceso se gestiona mediante una **agenda de eventos**, que es una estructura de datos que mantiene una lista ordenada de eventos futuros.

> ---

> **Clasificación de eventos**
>
> *Eventos externos*
> Ocurren fuera del sistema y afectan su estado.
> 
> *Eventos internos*
> Son generados por el propio sistema.
> 
> *Eventos de fallo y reparación*
> Representan la ocurrencia de fallos en recursos y su reparación.

> ---

> **Eventos típicos en simulaciones**
>
> *Llegada de entidad*
> Entrada de una nueva entidad al sistema.
> 
> *Inicio de servicio*
> Comienzo del servicio de una entidad por un recurso.
> 
>*Fin de servicio*
>Finalización del servicio de una entidad, permitiendo su salida o tránsito.
>
> *Reinicio de servicio*
> En sistemas preemptivos, marca la reanudación del servicio interrumpido.
> 
> *Cambio de estado de recurso*
> Representa la disponibilidad o no disponibilidad de un recurso.

---

## Generación de números y variables aleatorias

> **Números pseudoaleatorios**
> Los números pseudoaleatorios son secuencias de números generadas por algoritmos deterministas, pero que exhiben propiedades similares a los números aleatorios verdaderos.
> 
> **Características principales**
>
> *Determinismo*
> La secuencia está completamente determinada por una semilla inicial.
> 
> *Repetibilidad*
> Permite reproducir experimentos bajo las mismas condiciones.
> 
> *Longitud del período*
> Es la longitud de la secuencia antes de que comience a repetirse.
> 
> *Uniformidad*
> Los números deben estar distribuidos uniformemente en el intervalo \([0, 1)\).
> 
> *Independencia*
> Los números no deben tener correlaciones discernibles.

> ---

> **Método Congruencial Lineal (LCG)**
> La congruencia lineal es un método ampliamente utilizado en la generación de números pseudoaleatorios, basado en relaciones aritméticas modulares. Consiste en calcular una secuencia de números mediante una fórmula de recurrencia del tipo:
> 
> $$X_{n+1} = (aX_n + c) \cdot mod\space m$$
> 
> donde $X_n$ es el valor actual, $a$ es el multiplicador, $c$ el incremento, y $m$ el módulo. Este método es eficiente y sencillo de implementar, aunque su calidad depende de la elección adecuada de los parámetros para garantizar un período completo y una buena distribución de los números generados.

> ---

> **Método Mersenne Twister (MT19937)**  
> El Mersenne Twister es un generador de números pseudoaleatorios con un largo período de $(2^{19937} - 1)$ y una excelente distribución de números. Utiliza una matriz de estados de $624$ elementos para generar secuencias con baja correlación.  
> 
> Aunque es eficiente y rápido, su complejidad y consumo de recursos pueden ser desventajas en entornos con restricciones de rendimiento. Además, no es adecuado para aplicaciones criptográficas debido a su predictibilidad.
> 
> *Para generar números pseudoaleatorios mediante el método Mersenne Twister en python, podemos usar la función:* `numpy.random.randint()` o `numpy.random.rand()`.

> ---

> **Generador de Números Aleatorios basado en XOR Shift**  
> El generador XOR Shift utiliza operaciones de desplazamiento de bits y XOR para generar números aleatorios. Es rápido y sencillo de implementar, lo que lo hace adecuado para aplicaciones que requieren eficiencia.
> 
> Sin embargo, si no se implementa adecuadamente, puede generar patrones en la secuencia de números, lo que afecta la calidad de la aleatoriedad.

> ---

> **Generadores basados en multiplicadores múltiples y modulares**  
> Estos generadores utilizan múltiples congruencias lineales o métodos más complejos para mejorar la aleatoriedad.  
> 
> Ofrecen una mejor calidad de aleatoriedad en comparación con métodos más simples, pero su mayor complejidad y tiempo de computación son desventajas a considerar.

---

## Generación de números y variables aleatorias discretas

> **Variables aleatorias discretas**  
> Una variable aleatoria discreta es aquella que puede tomar un número finito o contable de valores distintos, cada uno con una probabilidad asociada de ocurrir.
> 
> Para generar variables aleatorias discretas, se utilizan funciones de distribución de probabilidad (FDP) que asignan probabilidades a cada valor posible de la variable.

> ---

> **Método de la Función de Distribución Acumulada (Inverse Transform Sampling)**  
> Este método genera una variable aleatoria discreta a partir de una distribución uniforme en $[0, 1)$ utilizando la función de distribución acumulada (FDA).
> 
> 1. Definir la función de distribución de probabilidad (FDP) de la variable aleatoria discreta.
> 
> | X  | P(X = x) |
> |----|----------|
> | 0  | 0.25     |
> | 1  | 0.50     |
> | 2  | 0.25     |
>
> 2. Calcular la función de distribución acumulada (FDA) de la variable.
> 
> | X  | F(x) |
> |----|------|
> | 0  | 0.25 |
> | 1  | 0.75 |
> | 2  | 1.00 |
> 
> 3. Invertir la FDA para mapear números uniformemente distribuidos en el intervalo $[0, 1)$ a los valores de la variable aleatoria deseada.
> 
> $$
> 	X = \begin{cases} 
> 	0 & \text{si } 0 \leq U < 0.25 \\
> 	1 & \text{si } 0.25 \leq U < 0.75 \\
> 	2 & \text{si } 0.75 \leq U < 1.00
> 	\end{cases}
> $$

---

## Generación de números y variables aleatorias continuas

> **Variables aleatorias continuas**  
> Son variables continuas aquellas que pueden tomar cualquier valor dentro de un intervalo o conjunto de intervalos, es decir, tienen un número infinito de posibles valores.
>
> Para generar variables aleatorias continuas, se utilizan métodos que transforman números pseudoaleatorios uniformemente distribuidos en $[0, 1)$ en variables que siguen una FDP específica.

> ---

> **Método de la Función de Distribución Acumulada para variables continuas**  
> Este método, adaptado de su versión para variables discretas, se utiliza para generar variables aleatorias continuas a partir de una distribución uniforme en $[0, 1)$ utilizando la función de distribución acumulada (FDA) invertida.
> 
> 1. Definir la función de densidad de probabilidad (FDP) de la variable aleatoria continua.
> $$f_X(x) = \lambda e^{-\lambda x}, \quad x \geq 0$$
>
> 2. Calcular la función de distribución acumulada (FDA) de la variable.
> $$F_X(x) = 1 - e^{-\lambda x}$$
>
> 3. Invertir la FDA para mapear números uniformemente distribuidos en el intervalo $[0, 1)$ a los valores de la variable aleatoria deseada.
> $$F_X^{-1}(u) = -\ln(u)$$  
> 
> 4. Dado que U y 1-U son igualmente distribuidos, generar $X$
> $$ X = -\ln(U) $$

> ---

> **Método de Box-Muller**  
> El Método de Box-Muller es utilizado para generar variables aleatorias continuas que siguen una distribución normal estándar a partir de números uniformemente distribuidos en el intervalo $[0, 1)$.
> 
> 1. Generar dos números aleatorios uniformemente distribuidos $U_1$ y $U_2$ en el intervalo $[0, 1)$.
> 
> 2. Aplicar la transformación de Box-Muller para obtener dos variables aleatorias $Z_0$ y $Z_1$ que siguen una distribución normal estándar $N(0, 1)$:
> 
> $$Z_0 = \sqrt{-2 \ln U_1} \cdot \cos(2 \pi U_2)$$
> 
> $$Z_1 = \sqrt{-2 \ln U_1} \cdot \sin(2 \pi U_2)$$
> 
> 3. Escalar y desplazar (si es necesario). Para obtener una distribución normal con media $\mu$ y desviación estándar $\sigma$:
> 
> $$
> X = \sigma Z + \mu
> $$
> 
> Este método genera dos variables aleatorias con distribución normal estándar en cada iteración, lo que permite simular muestras de una distribución normal para diversas aplicaciones.

---

## Validación de números pseudoaleatorios

> **Prueba de Uniformidad (Goodness-of-Fit)**  
> El objetivo de esta prueba es verificar que los números generados estén distribuidos uniformemente en el intervalo $[0, 1)$. Se utiliza una prueba estadística, como la Prueba de Chi-Cuadrado, para comparar la distribución observada con la distribución teórica uniforme.  
> 
> Los pasos incluyen dividir el intervalo en $k$ subintervalos, contar los números generados en cada uno y calcular la estadística de chi-cuadrado:
> 
> $$\chi^2 = \sum_{i=1}^{k} \frac{(O_i - E_i)^2}{E_i}$$
> 
> donde $O_i$ es el número observado y $E_i$ es el esperado. Finalmente, se compara con el valor crítico de chi-cuadrado para determinar si se rechaza la hipótesis nula.

> ---

> **Prueba de Autocorrelación**  
> El objetivo de esta prueba es detectar correlaciones entre números sucesivos en la secuencia. Se calcula el coeficiente de autocorrelación para diferentes retardos (lags).
> 
> Un coeficiente cercano a 0 indica que los números generados son independientes, lo que sugiere que no hay correlación significativa entre ellos.

> ---

> **Prueba de Entropía**  
> El objetivo de esta prueba es medir la aleatoriedad de la secuencia generada. Se calcula la entropía de la distribución de los números.
> 
> Una mayor entropía indica una mayor aleatoriedad en la secuencia generada.

> ---

> **Pruebas de series y subseries**  
> El objetivo de estas pruebas es evaluar la aleatoriedad en subsecuencias dentro de la serie principal. Se divide la secuencia en subseries y se aplican pruebas de uniformidad y autocorrelación en cada una.
> 
> Ejemplos de pruebas incluyen la Prueba de Runs y la Prueba de Longitud de Runs.

> ---

> **Prueba de Distancia de Kolmogorov-Smirnov**  
> El objetivo de esta prueba es comparar la distribución empírica de la secuencia con la distribución teórica uniforme. Se calcula la máxima diferencia entre las funciones de distribución acumulativa de la muestra y la distribución teórica.

> ---

> **Pruebas de Periodicidad**  
> El objetivo de estas pruebas es detectar cualquier repetición periódica en la secuencia. Se utiliza el análisis espectral o técnicas de transformada rápida de Fourier (FFT) para identificar patrones periódicos en los datos generados.

---

## Simulación de Monte Carlo

> **¿Qué es la simulación de Monte Carlo?**
> La Simulación de Monte Carlo es una técnica estadística utilizada para modelar fenómenos complejos y resolver problemas que involucran incertidumbre. Esta técnica se basa en la generación de múltiples escenarios aleatorios para estimar resultados probabilísticos, ayudando en la toma de decisiones cuando los métodos deterministas no son suficientes o viables.
> 
> Utilizando números aleatorios y técnicas estadísticas, se aproximan soluciones a problemas matemáticos que pueden ser difíciles o imposibles de resolver de manera analítica.
> 
> El nombre "Monte Carlo" proviene del famoso casino de Monte Carlo en Mónaco, reflejando el componente aleatorio presente en este método. Fue desarrollada durante la Segunda Guerra Mundial por científicos como Stanislaw Ulam, John von Neumann y Nicholas Metropolis, quienes la emplearon para simular procesos nucleares y físicos complejos.

> ---

> **Fundamentos teóricos**  
> La Simulación de Monte Carlo se apoya en varios principios fundamentales para su implementación y funcionamiento.
> 
> *1. Probabilidad y variables aleatorias*
> En el núcleo de Monte Carlo se encuentran conceptos de probabilidad y variables aleatorias, que pueden ser discretas o continuas. Estas variables representan los diferentes estados posibles de un sistema bajo estudio.
> 
> *2. Integración numérica*
> Monte Carlo se utiliza frecuentemente para aproximar integrales múltiples que son difíciles de calcular de manera analítica.
> 
> A medida que las dimensiones aumentan, los métodos tradicionales de integración numérica pierden eficiencia, mientras que Monte Carlo mantiene una eficiencia relativamente constante, incluso en dimensiones altas.
> 
> *3. Expectativa y Ley de los Grandes Números*
> El método se basa en la esperanza matemática (valor esperado) y la Ley de los Grandes Números, que establece que, al aumentar el número de experimentos o simulaciones, el valor medio de los resultados se acercará al valor esperado real.

> ---

> **Estructura general** 
> La simulación de Monte Carlo sigue un proceso estructurado que permite modelar fenómenos aleatorios mediante la generación de múltiples escenarios.
> 
> El código en python se vería de la siguiente manera:
> 
> ```python
> import numpy as np
> import matplotlib.pyplot as plt
> 
> # Paso 1: Definir el problema
> # El problema es estimar el valor de π usando el método de Monte Carlo.
> # Este método genera puntos aleatorios dentro de un cuadrado de lado 2
> # (rango [-1, 1]) y calcula cuántos caen dentro de un círculo de radio 1.
> 
> # Paso 2: Generar números aleatorios
> # Generamos un conjunto de puntos aleatorios (x, y) en el cuadrado [-1, 1] x [-1, 1].
> num_points = 10000  # Número de puntos a generar
> x = np.random.uniform(-1, 1, num_points)  # Coordenadas x aleatorias
> y = np.random.uniform(-1, 1, num_points)  # Coordenadas y aleatorias
> 
> # Paso 3: Transformar los números aleatorios
> # Calculamos la distancia de cada punto al origen (0, 0).
> # Si la distancia es menor o igual a 1, el punto cae dentro del círculo.
> distances = x**2 + y**2  # Distancia al origen (donde radio del círculo es 1)
> 
> # Paso 4: Ejecutar la simulación
> # Contamos cuántos puntos caen dentro del círculo (distancia <= 1).
> inside_circle = distances <= 1  # Puntos dentro del círculo
> 
> # Estimamos el valor de π: la relación de puntos dentro del círculo sobre el total de puntos.
> pi_estimate = np.sum(inside_circle) / num_points * 4  # Multiplicamos por 4 porque es el área del cuadrado
> 
> # Paso 5: Analizar los resultados
> print(f"Estimación de π: {pi_estimate}")
> ```

---

## Aplicaciones de la simulación de Monte Carlo

> **Simulación en análisis de fiabilidad**
> En el contexto de la fiabilidad y los fenómenos de espera, la simulación permite evaluar el desempeño, identificar cuellos de botella, optimizar recursos y diseñar políticas eficientes.
> 
> Los modelos de fiabilidad buscan representar matemáticamente el comportamiento de sistemas o componentes para predecir su rendimiento y probabilidad de fallos. Estos modelos son fundamentales para diseñar sistemas robustos, planificar mantenimientos preventivos y minimizar tiempos de inactividad.

> ---

> **Modelos de Vida Útil (Life Models)**
> 
> *1. Distribuciones de Vida*
> Las distribuciones de vida se utilizan para modelar el tiempo hasta que un componente falla. Las distribuciones más comunes son:
> 
> - *Exponencial:* Tasa de fallo constante $\lambda$.
> $$R(t) = e^{-\lambda t}$$
> 
> - *Weibull:* Tasa de fallo variable con el tiempo, controlada por parámetros $\lambda$ y $\beta$.
> $$R(t) = e^{-(t/\lambda)^\beta}$$
> 
> *2. Función de Fiabilidad $R(t)$:* Representa la probabilidad de que un componente funcione sin fallar hasta el tiempo $t$:
> $$R(t) = e^{-\lambda t}$$

> ---

> **Modelos de Sistemas**
> 
> *Serie:* En un sistema en serie, la falla de cualquier componente provoca la falla del sistema completo.
> 
> *Paralelo:* En un sistema paralelo, el sistema solo falla cuando todos los componentes han fallado. Esto proporciona redundancia y aumenta la fiabilidad del sistema.
> 
> *Redes Complejas:* Combinaciones de componentes en serie y paralelo, representando sistemas más complejos y realistas.

> ---

> **Modelos de Mantenimiento**
> 
> *Mantenimiento Preventivo:* Acciones programadas para reducir la probabilidad de fallos, como revisiones y reemplazos antes de que ocurra una falla.
> 
> *Mantenimiento Correctivo:* Reparaciones realizadas después de la detección de un fallo, generalmente cuando un componente ya ha fallado.

---

## Bibliografía

> 1. Hillier & Liebermann. *Introducción a la investigación de operaciones*.
> 2. Sixto Ríos Insua. _Investigación Operativa. Optimización_.
> 3. Sixto Ríos Insua. *Problemas de Investigación Operativa. Programación Lineal y Extensiones*.
> 4. Paul W. Williams. *Model Building in Mathematical Programming*.
> 5. González & García. *Manual práctico de investigación de operaciones*.

---