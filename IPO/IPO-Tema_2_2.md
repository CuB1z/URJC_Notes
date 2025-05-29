---
tags: URJC URJC_IPO
---

# Tema 2.2 - Interacción Persona Ordenador

---

## Tabla de Contenidos

1. [Ventanas](#Ventanas)
2. [Pestañas](#Pestañas)
3. [Operaciones con teclado](#Operaciones%20con%20teclado)
4. [Distribución de elementos](#Distribución%20de%20elementos)
5. [Iconos](#Iconos)
6. [Controles básicos](#Controles%20básicos)
7. [Programación de IUs gráficas](#Programación%20de%20IUs%20gráficas)

---

## Ventanas

> **🪟 Definición y características**  
> Las ventanas son áreas delimitadas en la pantalla que funcionan como espacios independientes donde se muestra información o interfaces para la interacción del usuario. Pueden contener texto, gráficos o ambos.
> 
> - Pueden moverse libremente y cambiar su tamaño según la necesidad.  
> - Se pueden superponer unas sobre otras (solapamiento), lo que permite gestionar múltiples tareas simultáneamente.  
> - Pueden incluir barras de desplazamiento horizontales y verticales para navegar en contenidos más extensos que el área visible.  
> - La barra de título permite identificar la ventana y facilita su manipulación.

> --- 

> **🔍 Problemas y soluciones en la gestión de ventanas**  
> Cuando existen muchas ventanas abiertas, puede resultar complicado para el usuario localizar la que necesita:  
> - **Listing:** Mostrar un listado textual de todas las ventanas activas para seleccionar.  
> - **Iconising:** Minimizar ventanas a iconos representativos para liberar espacio visual.  
> - **Shrinking:** Contraer ventanas para mostrar solo la barra de título o una versión reducida.

> --- 

> **🧩 Tipos de ventanas**  
> - **Principal:** Representa la aplicación en sí misma. Su cierre termina la aplicación.  
> - **Secundarias:** Apoyan funciones específicas dentro de la app.  
> - **Diálogo:** Ventanas temporales que solicitan al usuario información o confirmación para realizar acciones concretas.
> 
> **Importante:**  
> - Los diálogos no deben usarse solo para informar, sino para acciones que requieran interacción.  
> - Evitar diálogos modales innecesarios, pues bloquean la interacción con otras ventanas.

> --- 

> **🔒 Modalidad**  
> - **Ventanas modales:** Impiden el uso de otras ventanas de la aplicación hasta ser cerradas. Útiles para asegurar que el usuario atienda una acción importante (ejemplo: confirmación de borrado).  
> - **Ventanas no modales:** Permiten cambiar libremente entre ventanas, favoreciendo multitarea.

---

## Pestañas

> **📑 Función y uso**  
> Las pestañas permiten organizar contenido relacionado dentro de una misma ventana o diálogo, facilitando la clasificación y acceso rápido.  
> - Cada pestaña representa un conjunto de información o propiedades independiente.  
> - Se deben usar con moderación para evitar saturar la interfaz y confundir al usuario.  
> - Se recomienda ordenar las pestañas según la prioridad o frecuencia de uso.

---

## Operaciones con teclado

> **⌨️ Interacción y recomendaciones**  
> Para mejorar la accesibilidad y eficiencia en la navegación, las interfaces deben incorporar:  
> - **Mnemotécnicos:** Letra subrayada que se activa con `ALT + letra`. Facilitan la activación rápida de opciones del menú.  
> - **Atajos (shortcuts):** Combinaciones de teclas que ejecutan comandos comunes sin necesidad de usar el ratón.  
> - **Navegación completa:** Todo debe ser accesible desde el teclado.

> --- 

> **🔠 Mnemotécnicos**  
> - Deben elegirse letras sin conflicto, priorizando la primera letra del elemento.  
> - En caso de conflicto, elegir otras letras distintivas (vocales o consonantes).  
> - No repetir mnemotécnicos dentro del mismo menú para evitar confusión.

> --- 

> **🔢 Navegación del foco**  
> - El foco indica el componente activo donde se aplican las acciones del usuario.  
> - La tecla `Tab` mueve el foco hacia adelante, `Shift + Tab` hacia atrás.  
> - `Alt + Tab` cambia entre ventanas abiertas del sistema operativo.  
> - Es fundamental que el foco inicial esté en el componente más lógico para empezar la interacción (usualmente la esquina superior izquierda).

---

## Distribución de elementos

> **🧱 Organización y principios de diseño**  
> La disposición de los elementos en la IU debe:  
> - Priorizar las funciones más importantes en la ventana principal.  
> - Agrupar datos y funciones relacionados para facilitar su uso conjunto.  
> - Seguir criterios lógicos, como:  
>   - Elementos usados simultáneamente juntos.  
>   - Objetivos comunes.  
>   - Manipulación de datos del mismo tipo.  
>   - Elementos que se modifican o controlan mutuamente.

> --- 

> **📐 Áreas dentro de la ventana**  
> - Para organizar visualmente, se divide la ventana en áreas usando:  
>   - Líneas divisorias, colores o tipos de letra diferentes.  
>   - Objetos contenedores que agrupan componentes y definen la estructura.

---

## Iconos

> **🔷 Propósito y características**  
> - Mejoran la usabilidad al hacer los comandos y objetos fáciles de reconocer y recordar.  
> - Deben ser simples, claros y compactos para no saturar la pantalla.  
> - Pueden representar aplicaciones, herramientas, acciones o documentos.

> --- 

> **🎨 Tipos de representación gráfica**  
> - **Similares:** Iconos que se parecen al objeto real (ej. carpeta para archivos).  
> - **Análogos:** Iconos que representan acciones mediante símbolos (ej. tijeras para cortar).  
> - **Arbitrarios:** Símbolos convencionales que no tienen relación directa con el objeto (ej. X para borrar).

> --- 

> **⚠️ Consideraciones para diseño de iconos**  
> - Reutilizar iconos existentes cuando sea posible para consistencia.  
> - Añadir etiquetas junto a iconos pequeños para facilitar la identificación.  
> - Evitar iconos complejos que dificulten la rápida comprensión.

---

## Controles básicos

> **📋 Menús**  
> - Contienen ítems breves que representan comandos u opciones (copiar, pegar, abrir, etc.).  
> - Deben incluir mnemotécnicos y shortcuts consistentes con el sistema operativo para facilitar el uso.  
> - Usar (...) para indicar que el comando requiere información adicional (ej. "Guardar como...").  
> - Restringir visualmente opciones no disponibles para evitar confusión.  
> - Organizar con separadores para agrupar opciones relacionadas.  
> - Menús comunes: Archivo, Edición, Formato, Ver, Ayuda.

> --- 

> **🛠️ Barra de herramientas (Toolbar)**  
> - Proporciona acceso rápido a comandos frecuentes mediante botones y otros controles (combo boxes, campos de texto).  
> - Cuando no acompañan menús, deben incluir etiquetas o texto para accesibilidad.  
> - Se recomienda usar tooltips para describir la función de cada botón.

> --- 

> **🔘 Botones**  
> - Pueden incluir texto, iconos o ambos para indicar su función.  
> - Botón por defecto se activa con `Enter` y representa la acción principal.  
> - Botón de cancelación se activa con `Esc` y cancela la acción en curso.  
> - Botones de conmutación representan estados on/off y pueden agruparse para opciones independientes o exclusivas.  
> - Botones de verificación permiten seleccionar múltiples opciones no excluyentes (checkboxes).  
> - Botones de selección permiten seleccionar solo una opción dentro de un grupo (radio buttons).

> --- 

> **📃 Listas**  
> - Permiten mostrar conjuntos de opciones en texto o gráfico.  
> - Pueden ser listas fijas o desplegables.  
> - Se recomienda mostrar entre 3 y 8 opciones para mantener la claridad.  
> - Son útiles para opciones variables y permiten selección simple o múltiple.

> --- 

> **✍️ Componentes de texto**  
> - Incluyen etiquetas (solo lectura), campos de texto de una línea o varias líneas para entrada o visualización.  
> - Para información breve y fija usar etiquetas o texto de una línea.  
> - Para textos largos o comentarios, usar campos de texto multilinea.  
> - Si el texto es no editable, cambiar el color de fondo para indicar el estado.

> --- 

> **💡 Tooltips**  
> - Proporcionan información contextual adicional al usuario al posicionar el cursor sobre un elemento.  
> - Mejoran la comprensión sin saturar la IU con texto permanente.

---

## Programación de IUs gráficas

> **🛠️ Herramientas y tecnologías recomendadas**  
> - **JustinMind** y **Figma** para prototipado visual rápido y colaborativo.  
> - La programación web con HTML, CSS y JavaScript ofrece flexibilidad y accesibilidad multiplataforma.  
> - Se desaconseja el uso de Swing (Java) para proyectos modernos debido a su complejidad y limitaciones visuales.

---