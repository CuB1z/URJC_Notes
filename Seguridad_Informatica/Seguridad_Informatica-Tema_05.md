---
tags: URJC URJC_SI
---

# Tema 5 - Seguridad Informática

---

## Tabla de Contenidos

1. [Desbordamientos](#Desbordamientos)
2. [Inyecciones](#Inyecciones)
3. [PicoCTF - Aprende Ciberseguridad](#PicoCTF%20-%20Aprende%20Ciberseguridad)
4. [Forgeries](#Forgeries)
5. [Cross-Site Scripting (XSS)](#Cross-Site%20Scripting%20(XSS))

---

## Desbordamientos

> **🚀 Ataque por Desbordamiento (Overflow)**  
> Ataque en el que se aprovecha una vulnerabilidad en el software para ejecutar código malicioso.
> 
> Ocurre cuando una aplicación no valida correctamente el tamaño de los datos que recibe. Puede otorgar al atacante los mismos permisos que la aplicación vulnerable.
> 
> 🔍 **Dato curioso**
> Esta vulnerabilidad se conoce desde los años 80, pero aún sigue presente en muchos sistemas.

> ---

> **🗂️ Stack Overflow**  
> La pila (*stack*) se usa en cada llamada a funciones o procedimientos.  
> Almacena información importante como:  
> - 📌 Variables internas.  
> - 🔗 Punteros.  
> - 🔄 Dirección de retorno.  
> - 📦 Parámetros de la función.  
> 
> **💻 Ejemplo en C**
> ```C
> void copia_cadena(char * cadena) {
> 	char buffer[16];
> 	strcpy(buffer, cadena);
> }
> 
> void copia_main() {
> 	char frase[16];
> 	int i;
> 	for (i = 0; i < 255; i++) {
> 			frase[i] = 'M';
> 	}
> 	copia_cadena(frase);
> }
> ```
> 
> **⚠️ Problema Buffer Overflow**
> La función `copia_cadena` **no valida el tamaño del parámetro recibido**. Por lo tanto, cuando el buffer de 16 caracteres se llena, los **otros 240 caracteres se escriben fuera de los límites**.
> 
> Esto sobrescribe información crítica, incluida la **dirección de retorno** del programa.  
> 
> *💥 Consecuencia: Segmentation Fault*
> - El programa intenta ejecutar una dirección de memoria no válida.  
> - Resultado: **Crash del programa** con un **Segmentation Fault**.  
> 
> *🛑 Dirección de retorno sobrescrita*
> En este caso, la dirección de retorno queda reemplazada por cuatro 'M':  
> $$\text{0x4D4D4D4D}$$  
> 
> **🎯 Objetivo del atacante**  
> Manipular la dirección de retorno para que **apunte a su propio buffer**.
> - Inyectar **código malicioso** en esa dirección.  
> - Obtener **control total del sistema**.  

---

## Inyecciones

> **🚨 ¿Qué es una inyección?**  
> Un ataque de inyección ocurre cuando una aplicación **no valida correctamente los datos introducidos por el usuario**.
> 
> Esto permite que un atacante **inyecte código malicioso** para manipular el comportamiento del sistema.  

> ---

> **🎯 ¿Cómo funcionan?**  
> Se aprovechan de **entradas mal protegidas** en formularios, URLs o cabeceras HTTP para inyectar código malicioso.
> 
> Esto permite **ejecutar comandos**, **robar información** o **tomar el control** de la aplicación.  
> A menudo, los atacantes analizan los **mensajes de error** generados por el sistema para obtener más detalles sobre su funcionamiento.  

> ---

> **📝 Inyección de código**
> Si el atacante conoce el lenguaje de programación, base de datos o sistema operativo, **inyecta código** en campos de entrada para obligar al servidor a ejecutar acciones no previstas.  

> ---

> **💻 Command Injection**
> Se introducen **comandos del sistema operativo** en lugar de código y el servidor **ejecuta esos comandos** con los permisos de la aplicación.
> 
> Puede llevar a la **ejecución remota de código (RCE)**.
> 
> **Ejemplo**  
> El atacante ingresa en un campo de formulario   
> ```bash
> ; rm -rf /
> ```
> Esto podría borrar archivos del servidor si no hay protecciones adecuadas.

> ---

> **🛢️ SQL Injection**
> Este ataque explota vulnerabilidades en aplicaciones web que interactúan con bases de datos.
> 
> Si los datos ingresados por el usuario no son correctamente validados, un atacante puede insertar código SQL malicioso para:
> - *Acceder* a datos privados sin autorización.  
> - *Modificar* o *eliminar* registros.  
> - *Ejecutar comandos peligrosos* en la base de datos.
> 
> **Ejemplo de inyección clásica**
> ```sql
> SELECT * FROM usuarios WHERE usuario = 'admin' AND contraseña = '';
> ```
> 
> Si no hay una validación adecuada, un atacante podría escribir
> ```sql
> ' OR '1'='1
> ```
> 
> Esto convertiría la consulta en
> ```sql
> SELECT * FROM usuarios WHERE usuario = 'admin' OR '1'='1';
> ```
> 
> Y devolvería **todos los registros de la base de datos** 😨.

> ---

> **📜 Inyección de XPath**
> XPath es un lenguaje para navegar documentos XML. Si la aplicación no valida correctamente los datos, un atacante puede manipular las consultas XPath y extraer información no autorizada.
> 
> **Ejemplo**
> ```xml
> //usuarios/usuario[nombre='admin' and clave='']
> ```
> 
> Si el atacante introduce
> ```xml
> ' or '1'='1
> ```
> 
> **Obtendrá acceso a todos los usuarios 😱**

> ---

> **🖥️ Command Injection**
> Este ataque ocurre cuando una aplicación ejecuta comandos del sistema operativo sin restricciones adecuadas.
> 
> Un atacante puede inyectar comandos en los campos de entrada y tomar el control del servidor.
> 
> **Ejemplo de vulnerabilidad en PHP**
> ```php
> $usuario = $_GET['usuario'];
> system("ping " . $usuario);
> ```
> 
> Si el atacante introduce
> ```sh
> ; rm -rf /
> ```
> 
> **¡Se puede borrar el sistema entero! 💀**

> ---

> **📨 Inyección de CRLF**
> Este ataque introduce caracteres de salto de línea (`\r\n`) en las respuestas HTTP, lo que permite modificar cabeceras o inyectar contenido malicioso.
> 
> **Ejemplo de cabecera vulnerable**
> ```http
> HTTP/1.1 200 OK
> Set-Cookie: usuario=admin
> ```
> 
> Si el atacante introduce
> ```perl
> admin%0D%0ASet-Cookie:%20admin%3Dtrue
> ```
> 
> **Podría alterar cookies y obtener acceso sin autenticación 😵**

---

## PicoCTF - Aprende Ciberseguridad

> **🔍 ¿Qué es PicoCTF?**
> **PicoCTF** es una plataforma educativa diseñada por *Carnegie Mellon University* para enseñar *ciberseguridad* de forma práctica a través de desafíos de tipo **Capture The Flag (CTF)**.
> 
> [Página Oficial de PicoCTF](https://picoctf.org/)

> ---

> **🛠️ ¿Cómo funciona?**  
> Los desafíos están diseñados como **retos de hacking ético** con niveles desde principiante hasta avanzado. Se enfocan en áreas como **criptoanálisis, explotación web, forense digital, programación y binarios**.
> 
> Ideal para aprender sobre **ataques reales** como SQL Injection, XSS o buffer overflows de manera segura.
> 
> **🕵️‍♂️ Ejemplos de desafíos sobre SQL Injection**
> - [Basic SQL Injection](https://primer.picoctf.org/vuln/web/basicsql.php)  
> - [Blind SQL Injection](https://primer.picoctf.org/vuln/web/blindsql.php)  

---

## Forgeries - Falsificación Digital

> **🔍 ¿Qué son los ataques de forgeries?**  
> Los ataques de **forgeries** buscan **crear, imitar o adaptar** un entorno, aplicación o servicio real para **engañar al cliente** con intenciones maliciosas.  
> _Forgery_ significa **falsificación**.
> 
> **⚠️ El ataque más común en este tipo es el **Cross Site Scripting (XSS)** a aplicaciones web.**  
>
> Según los datos, al menos el **40% de los sitios web** presentan vulnerabilidades que permiten este tipo de ataques.

> ---

> **💻 ¿Cómo funcionan las aplicaciones web?**
> Las aplicaciones web suelen mezclar **contenido estático** (fijo) con **contenido dinámico** que proviene de una base de datos.
> 
> *Contenido estático*
> HTML fijo, imágenes, CSS.
> 
> *Contenido dinámico*
> Información actualizada por el usuario, como en foros, blogs o redes sociales.  
> 
> **🔑 El problema**
> Los usuarios maliciosos pueden aprovechar los componentes dinámicos para **insertar código malicioso** (como scripts). Si la página se actualiza, el navegador lee el código, lo interpreta y lo ejecuta.
> 
> Este tipo de ataque puede pasar desapercibido, ya que se inyecta código dentro de contenido legítimo y la aplicación lo presenta como si fuera parte del sistema original.

> ---

> **💻 Ataques de Clickjacking**  
> El **clickjacking** es un ataque en el que se engaña al usuario para que haga clic en un enlace o realice una acción sin saberlo, o creyendo que lo hace con otro propósito.  
> 
> Los objetivos pueden variar, desde **seguir a alguien en Twitter** hasta **dar un "Like" en Facebook** sin el consentimiento del usuario.  
> 
> El atacante utiliza una combinación de **HTML** e **iframe** para cargar una página web legítima de manera oculta, y superponerla con otro enlace aparentemente inocente. Si el enlace se posiciona correctamente, el usuario puede hacer clic en algo diferente a lo que cree.  
> 
> A diferencia de los ataques XSRF, el **clickjacking** puede aprovecharse de páginas que requieren autenticación sin perder la sesión del usuario.

---

## Cross-Site Scripting (XSS)

> **🎯 ¿Qué es XSS?**
> Cross-Site Scripting (XSS) es una vulnerabilidad web que permite a los atacantes **comprometer las interacciones** de los usuarios con el sitio web vulnerable.
> 
> Su gravedad puede variar, desde abrir **ventanas emergentes** hasta **robar información** o **comprometer el equipo del usuario**. Lo más común es que el atacante pueda hacerse pasar por la víctima, obteniendo **los mismos privilegios** que esta. 🔓💻

> ---

> **🔍 Funcionamiento**  
> El atacante manipula la página web vulnerable para que **devuelva código JavaScript malicioso**. Este código se ejecuta en el **navegador del usuario**, comprometiendo las interacciones con el servidor o el cliente. 🛠️
> 
> **⚠️ Confirmación de Vulnerabilidad**  
> Una manera simple de verificar la vulnerabilidad es inyectar código que haga que el navegador ejecute **JavaScript**.
> 
> Un ejemplo sencillo es la función `alert()`, que no representa ningún peligro para el navegador o el equipo.
> 
> En algunos navegadores, si esta función está deshabilitada, se puede usar `print()` como alternativa. 🖨️

> ---

> **🔐 DOM-based XSS (XSS Local)**  
> Este tipo de ataque ocurre en el **lado del cliente** cuando un usuario accede a una página web manipulada. En lugar de depender del servidor para inyectar el código malicioso, este ataque se ejecuta directamente en el navegador del usuario.  
> 
> El navegador descarga e interpreta el código malicioso sin realizar ninguna comprobación, lo que permite al atacante ejecutar scripts dañinos que pueden comprometer la seguridad del usuario. El código malicioso suele instalarse en un archivo dentro del navegador, y desde ahí se ejecuta sin que el usuario se dé cuenta.  

> ---

> **⚠️ Reflected XSS (XSS no almacenados)**  
> Este tipo de ataque ocurre cuando una página web recibe datos a través de una petición HTTP y, de forma insegura, incluye esa información directamente en la respuesta.  
> 
> Un ejemplo común es una página web de búsqueda donde el término de búsqueda es un parámetro en la URL.
> 
> Supongamos que la URL es
> ```http
> https://ejemplo.com/search?term=seguridad
> ```
> La respuesta sería algo como
> ```html
> <p>Resultados de búsqueda para: seguridad</p>
> ```
> 
> Sin embargo, un atacante podría manipular la URL para incluir un **script malicioso** de la siguiente manera
> ```http  
> https://ejemplo.com/search?term=<script>/*+Cod.Malicioso+*/</script>
> ```
> 
> Esto haría que la respuesta sea
> ```html
> <p>Resultados de búsqueda para: <script>/* Cod.Malicioso */</script></p>`  
> ```
> 
> Este tipo de ataque puede ser aprovechado para ejecutar código en el navegador de la víctima, lo que podría comprometer la seguridad de la aplicación y la información del usuario.

> ---

> **⚠️ Stored XSS (XSS almacenados)**  
> Este tipo de ataque ocurre cuando una página web almacena contenido generado por el usuario y lo incluye en futuras respuestas HTTP, sin realizar las adecuadas validaciones de seguridad.  
> 
> Un ejemplo común es una página de comentarios donde un usuario envía su mensaje, y este se almacena en la base de datos para mostrarlo posteriormente a otros usuarios.  
> 
> Supongamos que un usuario envía un comentario con el siguiente contenido
> ```http
> POST /post/comment HTTP/1.1
> Host: vulnerable-website.com
> Content-Length: 100
> postId=3&comment=Me+encanta+este+post.+Seguro+que+apruebo
> &name=Pepe&email=pepe%40usuario.com
> ```
> 
> La respuesta del servidor podría ser
> ```html
> <p>Me encanta este post. Seguro que apruebo.</p>
> ```
> 
> Sin embargo, un atacante podría enviar un comentario con un **script malicioso**, como el siguiente
> ```html
> <script>/* Script malicioso */</script>
> ```
> 
> Este comentario se almacenaría como
> ```http
> comment=%3Cscript%3E%2F*%2BScript%2Bmalicioso%2B*%2F%3C%2Fscript%3E
> ```
> 
> Y cuando otro usuario visite la página, la respuesta del servidor podría ser
> ```html
> <p><script>/* Script malicioso */</script></p>
> ```
> 
> Este tipo de ataque puede afectar a todos los usuarios que visiten el sitio web, ya que el **script malicioso** se ejecutará en sus navegadores sin que lo sepan, comprometiendo así la seguridad de la aplicación y la privacidad de los usuarios.  

> ---

> **⚔️ Cross-Site Request Forgery (XSRF)**
> El ataque **XSRF** (Cross-Site Request Forgery), también conocido como **Session Riding**, aprovecha las credenciales de sesión de un usuario para realizar acciones maliciosas sin su conocimiento.
> 
> El atacante crea una solicitud maliciosa que se envía desde un sitio confiable, haciendo que la víctima ejecute un código que afecte a un sistema o aplicación en la que ya está autenticado.  
> 
> El ataque es posible porque, en la mayoría de los casos, la autenticación se gestiona mediante **cookies**, y como la víctima ya está autenticada, el sistema autoriza el acceso a la solicitud maliciosa.  
> 
> Por ejemplo, el atacante podría enviar un enlace malicioso como el siguiente
> ```html
> <a href="http://www.universidad.es/calificacion?alumno=Pepe&valor=10">Pincha aquí</a>
> ```
> 
> Si la víctima está autenticada en la página **universidad.es**, al hacer clic en el enlace se modificaría la calificación del alumno **Pepe** sin que la víctima lo sepa.  
> 
> Este tipo de ataque se puede ejecutar a través de **XSS** de tipo 1 o 2.

> ---

> **🛡️ Prevención de XSRF y XSS**  
> Para protegerse de ataques **XSRF** y **XSS**, se utilizan **Content Security Policies (CSPs)**, que son medidas de seguridad implementadas por los navegadores.  
> 
> Los **CSPs** limitan los recursos que una página web puede cargar y desde qué dominios. Esto evita la ejecución de scripts maliciosos y restringe el uso de scripts solo a aquellos provenientes del mismo dominio, protegiendo la seguridad de la aplicación web.

---