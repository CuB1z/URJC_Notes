---

tags: URJC URJC_SO

---

# Tema 6 - Gestión de Ficheros

---

## Tabla de Contenidos

1. [Sistema de Ficheros](#Sistema%20de%20Ficheros)
2. [Ficheros](#Ficheros)
3. [Gestión de Archivos](#Gestión%20de%20Archivos)
4. [Directorios](#Directorios)
5. [Implementación del Sistema de Ficheros](#Implementación%20del%20Sistema%20de%20Ficheros)
6. [Sistemas de Archivos Actuales](#Sistemas%20de%20Archivos%20Actuales)

---

## Sistema de Ficheros

> **Definición**
> Un sistema de ficheros organiza la información en dispositivos de almacenamiento secundario y cumple los siguientes objetivos:
> 
> *Presentación lógica*
> Permite que los dispositivos sean vistos como ficheros.
> 
> *Primitivas de acceso*
> Proporciona métodos independientes de los detalles físicos.
> 
> *Mecanismos de protección*
> Garantiza la seguridad de los datos almacenados.

---

## Ficheros

 > **Unidad Lógica de Almacenamiento**
> La unidad lógica de almacenamiento se refiere a la forma en que el sistema operativo organiza y gestiona los datos en dispositivos de almacenamiento secundario (como discos duros, SSD, etc.).
> 
> Los ficheros son una de las unidades fundamentales en esta organización, ya que representan bloques de información o conjuntos de datos que el sistema operativo trata como una única entidad.
> 
> Estos ficheros son gestionados en el **sistema de archivos**, que es la estructura lógica que permite al sistema operativo almacenar, recuperar y manipular los datos. Un archivo puede estar compuesto de múltiples bloques de almacenamiento físicos, pero para el usuario y las aplicaciones, el archivo aparece como una unidad continua de datos.
> 
> | Atributo  | Descripción                                               |
> |---------------|-------------------------------------|
> | Nombre    | Identifica al archivo dentro de su directorio.                               |
> | Tipo      | Determina el formato de los datos (texto, imagen, audio, etc.).     |
> | Tamaño    | Indica la cantidad de datos que contiene.                                    |
> | Ubicación | El sistema de archivos gestiona la localización física de los bloques del archivo en el dispositivo de almacenamiento. |
> | Permisos  | Definen qué usuarios pueden acceder, modificar o ejecutar el archivo. |

---

## Gestión de Archivos

> **Operaciones sobre archivos**
> 
> | Operación  | Descripción                               |
> |----------------|----------------------------|
> | Creación  | El sistema crea nuevos archivos en el sistema de almacenamiento.   |
> | Lectura   | El sistema permite leer el contenido de los archivos.                     |
> | Escritura | Los archivos pueden ser modificados, añadiendo o cambiando su contenido.  |
> | Eliminación | El sistema permite la eliminación de archivos del almacenamiento.   |
> 
> El acceso a los archivos puede estar optimizado para eficiencia mediante el uso de índices, tablas de asignación o estructuras más complejas, dependiendo del tipo de sistema de archivos utilizado.
> 
> En resumen, los archivos son esenciales para estructurar y acceder a la información de manera ordenada y eficiente dentro de los sistemas computacionales.

> ---

> **Tipos de ficheros**
> 
> *Secuencia de bytes*
> Ficheros que contienen una secuencia de bytes sin ningún formato específico, como los ficheros binarios.
> 
> *Caracteres ASCII*
> Ficheros de texto que contienen caracteres representados en el conjunto de caracteres ASCII.
> 
> *Registros*
> Ficheros estructurados en registros de longitud fija o variable, como bases de datos.
> 
> *Documentos formateados*
> Ficheros que contienen texto con formato, como los documentos de Word o PDF.
> 
> *Binarios*
> Ficheros ejecutables o de objetos que contienen instrucciones de máquina o datos codificados de forma binaria (por ejemplo, archivos `.exe`).
> 
> *Especiales*
> Ficheros que no son datos tradicionales, como los dispositivos en `/dev` en sistemas Unix/Linux (ej. `/dev/sda` para un disco duro).

> ---

> **Atributos de un fichero**
> 
> *Nombre*
> Identificador que se utiliza para acceder al fichero dentro de su directorio.
> 
> *Identificador único*
> Un identificador interno (como el inode en Unix) que diferencia de manera única el fichero en el sistema.
> 
> *Tipo de información*
> El formato o tipo de los datos dentro del fichero (por ejemplo, texto, imagen, audio).
> 
> *Dueño y grupo*
> El propietario del archivo y el grupo al que pertenece, usado para la gestión de permisos.
> 
> *Tamaño*
> El tamaño total del fichero en bytes.
> 
> *Permisos (protección)*
> Determinan las acciones que los usuarios pueden realizar sobre el archivo (lectura, escritura, ejecución).
> 
> *Fecha y hora*
> Fechas relacionadas con el archivo, como la última modificación, creación o acceso.
> 
> *Número de enlaces*
> El número de referencias o enlaces al fichero, útil para la gestión de espacio y eliminar ficheros solo cuando ya no hay enlaces.

> ---

> **Estructuras utilizadas en la gestión de ficheros**
> 
> *Tabla de asignación de archivos (FAT)*
> Utilizada en sistemas antiguos o de almacenamiento simple, como disquetes o sistemas DOS.
> 
> *Inodos*
> En sistemas Unix/Linux, el inodo contiene la metadata del fichero, como su tamaño, permisos y localización en disco.
> 
> *Árboles B o B+*
> Estructuras de datos eficientes para la gestión y búsqueda de archivos en sistemas de archivos modernos, como NTFS o ext4.
> 
> El manejo adecuado de los ficheros permite a los sistemas operativos proporcionar un acceso eficiente y seguro a la información, optimizando el uso del almacenamiento y garantizando la integridad de los datos.

---

## Directorios

> **Operaciones comunes**
> 
> | Operación               | Descripción                                                    |
> |-------------------------|----------------------------------------------------------------|
> | Buscar                | Localiza archivos dentro de los directorios.                   |
> | Crear archivos          | Crea nuevos archivos dentro de un directorio.                  |
> | Borrar archivos         | Elimina archivos dentro de un directorio.                      |
> | Listar contenido        | Muestra los archivos y subdirectorios dentro de un directorio. |
> | Crear subdirectorios    | Crea nuevos directorios dentro de un directorio.               |
> | Eliminar subdirectorios | Elimina directorios vacíos o con contenido.                    |

> ---

> **Estructura de Directorios**
> 
> | Tipo de Estructura     | Descripción                     |
> |-----------------------|-------------------------|
> | Jerárquica             | Los directorios están organizados como un árbol, con una estructura de nodos y ramas. Cada directorio puede contener archivos o subdirectorios. |
> | Nombres de Ruta        | Las rutas indican cómo llegar a un archivo o directorio en el sistema.    |
> | Absolutos              | Ruta completa desde la raíz del sistema de archivos, comenzando desde el directorio raíz `/` (en sistemas Unix/Linux). |
> | Relativos              | Ruta basada en el directorio actual, sin necesidad de especificar la raíz. Ejemplo: `./subdirectorio/archivo.txt`. |

---
 
## Implementación del Sistema de Ficheros

> **Estructuras necesarias para la gestión**  
> El sistema de ficheros utiliza diversas estructuras para organizar y acceder a los datos almacenados.

> ---

> **Estructuras en disco**  
> El sistema de ficheros utiliza diversas estructuras en disco para gestionar y organizar los datos. A continuación, se describen algunas de las más importantes:
> 
> *Bloque de control de arranque*
> Contiene el cargador del sistema operativo, que se ejecuta al iniciar el sistema. Es responsable de la carga del núcleo (kernel) y la inicialización del sistema de ficheros.
> 
> *Superbloque*
> Contiene información esencial sobre el sistema de ficheros, como la cantidad de bloques libres, la estructura de directorios y los detalles del sistema de ficheros.
> 
> Es crucial para el correcto funcionamiento del sistema de ficheros.
> 
> *Bloque de control de fichero (FCB)*
> Almacena los atributos y las ubicaciones de los bloques que conforman un fichero.
> 
> Existen diferentes implementaciones según el sistema operativo:
>
> - **Unix**: Utiliza el concepto de i-nodos para almacenar esta información.
> - **Windows**: Utiliza estructuras como la **FAT** o la **MFT** en sistemas NTFS.

> ---

> **Asignación de bloques**  
> La asignación de bloques en el disco se gestiona mediante diferentes métodos, cada uno con ventajas y desventajas, que afectan el rendimiento y la gestión del espacio de almacenamiento:
> 
> *Contigua*
> Los bloques de un archivo se almacenan de forma continua en el disco.
> 
> - **Ventajas**: Acceso rápido, ya que los bloques están cercanos entre sí.  
> - **Problemas**: Puede producir fragmentación externa y dificultar la expansión del archivo.
> 
> *Enlazada*
> Los bloques del archivo no están necesariamente contiguos, sino que cada bloque contiene un puntero al siguiente.  
> 
> - **Ventajas**: Elimina la fragmentación externa.  
> - **Problemas**: Ineficiencia en el acceso directo.
> 
> *Indexada*
> Utiliza un índice que contiene punteros a todos los bloques del archivo.
> 
> - **Ventajas**: Acceso rápido y eficiente a los bloques del archivo.  
> - **Problemas**: Requiere espacio adicional para almacenar los índices, lo que puede aumentar el tamaño total del sistema de ficheros.

> ---

> **Gestión del espacio libre**  
> La gestión del espacio libre en un sistema de ficheros se realiza mediante varios métodos, cada uno con sus propios enfoques para optimizar el uso del almacenamiento:
> 
> *Mapa de bits*
> Utiliza un bit para cada bloque de datos en el sistema. Si el bit es 0, el bloque está libre; si es 1, está ocupado.
> 
> Es eficiente para gestionar el espacio, pero puede ser costoso en sistemas con muchos bloques.
> 
> *Lista enlazada*
> Mantiene una lista de bloques libres mediante punteros. Cada entrada en la lista apunta a un bloque libre en el disco.
> 
> Es una estructura simple y flexible, pero puede ser menos eficiente para grandes sistemas de almacenamiento debido al tiempo requerido para navegar por la lista.

---

## Sistemas de Archivos Actuales

> **Ext4**  
> Ext4 es una evolución de Ext3, utilizado principalmente en sistemas Linux.
> 
> *Evolución de Ext3*
> Ext4 mejora sobre Ext3 añadiendo características que permiten un rendimiento superior y una mayor fiabilidad.
> 
> *Soporte para volúmenes grandes*
> Ext4 soporta volúmenes de hasta 1024 PiB, lo que lo hace adecuado para sistemas de almacenamiento de gran capacidad.
> 
> *Uso de extents*
> Utiliza una estructura de extents (rangos de bloques consecutivos) para reducir la fragmentación y mejorar el rendimiento en la lectura y escritura de archivos grandes.

> ---

> **NTFS**  
> NTFS (New Technology File System) es el sistema de archivos utilizado por defecto en los sistemas operativos Windows.
> 
> *Diseñado para Windows*
> NTFS está optimizado para el entorno de Windows y ofrece un alto rendimiento y soporte para características avanzadas.
> 
> *Master File Table (MFT)*
> Utiliza la MFT para gestionar archivos y metadatos, lo que permite un acceso eficiente y la gestión de grandes volúmenes de datos.
> 
> *Soporte para permisos avanzados*
> NTFS ofrece un control detallado sobre los permisos de archivo, lo que mejora la seguridad.

> ---

> **XFS**  
> XFS es un sistema de archivos diseñado para manejar grandes volúmenes de datos, utilizado en sistemas Linux.
> 
> *Orientado a grandes volúmenes y ficheros*
> XFS es ideal para almacenar y gestionar grandes cantidades de datos y archivos grandes, siendo comúnmente usado en servidores y entornos empresariales.
> 
> *Ideal para entornos de Big Data*
> XFS se adapta bien a las necesidades de los sistemas de Big Data, proporcionando alta escalabilidad y rendimiento.

> ---

> **BTRFS**  
> BTRFS (B-tree File System) es un sistema de archivos avanzado, diseñado para ofrecer características de alta disponibilidad y tolerancia a fallos.
> 
> *Diseñado para tolerancia a fallos*
> BTRFS es ideal para entornos donde la fiabilidad de los datos es crítica. Utiliza tecnologías como la verificación de sumas de comprobación y la redundancia de datos.
> 
> *Uso de extents*
> Al igual que Ext4, BTRFS utiliza extents para gestionar bloques de datos de manera más eficiente, reduciendo la fragmentación.
> 
> *Sumas de verificación*
> Utiliza sumas de verificación para garantizar la integridad de los datos, lo que ayuda a detectar y corregir errores.

> ---

> **APFS**  
> APFS (Apple File System) es el sistema de archivos desarrollado por Apple, optimizado para dispositivos de almacenamiento basados en flash, como SSD.
> 
> *Diseñado para SSD y memorias flash*
> APFS está optimizado para aprovechar las ventajas de las unidades de estado sólido (SSD), mejorando la velocidad de lectura y escritura.
> 
> *Soporte para nombres de archivo en UTF-16*
> APFS permite nombres de archivo en formato UTF-16, lo que facilita la internacionalización.
> 
> *Soporte para volúmenes grandes*
> APFS puede gestionar volúmenes de hasta 8 EiB, lo que lo convierte en una opción escalable para dispositivos de almacenamiento de gran capacidad.

---