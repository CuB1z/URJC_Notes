---
tags: URJC URJC_SO
---

# Act. Tema 1 - Sistemas Operativos 💻

---

## Actividad 1
Mandato `whoami`: Permite conocer el usuario logeado actualmente.

Mandato `who`: Permite conocer los usuarios conectados en el sistema.

## Actividad 2
Mandato `echo`: Muestra una línea de texto (puede ser redirigida a un fichero / mostrarse por la salida estándar).

## Actividad 3
Mandato `man`: Permite acceder al manual del sistema en el que se pueden consultar la gran mayoría de mandatos.
- Para abandonar el manual, presionar la tecla `q` (quit).

## Actividad 4
Mandato `xman`: Ejecuta una versión gráfica del manual del sistema.

## Actividad 5
El manual del sistema tiene como secciones principales:
   1. Mandatos.
   2. Llamadas al sistema.
   3. Librerías del sistema.

Mandato `whatis`: Muestra descripciones cortas (una línea) de los comandos que son consultados.

Mandato `apropos`: Busca un término especificado en todas las páginas del manual.
- Nota: Esta tarea también puede ejecutarse mediante el comando `man -k [parámetro]`.

## Actividad 6
Mandato `info`: Comando usado para leer documentos de información en el sistema.
- Podemos movernos dentro mediante las teclas `t | l | q`.

## Actividad 7
Usando el atajo `ctrl+r` podemos buscar comandos previamente ejecutados en la terminal.

## Actividad 8
Podemos lanzar ejecuciones en segundo plano añadiendo el caracter `&` al final del comando.

Mandato `ps`: Muestra el listado de procesos activos.
- Nota: Para comprobar todos los procesos activos, ejecutamos: `ps aux`.
- Nota: Para comprobar todos los procesos lanzados por un usuario, ejecutamos: `ps -U [user]`.

## Actividad 9
Mandato `stat`: Muestra los datos y estado de un fichero del sistema (i-nodos).

Mandato `mount`: Muestra todos los sistemas de ficheros montados en el sistema.

Mandato `df`: Muestra el espacio libre y utilizado en los sistemas de ficheros.
- Nota: Este mandato acepta el parámetro `-h`, que muestra la información de manera más amigable (human readable).

Mandato `du`: Muestra el espacio ocupado por los directorios del usuario.
- Nota: Este mandato también acepta el parámetro `-h`.
- Nota: Este mandato también acepta el parámetro `-d` que especifica la profundidad máxima.

Mandato `tree`: Muestra el árbol de directorios y ficheros a partir de `/usr`.
- Nota: Este mandato no suele venir instalado en sistemas Debian, para instalarlo, lanzar el siguiente comando: `sudo apt install tree`.

## Actividad 10
Mandato `pwd`: Muestra el directorio de trabajo actual (print working directory).

Mandato `ls`: Muestra todos los ficheros del directorio actual.
- Parámetro `-a`: Indica que debe mostrar también los ficheros ocultos (ficheros ocultos que empiezan por punto (.xxx)).
- Parámetro `-l`: Indica que debe mostrar la información en formato extendido.

La variable `$HOME`: Contiene la ruta home del usuario.

Mandato `rmdir`: Elimina el directorio seleccionado.
- Nota: Se debe tener en cuenta que para eliminar el directorio, éste debe estar vacío.

Mandato `rm`: Elimina el fichero deseado.
- Nota: Se puede eliminar un directorio mediante el parámetro `-r` (recursive).

## Actividad 11
Mandato `touch`: Crea un fichero con el nombre especificado.
- Nota: Si el fichero ya existe, se actualizarán las fechas de modificación del mismo.

Mandato `cp`: Copia un fichero seleccionado en una ruta especificada con el nombre del nuevo fichero.

Mandato `nano`: Abre el fichero en el editor de terminal Nano.
- Nota: Existen diversos editores de terminal como: Less, Vim, Nvim.

Mandato `mv`: Mueve / Renombra ficheros.

Mandato `ln`: Crea enlaces (accesos directos) entre archivos.
- Nota: Los enlaces son fuertes por defecto.
- Nota: El parámetro `-s` indica que el enlace creado debe ser débil (soft).

Mandato `tar`: Utilidad para archivar / comprimir / descomprimir.
- Nota: Para crear un comprimido, debemos usar el parámetro `-cvf`.
- Nota: Para descomprimir un archivo, debemos usar el parámetro `-xvf`.
- Ejemplo: `tar -cvf archivo.tgz [Directorios / Archivos]` | `tar -xvf archivo.tgz -C [Directorio]`.

Mandato `find`: Busca el nombre o expresión regular especificada en el directorio requerido.
- Ejemplo: `find [directorio] -name [regex]`.

Para copiar todos los ficheros acabados en ".txt" a otro directorio, debemos ejecutar el siguiente comando:
```bash
cp $(find . -name "*.txt") [directorio_destino]
```

