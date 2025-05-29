---
tags: URJC URJC_SO
---

# Tema 2 - Sistemas Operativos

---

## Tabla de Contenidos

1. [¿Qué es un sistema operativo?](#¿Qué%20es%20un%20sistema%20operativo?)
3. [Estructura y funcionamiento del computador](#Estructura%20y%20funcionamiento%20del%20computador)
4. [Servicios del sistema operativo](#Servicios%20del%20sistema%20operativo)
5. [Diseño e implementación](#Diseño%20e%20implementación)
6. [Estructura y funcionamiento del sistema operativo](#Estructura%20y%20funcionamiento%20del%20sistema%20operativo)

---

## ¿Qué es un sistema operativo?

> **Sistema Operativo**
> Un sistema operativo (S.O) es un programa que actúa como intermediario entre el usuario y el hardware de un computador. Usualmente se le denomina _kernel_ o núcleo.  
> 
> El S.O proporciona al programador una serie de abstracciones que le permiten acceder al hardware de forma sencilla.  
> 
> *Objetivos del sistema operativo*
> - Gestionar la ejecución de los programas del usuario.  
> - Hacer que el computador sea cómodo de usar.  
> - Utilizar los recursos del computador de forma eficiente.  
> 
> *Tareas del sistema operativo*
> - Comunicación con los periféricos.  
> - Administración de recursos.  
> - Coordinación de procesos simultáneos (multiproceso y multitarea).  
> - Gestión de memoria.  
> - Gestión de datos, comunicaciones y redes.  

> ---

> **Componentes de un sistema informático**  
> Un sistema informático está compuesto por los siguientes elementos:  
> 
> *Usuarios*
> Utilizan los recursos del sistema para satisfacer sus necesidades.
> 
> *Programas*
> Aplicaciones que usan los recursos del computador para resolver problemas específicos.
> 
> *Sistema Operativo (S.O)*
> Coordina el uso del hardware entre varios programas y usuarios.
> 
> *Hardware*
> Proporciona los recursos de cómputo, como el procesador, memoria y dispositivos de entrada/salida.  

> ---

> **Punto de vista del usuario**  
> El tipo de computador determina cómo el sistema operativo optimiza la experiencia del usuario:  
> 
> *Computadores personales*  
> Diseñados para un único usuario en el que el S.O se enfoca en la facilidad de uso.  
> 
> *Dispositivos móviles*  
> Presentan limitaciones en alimentación, velocidad e interfaz, priorizando la usabilidad y el consumo eficiente de recursos.  
> 
> *Computadores compartidos (mainframes, servidores, etc.)*  
> Admiten varios usuarios simultáneamente, ya que el S.O maximiza el uso de recursos y los distribuye equitativamente.

> ---

> **Punto de vista del programador**  
> Desde la perspectiva del programador, el sistema operativo simplifica el acceso al hardware al proporcionar abstracciones útiles:  
> 
> *Acceso simplificado*  
> En lugar de gestionar directamente aspectos como las direcciones de bloques en un disco duro o los códigos de estado y errores, el S.O proporciona funciones estándar.  
> 
> *Funciones estándar*  
> - Abrir un archivo.  
> - Leer o escribir datos en un archivo.  
> - Cerrar un archivo.  

---

## Estructura y funcionamiento del computador

> **Arranque y funcionamiento del computador**  
> El arranque y funcionamiento del computador son esenciales para iniciar y operar el sistema:  
> 
> *Programa de arranque*  
> - Ejecutado al encender o reiniciar el computador, almacenado en ROM como firmware.  
> - Inicializa registros, controladoras y memoria, carga el kernel desde el disco y lo ejecuta.  
> 
> *Funcionamiento del computador*  
> - Los dispositivos de E/S y CPUs operan en paralelo, gestionados por controladoras (_controllers_) con buffers locales.  
> - Las interrupciones informan a la CPU cuando los dispositivos completan tareas.  
> - La CPU atiende interrupciones mediante una rutina específica, preservando registros y el estado del procesador.  
> - El kernel coordina estas operaciones para garantizar la continuidad del sistema.  

> ---

> **Estructura de almacenamiento**  
> El sistema operativo administra la memoria principal y la memoria secundaria:  
> 
> *Memoria principal*  
> Único medio de almacenamiento que el procesador puede acceder directamente y en el que los programas deben estar para ser ejecutados.
> 
> *Memoria secundaria*  
> Proporciona almacenamiento no volátil de gran capacidad y es utilizada para guardar datos y programas que no están en uso activo.

> ---

> **Modo dual**  
> El modo dual protege al sistema operativo y separa las operaciones críticas de las de usuario:  
> 
> *Características del modo dual*  
> El procesador tiene dos modos de funcionamiento: *Modo Usuario (1)* y *Modo kernel (0)*.
> 
> *Llamadas al sistema*  
> Interfaz que permite a los programas de usuario acceder de manera segura a recursos y funcionalidades del sistema.  
> 
> *Rings de protección*  
> Las CPUs x86 utilizan niveles adicionales de privilegio denominados _rings_:  
>   - **Ring 0**: Nivel más alto de privilegio (modo kernel).  
>   - **Ring 3**: Corresponde al modo usuario.  
>   - **Ring 1 y 2**: Usados ocasionalmente, principalmente en virtualización.  

> ---

> **Multiprogramación y Tiempo Compartido**  
> Estos conceptos optimizan el uso de recursos en sistemas informáticos, mejorando el rendimiento y la experiencia del usuario.
> 
> *Multiprogramación*  
> - Mejora la eficiencia compartiendo los recursos entre múltiples trabajos.  
> - Si un trabajo está en espera (p. ej., por una operación de E/S), otro puede ejecutarse inmediatamente.  
> - Mantiene el procesador ocupado la mayor parte del tiempo.  
> 
> *Tiempo compartido*  
> - Extiende la multiprogramación para permitir interacción simultánea con varios procesos.  
> - Asigna un tiempo máximo de ejecución a cada proceso (planificación de CPU).  
> - Los cambios rápidos entre procesos dan la sensación de ejecución simultánea.
> - Permite que múltiples usuarios utilicen el sistema de forma concurrente.

---

## Servicios del sistema operativo

> **Servicios del sistema operativo**  
> Los sistemas operativos ofrecen servicios tanto para los usuarios como para garantizar la eficiencia del sistema:  
> 
> *Servicios útiles para los usuarios*
> 
> | Servicios                | Descripción                                                                 |
> | ------------------------ | ------------------------------------------------------- |
> | Interfaz de usuario (UI) | Línea de comandos (CLI), interfaz gráfica (GUI), proceso por lotes (batch). |
> | Ejecución de programas   | Facilita la ejecución de aplicaciones.                      |
> | Operaciones de E/S       | Gestiona las interacciones entre el hardware y el software. |
> | Manipulación de archivos | Creación, eliminación y organización de archivos.           |
> | Comunicaciones           | Gestión de la comunicación entre procesos y sistemas.       |
> | Detección de errores     | Identificación y respuesta a problemas del sistema.         |
> 
> *Funciones internas para la eficiencia del sistema:*  
> 
> | Función                   | Descripción                                                          |
> | ------------------------- | -------------------------------------------------------------------- |
> | Asignación de recursos     | Distribución de CPU, memoria y dispositivos entre procesos.          |
> | Contabilidad               | Registro del uso de recursos del sistema.                            |
> | Protección y seguridad     | Control del acceso a los recursos para prevenir errores y accesos no autorizados. |


> ---

> **Interfaz de usuario**  
> La interfaz de usuario permite interactuar con el sistema operativo:  
> 
> *Interfaz modo texto (Shell)*  
> Interpreta y ejecuta mandatos introducidos por el usuario.
> 
> *Interfaz gráfica (GUI)*  
> Utiliza ventanas y periféricos como teclado, ratón o pantallas multitáctiles.  

> ---

> **Llamadas al sistema**  
> Las llamadas al sistema son una interfaz de programación para acceder a los servicios del sistema operativo (generalmente escritas en lenguajes cercanos a la máquina C o C++).
> 
> Los programadores utilizan APIs de alto nivel en lugar de llamadas directas. Algunas APIs comunes son *Win32 API (Windos)* o *POSIX (UNIX, GNU/Linux y macOS)*.
> 
> **Implementación de llamadas al sistema**
> Cada llamada está asociada a un número en una tabla indexada.
> 
> La interfaz de llamadas invoca al sistema operativo y devuelve el estado y los valores de retorno de manera que los programadores solo necesitan la API, sin preocuparse por los detalles internos.  
> 
> **Categorías principales de llamadas al sistema**  
> 
> | Categoría                  | Descripción                                      |
> | -------------------------- | ------------------------------------------------ |
> | Control de procesos         | Gestión de la ejecución de procesos y su ciclo de vida. |
> | Administración de archivos  | Creación, lectura, escritura y eliminación de archivos. |
> | Administración de dispositivos | Manejo de hardware y controladores de dispositivos. |
> | Mantenimiento de información | Gestión de información del sistema y configuración. |

---

## Diseño e implementación

> **Objetivos del diseño**
> La estructura interna de un sistema operativo depende del hardware y del tipo de sistema.
> 
> **Objetivos del usuario**
> El sistema debe ser *fácil de usar*, *fiable* y *seguro*, para asegurar una experiencia sin complicaciones y libre de problemas.
> 
> **Objetivos del sistema**
> El sistema operativo debe ser *fácil de diseñar e implementar*, *flexible*, *fiable* y *eficiente* en el uso de recursos, para garantizar un rendimiento óptimo y adaptabilidad a diferentes entornos.

> ---
 
> **Aspectos clave de la implementación**
> 
> *Cambios de contexto*
> Guardar y restaurar el estado de los registros.  
> 
> *Drivers*
> Permiten la interacción con dispositivos.

---

## Estructura y funcionamiento del sistema operativo

> **Sistemas monolíticos**  
> Los sistemas monolíticos, típicos de la familia UNIX (Linux), son una arquitectura en la que el sistema operativo se compone de un único programa, el núcleo (*kernel*), que se ejecuta en modo sistema.
> 
> Los sistemas monolíticos son eficientes al integrar todo el código del sistema operativo en un único programa, lo que facilita la comunicación entre sus componentes.
> 
> Sin embargo, esta arquitectura dificulta la depuración, ya que un error en cualquier parte puede afectar todo el sistema.
> 
> *Modularización en sistemas monolíticos*  
> Los sistemas monolíticos actuales suelen no estar "cerrados", sino que implementan un kernel modular. Tienen interfaces bien definidas para comunicarse entre ellos y pueden cargarse en tiempo de ejecución.
>  
> Este enfoque permite una mayor adaptabilidad y extensibilidad, aunque mantiene algunos de los mismos problemas de fiabilidad.  
> 
> *Comparación con sistemas modulares*
> 
> | Característica                   | Sistema Monolítico                             | Sistema Modular                                                          |
> | -------------------------------- | ---------------------------------------------- | ------------------------------------------------------------------------ |
> | Arquitectura                     | Cerrada, inmodificable por otros programadores | Abierta, compatible con agentes externos                                 |
> | Vulnerabilidad frente a ataques  | Muy vulnerable                                 | Vulnerabilidad controlada                                                |
> | Extensibilidad                   | No permite extensiones fáciles                 | Permite extensiones mediante APIs en un modelo cliente-servidor          |
> | Cambios dinámicos en el software | No                                             | Sí, cada módulo puede ser activado o desactivado de manera independiente |

> ---

> **Sistemas modulares**  
> En los sistemas modulares, el sistema operativo se organiza en módulos que pueden cargarse y descargarse dinámicamente.
> 
> Cada módulo tiene interfaces bien definidas, lo que facilita la extensibilidad y permite adaptar el sistema a diferentes plataformas de manera más eficiente.


> ---

> **Sistemas por capas**  
> Los sistemas por capas organizan el sistema operativo en *capas independientes*, cada una en su propio espacio de direcciones. Estas capas se ordenan según niveles de *privilegio* y se comunican mediante *llamadas al sistema*.
> 
> Aunque son menos eficientes, facilitan la *depuración* y limitan la propagación de errores. Requieren procesadores con múltiples niveles de privilegio, y son más *transportables*.

> ---

> **Sistemas basados en micronúcleos (MicroKernel)**  
> En los sistemas basados en micronúcleos, el *kernel* se limita a lo esencial, gestionando procesos y memoria de bajo nivel, mientras que otras funcionalidades del sistema operativo se implementan como programas del sistema en modo usuario.
> 
> La comunicación entre estos programas se realiza mediante *mensajes*, incluyendo entre clientes, servidores y hardware.
> 
> Aunque este enfoque mejora la *extensibilidad*, *facilita la depuración* y aumenta la *confiabilidad*, presenta una desventaja en términos de *eficiencia* debido a la sobrecarga de mensajes y cambios de proceso.

> ---

> **Sistemas híbridos**  
> Los sistemas híbridos combinan características de los sistemas monolíticos y los micronúcleos, buscando equilibrar la *eficiencia* con la *modularidad*.
> 
> Ejemplos de estos sistemas incluyen **macOS** (basado en el microkernel Mach) y **Microsoft Windows**.  

> ---

> **Exokernel**  
> El *exokernel* proporciona abstracciones mínimas y permite que las aplicaciones gestionen los recursos de manera más directa, utilizando bibliotecas en modo usuario para implementar las funciones del sistema operativo. Aún en fase de investigación, no se utiliza en sistemas operativos comerciales.  

> ---

> **Máquinas virtuales**  
> Las *máquinas virtuales* implementan un sistema operativo sobre una máquina virtual, permitiendo ejecutar varios sistemas operativos invitados en un solo hardware físico. Ejemplos incluyen **Amazon EC2**, **Xen**, y **VirtualBox**.  

> ---

> **Contenedores**  
> Los *contenedores* permiten ejecutar aplicaciones en entornos aislados sin necesidad de un sistema operativo completo, siendo más *ligeros* y *rápidos* que las máquinas virtuales, pero con un aislamiento menor.

---