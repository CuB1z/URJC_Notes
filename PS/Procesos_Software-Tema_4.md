---
tags: URJC URJC_PS
---

# Tema 4 - Procesos Software

---

## Tabla de Contenidos

1. [Tema 4.1 - Gráficos básicos para el seguimiento](#Tema%204.1%20-%20Gráficos%20básicos%20para%20el%20seguimiento)
2. [Tema 4.2 - Estimación por Puntos de Historia](#Tema%204.2%20-%20Estimación%20por%20Puntos%20de%20Historia)
3. [Tema 4.3 - Kanban Cycle Time y WIP](#Tema%204.3%20-%20Kanban%20Cycle%20Time%20y%20WIP)
4. [Tema 4.4 - Curva de Seguimiento Rayleigh](#Tema%204.4%20-%20Curva%20de%20Seguimiento%20Rayleigh)

---

## Tema 4.1 - Gráficos básicos para el seguimiento

> **Gráficos básicos**
> Herramientas que ayudan a los equipos a evaluar cómo están gestionando su carga de trabajo, a identificar bloqueos y a mejorar la planificación de futuros Sprints.

> ---

> **Gráfico de Velocidad**
> El gráfico de velocidad se utiliza en modelos ágiles para medir la cantidad de trabajo completado por el equipo en un Sprint.
> 
> La velocidad representa cuántos items de historia se completaron en un Sprint, ayudando a predecir cuánto trabajo se puede terminar en futuros Sprints.
> 
> _Eje Horizontal (X)_
> Representa los diferentes Sprints.
> 
> _Eje Vertical (Y)_
> Representa la cantidad de trabajo completado, normalmente medido en items de historia.
> 
> **¿Cómo se usa?**
> Los equipos miran la velocidad pasada para planificar los próximos Sprints, ajustando expectativas y mejorando la predictibilidad del proyecto.
> 
> La idea es tener una velocidad constante, lo cual indica que el equipo tiene un buen ritmo de trabajo (_Más velocidad no siempre significa mejor rendimiento_).
> 
> [Referencia Gráfico de Velocidad](https://keepcoding.io/blog/que-es-un-velocity-chart/)

> ---

> **Burndown Chart**
> El burndown chart se usa para visualizar cuánto trabajo queda pendiente en un Sprint o proyecto.
> 
> Permite ver a simple vista si el equipo está avanzando de acuerdo a lo planeado o si se está quedando atrás.
> 
> _Eje Horizontal (X)_
> Representa el tiempo, como días del Sprint o semanas del proyecto.
> 
> _Eje Vertical (Y)_
> Representa la cantidad de trabajo restante, medido en items de historia o tareas.
> 
> _Línea Ideal_
> En el gráfico suele haber una línea diagonal ideal que muestra cómo debería reducirse el trabajo a lo largo del Sprint si todo fuera según lo planeado.
> 
> _Línea Real_
> Muestra el progreso real del equipo día a día.
> 	- Si la línea real está por encima de la línea ideal, significa que el equipo está retrasado.
> 	- Si está por debajo, van adelantados.
>
> [Referencia Burndown Chart](https://www.atlassian.com/agile/tutorials/burndown-charts)

> ---

> **Diferencias**
> La _Velocidad_ mide cuánto trabajo se completa por Sprint, mientras que el _Burndown Chart_ mide cuánto trabajo queda por hacer.
> 
> La _Velocidad_ sirve más para planificar y predecir, mientras que el _Burndown Chart_ se usa durante el Sprint para ver si el equipo está cumpliendo con el ritmo esperado.
> 
> **Usos Complementarios**
> Estos gráficos se complementan muy bien para tener una buena visión del estado del equipo y del proyecto.
> 
> Uno mide _cuánto trabajo se hace_ y el otro muestra _cómo avanza ese trabajo_ con el tiempo.
> 
> Ayudan a ser _más transparentes_, a _detectar problemas_ a tiempo y a _mejorar continuamente_.

---

## Tema 4.2 - Estimación por Puntos de Historia

> **Estimación por Puntos de Historia (PH)**
> Técnica de comparación relativa para evaluar el esfuerzo requerido para completar diferentes tareas en proyectos ágiles.
> 
> Esta técnica usa la secuencia de Fibonacci para asignar valores, comenzando en 0,5 y avanzando hacia números mayores.

> ---

> **Puntos clave**
> 
> _Uso de Fibonacci_
> Los valores (0,5, 1, 2, 3, 5...) representan "tiempo ideal" en días para completar los items.
> 
> _Elemento Unidad_
> Se identifica una tarea base con valor de 1 PH como referencia. Ejemplo: "Diseñar un personaje simple = 1 PH".
> 
> _Comparación y Asignación_
> Las tareas se comparan con el elemento unidad para asignarles valores adecuados.
> 
> _Planificación de Sprints_
> Basándose en la velocidad del equipo (e.g., entre 10 y 15 PH por Sprint), se decide qué historias de usuario incluir.
> 
> **Ejemplo**
> Supongamos que diseñar un personaje simple se valora en 1 PH (1 jornada de trabajo del equipo). Diseñar un nivel del juego que requiera el doble de esfuerzo se asignaría 2 PH.

---

## Tema 4.3 - Kanban Cycle Time y WIP

> **Kanban**
> Metodología de gestión visual del trabajo originada en las fábricas de Toyota en Japón. Su objetivo es mejorar la eficiencia mediante la visualización del flujo de trabajo y la limitación del trabajo en progreso (WIP).
> 
> [Referencia de Kanban](https://miro.com/es/agile/que-es-tablero-kanban/)

> ---

> **Principios básicos**
> 
> _Visualización del trabajo_
> Representar las tareas como tarjetas permite identificar cuellos de botella.
> 
> _Limitación del WIP_
> Restringir la cantidad de tareas simultáneas mejora el enfoque y reduce el tiempo de entrega.
> 
> _Gestión del flujo_
> Observar y ajustar el flujo de trabajo para maximizar la eficiencia.
> 
> _Mejora continua_
> Evaluar y optimizar constantemente el proceso.

> ---

> **Aplicación de Kanban al Desarrollo**
> 
> _Definir etapas_
> Desde la concepción hasta el lanzamiento.
> 
> _Tablero Kanban_
> Crear un tablero con columnas que representen las etapas del flujo.
> 
> _Limitar WIP_
> Establecer límites para cada etapa.
> 
> _Monitorizar y ajustar_
> Reuniones regulares para revisar y adaptar.
> 
> **Tiempos en Kanban**
>  _Cycle Time_
>  Tiempo desde que una tarea comienza hasta que se completa.
>  
>   _Lead Time_
>   Tiempo desde que se solicita una tarea hasta que se entrega.

---

## Tema 4.4 - Curva de Seguimiento Rayleigh

> **Curva de Seguimiento Rayleigh**
> Representa la probabilidad de completar una historia de usuario asignada con un número determinado de Puntos Historia (PH) dentro de un rango estimado de tiempo.
> 
> Las historias con el mismo número de PH suelen completarse en un rango de tiempo similar.
> - Historias de 5 PH: entre 4 y 6 días.
> - Historias de 10 PH: entre 6 y 14 días.

> ---

> **Probabilidad de un tiempo menor al estimado**
> - Existe una baja probabilidad de resolver historias en un tiempo inferior al rango estimado, como muestra la parte izquierda de la curva de Rayleigh.
> - Este límite inferior no puede ser cero ni acercarse a cero, ya que es imposible resolver historias en 0 días, incluso con más recursos.
>   
> **Probabilidad de un tiempo mayor al estimado**
> - También hay probabilidad de que las historias tarden más del rango estimado, extendiéndose hasta tiempos «anormalmente» largos, aunque esta probabilidad disminuye progresivamente.
> - Ejemplo: Una historia de 5 PH podría tardar 10 días, aunque esta probabilidad es baja.

> ---

>**Impacto del tamaño de los Puntos Historia**
>
> _Rangos mayores y menor precisión_
> Al asignar más Puntos Historia (e.g., 21 PH), el rango mínimo-máximo de tiempo real crece, y la probabilidad de acertar disminuye.
> 
> _Mayor estabilidad en estimaciones pequeñas_
> Historias con menos Puntos Historia (e.g., 1 PH) son más estables y tienen rangos más pequeños.

> ---

> **Recomendación**
> 
> _Historias pequeñas_
> Se recomienda dividir las historias de usuario en partes más pequeñas para facilitar estimaciones precisas y reducir la oscilación en los tiempos de entrega.
> 
> Mantener historias pequeñas ayuda a minimizar la incertidumbre y aumentar la precisión en la planificación del proyecto.

---