Para borrar todos los ficheros que tienen por nombre "Trimestre.17" seguidos de cualquier cosa, hacemos:
```bash
rm $(find . -name "Trimestre17*")
```

Para borrar todos ficheros que tienen por nombre "Trimestre.18.$1.txt" siendo $1 (1 / 2), hacemos:
```bash
rm $(find . -name "Trimestre.18.[12].txt")
```

## Actividad 12
Mandato `wc`: Imprime cuántas líneas, palabras y bytes tiene un fichero especificado.
- Nota: Mediante los parámetros podemos especificar qué queremos contar.
    1. Bytes con `-c`.
    2. Caracteres con `-m`.
    3. Líneas con `-l`.
    4. Palabras con `-w`.
- Nota: Si queremos especificar varias opciones como por por ejemplo líneas y palabras, podriamos utilizar `-lw`.

Mandato `cut`: Imprime partes seleccionadas de un archivo o varios archivos por la salida estándar.
- Se debe especificar el delimitador `-d` y los campos seleccionados `-f`, así como el fichero seleccionado.

El archivo que contiene todos los usuarios del sistema es el localizado en `/etc/passwd`.
- La estructura que tienen los datos en el arhivo es: `nombre_usuario:x:UID:GID:info_usuario:directorio_home:shell`-

Para mostrar el uid, el directorio raíz y la shell predeterminada, ejecutamos el siguiente comando:
```bash
cut -d: -f3,6,7 /etc/passwd
```

Mandato `head`: Imprime las 10 primeras líneas del fichero especificado.

Mandato `tail`: Imprime las 10 últimas líneas del fichero especificado.
- Nota: El parámetro `-n` (number) indica cuantas líneas debe mostrar (sobreescribe las 10 líneas predeterminadas).

Mandato `cat`: Imprime y concatena archivos en la salida estándar.

Mandato `sort`: Imprime y concatena archivos ordenados por orden alfabético en la salida estándar.
- Nota: El parámetro `-r` (reverse) indica que el orden debe ser invertido.

Mandato `tr`: Reemplaza o elimina caracteres especificados.

Mandato `more`: Muestra el contenido de un fichero con paginación.

Mandato `tee`: Lee la entrada estándar y la imprime en la salida estándar o en un fichero.

Mandato `sed`: Editor de streamings para filtrar y transformar texto.
- Expresión básica de sustitución en `sed`:
```bash
sed 's/patrón/reemplazo/flags' fichero
```

Para mostrar los datos de los cinco primeros usuarios del sistema, ejecutamos:
```bash
head -n 5 /etc/passwd
```

Para mostrar los datos de todos los usuarios del sistema menos los 5 últimos, hacemos:
```bash
head -n $(($(wc -l < /etc/passwd) - 5)) /etc/passwd
```

Para mostrar los primeros 100 bytes del fichero, ejecutamos:
```bash
head -c 100 /etc/passwd
```

Para mostrar los datos de los últimos cinco usuarios del sistema, ejecutamos:
```bash
tail -n 5 /etc/passwd
```

Para mostrar todos los usuarios menos los cinco primeros, hacemos:
```bash
tail -n $(($(wc -l  < /etc/passwd) - 5)) /etc/passwd
```

Para mostrar todas las líneas del fichero /etc/passwd en orden alfabético, lanzamos:
```bash
sort /etc/passwd
```

Para mostrar todas las líneas del fichero /etc/passwd en orden alfabético inverso, hacemos:
```bash
sort -r /etc/passwd
```

Para reemplazar x, y, z por X, Y, Z, hacemos lo siguiente:
```bash
tr [xyz] [XYZ]
```

Para reemplazar todas las letras minúsculas a mayúsculas, ejecutamos:
 ```bash
 tr [a-z] [A-Z]
 ```

Para mostrar el contenido del fichero /etc/passwd, pero reemplazando 'sys' por 'SYSTEM', hacemos:
```bash
sed 's/sys/SYSTEM/g' /etc/passwd
```

Para copiar la entrada estándar y guardarla en un fichero, lanzamos el siguiente comando:
```bash
tee /fichero.txt
```

## Actividad 13
Mandato `grep`: Busca patrones especificados en los datos contenidos por cada fichero.
- Nota: El parámetro `-E` indica que la expresión regular es extendida.

- Regex para buscar una palabra: `palabra`.
- Regex para buscar una palabra al principio de una línea: `^palabra`.
- Regex para buscar una palabra al final de una línea: `palabra$`.
- Regex para buscar una palabra que empiece por c, termine por h, y que tenga 4 letras: `\<c..h\>`.
- Regex para buscar una palabra que empiece por b, termine por g, que tenga 3 letras y en medio tengan una a o e: `\<b[ae]g\>`.
- Regex para buscar una palabra que empiece por b, termine por g, que tenga 3 letras y en medio no tengan una a o e: `\<b[^ae]g\>`.
- Regex extendida para buscar palabras que contengan las subcadenas 'car' | 'truck': `car|truck`.

