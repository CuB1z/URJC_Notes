---
tags: URJC URJC_EAS
---

# Tema 2 - Evolución y Adaptación Software

---

## Tabla de Contenidos

1. [Leyes de la Evolución del Software](#Leyes%20de%20la%20Evolución%20del%20Software)
2. [Tipos de Sistemas de Lehman](#Tipos%20de%20Sistemas%20de%20Lehman)
3. [Las 8 Leyes de Lehman](#Las%208%20Leyes%20de%20Lehman)
4. [Reflexión Final](#Reflexión%20Final)

---

## Leyes de la Evolución del Software

> **📘 Origen y Propósito**
> Formuladas inicialmente por *Meir M. Lehman* y *László Belady* en 1974, y revisadas en varias ocasiones posteriores (1978, 1980, 1991, 1997).
> Estas leyes tratan de explicar cómo y por qué evoluciona el software a lo largo de su vida útil, especialmente el software que interactúa con el mundo real (sistemas tipo-E).
> 
> En resumen, las leyes:
> - Describen fuerzas impulsoras y restrictivas del cambio.
> - Reflejan el impacto del entorno cambiante sobre el software.
> - Enfatizan la necesidad de adaptación continua.

---

## Tipos de Sistemas de Lehman

> **🧩 Tipo S (Specified)**
> Sistemas construidos a partir de una especificación exacta. El comportamiento está definido completamente. Ejemplo: una librería matemática que cumple con un estándar.

> ---

> **📐 Tipo P (Procedural)**
> Sistemas cuya funcionalidad se deriva de la interacción entre procedimientos definidos, pero cuyo comportamiento global no está especificado en detalle. Ejemplo: programas que juegan ajedrez.

> ---

> **🌍 Tipo E (Evolving)**
> Sistemas inmersos en el mundo real. Su comportamiento depende del entorno en el que operan y deben adaptarse continuamente a sus cambios. Son los sistemas a los que aplican las leyes de Lehman.

---

## Las 8 Leyes de Lehman

> **⚙️ 1. Ley del Cambio Continuo**
> *"Todo sistema tipo-E debe ser adaptado de manera continua o se vuelve menos útil con el tiempo."*
> 
> El entorno cambia constantemente. Si el software no evoluciona, pierde relevancia.
> 
> Ejemplo: un sistema bancario que no se adapta a nuevas regulaciones queda obsoleto.

> ---

> **📈 2. Ley de la Complejidad Creciente**
> *"La complejidad del sistema tiende a aumentar a medida que evoluciona, a menos que se realicen esfuerzos para controlarla."*
> 
> Cada nueva funcionalidad o cambio introduce más dependencias. El código se hace más difícil de entender y mantener.

> ---

> **🔁 3. Ley de la Auto-Regulación**
> *"La evolución de sistemas tipo-E sigue un proceso autorregulado."*
> 
> La evolución tiene sus propios mecanismos de control (gestión, planificación, revisión) que estabilizan el crecimiento. Las métricas de proceso/producto tienden a seguir distribuciones normales.

> ---

> **🏃‍♂️ 4. Ley de la Estabilidad Organizacional**
> *"La tasa de actividad global en el mantenimiento/evolución del sistema permanece constante a lo largo del tiempo."*
> 
> Por más que se agregue personal o recursos, existen límites organizacionales y de gestión que tienden a mantener estable el ritmo de evolución.

> ---

> **👥 5. Ley de la Familiaridad**
> *"Durante la evolución, el ritmo de crecimiento funcional debe ser constante para que los desarrolladores mantengan familiaridad con el sistema."*
> 
> Cambios demasiado grandes dificultan la comprensión, provocando errores y afectando la calidad.

> ---

> **📤 6. Ley del Crecimiento Continuo**
> *"Para satisfacer las expectativas de los usuarios, la funcionalidad del sistema debe incrementarse continuamente."*
> 
> Los usuarios siempre esperan más funcionalidades. No basta con mantener el sistema: hay que mejorarlo.

> ---

> **📉 7. Ley de la Calidad Decreciente**
> *"A menos que se mantenga cuidadosamente, la calidad percibida del sistema disminuirá con el tiempo."*
> 
> Aunque el sistema funcione correctamente, si no se adapta, parecerá viejo y será visto como de menor calidad.

> ---

> **🔄 8. Ley del Sistema de Retroalimentación**
> *"La evolución del software debe tratarse como un sistema de retroalimentación multilateral, con múltiples agentes y lazos."*
> 
> Las decisiones de cambio generan nuevos efectos que a su vez necesitan ajustes. La evolución es un proceso iterativo, no lineal.

---

## Reflexión Final

> **🧠 Observaciones Clave**
> - Las leyes no son reglas estrictas, sino observaciones empíricas.
> - Se basan en estudios reales (como el sistema OS/360 de IBM).
> - Ayudan a entender el comportamiento y los desafíos del mantenimiento y evolución de software en entornos reales.
> - Son aplicables más allá de lo técnico: afectan organización, gestión y economía del software.

---