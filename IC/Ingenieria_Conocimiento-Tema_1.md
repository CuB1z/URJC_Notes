---
tags: URJC URJC_IC
---

# Tema 1 - Ingeniería del Conocimiento

---

## Tabla de Contenidos

1. [¿Qué es la Inteligencia Artificial?](#¿Qué%20es%20la%20Inteligencia%20Artificial?)
2. [Inteligencia Artificial](#Inteligencia%20Artificial)
3. [Pensar como humanos](#Pensar%20como%20humanos)
4. [Actuar como humanos](#Actuar%20como%20humanos)
5. [Actuar de forma racional](#Actuar%20de%20forma%20racional)
6. [Historia de la Inteligencia Artificial](#Historia%20de%20la%20Inteligencia%20Artificial)
7. [Agentes](#Agentes)
8. [Agente Inteligente](#Agente%20Inteligente)
9. [Programa y Arquitectura de Agente](#Programa%20y%20Arquitectura%20de%20Agente)
10. [Propiedades de entorno](#Propiedades%20de%20entorno)

---

## ¿Qué es la Inteligencia Artificial?

> **🤖 Inteligencia Artificial**
> Intento de reproducir inteligencia (humana) mediante métodos computacionales, buscando desarrollar sistemas capaces de aprender, razonar y tomar decisiones de manera autónoma.

---

## Inteligencia Artificial

> **🎯 Objetivo**
> Estudiar los entes inteligentes.
> - _Científico_: Entender los entes inteligentes.
> - _Ingenieril_: Construir entes inteligentes.

Otras definiciones enunciadas en la historia:

> **🧠 Sistemas que piensan como humanos**
> _"La interesante tarea de lograr que las computadores piensen...
> Máquinas con mente, en su amplio sentido literal"_
> (Haugeland 1985)

> **🤖 Sistemas que actúan como humanos**
> _"El arte de crear máquinas con capacidad de realizar funciones que
> realizadas por personas requieren inteligencia"_
> (Kurzweil 1990)

> **🧩 Sistemas que actúan de forma racional**
> _"La rama de la Informática que se ocupa de la automatización del
> comportamiento inteligente"_
> (Luger & Stubblefield 1993)

---

## Pensar como humanos

> **🧠 Modelado Congitivo**
> - Abrir la "caja negra" de la mente humana.
> - Analizar los procesos mentales (introspección, experimentos).
> - Desarrollar una teoría acerca de los procesos mentales.
> - Aplicar esta teoría en la simulación de dichos procesos en un ordenador.

> **🧩 General Problem Solver (GPS)**
>  _[Newell & Simon 1961]_
>  
> - Resuelve problemas mediante la descomposición en subproblemas más simples.
> - Se centra en la comparación de los pasos de razonamiento del GPS con los pasos seguidos por una persona al resolver el mismo problema.

> **🧪 Ciencia Cognitiva**
> - Modelos computacionales (IA) + técnicas experimentales (psicología).
> - Construir teorías rigurosas y verificables acerca de los procesos mentales.

---

## Actuar como humanos

> **🧠 Prueba de Turing**
>  _[Alan Turing 1950]_
>  
> - Un evaluador humano y un interlocutor están separados por una mampara.
> - El interlocutor puede ser bien otra persona o bien un ordenador.
> - El evaluador formula preguntas a través de un teletipo, y el interlocutor da sus respuestas del mismo modo.
> - El ordenador supera la prueba, si el evaluador no es capaz de distinguir entre él y un humano.

---

## Actuar de forma racional

> **🧠 Racionalidad**
> - _Prescriptivo_: Como las personas deberían actuar.
> - _Sentido estricto_: ¿Cómo sacar "conclusiones verdaderas"?
> - _Sentido amplio_: ¿Cómo actuar y "sobrevivir" en un entorno?

> **🧩 Pensar de forma Racional**
> - _Leyes de pensamiento de Aristóteles_: Razonamiento irrefutable.
> - _Lógica formal_: Lenguaje formal para representar todo tipo de entes en el mundo y un modelo riguroso para razonar sobre dichos entes.
> - Sistemas basados en métodos computacionales de inferencia lógica, programación lógica.

> **🤖 Actuar de forma racional**
> - Sistemas que requieren acciones racionales.

> **🧠 Agentes Racionales**
> - Enfoque relativo al contexto de actuar de forma "correcta" en un entorno.
> - Las acciones no tienen por qué determinarse mediante inferencia lógica.
> - Sistemas que generan acciones que son eficientes en su entorno con respecto a unos valores / objetivos.

> **🎯 Ventajas**
> - Pone énfasis en una perspectiva _ingenieril_.
> - Proporciona criterios transparentes para evaluar conducta inteligente.
> - Destaca la relación entre comportamientos inteligentes y el entorno en el que se desarrollan (_noción gradual de inteligencia_).
> - Permite una concepción integrada de las distintas técnicas y subáreas de la Inteligencia Artificial.

---

## Historia de la Inteligencia Artificial

> **📜 1940 ~ 1950**
> - Programas que resuelven tareas básicas de razonamiento (jugar ajedrez / jugar damas / probar teoremas geométricos).
> - Primeros modelos de neuronas artificiales (McCulloch & Pitts 1943).
> - _Conferencia de Darthmouth, EEUU (1956)_
> 	- Acuña el término "Inteligencia Artificial".
> 	- John McCarthy, Marvin Minsky, Cluade Shannon, Allen Newell, ...

> **📜 1960 ~ 1970**
> - General Problem Solver (GPS) (Newell & Simon 1961).
> - Entrenamiento de redes neuronales simples (Rosenblatt 1962).
> - Representaciones especializadas del conocimiento (reglas, marcos, guiones).
> - Primeros sistemas expertos (Dendral, Propector, Mycin).
> - Declive de la computación neuronal (Análisis de los Perceptrones de Minsky).

> **📜 1970 ~ 1980**
> - La Inteligencia Artificial entra en la industria
> 	- Aplicaciones comerciales de los sistemas expertos.
> 	- Proyecto de software de "5ª Generación" para crear ordenadores inteligentes en Japón.
> - No se cumplen las promesas: "Invierno de IA".

> **📜 1990**
> - Regreso de las redes neuronales (algoritmo de propagación hacia atrás).
> - Modelos rigurosos y computacionalmentre eficientes de manejo de incertidumbre (cadenas de Markov, redes Bayesianas).
> - La investigación se centra más en construir artefactos útiles en lugar de resolver el problema de la "IA general".

> **📜 2000**
> - Cambio de interés de sde la _IA Simbólica_ a la _IA Conexionista / Machine Learning_.
> - Aumento de capacidad computacional + aumento de datos e información (internet) llevan a nuevos resultados.
> - _Big Data_: Algoritmos de aprendizaje automático para grandes volúmenes de datos.
> - _Deep Learning (2010)_
> 	- Redes con múltiples capas y "niveles" de aprendizaje.
> - Éxitos relevantes en Machine Learning
> - La Inteligencia Artificial entra en la vida diaria
> 	- Sistemas autónomos: Robótica, vehículos autónomos, sistemas multiagente.
> 	- IA generativa (ChatGPT, Dall-E).

---

## Agentes

> **🤖 Agente**
> Ente activo embebido en un entorno.
> - _Cuerpo_
> 	- Percibe el entorno por medio de sensores.
> 	- Actúa sobre el entorno por medio de efectores.
> - _Mente_
> 	- Determina las acciones a partir de las percepciones.
> 	- Medida de rendimiento que guía dicho proceso.

Existen dos tipos de agentes:

> **🌱 Agentes Naturales**
> - Cuerpo biológico y entorno natural.
> - _Sensores_: Ojos, oídos, lengua, etc.
> - _Efectores_: Piernas, brazos, manos, etc.
> - _Medida de rendimiento_: Sobrevivir, reproducirse, etc.

> **🤖 Agentes Artificiales**
> 1. Agentes Hardware (Robots)
> 	- Interactúan directamente con un entorno físico.
> 	- Disponen de un "cuerpo" físico.
> 	- _Sensores_: Cámaras, telémetros infrarrojos, etc.
> 	- _Efectores_: Ruedas / piernas, manipuladores, etc.
> 2. Agentes Software (Softbots)
> 	- Actúan en entornos virtuales como Internet.
> 	- _Todo es software_: No necesitan manipular fisicamente el entorno.
> 	- _Sensores y efectores_: Dependientes del entorno.

---

## Agente Inteligente

> **🤖 Agentes Inteligentes**
> - Actúan de forma racional en su entorno.
> - Determinantes de un comportamiento racional
> 	- _Medida de rendimiento_: Define el grado de éxito del agente.
> 	- _Secuencia de percepciones_: La experiencia del agente.
> 	- _Capacidades_: Las acciones que el agente pueda emprender.
> 	- Conocimiento a priori sobre su entorno.

> **🧠 Comportamiento Racional**
> A partir de la secuencia de percepciones hasta el momento, y el conocimiento a priori sobre el entorno, elegir entre las capacidades la acción que maximice la medida de rendimiento.

> **🤔 Racionalidad ≠ Omnisciencia**
> La selección racional de acciones sólo se basa en la información disponible.

> **❓ Problema**
> Los conocimientos a priori compilan la "inteligencia" del diseñador un agente que no presta atención a sus percepciones.
> - No sería inteligente.
> - Sólo podría actuar en entornos extremadamente simples.
> - No puede actuar con éxito en situaciones no anticipadas.

> **🔄 Autonomía**
> "No bajo el control inmediato de una persona" un agente es más _autónomo_
> - Cuanto más se rige su comportamiento por su propia experiencia.
> - Cuanto menos depende de sus conocimiento a priori.

> **🤖 Agente Inteligente = Comportamiento Racional + Autonomía**

---

## Programa y Arquitectura de Agente

> **💻 Programas de Agente**
> Software que determina el comportamiento del agente, y que implementa la función percepción-acción.
> 
> ```pseudocode
> {simple agent program}
> memory <- perceive(memory, percept)
> action <- action-selection(memory, performance-measure)
> memory <- act(memory, action)
> ```

> **🏗️ Arquitectura de Agente**
> - Los módulos que componen el agente.
> - Estructura el programa de agente.
> - Partes imprescindibles
> 	- Componente de percepción.
> 	- Componente de selección de acciones.
> 	- Componente de acción.

---

## Propiedades de entorno

> **🌍 Accesible / Inaccesible**
> _¿El agente puede determinar inequívocamente el estado de su entorno?_
> - Accesible: Ajedrez, Tres en raya.
> - Inaccesible: Póker, laberinto, videojuego.

> **🔄 Determinista / No Determinista**
> _¿Las acciones del agente en un estado actual determinan completamente el estado resultante?_
> - Determinista: Ajedrez, agente software en entorno simulado.
> - No Determinista: Gestión de tráfico, robot en sala real.

> **🕒 Estático / Dinámico**
> _¿El estado del entorno puede cambiar mientras el agente delibera? ¿Puede cambiar sin que el agente actúe?_
> - Estático: Agente software en un laberinto simulado (entorno no cambia).
> - Semidinámico: Ajedrez (cambios previsibles).
> - Dinámico: Gestión de tráfico (cambios imprevisibles).

> **🔢 Discreto / Continuo**
> _¿Los conjuntos de posibles percepciones y/o acciones son discretos (estados finitos)?_
> - Discreto: Ajedrez, agente software en un laberinto simulado.
> - Continuo: Robot navegando en una sala real.

---