## Actividad 14
Mandato `find`: Busca patrones especificados en los metadatos de cada fichero.
- Nota: El parámetro `-type` indica el tipo de que se busca, directorio o fichero.

Buscar los ficheros que empiecen por 'ls' y termine por '.so':
```bash
find [path] -type f -name 'ls*.so'
```

Buscar los ficheros cuyo tamaño sea mayor que 2 MB:
```bash
find [path] -type f -size +2M
```

Buscar los ficheros bajo el directorio raíz sobre los que el propio usuario tenga permiso de escritura:
```bash
find ~ -type d -name '*os*' -writable
```

## Actividad 15
Mandato `umask`: Imprime / Permite cambiar los permisos predeterminados cuando se crea un fichero o un directorio.
- Nota: Si se omite el modo, se imprimirán los permisos que no han sido establecidos en formato octal.
- Nota: Si se incluye el modo, se actualizarán los permisos predeterminados.
- Nota: Si se incluye la flag `-S`, se imprimirán los permisos presentes actualmente.

Mandato `chmod`: Permite cambiar los permisos de un directorio o fichero.
- Nota: Los permisos pueden especificarse mediante un número octal: `064`.
- Nota: Los permisos pueden especificarse mediante los caracteres representativos: `u=,g=rw,o=w`.
- Nota: Los permisos pueden modificarse con los operadores: `+-=`.

## Actividad 16
Para redirigir la entrada desde un fichero, usamos los operadores `<`.
Para redirigir la salida hacia un fichero, usamos los operadores `> >>`.

## Actividad 17
Para usar como entrada de otros comandos la salida de un comando que es ejecutado justo antes de él, usamos el operador `|` o pipeline.

Ver la lista de ficheros de `/usr/bin` página a página:
```bash
ls /usr/bin | more
```

Filtrar la lista de nombres de ficheros de `/usr/bin`, página a página, para ver sólo los que contengan el caracter `m`:
```bash
ls /usr/bin | grep 'm' | more
```

Mostrar cuántos usuarios se encuentran conectados en el sistema:
```bash
who | wc -l
```

Mostrar cuántos usuarios se encuentran en el sistema (sin tener en cuenta si están conectados o no):
```bash
cat /etc/passwd | wc -l
```

Mostrar por pantalla los _login names_ de los usuarios del sistema alfabéticamente:
```bash
cut -d: -f1 /etc/passwd | sort
```

Mostrar por pantalla los _login names_ de los usuarios del sistema que empiezan por la letra `r`:
```bash
cut -d: -f1 /etc/passwd | grep '^r'
```

Mostrar por pantalla los _login names_ de los usuarios junto a su directorio home, separados por un `\t`:
```bash
cut -d: -f1,6 /etc/passwd | sort | tr ':' '\t'
```

Mostrar por pantalla cuántos subdirectorios hay en el directorio actual:
```bash
ls -la | grep '^d' | wc -l
```

Mostrar por pantalla cuántos ficheros hay en el directorio actual:
```bash
ls -la | grep '^-' | wc -l
```

Mostrar por pantalla sobre cuántos ficheros y directorios tenemos permiso de escritura en el directorio actual:
```bash
ls -la | cut -c 3 | grep 'w' | wc -l
```

## Actividad 18
Mandato `xargs`: Permite pasar parámetros salientes de un pipe a otro comando que no lea de la entrada estándar.
- Ejemplo: `find ./ -type f -name "*~" | xargs rm -f`.
- Ejemplo: `find /home -type f -name "*.sh" | xargs cp -t /tmp/temporal`.

## Actividad 19
Para crear variables en el sistema, hacemos lo siguiente: `VAR_A=valor`.

Mandato `expr`: Permite evaluar expresiones matemáticas y lógicas.
- Ejemplo: `expr $VAR_A \* $VAR_B + 5`.

Mandato `bc`: Evalúa una expresión que recibe por entrada estándar.
- Ejemplo: `echo $VAR_A \* $VAR_B + 5 | bc`.

Sintaxis `$((operación))`: Permite evaluar expresiones matemáticas y lógicas.
- Ejemplo: `echo $((VAR_A * VAR_B + 5))`.

Mandato `env`: Muestra todas las variables de entorno del sistema.
- Ejemplo: `env | grep "PATH=*"`.

## Actividad 20
Scripts
- `$$`: Contiene el PID de la shell.
- `$#`: Contiene el número de argumentos recibidos por el script.
- `$*`: Contiene todos los argumentos recibidos por el script.
- `$@`: Similar a `$*`, pero trata cada argumento como una cadena separada.
- `$0`: Contiene el nombre del script o del comando invocado.

Podemos simplificar el bucle `for` para iterar sobre los argumentos recibidos por el script.
```bash
for ARG; do
    echo $ARG
done
```
