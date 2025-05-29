---
tags: URJC URJC_ED
---

# Tema 1 - Estructuras de Datos

---

## Tabla de Contenidos

1. [Abstracción](#Abstracción)
2. [Tipos de Datos](#Tipos%20de%20Datos)
3. [Memoria Dinámica](#Memoria%20Dinámica)
4. [Punteros](#Punteros)
5. [Procedimientos y Funciones con Punteros](#Procedimientos%20y%20Funciones%20con%20Punteros)

---

## Abstracción

> **❓ ¿Qué es la abstracción?**  
> Proceso mental mediante el cual el ser humano extrae las características esenciales de algo, ignorando los detalles que no son fundamentales.
> 
> Es esencial para modelar el mundo real de manera efectiva, sin perderse en aspectos innecesarios que no afectan al objetivo principal.

> ---

> **🖤 Caja Negra**  
> Estudio del comportamiento de un sistema sin considerar su funcionamiento interno, solo observando lo que es visible desde el exterior.
>  
> Esto permite centrarse en cómo interactuar con el sistema sin preocuparse de los detalles internos.

> ---

> **💊 Encapsulamiento**  
> El encapsulamiento es el proceso de ocultar los detalles internos de una abstracción.
> 
> En programación, esto es fundamental para la reutilización de código. Al ocultar los detalles de implementación de un módulo o programa, pero dejando disponible una interfaz pública para interactuar con él, el código puede ser reutilizado en distintos contextos.
> 
> Además, el encapsulamiento protege el estado interno de la abstracción y previene el uso no deseado del objeto, garantizando que solo se acceda a él a través de las operaciones definidas en su interfaz.

> ---

> **📱 Interfaz**  
> La interfaz es el conjunto de elementos que permiten interactuar con un objeto tratado como una caja negra.
>  
> Es el medio por el cual los objetos se comunican entre sí, sin necesidad de conocer sus detalles internos.

> ---

> **📜 Contrato**  
> El contrato es una metáfora que describe cómo los elementos de un sistema de software colaboran sobre la base de obligaciones y beneficios mutuos explícitos, similares a un contrato en el mundo real (según B. Meyer).
>   
> El diseñador del sistema pone a disposición ciertos componentes a través de la interfaz y oculta los detalles internos, sin preocuparse por posibles usos incorrectos.
>  
> El usuario del sistema usa esos componentes garantizando ciertas salidas y se enfoca en resolver su problema. Este enfoque permite cambiar la implementación interna sin afectar el uso del sistema.

---

## Tipos de Datos

> **🔢 Clasificación de los Tipos de Datos**
> 
> Los tipos de datos se pueden clasificar en dos grandes categorías:
> 
> 1. **Predefinidos**
> 	Son los tipos de datos que se utilizan comúnmente en la programación, ya que están definidos por el lenguaje.
>    - *Simples*
>      Por ejemplo, `Integer`, `Real`, `Boolean`, `Char`.
>    - *Estructurados*
>      Como `String`, que se usa para almacenar cadenas de texto.
> 
> 2. **Definidos por el usuario**
>    Son tipos de datos creados por el programador utilizando herramientas del lenguaje.
>	- *Simples*
>	  Como los tipos `Subrango`, `Enumerado` o `Puntero`.
>	- *Estructurados*
>	  Incluyen tipos como `Conjunto`, `Array`, `Registro`, y `Archivo`.
> 
> **🖥️ Ejemplo en Pascal**
> ```pascal
> type
>   TColor = (Red, Green, Blue);
>   TArrayEnteros = array[1..10] of Integer;
> ```

> ---

> **⚙️ Especificación de Tipos Simples**
> 
> Los mecanismos de construcción de tipos en los lenguajes de programación tienen dos limitaciones importantes:
> 
> 1. *Solo modelan estructura, no comportamiento*
> Este aspecto se resuelve en la programación orientada a objetos (POO) mediante las clases, que no solo definen la estructura, sino también el comportamiento del tipo.
> 
> 2. *Limitación a los tipos disponibles en el lenguaje*
> Sin embargo, los punteros pueden ayudar a superar esta limitación, permitiendo la creación de estructuras más complejas como diccionarios, pilas, colas y listas.
> 
> **🖥️ Ejemplo en Pascal**
> ```pascal
> var
>   P: ^Integer;
> begin
>   New(P);
>   P^ := 10;
>   WriteLn(P^);
> end.
> ```

> ---

> **🔒 Tipo de Datos como Abstracción**
> 
> Los tipos de datos pueden considerarse **abstracciones**, en las cuales cada elemento del tipo está sujeto a un contrato que define su comportamiento.
> 
> **Ejemplo Booleanos**
> 
> | Atributo          | Booleanos           |
> |------------------|---------------------|
> | Nombre           | `boolean`           |
> | Valores posibles | `true`, `false`     |
> | Operaciones      | `and`, `or`, `not`  |
> | Uso de otros tipos | No, solo booleanos |
> 
> ```pascal
> var
>   b: Boolean;
> begin
>   b := True and False;  // Operación booleana
>   WriteLn(b);  // Imprime False
> end.
> ```
> 
> ---
> 
> **Ejemplo Array de Enteros**
> 
> | Atributo          | Array de enteros     |
> |------------------|----------------------|
> | Nombre           | `array of integer`   |
> | Valores posibles | Infinitos, depende del tamaño del array |
> | Operaciones      | Cambiar elemento, consultar elemento, consultar tamaño, etc. |
> | Uso de otros tipos | Sí, en este caso son enteros |
> 
> ```pascal
> var
>   A: array[1..5] of Integer;
> begin
>   A[1] := 10;
>   A[2] := 20;
>   WriteLn(A[1]);  // Imprime 10
>   WriteLn(Length(A));  // Imprime 5
> end.
> ```

> ---

> **📝 Especificación de un Tipo de Datos**
> 
> La especificación de un tipo de datos describe lo que un cliente (quien utilizará el tipo) debe conocer sobre el tipo de datos. Es el **contrato** entre el tipo de datos y el usuario.
> 
> **🔑 Composición**
> 
> 1. *Signatura*
>
> | Componente             | Descripción                                           |
> |------------------------|-------------------------------------------------------|
> | Nombre del tipo     | Ejemplo: `integer`, `boolean`                         |
> | Operaciones         | Ejemplo: `+`, `-`, `and`, `or`, etc.                  |
> | Argumentos          | Los parámetros que reciben las operaciones (ej. dos números para `+`) |
> | Resultados          | El valor que devuelve la operación (ej. el resultado de sumar dos números) |
> 
> 2. *Axioma*
> Detalla cómo se comportan las operaciones sobre el tipo de datos.
> 
> **🔜 Más detalles sobre esto se cubrirán más adelante.**

---

## Memoria Dinámica

> **🧠 Memoria Dinámica**
> 
> La memoria dinámica se refiere a la memoria que se gestiona en tiempo de ejecución, es decir, durante la ejecución del programa, el espacio de memoria se puede solicitar y liberar dinámicamente según sea necesario.
> 
> **⚙️ Gestión de Memoria**
> 
> 1. *📦 Estructuras Estáticas*
> 	Las estructuras de datos estáticas tienen un tamaño fijo durante la ejecución del programa. Un ejemplo de este tipo de estructura es el _array_.
>  
> 	 Las limitaciones que presentan las estructuras estáticas son varias. En primer lugar, no es posible cambiar el tamaño de la estructura en tiempo de ejecución, lo que limita su flexibilidad.
>      
> 2. *🔄 Estructuras Dinámicas*
>	Las estructuras de datos dinámicas tienen la capacidad de cambiar su tamaño durante la ejecución del programa. Esta flexibilidad les permite adaptarse a situaciones donde no se conoce de antemano cuántos elementos se van a manejar.
>	
>	Las estructuras dinámicas son gestionadas mediante punteros, lo que permite crear y destruir estructuras a medida que se necesiten, sin que sea necesario definir un tamaño fijo en el momento de la compilación.
> 
> **📚 Ejemplo en Pascal**
> ```pascal
> PROGRAM Memoria;
> VAR
>   precio: real;
> FUNCTION CalculoIVA(p: real): real;
> BEGIN
>   CalculoIVA := p * 0.21;
> END;
> BEGIN
>   precio := 200.25;
>   WriteLn('El IVA es: ', CalculoIVA(precio));
> END.
> ```

> ---

> **💾 Stack o Pila**
> La **pila** se usa para la memoria local de los subprogramas. Cada proceso tiene su propia pila, que generalmente tiene un tamaño limitado.
> 
> **🧑‍💻 Heap o Montículo**
> El **heap** es donde se almacena la memoria dinámica. A diferencia de la pila, la memoria del heap es mucho más grande y su gestión es manual.
> 
> **🔑 Definición del Problema**
> 
> En muchos casos, no sabemos cuánto espacio de memoria necesitaremos ni cómo se organizarán los datos al principio del programa. Por ello, utilizamos estructuras de datos dinámicas que se gestionan durante la ejecución del programa.

---

## Punteros

> **📍 Punteros**
> 
> Los punteros en son variables que almacenan direcciones de memoria, permitiendo la manipulación directa de la memoria. Se utilizan para crear estructuras de datos dinámicas y gestionar memoria de manera más eficiente.
> 
> **Operaciones básicas con punteros:**
> `New` $\to$ Asigna memoria para una variable de tipo puntero.
> `Dispose` $\to$ Libera la memoria previamente asignada a un puntero.
> `^` $\to$ El operador se utiliza para acceder al valor almacenado en la dirección de memoria que apunta el puntero.
> 
> **🖥️ Ejemplo en Pascal**
> ```pascal
> VAR
>   P: ^Integer;
> BEGIN
>   New(P);  
>   P^ := 10; 
>   WriteLn(P^); 
>   Dispose(P); 
> END.
> ```
> 
> En **Pascal**, el valor `NIL` representa un puntero nulo, es decir, un puntero que no apunta a ninguna posición de memoria válida. Se utiliza para indicar que una variable de puntero aún no ha sido asignada o que se ha liberado la memoria que apuntaba.
> 
> `NIL` es una constante especial que se asigna a punteros para indicar que no están apuntando a ninguna ubicación de memoria válida.
> - **Seguridad**: Asignar un puntero a `NIL` ayuda a evitar errores al intentar acceder a áreas de memoria no válidas, proporcionando una "dirección segura".

> ---

> **🛑 Problemas en la Gestión de Memoria Dinámica**
> 
> El **heap** tiene una capacidad finita de espacio reservado para crear memoria dinámica, lo que significa que se debe gestionar cuidadosamente la memoria asignada. Si no se libera correctamente, pueden surgir problemas graves:
> 
> *⚠️ Sobrescritura de memoria*
> Si el montículo (heap) y la pila (stack) se encuentran, pueden sobrescribirse mutuamente, lo que corrompe partes de la memoria, afectando el funcionamiento de los programas y del sistema operativo.
> 
> *❌ Bloqueo del sistema operativo*
> En casos extremos, el sistema operativo puede bloquearse debido a la falta de espacio en el heap.
> 
> *💥 Memory leaks*
> En situaciones menos graves, la falta de liberación de memoria produce fugas de memoria (memory leaks), lo que reduce la disponibilidad de memoria para otros procesos y puede hacer que el sistema funcione de manera ineficiente.
> 
> **💡 Solución moderna: Recolector de basura**
> Los lenguajes modernos, como Java o Python, incluyen un recolector de basura que automáticamente gestiona la memoria, liberando los bloques que ya no se utilizan. Sin embargo, este enfoque no está disponible en **Pascal**.

---

## Procedimientos y Funciones con Punteros

> **📍 Modificación de Punteros dentro de Procedimientos**
> Si intentamos cambiar la dirección de memoria que contiene el puntero dentro del procedimiento:
> 
> ```pascal
> PROCEDURE miProc(dato: tPtrRegistro);
> BEGIN
>   dato^.iniciales := 'NRU';
>   dato := NIL;  // El puntero local 'dato' ahora es NIL
> END;
> ```
> 
> Aunque `dato` cambia el valor del campo `iniciales` a `NRU`, el puntero original (`pRegistro`) no se ve afectado por la asignación de `NIL`.

> ---

> **🛠️ Paso por Referencia de Punteros**
> Si el puntero se pasa por referencia, podemos modificar tanto el valor apuntado como la dirección de memoria que contiene el puntero:
> 
> ```pascal
> PROCEDURE miProc(var dato: tPtrRegistro);
> BEGIN
>   dato^.iniciales := 'NRU';
>   dato := NIL;  // Cambia la dirección del puntero original
> END;
> ```
> 
> La modificación en el campo `iniciales` se refleja en el puntero original, y también el puntero original se asigna a `NIL`.

---