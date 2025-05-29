---
tags: URJC URJC_SO
---

# Tema 5 - Sistemas Operativos

---

## Tabla de Contenidos

1. [Servidor de Memoria de Procesos](#Servidor%20de%20Memoria%20de%20Procesos)
2. [Memoria del Proceso](#Memoria%20del%20Proceso)
3. [Mapa de Memoria](#Mapa%20de%20Memoria)
4. [Paginación de memoria](#Paginación%20de%20memoria)
5. [Soporte físico a la Memoria Virtual](#Soporte%20físico%20a%20la%20Memoria%20Virtual)
6. [Páginas de un proceso](#Páginas%20de%20un%20proceso)
7. [Gestión del espacio de swap](#Gestión%20del%20espacio%20de%20swap)
8. [Asignación de páginas](#Asignación%20de%20páginas)
9. [Creación de regiones](#Creación%20de%20regiones)

---

## Servidor de Memoria de Procesos

> **¿Qué es un servidor de memoria de procesos?**  
> Es un componente clave en los sistemas operativos que gestiona los recursos de memoria, garantizando que cada proceso tenga acceso a lo necesario para su ejecución, con protección y aislamiento.
> 
> **Funciones principales**  
> - Asignar a cada proceso los recursos de memoria requeridos.  
> - Gestionar la memoria principal y de intercambio, diferenciando entre áreas ocupadas y libres.  
> - Crear la imagen de los procesos desde los ejecutables.  
> - Proteger y aislar los procesos entre sí.  
> - Detectar y tratar errores en el acceso a memoria.  
> - Permitir el uso compartido de memoria de forma controlada.  
> - Liberar memoria no utilizada por los procesos.  
> - Optimizar el rendimiento del sistema.  
> - Proveer grandes espacios de memoria según las necesidades de los procesos.

---

## Memoria del Proceso

> **Gestión de memoria de un proceso**  
> Las necesidades de memoria se resuelven a dos niveles:  
> 
> *1. Por el Sistema Operativo*  
> Gestión global mediante regiones (grandes bloques de memoria contigua).  
> 
> *2. Por las bibliotecas del lenguaje*  
> Gestión detallada de objetos dentro de las regiones, como variables y estructuras.  

> ---

> **Imagen de memoria**  
> Conjunto de regiones (o segmentos) de memoria asignados a un proceso.  
> 
> *Características de una región*  
> - Es una zona contigua de direcciones de memoria.  
> - Definida por la dirección inicial, el tamaño y la fuente.  
> - Puede ser compartida o privada.  
> - Posee niveles de protección típicos: RWX (Lectura, Escritura, Ejecución).  
> - Su tamaño puede ser fijo o variable.  

> ---

> **Regiones del proceso**  
> Las regiones más relevantes de la imagen de memoria de un proceso son:  
> 
> | **Región**       | **Descripción**                                 | **Propiedades**                                |
> |-------------------|-----------------------------------------------|-----------------------------------------------|
> | Código    | Contiene el código máquina del programa.      | Compartida, RX, tamaño fijo.                  |
> | Datos inicializados | Variables globales inicializadas.            | Privada, RW, tamaño fijo, fuente: ejecutable. |
> | Datos no inicializados | Variables globales no inicializadas.         | Privada, RW, tamaño fijo, rellenar con 0.     |
> | Heap              | Memoria gestionada dinámicamente.             | Privada, RW, tamaño variable, rellenar con 0. |
> | Pila              | Registros de activación de procedimientos.    | Privada, RW, tamaño variable, rellenar con 0. |
> 
> La estructuración de las regiones depende del diseño del Sistema Operativo, es decir, puede existir una única región que agrupe todos los tipos de datos.
> 
> ---
> 
> **Otras regiones en la imagen de memoria**  
> 
> | **Región**          | **Descripción**                                                    | **Propiedades**                                |
> |----------------------|------------------------------------------------------------------|-----------------------------------------------|
> | Memoria compartida   | Utilizada para la comunicación entre procesos.                   | Compartida, tamaño variable, rellenar con 0.  |
> | Ficheros proyectados | Asociada a cada fichero proyectado.                              | Compartida, tamaño variable, fuente: fichero. |
> | Bibliotecas dinámicas| Código y datos específicos de cada biblioteca dinámica.          | Depende de la biblioteca.                     |
> | Pilas de threads     | Cada thread tiene su propia pila.                                | Privada, RW, tamaño variable.                 |

---

## Mapa de Memoria

> **¿Qué es un mapa de memoria?**
> Un mapa de memoria es una representación estructurada de cómo se organiza la memoria en un sistema operativo, mostrando las diferentes secciones de memoria y cómo se asignan a los distintos componentes de un programa o proceso en ejecución.
> 
> Cada segmento de memoria tiene permisos de acceso específicos (lectura, escritura, ejecución) y puede estar dedicado a diferentes tipos de datos (código, datos, pila).
> 
> [Más información](https://juncotic.com/mapa-de-memoria-de-un-proceso-en-linux/)

> ---

> **Mapa de Memoria Típico**  
> 
> | Sección de Memoria            | Descripción                                                                  | Permisos                                    |
> |-------------------------------|------------------------------------------------------------------------------|---------------------------------------------|
> | Código                        | Contiene el código ejecutable del proceso.                                    | Lectura y Ejecución (RX)                   |
> | Datos con valor inicial       | Almacena datos globales o estáticos inicializados.                           | Lectura y Escritura (RW)                   |
> | Datos sin valor inicial      | Almacena datos globales o estáticos no inicializados.                        | Lectura y Escritura (RW)                   |
> | Heap                          | Área para la asignación dinámica de memoria durante la ejecución.            | Lectura y Escritura (RW)                   |
> | Fichero proyectado            | Mapea un archivo en el espacio de direcciones de un proceso.                  | Lectura y Escritura (RW)                   |
> | Zona de memoria compartida    | Permite que varias aplicaciones o procesos compartan datos.                   | Dependiendo de la configuración, generalmente RW |
> | Código biblioteca dinámica    | Código de bibliotecas compartidas que se cargan en tiempo de ejecución.      | Lectura y Ejecución (RX)                   |
> | Datos biblioteca dinámica     | Contiene los datos de las bibliotecas compartidas.                           | Lectura y Escritura (RW)                   |
> | Pilas de procesos y threads   | Almacena el contexto de ejecución de los procesos y threads.                 | Lectura y Escritura (RW)                   |

> ---

> **Esquemas de Gestión de Memoria**
> En el nivel de procesos, existen varias formas de repartir la memoria principal disponible entre los procesos activos en el sistema:
> 
> *1. Asignación contigua*
> Asigna bloques contiguos de memoria a cada proceso. No es muy flexible y no aprovecha bien la memoria.
> 
> *2. Segmentación*
> Divide la memoria en segmentos, donde cada segmento corresponde a una parte lógica del programa (como el código, datos o pila). Los segmentos pueden estar ubicados de forma no contigua.
> 
> *3. Paginación*
> La memoria se divide en bloques de tamaño fijo llamados "páginas". Esta técnica permite una gestión más eficiente de la memoria.
> 
> *4. Segmentación paginada*
> Combina la segmentación y la paginación, proporcionando más flexibilidad y eficiencia al asignar bloques de memoria contigua (segmentos) que se dividen en páginas.
>  
> El esquema que más funcionalidad ofrece es **la segmentación paginada**, ya que combina lo mejor de ambos mundos, brindando flexibilidad y eficiencia.

> ---

> **Segmentación de Memoria**
> Cada proceso tiene varias *regiones* llamadas *segmentos*.
> 
> Estos segmentos pueden estar separados, lo que permite gestionarlos de forma independiente. Sin embargo, cada segmento se guarda de manera contigua en la memoria.
> 
> El *BCP (Bloque de Control de Proceso)* contiene una tabla de segmentos que guarda información sobre cada segmento, incluyendo:
> 
> - Dirección de carga.
> - Tamaño del segmento.
> - Bits de protección (RWX).
> - Bit de validez, que indica si el segmento está accesible o no.

> ---

> **Traducción de Direcciones Lógicas a Físicas**
> La Traducción de Direcciones se realiza mediante la *MMU (Unidad de Gestión de Memoria)*, que convierte las direcciones lógicas generadas por el proceso en direcciones físicas correspondientes en la memoria.
> 
> Para acelerar este proceso, la MMU utiliza una *TLB (Translation Lookaside Buffer)*, que es una pequeña caché que almacena una parte de la tabla de páginas.
> 
> La tabla de segmentos se copia a la MMU al realizar el cambio de contexto entre procesos. Este proceso asegura que cada proceso tenga un espacio de direcciones aislado y no interfiera con otros procesos en ejecución.

---

## Paginación de Memoria

> **¿Qué es la Paginación de Memoria?**  
> La paginación de memoria es una técnica utilizada por los sistemas operativos para gestionar la memoria de los procesos.
> 
> La memoria principal se divide en bloques de igual tamaño llamados *marcos de página*.  
> 
> Un proceso tiene un mapa de memoria dividido en *páginas*, donde el tamaño de una página es igual al tamaño de un marco de página.
>
> 
> *Gestión de Memoria en el Sistema Operativo*
> Los marcos de página asignados a un proceso no tienen que ser contiguos.

> ---

> **Modalidades de Segmentación Paginada**  
> Existen dos modalidades para gestionar la segmentación paginada:
> 
> *1. Segmentación Paginada Local*
> Cada proceso tiene su propio espacio de direcciones, con una tabla de páginas asociada a cada segmento.
> 
> El puntero a cada tabla de páginas se encuentra en la tabla de segmentos.
> 
> *2. Segmentación Paginada Global*
> Hay un espacio único de direcciones para todos los procesos, y se utiliza una única tabla de páginas global para todos los procesos.

> ---

## Soporte físico a la Memoria Virtual

> **Metainformación**  
> La metainformación de la memoria virtual incluye las tablas de páginas, que son almacenadas en la *memoria principal*.
> 
> Estas tablas contienen la información necesaria para realizar la traducción de direcciones lógicas a físicas.

> ---

> **Información**  
> La información que define la memoria virtual se distribuye entre diferentes lugares:
> 
> *Páginas almacenadas en la zona de intercambio del disco (swap)*
> Cuando no caben en la memoria principal, las páginas pueden ser almacenadas temporalmente en el disco.
> 
> *Páginas almacenadas en marcos de página de la memoria principal*
> Cuando las páginas son necesarias, se cargan en la memoria principal, donde se asignan a marcos de página.
> 
> *Liberación de páginas*
> En algunos sistemas operativos, las páginas que se copian a memoria principal se liberan del disco, mientras que en otros, la copia en disco se mantiene para su posible reutilización.

> ---

> **Diagrama de Soporte Físico a la Memoria Virtual**  
> En los sistemas con memoria virtual, el soporte físico se distribuye entre la *memoria principal* y la *zona de intercambio (swap)* en el disco.
> 
> Cada proceso puede tener su propia tabla de páginas, y estas tablas pueden estar almacenadas en el espacio del sistema operativo.

> ---

> **Gestión del espacio de swap**
> 
> *Preasignación de swap*
> Cada página virtual asignada tiene un espacio fijo en el swap.
> 
> *Sin preasignación de swap*
> Una página virtual asignada o está en el swap o está en un marco de memoria. En reemplazo hay que copiar la página a swap.

---

## Páginas de un proceso

> **Conjunto residente de un proceso**  
> Conjunto de páginas del proceso que en un momento dado se encuentran ubicadas en marcos de página de la memoria principal.
> 
> **Conjunto de trabajo de un proceso**  
> Conjunto de páginas en las que se encuentran los datos y las instrucciones que el proceso está utilizando.

> ---

> **Políticas de reemplazamiento de páginas de un proceso**
> 
> *Reemplazamiento local*  
> La nueva página se asigna a un marco libre o un marco ya asociado al proceso.
> 
> *Reemplazamiento global*  
> Ante un fallo de página, la nueva página se puede asignar a un marco cualquiera (propio, ajeno o libre).
> 
> **Algoritmos de reemplazamiento**
> 
> *FIFO (First In, First Out)*
> Este algoritmo reemplaza la página que lleva más tiempo en la memoria.
> 
> *Reloj (o algoritmo de segunda oportunidad)*  
> Basado en una cola FIFO, utiliza el bit de referencia. Si una página tiene el bit de referencia activado, se coloca al final de la cola y se borra el bit. Si la página tiene el bit de referencia a 0, se reemplaza por la nueva.
> 
> *LRU* (Least Recently Used)  
> Este algoritmo reemplaza la página que no ha sido utilizada durante el mayor tiempo.

---

## Gestión del Espacio de Swap

> **Preasignación de Swap**  
> Se asigna un espacio fijo en el swap para cada página virtual.
> 
> *Ventaja*
> Fácil detección del agotamiento del espacio.
> 
> *Desventaja*
> Uso ineficiente del espacio.

> ---

> **Sin Preasignación de Swap**  
> El espacio en el swap se asigna solo cuando es necesario.
> 
> *Ventaja*
> Uso más eficiente del espacio.
> 
> *Desventaja*
> Puede generar retrasos en el manejo de fallos de página.

> ---

> **Agotamiento de Swap**  
> Si el swap se llena, el sistema debe abortar procesos para liberar espacio y seguir funcionando.

---

## Asignación de páginas

> **Política de asignación de páginas a un proceso**
> 
> *Asignación fija*  
> Cada proceso dispone de un número fijo de marcos de página.
> 
> *Asignación dinámica*  
> El número de marcos de página asignados a un proceso puede variar en función de sus necesidades.

> **Política de asignación + política de reemplazamiento:**
> 
> *Asignación fija*  
> Solo tiene sentido utilizar reemplazamiento local.
> 
> *Asignación dinámica + reemplazamiento local*  
> El proceso aumenta o disminuye su conjunto residente según su comportamiento.
> 
> *Asignación dinámica + reemplazamiento global*  
> Los procesos se quitan páginas entre ellos.

---

## Creación de regiones

> **Creación de regiones de memoria**  
> El gestor de memoria crea las regiones de memoria cuando:
> 
> - Se crea un proceso (fork).
> - Se cambia el programa del proceso (exec).
> - O se solicita una nueva región.

> ---

> **Requisitos para la creación de una región**  
> - Definir la ubicación de la región en el espacio virtual.
> - Asignar espacio de swap como soporte físico, si es necesario.
> - Las regiones compartidas comparten el espacio físico.
> - Dar contenido al soporte físico, si es necesario.
> - Crear la tabla de páginas para gestionar la memoria.

---