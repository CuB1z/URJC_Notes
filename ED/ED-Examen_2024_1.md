---
tags: URJC URJC_ED
---

# Examen 2024 - Estructura de Datos

---

## Tabla de Contenidos

1. [Caso Práctico 1](#Caso%20Práctico%201)
2. [Caso Práctico 2](#Caso%20Práctico%202)
3. [Problema 2](#Problema%202)
4. [Problema 3](#Problema%203)

---

## Caso Práctico 1

> **📄 Enunciado**
> Te piden completar la implementación de un TAD pila con una operación nueva, `get_num_elems()` que devuelva el número de elementos almacenados.
> 
> Si la complejidad debe ser 0(1), ¿cómo resolverías el problema?
> 
> _✅ Respuesta correcta_
> Modificando la estructura del TAD pila con una variable entera contador inicializada a 0.
> Cuando se mete un elemento en la pila, se incrementa el contador.
> Cuando se saca un elemento de la pila, se decrementa el contador.

---

## Caso Práctico 2

> **📄 Enunciado**
> Supongamos que los elementos `A`, `B`, `C`, `D` y `E` se introducen, en ese orden, en una pila inicialmente vacía.
> 
> A continuación, se extraen cuatro elementos mediante pop(), los cuales a medida que se extraen se insertan en una cola inicialmente vacía.
> 
> Si a continuación se retiran dos elementos de la cola, ¿cuál es el siguiente elemento que se retiraría de la cola?
> 
> _✅ Respuesta correcta_
> El siguiente elemento que se retiraría de la cola sería el elemento `C`.

---

## Problema 2

> **📄 Enunciado**
> Implementar un subprograma `eliminar_valor(C, x)` que elimine todas las ocurrencias de un valor x en una cola de enteros C. Ejemplo: si C = {1, 3, 5, 4, 2, 3, 7, 3, 5}, después de ejecutar el subprograma con x = 3 tendríamos C = {1, 5, 4, 2, 7, 5}.
> 
> El algoritmo debe tener un tiempo de ejecución O(n), siendo n el número de elementos en la cola original, por lo que se sugiere usar una estructura auxiliar.
> 
> El subprograma será externo al TAD ColaEnteros por lo que no conocerá su implementación interna.
> 
> Sí podrás utilizar, sin necesidad de implementarlas, las primitivas del TAD ColaEnteros: `init(C)`, `enqueue(C, x)`, `dequeue(C)`, `is_empty(C)` y `first(C)`.
> 
> _✅ Respuesta correcta_
> 
> ```pascal
> procedure eliminar_valor(var c: TColaEnteros, x: Integer);
> var
> 	current: Integer;
> 	auxC: TColaEnteros;
> begin
> 	init(auxC);
> 	
> 	while (not is_empty(c)) do
> 	begin
> 			current := first(c);
> 			dequeue(c);
> 			if (x <> current) then enqueue(c, current);
> 	end;
> 
> 	c := auxC;
> end;
> ```

---

## Problema 3

> **📄 Enunciado**
> Escribe un subprograma `rotar(var C: TColaEnteros, n: Integer)` que saque n enteros del frente de una cola C y los vuelva a insertar al final.
> 
> Por ejemplo, si C = {1, 3, 5, 2, 4} después de `rotar(C, 3)` debe quedar C = {2, 4, 1, 3, 5}.
> 
> El subprograma será externo al TAD ColaEnteros por lo que no conocerá su implementación interna.
> 
> Sí podrás utilizar, sin necesidad de implementarlas, las primitivas del TAD ColaEnteros: `init(C)`, `enqueue(C, x)`, `dequeue(C)`, `is_empty(C)` y `first(C)`.
> 
> _✅ Respuesta correcta_
> 
> ```pascal
> procedure rotar(var C: TColaEnteros, n: Integer);
> var
> 	x, i: Integer;
> begin
> 	if (not is_empty(C)) then
> 	begin
> 		for i := 1 to n do
> 		begin
> 			x := first(C);
> 			dequeue(C);
> 			enqueue(C, x)
> 		end;
> 	end;
> end;
> ```

---