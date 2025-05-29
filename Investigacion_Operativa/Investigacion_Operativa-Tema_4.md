---
tags: URJC URJC_IO
---

# Tema 4 - Investigación Operativa

---

## Tabla de Contenidos

1. [¿Qué es la Teoría de Colas?](#¿Qué%20es%20la%20Teoría%20de%20Colas?)
2. [¿Qué son los Fenómenos de Espera?](#¿Qué%20son%20los%20Fenómenos%20de%20Espera?)
3. [Historia de la Teoría de Colas](#Historia%20de%20la%20Teoría%20de%20Colas)
4. [Sistemas de Colas](#Sistemas%20de%20Colas)
5. [¿Qué son las Medidas de Eficiencia?](#¿Qué%20son%20las%20Medidas%20de%20Eficiencia?)
6. [Modelos Poissonianos](#Modelos%20Poissonianos)
7. [¿Qué es la Ley de Little?](#¿Qué%20es%20la%20Ley%20de%20Little?)
8. [Redes de Colas](#Redes%20de%20Colas)
    - [Red Abierta](#Red%20Abierta)
    - [Red Cerrada](#Red%20Cerrada)
    - [Redes Mixtas](#Redes%20Mixtas)
9. [Sistemas Apropiativos y Expulsivos](#Sistemas%20Apropiativos%20y%20Expulsivos)
	- [Sistemas apropiativos (no expulsivos)](#Sistemas%20apropiativos%20(no%20expulsivos))
	- [Sistemas expulsivos (preemptive)](#Sistemas%20expulsivos%20(preemptive))
1. [Bibliografía](#Bibliografía)



---

## ¿Qué es la Teoría de Colas?

> **Teoría de Colas**
> La teoría de colas emerge como una herramienta vital en la investigación operativa para analizar y mejorar sistemas donde los recursos son limitados y la demanda es variable.
> 
> Se centra en proporcionar una visión detallada y profunda de los conceptos y modelos que permiten entender y gestionar las líneas de espera en diversos contextos.
> 
> - Los fenómenos de espera afectan la satisfacción del cliente y la productividad de las organizaciones.
> - Proporcionan un marco para entender y gestionar líneas de espera en contextos diversos.

---

## ¿Qué son los Fenómenos de Espera?

> **Fenómenos de Espera**
> Los fenómenos de espera surgen cuando existe un desequilibrio temporal entre la demanda de un servicio y la capacidad para proporcionarlo.
> 
> Los desequilibrios pueden deberse a:
> - Variabilidad en la llegada de clientes.
> - Variabilidad en el tiempo de servicio.
> - Capacidad limitada de recursos.

---

## Historia de la Teoría de Colas

> **1878-1929 (Agner Krarup Erlang)**  
> Matemático danés considerado el pionero de la teoría de colas. En 1909, mientras trabajaba en la compañía telefónica de Copenhague, desarrolló métodos para optimizar el número de líneas telefónicas y operadores.
> 
> ---
> 
> **1917 ("The Theory of Probabilities and Telephone Conversations")**  
> Erlang publicó fórmulas para calcular la probabilidad de pérdida de llamadas y tiempos de espera, sentando las bases de la teoría de colas.
> 
> ---
> 
> **1920-1940 (Expansión de modelos)**  
> Se ampliaron los modelos de Erlang, incorporando distribuciones de llegadas y tiempos de servicio. Se utilizaron procesos estocásticos y teoría de probabilidades.
> 
> ---
> 
> **Segunda Guerra Mundial (Logística militar)**  
> La teoría de colas fue aplicada en la logística y gestión de recursos, lo que impulsó su desarrollo.
> 
> ---
> 
> **Años 50-60 (Formalización de modelos matemáticos)**  
> Se desarrollaron procesos de Markov y cadenas de Markov, aplicándolos a sistemas de colas cada vez más complejos.
> 

---

## Sistemas de Colas

> **Proceso de llegadas**
> Describe cómo los clientes o unidades de demanda llegan al sistema.
>
> *Tasa de llegada ($\lambda$)*
> Número promedio de llegadas por unidad de tiempo.
> 
> *Distribución de llegadas*
> Puede ser determinística o estocástica (frecuentemente modelada con distribución de Poisson).
> 
> *Patrones de llegada*
> Pueden ser llegadas individuales (uno por uno) o en lotes (en grupos o paquetes).
> 
> *Fuente de clientes*
> Puede ser infinita (no se afecta la tasa de llegada futura) o finita (se reduce la población fuente).

> ---

> **Proceso de servicio**
> Describe la forma en que los clientes son atendidos en el sistema.
> 
> *Tasa de servicio ($\mu$)*
> Número promedio de clientes atendidos por unidad de tiempo.
> 
> *Distribución de tiempos de servicio*
> Puede ser constante o seguir una distribución probabilística, como la exponencial.
> 
> *Número de servidores*
> Puede ser de servidor único o multiservidor (en paralelo).
> 
> *Estructura de servicio*
> Puede ser en paralelo (un cliente puede ser atendido por cualquier servidor disponible) o en serie (los clientes deben seguir una secuencia determinada).

> ---

> **Disciplina de la cola**
> 
> *FIFO*
> Primero en llegar, primero en ser atendido.
> 
> *LIFO*
> Último en llegar, primero en ser atendido.
> 
> *SIRO*
> Selección aleatoria para el servicio.
> 
> *Prioridad*
> Los clientes con prioridad mayor son atendidos antes. Se diferencia la de tipo preemptiva (se pueden interrumpir servicios) y la de tipo no preemptiva (no se interrumpen procesos).

> ---

> **Capacidad y población del sistema**
> 
> *Capacidad del sistema*
> Puede ser infinita (no hay límite de clientes en cola) o finita $k$ (existe un límite máximo de clientes en el sistema. Si se alcanza este límite, los nuevos clientes son rechazados o bloqueados).
> 
> *Bloqueo o pérdida de clientes*
> En sistemas con capacidad limitada, los clientes que llegan cuando el sistema está lleno pueden ser perdidos, lo que afecta el rendimiento y la satisfacción.
> 
> *Población fuente*
> La población puede ser infinita (la tasa de llegada no se ve afectada por el número de clientes en el sistema) o finita (la tasa de llegada puede depender del número de clientes en el sistema).

---

## ¿Qué son las Medidas de Eficiencia?

> **Medidas de Eficiencia**
> Métricas cuantitativas que describen el comportamiento y desempeño de un sistema de colas.
> 
> - Permiten identificar cuellos de botella.
> - Ayudan a equilibrar recursos.
> - Contribuyen a mejorar la satisfacción del cliente.
> - Facilitan la toma de decisiones estratégicas y operativas.
> - Proporcionan una base para comparar diferentes configuraciones.

> ---

> **Tiempo promedio en cola ($W_q$)**
> Tiempo promedio que un cliente pasa esperando en la cola antes de ser atendido. Refleja la eficiencia del sistema en la gestión de la espera.
> 
> Un $W_q$ alto indica que los clientes esperan mucho tiempo, lo cual puede disminuir la satisfacción y afectar la productividad.
> 
> Un $W_q$ bajo es deseable, pero puede implicar costes más altos si se requieren más recursos para lograrlo.

> ---

> **Número promedio de clientes en cola ($L_q$)**
> Número promedio de clientes que están esperando en la cola en un momento dado. Proporciona una medida de la saturación en la cola.
> 
> Un Lq alto puede indicar necesidad de aumentar la capacidad de servicio.
> 
> Un Lq bajo sugiere que el sistema está manejando eficientemente la demanda.

> ---

> **Tiempo promedio en el sistema ($W$)**
> Tiempo total promedio que un cliente pasa en el sistema, incluyendo tanto el tiempo en cola ($W_q$) como el tiempo de servicio ($W_s$). Refleja la experiencia completa del cliente en el sistema.
> 
> $$W = W_q + (1 / \mu)$$
> 
> Donde $1 / \mu$ es el tiempo promedio de servicio ($W_s$).
> 
> Un $W$ alto puede afectar negativamente la satisfacción del cliente.
> Es crucial equilibrar $W_q$ y $W_s$ para optimizar $W$.

> ---

> **Número promedio de clientes en el sistema ($L$)**
> Número promedio de clientes presentes en el sistema, incluyendo tanto los que están en cola como los que están siendo atendidos. Indica el nivel general de actividad en el sistema.
> 
> $$𝐿 = 𝐿_𝑞 + \rho_L$$
> 
> Donde $\rho$ es la utilización del servidor.
> 
> Un $L$ alto puede señalar saturación y potenciales demoras.
> Ayuda en la planificación de recursos y espacio físico necesario.

> ---

> **Utilización del servidor ($\rho$)**
> Proporción del tiempo que el servidor está ocupado atendiendo clientes. Refleja la eficiencia en el uso del recurso de servicio
> 
> $$\rho = \lambda / \mu$$
> 
> Donde $\lambda$ es la tasa promedio de llegadas y $\mu$ es la tasa promedio de servicio.
> 
> Un $\rho$ cercano a 1 indica que el servidor está casi siempre ocupado.
> Un $\rho$ muy bajo puede implicar subutilización y costes innecesarios.

---

## Modelos Poissonianos

> **Notación Kendall**
> Las medidas de eficiencia se calculan utilizando modelos matemáticos que representan el comportamiento del sistema de colas.
> 
> $A / S / c / K / N / D$
> 
> - ($A$) Llegadas
> - ($S$) Servicio
> - ($c$) Nº de Servidores
> - ($K$) Capacidad del sistema (opcional)
> - ($N$) Tamaño de la población fuente (opcional)
> - ($D$) Disciplina de Cola (opcional)

> ---

> **Modelo M/M/1**
>
> | Característica                      | Descripción                                     |
> |-------------------------------------|------------------------------------------------|
> | Llegadas                            | Proceso de Poisson con tasa $\lambda$.               |
> | Tiempos de servicio                 | Distribución exponencial con tasa $\mu$.         |
> | Número de servidores                | Un solo servidor.                              |
> | Capacidad                           | Infinita.                                      |
> | Población fuente                    | Infinita.                                      |
> | Disciplina                          | FIFO.                                         |
> | Condición de estabilidad            | $$\rho = \frac{\lambda}{\mu} < 1$$                                |
> | Utilización del servidor ($\rho$)        | Donde $\rho$ es la utilización del servidor.      |
>   
> | Métrica                                              | Fórmula                                         |
> | --------------------------------------- | ------------------------------------- |
> | Utilización del servidor ($\rho$)                | $$\rho = \frac{\lambda}{\mu}$$                                   |
> | Número promedio en cola (Lq)        | $$L_q = \frac{ρ^2}{1 - \rho}$$                    |
> | Número promedio en el sistema (L) | $$L = \frac{\rho}{1 - \rho}$$                        |
> | Tiempo promedio en cola (Wq)        | $$W_q = \frac{L_q}{\lambda} = \frac{\rho}{\mu \space (1 - \rho)}$$ |
> | Tiempo promedio en el sistema (W) | $$W = \frac{L}{\lambda} = \frac{1}{\mu \space (1 - \rho)}$$     |

> ---

> **Modelo M/M/c**
> 
> | Característica                         | Descripción                                                 |
> | ------------------------------- | ---------------------------------------------- |
> | Llegadas                                | Proceso de Poisson con tasa $\lambda$.               |
> | Tiempos de servicio               | Distribución exponencial con tasa $\mu$.      |
> | Número de servidores           | $c$ servidores en paralelo.                         |
> | Capacidad                              | Infinita.                                                        |
> | Población fuente                    | Infinita.                                                        |
> | Disciplina                                | FIFO.                                                            |
> | Condición de estabilidad        | $$\rho = \frac{\lambda}{c\mu} < 1$$                             |
> | Utilización del sistema ($\rho$)       | Donde $\rho$ es la utilización del sistema.     |
> 
> | Métrica                              | Fórmula                                              |
> |--------------------------------------|-----------------------------------------------------|
> | Utilización del sistema ($\rho$)          | $$\rho = \lambda / (c * \mu)$$                                   |
> | Probabilidad de que todos estén ocupados ($P0$) | $$P0 = \frac{1}{\sum_{n = 0}^{c - 1}{\frac{(\lambda / \mu)^n}{n!} + \frac{(\lambda / \mu)^c}{c!} \cdot \frac{(c\mu)}{c\mu - \lambda}}}$$ |
> | Número promedio en cola ($Lq$)         | $$L_q = \frac{P0 \cdot (λ/μ)^c \cdot ρ}{c! \cdot (1 - \rho)^2}$$         |
> | Número promedio en el sistema ($L$)    | $$L = L_q + (\lambda / \mu)$$                                  |
> | Tiempo promedio en cola ($W_q$)         | $$W_q = \frac{L_q}{\lambda}$$                                       |
> | Tiempo promedio en el sistema ($W$)    | $$W = W_q + \frac{1}{\mu}$$                                  |

> ---

> **Modelo M/M/1/K**
> 
> | Característica                       | Descripción                                                          |
> | ------------------------------ | ---------------------------------------------------- |
> | Llegadas                               | Proceso de Poisson con tasa $\lambda$.             |
> | Tiempos de servicio             | Distribución exponencial con tasa $\mu$.             |
> | Número de servidores         | Un solo servidor.                                                   |
> | Capacidad                            | Limitada a $K$ clientes (incluyendo el servicio).   |
> | Población fuente                  | Infinita.                                                                  |
> | Disciplina                              | FIFO.                                                                     |
> | Condición de estabilidad     | $$\rho = \frac{\lambda}{\mu} < 1$$                                                  |
> 
> | Métrica                              | Fórmula                                              |
> |--------------------------------------|-----------------------------------------------|
> | Suma del denominador ($S$) | $$S = \begin{cases}K + 1, & si \space \rho = 1 \\ \frac{1 - \rho^{k + 1}}{1 - \rho} & si \space \rho \neq 1 \\ \end{cases}$$ |
> | Probabilidad estado ($P_n$) | $$P_n = \frac{\rho^n}{S}$$|
> | Número promedio en el sistema ($L$)    | $$L = \sum_{n = 0}^K{n \cdot P_n}$$ |
> | Tiempo promedio en el sistema ($W$)    | $$W = \frac{L}{\lambda_e}$$                |
> | Número promedio en cola ($L_q$)         | $$L_q = L - (1 - P_0)$$                          |
> | Tiempo promedio en cola ($W_q$)         | $$W_q = W \frac{1}{\rho}$$                    |

> ---

> **Modelo M/M/∞**
> 
> | Característica                       | Descripción                                                            |
> | ------------------------------------ | ----------------------------------------------- |
> | Llegadas                             | Proceso de Poisson con tasa $\lambda$.                 |
> | Tiempos de servicio                  | Distribución exponencial con tasa $\mu$.         |
> | Número de servidores                 | Infinito.                                                           |
> | Capacidad                            | Ilimitada.                                                          |
> | Población fuente                     | Infinita.                                                           |
> | Disciplina                           | Sin restricciones (debido al número ilimitado de servidores).  |
> | Condición de estabilidad             | Siempre estable debido a la capacidad ilimitada.  |
> 
> | Métrica                              | Fórmula                                                             |
> | ------------------------------------ | ------------------------------------------------------------------- |
> | Probabilidad de estado ($P_n$) | $$P_n = \frac{\rho^n \cdot e^{-\rho}}{n!}$$                                           |
> | Número promedio en el sistema ($L$)    | $$L = \rho$$                           |
> | Tiempo promedio en el sistema ($W$)    | $$W = \frac{1}{\mu}$$           |
> | Número promedio en cola ($L_q$)         | $$Lq = 0$$                               |
> | Tiempo promedio en cola ($W_q$)         | $$Wq = 0$$                                    |

---

## ¿Qué es la Ley de Little?

> **Ley de Little**
> La Ley de Little es una relación fundamental en la teoría de colas que conecta tres métricas clave:
> 
> | Métrica            | Descripción                                                                   |
> | ---------------- | ---------------------------------------------------------- |
> | $L$                  | Número promedio de clientes en el sistema.               |
> | $\lambda$       | Tasa promedio de llegadas al sistema.                         |
> | $W$                  | Tiempo promedio que un cliente pasa en el sistema.  |
>
> | Fórmula                              |
> | ----------------------------- |
> | $$L = \lambda \cdot W$$ |

---

## Redes de Colas

> **Elementos Clave**
> 
> *Estaciones (Nodos)*
> Puntos donde se ofrece un servicio. Cada estación tiene su propia disciplina de cola, tasa de servicio y capacidad.
> 
> *Clientes*
> Entidades que requieren servicio y se mueven a través de la red.
> 
> *Enrutamiento*
> Las reglas o probabilidades que determinan cómo los clientes se mueven de una estación a otra.
> 
> *Redes Abiertas, Cerradas y Mixtas*
> Clasificación basada en cómo los clientes entran y salen del sistema.

---

### Red Abierta

> **Conceptos Básicos**
> 
> *Clientes en una red abierta*
> 	- Los clientes pueden entrar desde el exterior.
> 	- Pueden moverse entre estaciones dentro de la red.
> 	- Pueden salir al completar su servicio.
>
> *Fuente infinita de clientes*
> Se asume que hay un número ilimitado de clientes potenciales.
>
> *Tasas de llegada externas*
> Los clientes llegan a estaciones desde fuera con una tasa determinada.
>
> *Probabilidades de enrutamiento*
> Un cliente puede moverse a otra estación o salir del sistema tras el servicio. Estas acciones están determinadas por probabilidades específicas.
>
> *Estado estacionario*
> 	- El análisis se enfoca en el comportamiento a largo plazo.
> 	- Esto ocurre cuando el sistema alcanza un estado estable.

> ---

> **Fórmulas clave**
>
> *Tasa de llegada a cada estación ($\lambda_i$)*
> $$\lambda_i = e_ᵢ + \sum_{r = 1}^{N}{\lambda_r \cdot P_{ri}}$$
> - **$e_i$** $\to$ Tasa de llegadas externas a la estación $i$.
> - **$P_{ri}$** $\to$ Probabilidad de moverse de la estación $r$ a la estación $i$.
> - **$N$** $\to$ Número total de estaciones.
>
>*Utilización de la estación $i$ ($\rho_i$)*
> $$\rho_i = \frac{\lambda_i}{\mu_i}$$
> - **$\mu_i$** $\to$ Tasa de servicio de la estación $i$.

---

### Red Cerrada

> **Conceptos Básicos**
> 
> *Población fija*
> Un número fijo de $K$ clientes circula continuamente dentro de la red.
> 
> *Recirculación*
> Los clientes completan su servicio en una estación y se mueven a otra según probabilidades de enrutamiento.
> 
> *Sin entradas ni salidas externas*
> Los clientes permanecen siempre dentro del sistema.

> ---

> **Cálculo de medidas de rendimiento**
>
> *Tasa de visita a la estación $i$ ($V_i$)*
> Representa el número promedio de veces que un cliente visita la estación i por ciclo.
>
> *Tiempo de servicio en la estación $i$ ($S_i$)*
> Es el tiempo promedio que un cliente pasa en la estación $i$.
>
> *Tiempo de respuesta del sistema ($R$)*
> Es el tiempo promedio que un cliente tarda en completar un ciclo completo.
>
> *Rendimiento del sistema (Throughput, $X$)*
> Es el número promedio de ciclos completados por unidad de tiempo.

> ---

> **Fórmulas clave**
>
> *Tasa de visita a la estación $i$ ($V_i$)*
> $$V_i = \frac{\text{Número de visitas a la estación} \space i}{\text{Número total de ciclos}}$$
>
> *Tiempo de servicio en la estación $i$ ($S_i$)*
> $$S_i = \frac{\text{Tiempo total de servicio en la estación} \space i}{\text{Número de clientes atendidos en la estación} \space i}$$
>
> *Tiempo de respuesta del sistema por recurso ($R_i$)*
> $$R_i(n) = S_i \cdot (1 + Q_i(n - 1))$$
> 
> *Tiempo promedio de respuesta del sistema*
> $$R(n) = \sum_i{V_i \cdot R_i(n)}$$
> 
> *Rendimiento del sistema (X)*
> $$X(n) = \frac{n}{R(n)}$$

> ---

> **Algoritmo de Mean Value Analysis (MVA)**
> ```python
> # Definición de los parámetros del sistema
> resources = {
>     "CPU": {"S": 0.04, "V": 2},     # Tiempo de servicio y número de instancias
>     "I/O": {"S": 0.1, "V": 1},      # Tiempo de servicio y número de instancias
>     "Terminal": {"S": 12, "V": 1}   # Tiempo de servicio y número de instancias
> }
> 
> N = 10  # Número de procesos en el sistema
> 
> # Inicialización de las variables
> Q = {resource: 0 for resource in resources}  # Número promedio de procesos en cada recurso
> R = {resource: 0 for resource in resources}  # Tiempo de respuesta en cada recurso
> X = 0  # Rendimiento del sistema
> R_total = 0  # Tiempo de respuesta total
> 
> # Iteración para calcular los valores
> for n in range(1, N+1):
>     # Calcular el tiempo de respuesta en cada recurso
>     for resource in resources:
>         R[resource] = resources[resource]["S"] * (1 + Q[resource])
>     
>     # Calcular el tiempo de respuesta total
>     R_total = sum(R[resource] * resources[resource]["V"] for resource in resources)
>     
>     # Calcular el rendimiento
>     X = n / R_total
>     
>     # Actualizar el número promedio de procesos en cada recurso
>     for resource in resources:
>         Q[resource] = X * resources[resource]["V"] * R[resource]
>     
>     # Mostrar resultados para cada iteración
>     print(f"Iteración {n}:")
>     print(f"  Tiempo de respuesta total (R({n})) = {R_total:.4f} segundos")
>     print(f"  Rendimiento (X({n})) = {X:.4f} procesos por segundo")
>     for resource in resources:
>         print(f"  Q_{resource}({n}) = {Q[resource]:.4f} procesos en el recurso {resource}")
>     print("")
> ```

---

### Red Mixta

> **Definición**
> Las redes mixtas son sistemas de colas que combinan elementos de redes abiertas y redes cerradas.
> 
> Esta combinación permite modelar sistemas donde hay interacción entre procesos internos y externos, reflejando situaciones más realistas y complejas que las que pueden modelar las redes abiertas o cerradas por separado.

> ---

> **Conceptos Básicos**
> 
> *Componentes abiertos*
> Parte de la red donde los clientes pueden llegar desde el exterior y salir del sistema después de recibir servicio.
> 
> *Componentes cerrados*
> Parte de la red donde hay un número fijo de clientes circulando internamente, sin entradas ni salidas externas.
> 
> *Interacción directa entre clientes*
> Los clientes de la parte cerrada pueden requerir servicios que son proporcionados por servidores que también atienden a clientes de la parte abierta.
> 
> *Recursos compartidos*
> Los recursos del sistema son compartidos entre ambos tipos de clientes, lo que puede generar competencia y afectar el rendimiento.

> ---

> **Complejidad de Análisis**
> 
> *Dependencias cruzadas*
> La presencia de ambos tipos de clientes introduce dependencias adicionales, complicando el análisis matemático.
> 
> *Variabilidad en tiempos de servicio*
> Los tiempos de servicio pueden depender del tipo de cliente y del estado del sistema.
> 
> *Necesidad de simulación*
> A menudo, el análisis exacto es intratable, por lo que se recurre a métodos aproximados o simulación.

> ---

> **Fórmulas Clave**
> Tomando la nomenclatura de $UE$ como "usuarios externos":
> 
> *Número promedio total de $UE$ por recurso*
> $$Q_i^{UE} = X^{UE} \cdot V_i^{UE} \cdot R_i^{UE}$$
> 
> *Rendimiento del Sistema para Usuarios Externos ($X^{UE}$)*
> $$X^{UE} = \lambda$$
>
> *Tiempo de Respuesta por Recurso ($R_i$)*
> $$R_i = S_i \cdot (1 + \frac{Q_i^{UE} + Q_i^{PI}}{m_i})$$
>
> *Tiempo de Respuesta Total para Usuarios Externos ($R^{UE}$)*
> $$R^{UE} = \sum_i{V_i^{UE} \cdot R_i^{UE}}$$
>
>*Tiempo de respuesta para $PI$*
> $$R_i^{PI}(N) = S_i^{PI} \cdot (1 + Q_i^{PI}(n - 1) + \frac{Q_i^{UE}}{m_i})$$

> ---

> **Algoritmo de Análisis**
>
> 1. Calcular los tiempos de respuesta para PI utilizando el Algoritmo de Mean Value Analysis (MVA).
> 2. Determinar los tiempos de respuesta para UE considerando el impacto de los PI en cada recurso.
> 3. Calcular las métricas de rendimiento: ($R^{UE}$), ($X^{UE}$), y ($Q_i^{UE}$).
>
> *Código en Python*
> 
> ```python
> # Parámetros del sistema
> resources = {
>     "SP": {"S_UE": 0.10, "S_PI": 0.20, "V_UE": 1, "V_PI": 1},
>     "DA": {"S_UE": 0.05, "S_PI": 0.15, "V_UE": 0.7, "V_PI": 1},
>     "RC": {"S_UE": 0.02, "S_PI": 0.02, "V_UE": 2, "V_PI": 0}
> }
> N = 5  # Número de PI
> lam = 4  # Tasa de llegada de UE
> 
> # Inicialización
> Q_PI = {res: 0 for res in resources}
> R = {res: 0 for res in resources}
> R_total = 0
> X_UE = lam
> Q_UE = {res: 0 for res in resources}
> 
> # MVA para PI
> for n in range(1, N + 1):
>     for res, params in resources.items():
>         R[res] = params["S_PI"] * (1 + Q_PI[res])
>     R_total_PI = sum(params["V_PI"] * R[res] for res, params in resources.items())
>     X_PI = n / R_total_PI
>     for res, params in resources.items():
>         Q_PI[res] = X_PI * params["V_PI"] * R[res]
> 
> # Calcular métricas para UE
> for res, params in resources.items():
>     R[res] = params["S_UE"] * (1 + Q_PI[res])
> R_total_UE = sum(params["V_UE"] * R[res] for res, params in resources.items())
> for res, params in resources.items():
>     Q_UE[res] = X_UE * params["V_UE"] * R[res]
> 
> # Resultados
> print(f"Tiempo de respuesta total para UE: {R_total_UE:.4f} minutos")
> print(f"Rendimiento efectivo para UE: {X_UE:.4f} tareas/minuto")
> print("Números promedio de UE en cada recurso:")
> for res, q in Q_UE.items():
>     print(f"  {res}: {q:.4f}")
> ```

---

## Sistemas Apropiativos y Expulsivos

> **Conceptos Básicos**
> En la teoría de colas y análisis de sistemas de servicio, la disciplina de servicio es un aspecto crucial que determina cómo los clientes son atendidos cuando compiten por un recurso compartido.
> 
> Dos de las disciplinas de servicio más importantes y ampliamente estudiadas son los sistemas apropiativos (no expulsivos) y los sistemas expulsivos.
> 
> El análisis de sistemas expulsivos y apropiativos es esencial para modelar y diseñar sistemas donde la prioridad y la interrupción del servicio juegan un papel significativo, como en sistemas operativos, redes de comunicación y procesos industriales.

---

### Sistemas apropiativos (no expulsivos)

> **¿En qué consiste un sistema apropiativo?**
> En un sistema apropiativo, una vez que un cliente comienza a ser atendido por el servidor, su servicio no puede ser interrumpido hasta que se complete.
> 
> Las prioridades de los clientes solo afectan el orden de entrada en la cola, pero no pueden interrumpir el servicio en curso. Los clientes pueden ser ordenados en la cola según alguna política de prioridad, como FIFO, SJF o prioridades estáticas.
> 
> Tiene su aplicación en procesos de producción, sistemas donde la interrupción es costosa o impráctica.

---

### Sistemas expulsivos (preemptive)

> **¿En qué consiste un sistema expulsivo?**
> En un sistema expulsivo, los clientes en servicio pueden ser interrumpidos si llega un cliente con mayor prioridad. El cliente interrumpido regresa a la cola o a un estado de espera, y su servicio puede reanudarse más tarde.
> 
> Reanudación del servicio: El servicio del cliente interrumpido puede reanudarse desde donde se dejó (preemptive resume) o reiniciarse (preemptive repeat).
> 
> Tiene su aplicación en sistemas operativos (gestión de procesos), redes de comunicación con prioridades, sistemas en tiempo real.

> ---

> **Tipos de sistemas expulsivos**
> 
> *Preemptive Resume (Reanudación)*
> Cuando un cliente es interrumpido, al reanudar su servicio, continúa desde el punto donde fue interrumpido.
> 
> *Preemptive Repeat (Reinicio)*
> Cuando un cliente es interrumpido, al reanudar su servicio, debe comenzar desde el inicio.

---

## Bibliografía

> 1. Hillier & Liebermann. *Introducción a la investigación de operaciones.*
> 2. Sixto Ríos Insua. _Investigación Operativa. Optimización._
> 3. Sixto Ríos Insua. *Problemas de Investigación Operativa. Programación Lineal y Extensiones.*
> 4. Paul W. Williams. *Model Building in Mathematical Programming.*

---