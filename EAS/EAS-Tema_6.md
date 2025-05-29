---
tags: URJC URJC_EAS
---

# Tema 6 - Evolución y Adaptación Software

---

## Tabla de Contenidos

1. [Evolución del Software](#Evolución%20del%20Software)
2. [Procesos de Mantenimiento](#Procesos%20de%20Mantenimiento)
3. [Sistemas Heredados y Evaluación](#Sistemas%20Heredados%20y%20Evaluación)
4. [Reingeniería de Software](#Reingeniería%20de%20Software)
5. [Ingeniería Inversa](#Ingeniería%20Inversa)
6. [Relación entre Ingeniería Directa, Inversa y Reingeniería](#Relación%20entre%20Ingeniería%20Directa,%20Inversa%20y%20Reingeniería)
7. [Conclusión](#Conclusión)

---

## Evolución del Software

> **🔄 Evolución del Software**
> El software no es un producto estático. Desde su primera entrega comienza su transformación para adaptarse a cambios organizacionales, tecnológicos o de mercado.  
> Esta transformación es conocida como **evolución del software**.

> ---

> **📘 Definiciones clave**
> *Lehman y Ramil*
> La evolución comprende todas las actividades orientadas a generar una nueva versión operativa a partir de una ya existente.
> 
> *SWEBOK*
> La evolución incluye mantenimiento, adaptación tecnológica, cambios en los requisitos y mejora continua del producto.

> ---

> **📈 Factores que impulsan la evolución:**
> - Cambios normativos o legales
> - Nuevas plataformas tecnológicas
> - Necesidad de nuevas funcionalidades
> - Obsolescencia de componentes existentes
> - Mejora de calidad o rendimiento

> ---

> **🌀 Modelo en espiral**
> La evolución del software se visualiza mejor como un ciclo continuo y recurrente, donde mantenimiento, mejora y rediseño coexisten.

---

## Procesos de Mantenimiento

> **🔧 Tipos de Mantenimiento**
> - **🛠 Correctivo**: Reparar defectos encontrados en producción.
> - **✨ Perfectivo**: Mejorar prestaciones o añadir funciones no previstas inicialmente.
> - **🔁 Adaptativo**: Modificar el software para nuevos entornos (hardware, SO, librerías, etc.).
> - **🛡 Preventivo**: Mejorar la mantenibilidad del código para facilitar futuras modificaciones.

> ---

> **🔁 Mantenimiento como parte de la evolución**
> Históricamente se separaba del desarrollo, pero hoy se entiende como una fase continua del ciclo de vida.

> ---

> **💸 Coste del mantenimiento**
> - Puede representar hasta el **80%-90% del presupuesto total** de una aplicación.
> - Implica tareas de diagnóstico, rediseño, documentación, pruebas y despliegue.
> - La *falta de documentación* y *complejidad acumulada* aumentan su coste con el tiempo.

---

## Sistemas Heredados y Evaluación

> **🏚️ ¿Qué es un sistema heredado (legacy)?**
> Software aún en uso dentro de una organización, pero que ha sido construido con tecnologías, estructuras o prácticas obsoletas.

> ---

> **📊 Criterios de Evaluación Técnica**
> - Comprensibilidad del código
> - Calidad y disponibilidad de la documentación
> - Modelo de datos y estructura lógica
> - Uso de tecnologías obsoletas
> - Nivel de automatización de pruebas
> - Habilidades del equipo de mantenimiento

> ---

> **💼 Evaluación del valor de negocio**
> - Frecuencia de uso del sistema
> - Dependencia operativa
> - Nivel de integración con otros procesos críticos
> - Riesgo ante fallos o interrupciones

> ---

> **📉 Clasificación y acciones recomendadas**
> 
> | Calidad Técnica | Valor de Negocio | Acción recomendada              |
> |------------------|------------------|---------------------------------|
> | Baja             | Baja             | Desechar                        |
> | Baja             | Alta             | Reingeniería o reemplazo        |
> | Alta             | Baja             | Mantener si el coste lo justifica |
> | Alta             | Alta             | Continuar mantenimiento y mejora|

---

## Reingeniería de Software

> **♻️ ¿Qué es?**
> Proceso sistemático de transformación de un sistema existente, **sin cambiar su funcionalidad**, para mejorar su calidad interna, estructura, rendimiento o plataforma.

> ---

> **🧰 Actividades típicas**
> *📄 Redocumentación*
> Recuperar especificaciones y diagramas.
> 
> *🔧 Reestructuración*
> Refactorización, separación de responsabilidades, modularización.
> 
> *🚀 Migración tecnológica*
> Cambio de lenguaje, arquitectura (por ejemplo, monolito → microservicios), actualización de librerías.

> ---

> **🎯 Objetivos**
> - Incrementar la mantenibilidad
> - Eliminar redundancias y código obsoleto
> - Facilitar el testeo y la integración
> - Reducir los costes operativos

> ---

> **💡 Reingeniería ≠ Mantenimiento**
> La reingeniería implica una *intervención planificada y profunda*, mientras que el mantenimiento suele centrarse en cambios locales o correctivos.

---

## Ingeniería Inversa

> **🔍 ¿Qué es?**
> Es el proceso de **analizar un sistema software existente** para identificar sus componentes, relaciones y lógica interna, normalmente partiendo del código fuente o binarios.

> ---

> **🔧 Técnicas comunes**
> - Análisis estático de código (sin ejecutarlo)
> - Generación automática de diagramas UML
> - Extracción de dependencias, estructuras y flujos
> - Decompilación de binarios o bytecode

> ---

> **🎯 Usos prácticos**
> - Recuperar conocimiento perdido
> - Crear documentación inexistente
> - Identificar riesgos o vulnerabilidades
> - Preparar el sistema para una futura reingeniería

---

## Relación entre Ingeniería Directa, Inversa y Reingeniería

> **🔁 Interacciones clave**
> 
> *🛠️ Ingeniería directa*
> Diseño e implementación del sistema siguiendo un flujo normal: requisitos $\to$ diseño $\to$  código $\to$  despliegue.
> 
> *🔍 Ingeniería inversa*
> Proceso inverso: del código o ejecución se obtiene diseño y comprensión estructural.
> 
> *♻️ Reingeniería*
> Combina ingeniería inversa (análisis) con ingeniería directa (reconstrucción) para modificar profundamente el sistema sin alterar sus funcionalidades.

> ---

> **📐 Ciclo de Reingeniería típico**
> 
> 1. **🔎 Análisis** del sistema actual (ingeniería inversa).
> 2. **📋 Redefinición** de objetivos de mejora.
> 3. **🔧 Refactorización o rediseño**.
> 4. **🚀 Reimplementación** y validación.
> 5. **📂 Documentación actualizada** y nuevos entregables.

---

## Conclusión

> **📌 Reflexión final**
> La evolución del software no es opcional, sino **inevitable**. La clave es gestionarla estratégicamente mediante:
> - Buen mantenimiento
> - Evaluación continua del valor y calidad
> - Aplicación oportuna de ingeniería inversa y reingeniería
> 
> **🎯 En lugar de desechar, muchas veces es mejor transformar.**
> Esto reduce riesgos, preserva el valor y alinea el software con las necesidades actuales del negocio.

> ---

> **📚 Recursos recomendados**
> - *SWEBOK* – Software Engineering Body of Knowledge  
> - *IEEE 1219* – Standard for Software Maintenance  
> - *ISO/IEC 14764* – Software Life Cycle Maintenance  

---