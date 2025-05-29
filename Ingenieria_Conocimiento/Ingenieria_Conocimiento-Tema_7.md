---
tags: URJC URJC_IC
---

# Tema 7 - Ingeniería del Conocimiento

---

## ¿Qué es la lógica de descripciones?

> **Lógica de Descripciones**
> Familia de formalismos lógicos utilizados para representar el conocimiento de un dominio mediante conceptos, roles y relaciones, permitiendo realizar razonamientos sobre la estructura y propiedades de los datos.

---

## ALC (Attributive Language with Complements)

> **Descripción de conceptos ALC**
> Sea `C` un conjunto de nombres de conceptos y `R` un conjunto de nombres de roles distinto de `C`, se tiene que:
> - Cada nombre de concepto es concepto ALC.
> - `⊤` y `⊥` son conceptos ALC.
> - Si `C` y `D` son conceptos ALC y `r` es un nombre de rol, entonces también son conceptos ALC:
> 	- `¬C` _negación_
> 	- `C ∩ D` _conjunción_
> 	- `C ∪ D` _disyunción_
> 	- `∃r.C` _restricción existencial_
> 	- `∀r.C` _restricción de valores_
> - Orden de precedencia de operadores como en lógica de primer orden:
> 	- `∃r.C, ∀r.C, ¬ , ∩ , ∪ ; ∃r.C ∩ D ≣ (∃r.C) ∩ D`

> ---

> **Ejemplos Bien Formados**
> - Persona ⊓ Femenino.
> - Persona ⊓ ∃asiste.Curso.
> - A ⊓ ∃r.∀s.(E ⊓ ¬F).
> - Persona ⊓ ∃imparte.(Curso ⊓ ∀matriculadoPor.(Inteligente ⊓ ¬Vago)).
> - Hombre ⊓ ∃tieneHijo.Femenino ⊓ ∃tieneHijo.Masculino ⊓ ∀tieneHij@.(Rico ∪ Feliz).

> **Ejemplos Mal Formados**
> - ∀s.s.
> - Persona ¬ Femenino.
> - Persona ⊓ ∃Curso.

> ---

> **Bases de Conocimientos ALC**
> Normalmente, una Base de Conocimiento se divide en dos partes <T, A>
> 
> _TBox (Terminological KB)_
> Conjunto de axiomas que describen la estructura de un dominio mediante inclusiones `⊆` o equivalencias `≣`.
> 
> _Abox (Assertional KB)_
> Conjunto de axiomas que describen una situación concreta mediante aserción de conceptos `C(a)` o aserción de roles `r(a, b)`.

---

## Inferencia

> **Mecanismos de razonamiento**
> Dada una Base de Conocimiento K = <T, A>, los conceptos C y D, y un individuo a:
> - _Satisfacibilidad_: C es satisfacible
> 	- Si existe un modelo I de T y un `b ∈ Δ con b ∈ C (C ≠ ⌀)`.
> 	- Si algún concepto es insatisfacible y hay algún error de modelado.
> - _Subsunción_: C es subsumido por D (`C ⊆ D` o `T ⊨ C ⊆ D`)
> 	- Si `C ⊆ D` para cada modelo I de T.
> 	- Propiedades
> 		- Reflexiva: `C ⊆ C`.
> 		- Transitiva: Si `C ⊆ D` y `D ⊆ E`, entonces `C ⊆ E`.
> 		- Si `a` es una instancia de `C` y `C ⊆ D`, entonces `a` es una instancia de `D`.
> - _Equivalencia_: C y D son equivalentes (`C ≣ D`).
> 	- Si `C = D` para cada modelo I de T.
> - _DIsjunto_: C y D son disjuntos (`C ⊓ D ≣ ⊥` o `C ⊆ ¬D`).
> 	- Si para cada modelo I de T `C ⊓ D = ⌀`.
> - _Consistencia_: K es consistente
> 	- Si existe algún modelo de `K`.
> - _Instancia_: a es una instancia de C
> 	- Si `a ∈ C` para cada modelo I de T.

> ---

> **Ejemplos**
> - A ⊓ ¬A es insatisfacible.
> - ⊥ y A ⊓ ¬A son equivalentes.
> - ∃r.A ⊓ ∀r.¬A es insatisfacible.
> - A ⊓ B es subsumido por A (A ⊓ B ⊆ A).

---

## ALC como Lógica de primer orden

> **Interpretación**
> - Nombres de conceptos ⇔ Predicados unarios.
> - Nombres de roles ⇔ Predicados binarios.
> - Conceptos ⇔ Fórmulas con una variable libre.

> **Definición de conceptos**
> _π_x(C)_: Función que traduce C de ALC a LPO.
> - π_x(A) = A(x).
> - π_x(¬C) = ¬π_x(C).
> - π_x(C ⊓ D) = π_x(C) ∧ π_x(D).
> - π_x(C ⊔ D) = π_x(C) ∨ π_x(D).
> - π_x(∃r.C) = ∃y(r (x, y) ∧ π_y(C)).
> - π_x(∀r.C) = ∀y(r (x, y) → π_y(C)).