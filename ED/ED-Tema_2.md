---
tags: URJC URJC_ED
---

# Tema 2 - Estructuras de Datos

---

## Tabla de Contenidos

1.  [Definición de TAD](#Definición%20de%20TAD)
2. [Operaciones de los TADs](#Operaciones%20de%20los%20TADs)
3. [Especificación de los TADs](#Especificación%20de%20los%20TADs)
4. [Ejemplo de TAD: Semáforo](#Ejemplo%20de%20TAD%20Semáforo)
5. [Ejemplo de TAD: Contador](#Ejemplo%20de%20TAD%20Contador)
6. [Implementación de TAD en Pascal](#Implementación%20de%20TAD%20en%20Pascal)
7. [Beneficios del uso de TADs](#Beneficios%20del%20uso%20de%20TADs)

---

## Definición de TAD

> **❓ ¿Qué es un TAD?**  
> Un Tipo Abstracto de Datos (TAD) es una descripción de alto nivel de una colección de datos y de las operaciones que se pueden realizar sobre ella. Define la estructura de datos con un conjunto de reglas y comportamientos sin especificar la implementación real.
> 
> Es esencial que un TAD sea independiente de su implementación.

> ---

> **📦 Ejemplo de TAD**  
> Un ejemplo común es la **cola de espera**, que permite operaciones como: entrar, salir, consultar si está vacía, ver cuál es el primero y el último. Internamente, puede implementarse de varias formas, pero su comportamiento siempre será el mismo externamente.

---

## Operaciones de los TADs

> **🔧 Tipos de operaciones**  
> Las operaciones de un TAD se pueden clasificar en:
> 
> 1. **Creación**: Permiten inicializar y obtener nuevos objetos del tipo. En programación orientada a objetos (POO), se conocen como constructores.
> 2. **Modificación**: Permiten realizar cambios en el estado interno de un objeto del tipo.
> 3. **Consulta**: Extraen información del TAD.
> 4. **Propias del TAD**: Operaciones entre los elementos del tipo que no están definidas para otros tipos, por ejemplo, el determinante de una matriz.

> ---

## Especificación de los TADs

> **📝 Especificación de un TAD**  
> Para definir un TAD se emplea una especificación que debe ser independiente de cualquier implementación. Se puede realizar en lenguaje natural, especificación algebraica o lenguajes formales. La especificación separa el comportamiento esperado del TAD de su implementación concreta.

> ---

> **📋 Especificación en lenguaje natural**  
> Para la especificación en lenguaje natural, se deben definir:
> - Nombre del TAD
> - Valores posibles
> - Operaciones disponibles (algunas con restricciones mediante precondiciones)
> - Uso de otros tipos de datos

---

## Ejemplo de TAD: Semáforo

> **🚦 Semáforo**  
> - **Valores posibles**: rojo, verde.
> - **Operaciones**:
>   - `abrir()`: pone el valor interno a verde.
>   - `cerrar()`: pone el valor interno a rojo.
>   - `esta_abierto()`: retorna verdadero o falso según el valor interno.
> 
> **📋 Especificación en Pascal**  
> ```pascal
> PROCEDURE abrir();
> BEGIN
>   valorInterno := verde;
> END;
> 
> PROCEDURE cerrar();
> BEGIN
>   valorInterno := rojo;
> END;
> 
> FUNCTION esta_abierto(): Boolean;
> BEGIN
>   IF valorInterno = verde THEN
>     RETURN True
>   ELSE
>     RETURN False;
> END;
> ```

---

## Ejemplo de TAD: Contador

> **🔢 Contador**  
> - **Valores posibles**: enteros positivos.
> - **Operaciones**:
>   - `inicializar()`: pone el valor interno a cero.
>   - `incrementar()`: suma 1 al valor interno.
>   - `obtener_valor()`: retorna el valor interno.
>   - `decrementar()`: disminuye 1 al valor interno (precondición: no puede ser cero).
> 
> **📋 Especificación en Pascal**  
> ```pascal
> PROCEDURE inicializar();
> BEGIN
>   valorInterno := 0;
> END;
> 
> PROCEDURE incrementar();
> BEGIN
>   valorInterno := valorInterno + 1;
> END;
> 
> FUNCTION obtener_valor(): Integer;
> BEGIN
>   RETURN valorInterno;
> END;
> 
> PROCEDURE decrementar();
> BEGIN
>   IF valorInterno > 0 THEN
>     valorInterno := valorInterno - 1;
> END;
> ```

---

## Implementación de TAD en Pascal

> **💻 Implementación en Pascal**  
> Para implementar un TAD en Pascal, utilizamos unidades (unit) que contienen una parte de interfaz pública y otra de implementación privada. La interfaz define las operaciones disponibles, mientras que la implementación es interna y no es accesible desde fuera de la unidad.

> ---

> **🔑 Ejemplo de uso de TAD en Pascal**  
> Para usar la unidad en un programa, se añade la cláusula `USES nombre_de_la_unidad` y se hace uso de las operaciones definidas en la interfaz pública de la unidad.

---

## Beneficios del uso de TADs

> **🎯 Ventajas del uso de TADs**  
> El uso de TADs promueve la separación de tareas en un programa. El programa que usa el TAD solo necesita conocer la interfaz del TAD y no los detalles de su implementación. Esto hace que el código sea más sencillo de mantener, más reutilizable y más legible.

> ---

> **🔄 Mantenimiento y reutilización**  
> Al emplear TADs, se facilita el mantenimiento del código, ya que los cambios en la implementación de un TAD no afectan al código cliente que lo utiliza. Además, los TADs permiten reutilizar código probado y mejorar la calidad del software.

---