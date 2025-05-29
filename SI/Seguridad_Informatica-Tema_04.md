---
tags: URJC URJC_SI
---

# Tema 4 - Seguridad Informática

---

## Tabla de Contenidos

1. [Protocolos de Redes TCP / IP](#Protocolos%20de%20Redes%20TCP%20/%20IP)
2. [Protocolos Clave para la Conectividad](#Protocolos%20Clave%20para%20la%20Conectividad)
3. [ARP Poisoning, ARP Spoofing y MitM](#ARP%20Poisoning,%20ARP%20Spoofing%20y%20MitM)
4. [TCP Hijacking](#TCP%20Hijacking)
5. [Rogue DHCP](#Rogue%20DHCP)
6. [Typosquatting](#Typosquatting)
7. [Denial of Service (DoS)](#Denial%20of%20Service%20(DoS))
8. [DoS Distribuido (Distributed DoS, DDos)](#DoS%20Distribuido%20(Distributed%20DoS,%20DDos))
9. [Ataque DDoS por Reflexión](#Ataque%20DDoS%20por%20Reflexión)
10. [Ataque DDoS por amplificación](#Ataque%20DDoS%20por%20amplificación)

---

## Protocolos de Redes TCP / IP

> **🌐 ¿Qué son los protocolos de Internet?**
> Los protocolos son el conjunto de reglas que permiten la transmisión de datos entre redes de ordenadores.
> 
> Los dos más importantes son TCP e IP, que permiten la comunicación entre equipos, independientemente del sistema operativo o de las redes en las que están.

> ---

>**📡 Modelos de Comunicación**
>
> *🔵 Modelo TCP/IP*
> Es el modelo que sustenta Internet y permite la comunicación entre equipos. Es la base para la transmisión de datos entre redes.
> 
> *🌍 Modelo OSI*
> Es el modelo para la Interconexión de Sistemas Abiertos (OSI), con 7 capas que definen cómo se comunican los sistemas.
> 
> Cada capa realiza una función específica y se apoya en la capa inferior.

> ---

> **🖥️ Las 7 Capas del Modelo OSI**
> 
> *📱 Capa de Aplicación*
> Proporciona servicios utilizados por las aplicaciones.
> 
> *📝 Capa de Presentación*
> Define el formato de los datos intercambiados entre aplicaciones.
> 
> *💬 Capa de Sesión*
> Controla el diálogo entre las aplicaciones.
> 
> *🚚 Capa de Transporte*
> Divide los datos en fragmentos para intercambiarlos entre sistemas.
> 
> *🌍 Capa de Red*
> Define el camino que seguirán los datos.
> 
> *🔗 Capa de Enlace de Datos*
> Gestiona el direccionamiento físico dentro de la red.
> 
> *⚡ Capa Física*
> Controla las señales físicas que viajan por la red.

---

## Protocolos Clave para la Conectividad

> **🔍 DNS (Domain Name System)**  
> Se encarga de traducir el nombre de dominio a una dirección IP. Un cliente envía una solicitud a su servidor DNS, que responde si tiene la información o la reenvía a otro servidor.
> 
> **🔑 ARP (Address Resolution Protocol)**  
> Busca la dirección MAC correspondiente a una IP. Se envía una solicitud ARP y la máquina receptora responde con la dirección MAC correspondiente.
> 
> **📦 TCP / IP**  
> Utiliza el sistema *three-way handshake* para establecer una conexión entre el cliente y el servidor, sincronizando y asegurando la recepción de los paquetes.
> 
> **⚠️ ICMP (Internet Control Message Protocol)**  
> Envía mensajes de error y operativos, como notificaciones de tiempo de vida expirado o un servicio no disponible.

---

## ARP Poisoning, ARP Spoofing y MitM

> **⚙️ Pila de Protocolos TCP / IP**  
> La pila se basa en identificadores y protocolos que traducen estos identificadores de manera transparente.
> 
> *Ejemplo*
> Nombre de dominio $\to$ Dirección IP $\to$ Dirección MAC.

> ---

> **⚠️ Técnicas de Poisoning**
> Los ataques de poisoning aprovechan los protocolos dinámicos para "envenenar" la traducción de direcciones, introduciendo información falsa en las cachés ARP de las víctimas.
> 
> Una vez que se tienen las tablas ARP envenenadas, se abre la posibilidad a diferentes ataques.
> 
> *Ejemplo*
> El atacante envía tramas ARP Reply falsas para envenenar las tablas ARP de sus víctimas, haciendo que las direcciones MAC asociadas con una IP sean incorrectas.

> ---

> **🔒 Ataques posibles**
> 
> *🔑 Man-in-the-Middle (MitM)*  
> El atacante intercepta y modifica la comunicación entre dos sistemas.
> 
> *🚫 Denegación de Servicio (DoS)*  
> Puede realizarse para hacer que muchos dispositivos se asocien con la MAC de la víctima.
> 
> *🔐 Secuestro de sesión (Session Hijacking)*  
> El atacante suplanta la identidad de la víctima mediante el secuestro de su número de secuencia TCP o cookies.
> 
> **📡 Condiciones para un ataque exitoso**
> 1. Visibilidad del atacante sobre las víctimas y el router.
> 2. Envenenamiento continuo mediante tramas ARP Reply falsas.
> 3. Respuestas válidas del atacante para mantener la comunicación.

> ---

> **🚫 Contramedidas**
> 
> *🔒 Tablas ARP estáticas*
> Se pueden usar tablas ARP estáticas para prevenir el envenenamiento, aunque requiere mucho trabajo administrativo.
> 
> *💻 DHCP Snooping*
> Implementando DHCP Snooping, el switch puede analizar el tráfico y conocer en qué puerto se realizan las comunicaciones, mejorando la seguridad.
> 
> *🔧 Herramientas útiles*
> - **📧 ARPwatch**
> 	Notifica al administrador cuando una entrada ARP cambia.
> - **🔍 ReverseARP**
> 	Detecta clonación de direcciones MAC cuando se devuelve más de una IP para una MAC.

---

## TCP Hijacking

> **🔍 ¿Qué es el TCP Hijacking?**  
> A diferencia del **Spoofing**, donde la identidad se suplanta desde el inicio, el **TCP Hijacking** ocurre cuando el atacante toma control de una sesión ya establecida.
> 
> Después de que el usuario se ha logueado, el atacante se adueña de la sesión y actúa como si fuera el usuario legítimo.
> 
> Sin embargo, no puede iniciar la comunicación desde el principio, solo cuando la sesión ya está activa.

> ---

> **💡 Descripción del ataque**  
> Las comunicaciones TCP/IP se realizan intercambiando paquetes. La seguridad de una sesión TCP/IP depende de los **números de secuencia** y los **ACKs** intercambiados en cada paquete. 
> 
> *🔄 UDP*
> En UDP, el secuestro es inmediato, ya que no se utilizan números de secuencia.  
>
> *🔒 TCP*
> En TCP, no existen mecanismos para verificar la identidad del otro extremo, lo que hace que la comunicación sea vulnerable. En este caso, la seguridad depende únicamente del par **dirección MAC-dirección IP**.

> ---

> **📡 Parámetros de una conexión TCP**  
> Una conexión TCP se define por 4 parámetros:
> - *🌐 Dirección IP del emisor*.
> - *🌐 Dirección IP del receptor*.
> - *🔌 Puerto TCP del emisor*.
> - *🔌 Puerto TCP del receptor*.
> 
> Además, todos los paquetes incluyen dos números clave:  
> 
> *🔢 SEQ (32 bits)*
> El número de secuencia que se inicializa aleatoriamente y se incrementa conforme se envían datos (en los paquetes de control se incrementa por 1).
> 
> *🔑 ACK*
> El número de secuencia del siguiente paquete esperado.

> ---

> **🛠️ ¿Cómo se realiza el ataque de TCP Hijacking?**
> El atacante sigue estos pasos:
> 
> *1. 👀 Monitoreo*
> El atacante vigila el tráfico TCP entre los dos equipos que van a mantener la sesión a secuestrar (usualmente con un sniffer).
> 
> *2. ⏳ Espera*
> Espera a que ambos extremos negocien el inicio de la sesión y el tamaño de la ventana.
> 
> *3. 📥 Interceptación*
>    Una vez establecida la sesión, el atacante intercepta los números de secuencia y ACK.
> 
> *4. 🔄 Spoofing/MitM*
> El atacante, usando spoofing o un ataque MitM, envía datos al otro extremo con los números de secuencia y ACK correspondientes.
> 
> La víctima rechaza estos datos, ya que los parámetros ya no coinciden.
> 
> *5. 🎮 Secuestro de la sesión*
> La víctima pierde la capacidad de comunicarse con el receptor y piensa que su sesión fue cerrada. Sin embargo, el atacante tiene ahora el control completo de la sesión.

---

## Rogue DHCP

> **⚠️ ¿Qué es el Rogue DHCP?**
> Tipo de ataque que se basa en la implementación de un **servidor DHCP falso** para engañar a los clientes y tomar el control de su configuración de red.
> 
> El objetivo de este ataque **no** es un MitM tradicional.

> ---

>**🔍 ¿Qué es el DHCP?**
> Dynamic Host Configuration Protocol (DHCP) es un protocolo que sirve para asignar una dirección IP a una máquina, de manera automática, así como la configuración completa a nivel TCP / IP.
> 
> Es un protocolo **muy utilizado** ya que simplifica el esfuerzo de administración. Sin embargo, el problema radica en que la funcionalidad del protocolo es un poco anárquica.
> 
> **🔄 Proceso de asignación DHCP**
> 
> *1. 🔎 DISCOVERY*  
> El cliente envía una solicitud en busca de un servidor DHCP.  
> 
> *2. 🎁 OFFER*  
> Un servidor DHCP responde con una oferta de configuración (IP, máscara, puerta de enlace, etc.).  
> 
> *3. 📩 REQUEST*  
> El cliente elige la oferta y solicita la asignación de esos parámetros.
> 
> *4. ✅ ACK*  
> El servidor confirma la asignación y el cliente aplica la configuración recibida.  

> ---

> **🚨 ¿Cómo se explota el Rogue DHCP?**
> Si hay **dos servidores DHCP** en la red, el cliente elegirá **el primero en responder**.
> 
> Un atacante puede implementar un **servidor DHCP falso** y responder antes que el legítimo.
> 
> - El atacante **asigna direcciones IP falsas**, redirigiendo el tráfico o dejando al cliente sin conexión.

> ---

> **🛠️ Técnicas avanzadas: DHCP ACK Injection**  
> - Evita conflictos con direcciones IP ya asignadas.
> - No requiere conocer el rango de direcciones IP de la red.
> 
> **⚙️ Método de ataque**
>    - 👁️ El atacante monitorea el tráfico de la red.  
>    - ⏳ Espera a que un cliente envíe un **REQUEST**.  
>    - 🎭 Inyecta un **ACK falso**, asignando su propia configuración maliciosa.  

---

## DNS Poisoning

> **💀 ¿Qué es el DNS Poisoning?**  
> Es un ataque que permite redirigir el tráfico de una página legítima hacia una web maliciosa.
> 
> **⚠️ Métodos de ataque**
> 
> *🦠 Infección del equipo*
> El atacante introduce un código malicioso en el dispositivo de la víctima para modificar la configuración del DNS.
> 
> *📡 Ataque Man-in-the-Middle (MitM)*
> El atacante intercepta la comunicación entre la víctima y el servidor DNS legítimo.
> 
> *🔧 DNS Server Hijack*
> Se explotan vulnerabilidades del router para modificar los servidores DNS y redirigir a la víctima a páginas falsas.

> ---

> **🚨 Riesgos del DNS Poisoning**
> 
>  *🔴 Robo de datos*
> Se pueden crear sitios falsos de bancos u otras entidades para capturar credenciales.
> 
> *🔴 Infección por malware*
> La víctima es redirigida a una web que distribuye virus, spyware o keyloggers.
> 
> *🔴 Bloqueo de actualizaciones de seguridad*
> Si los servidores DNS son alterados, las actualizaciones de software legítimas pueden ser bloqueadas.
> 
> *🔴 Censura*
> Se pueden modificar los DNS para restringir el acceso a ciertos sitios web.

---

## Typosquatting

> **🎭 ¿Qué es el Typosquatting?**  
> Es un ataque que se aprovecha de los errores tipográficos al escribir una URL, redirigiendo a la víctima a sitios maliciosos.  

> ---

> **📌 ¿Cómo funciona?**  
> 1. Un usuario comete un error al teclear la dirección web.  
> 2. En lugar de acceder al sitio legítimo, es dirigido a una página fraudulenta.  
> 3. El atacante puede usar este sitio para robar datos o distribuir malware.

> ---

> **🛡️ Medidas de protección**
> - 🏢 Las grandes empresas compran dominios con errores comunes para evitar fraudes.  
> - 🔎 Verifica siempre la URL antes de ingresar información sensible.  
> - 🛑 Usa herramientas de protección como extensiones anti-phishing.  

---

## Denial of Service (DoS)

> **🚫 ¿Qué es un ataque de Denegación de Servicio (DoS)?**  
> Tipo de ciberataque que busca hacer que un sistema, servicio o red quede inaccesible para sus usuarios legítimos.
> 
> Para lograrlo, el atacante satura los recursos del objetivo, como el ancho de banda, la capacidad de procesamiento o la memoria del sistema, impidiendo su funcionamiento normal.

> ---

> **💥 Tipos de ataques DoS**
> 
> *🔄 Inundación por ping (Ping Flood)*  
> En este ataque, el atacante envía una gran cantidad de paquetes ICMP (ping) al sistema objetivo. Como cada paquete requiere una respuesta, el servidor consume sus recursos al intentar procesarlos.
>   
> - Si el volumen de pings es lo suficientemente alto, la víctima no podrá responder a solicitudes legítimas.
> - Para evitar ser detectado, el atacante puede falsificar la dirección de origen de los paquetes.
> 
> Este ataque se dirige principalmente contra el ancho de banda de la red.  
> 
> *🎭 SYN Spoofing (Ataque a la tabla de conexiones TCP)*  
> Este ataque explota el mecanismo de establecimiento de conexiones TCP de tres vías (SYN-SYN / ACK-ACK). El atacante envía múltiples paquetes SYN con direcciones IP falsas, obligando al sistema objetivo a reservar recursos para completar la conexión.  
> - Como las direcciones IP son falsas, el sistema nunca recibe una respuesta ACK, dejando la conexión a la espera.  
> - Si se envían suficientes solicitudes SYN falsas, la tabla de conexiones TCP sellena y no puede procesar nuevas peticiones legítimas.
> 
> Esto afecta gravemente a servidores que dependen de conexiones TCP, como servidores web y de bases de datos.  
> 
> *📡 Ataque UDP Flood*  
> En este ataque, el atacante envía un gran número de paquetes UDP a puertos específicos del sistema víctima. Como los paquetes UDP no tienen un mecanismo de verificación, el servidor intenta procesarlos sin poder confirmar su autenticidad.  
> - Si los paquetes van dirigidos a un puerto con un servicio activo, el servidor intentará responder, consumiendo aún más recursos.  
> - En algunos casos, se aprovechan servicios como el **echo (puerto 7)** para generar respuestas automáticas, amplificando el ataque.  
> 
> Puede usarse para interrumpir servidores DNS, VoIP y otros servicios basados en UDP.  
> 
> *🌐 Inundaciones HTTP*
> Este tipo de ataque está dirigido a servidores web y consiste en enviar una gran cantidad de peticiones HTTP para consumir los recursos del sistema y ralentizar o colapsar el servicio. Existen diferentes variantes:
> 
> **1. 📌 Fragmentación HTTP**
> Se establecen conexiones HTTP válidas, pero el tráfico de datos se divide en pequeños fragmentos que se envían muy lentamente.
>   
> Esto evita que el servidor cierre la conexión por inactividad, manteniéndola abierta durante largos períodos.
>  
> Con suficientes conexiones activas, los recursos asignados a la gestión de sesiones pueden agotarse.
> 
> **2. 📌 Conexiones HTTP excesivas**
> Se generan múltiples conexiones simultáneas al servidor web, solicitando archivos grandes o recursos que requieren mucho procesamiento.
> 
> Un atacante puede, por ejemplo, solicitar repetidamente una imagen de gran tamaño o un archivo pesado.
> 
> Esto fuerza al servidor a usar su ancho de banda y recursos de CPU en solicitudes maliciosas en lugar de atender a usuarios legítimos.
> 
> **3. 📌 Peticiones masivas en una sola sesión**
> En lugar de realizar múltiples conexiones, el atacante agrupa muchas solicitudes en un único paquete HTTP.
> 
> Cada solicitud debe ser procesada individualmente, lo que puede sobrecargar la capacidad de respuesta del servidor.
> 
> Este método se usa para evadir mecanismos de protección que limitan el número de conexiones por usuario.  
> 
> ⚠️ **Los ataques DoS pueden causar graves interrupciones en los servicios y pérdidas económicas. Por eso, se recomienda implementar medidas de mitigación como firewalls, sistemas de detección de intrusos (IDS) y herramientas anti-DDoS.**  

---

## DoS Distribuido (Distributed DoS, DDos)

> **🌐 ¿Qué es un ataque DDoS?**  
> Un ataque de Denegación de Servicio Distribuido (DDoS) es una variante del DoS en la que múltiples dispositivos atacan simultáneamente a un mismo objetivo.  
>   
> **⚙️ ¿Cómo se lleva a cabo?**
> 
> *1. 🧟‍♂️ Infección*
> Un atacante primero compromete equipos o redes y los convierte en "zombis".
> 
> *2. 🌍 Organización*
> Estos dispositivos infectados se organizan en una red llamada **botnet** y son controlados de forma remota.
> 
> *3. 💥 Ataque*
> Cuando el atacante da la orden, todos los zombis envían tráfico al objetivo, saturando sus recursos y provocando que deje de responder a solicitudes legítimas.
>   
> A diferencia de un ataque DoS tradicional, un DDoS es mucho más difícil de mitigar, ya que el tráfico proviene de múltiples fuentes.  

> ---

> **🔗 ¿Cómo se controlan las botnets?**  
> Originalmente, los atacantes utilizaban programas específicos para comunicarse con los dispositivos infectados.
> 
> Actualmente, las botnets suelen operar a través de **servidores HTTP o IRC**, lo que las hace más difíciles de rastrear. Además, incluyen mecanismos criptográficos para evitar ser detectadas mediante análisis de tráfico en la red.  

> ---

> **🦠 Creación y uso de botnets**
> Las botnets pueden crearse a través de ataques con malware que infectan dispositivos.  
> 
> Sin embargo, hoy en día es posible **alquilar botnets en la Deep Web**, permitiendo que atacantes sin conocimientos técnicos las utilicen. Las botnets ya no solo incluyen computadoras, sino también **dispositivos IoT**.
> 
> Muchos dispositivos IoT son inseguros porque los fabricantes no implementan medidas de seguridad adecuadas y los usuarios no cambian las configuraciones por defecto.  

> ---

> **📌 Caso real - Mirai**  
> Mirai es un malware que **escanea internet** en busca de dispositivos IoT vulnerables. Si un dispositivo IoT tiene credenciales por defecto o está desprotegido, Mirai lo infecta y lo integra a su botnet.
> 
> En 2016, Mirai fue utilizado para lanzar un ataque masivo contra **Dyn**, un proveedor de DNS, afectando a servicios como **Twitter, Reddit, Spotify, PayPal y CNN**.  

> ---

> **📆 Ejemplos de ataques DDoS famosos**
> 
> *🎮 Navidades de 2014*
> Ataques DDoS derribaron **PlayStation Network y Xbox Live**, impidiendo a millones de jugadores conectarse durante las festividades.
> 
> *🌍 Octubre de 2016*
> Un ataque masivo dirigido a **Dyn (proveedor de DNS)** afectó a grandes plataformas como **Twitter, Reddit, Spotify y CNN**.
> 
> *💥 Verano de 2021*
> Se reportó el mayor ataque DDoS hasta la fecha, alcanzando **330 millones de solicitudes en segundos** con una tasa de **17,2 millones de peticiones por segundo (rps)**.
> 
> *🕵️‍♂️ Botnet Meris (2021)*
> Batió récords con **21,8 millones de rps** y utilizó **250.000 dispositivos** para atacar infraestructuras en **Rusia, Reino Unido, EE.UU. y Nueva Zelanda**.
> 
> *🚀 Junio de 2020*
> Amazon AWS lidió con un **ataque de 2,3 Tbps**, superando el promedio de ataques DDoS volumétricos, que suelen rondar los **500 Gbps**.
> 
> *📂 GitHub (2018)*
> Recibió un ataque de **1,3 Tbps**, uno de los más grandes dirigidos contra una plataforma de desarrollo.

> ---

> **🔐 ¿Cómo mitigar un ataque DDoS?**
>   
> *1. 🛑 Firewalls y filtrado de tráfico*
> Configurar reglas que bloqueen tráfico sospechoso.
> 
> *2. 🌍 Uso de CDNs (Redes de Distribución de Contenidos)*
> Ayudan a distribuir la carga y mitigar ataques volumétricos.
> 
> *3. 📡 Servicios anti-DDoS*
> Plataformas como Cloudflare, AWS Shield y Akamai ofrecen protección avanzada contra estos ataques.
> 
> *4. 📊 Monitoreo de tráfico*
> Implementar sistemas de detección de anomalías para identificar picos inusuales de tráfico.
> 
> *5. 🔑 Segurizar dispositivos IoT*
> Cambiar credenciales por defecto y mantener firmware actualizado.
> 
> **⚠️ Un ataque DDoS puede generar pérdidas millonarias y dejar fuera de servicio a empresas e instituciones enteras. La mejor estrategia es una combinación de prevención, monitoreo y mitigación activa.**  

---

## Ataque DDoS por Reflexión

> **🔄 ¿Qué es un Ataque DDoS por Reflexión?**
> Un ataque DDoS por reflexión es un tipo de ataque con intermediario, donde la acción del atacante se refleja contra la víctima.
> 
> En algunos casos, esto puede generar un bucle de tráfico entre el intermediario y la víctima, agravando el impacto del ataque.

> ---

> **🕵️‍♂️ Ataque por intermediario**
> 
> *1. 🔍 Suplantación de identidad*
> El atacante envía paquetes de petición a un servicio, pero usa la dirección de la víctima como origen.
> 
> *2. 🚀 Amplificación del tráfico*
> Se eligen servicios que generan respuestas voluminosas para que el tráfico reflejado contra la víctima sea aún mayor.
> 
> *3. 🎯 Doble beneficio*
> Si el atacante logra redirigir todo el tráfico, la víctima sufrirá una sobrecarga masiva.
> 
> Si no, el ataque quedará camuflado entre el tráfico legítimo de la red.  

> ---

> **🌍 Ejemplo con DNS**
> Una petición DNS típica es un paquete UDP de **60 bytes**, pero la respuesta puede ser de hasta **512 bytes** o más.
> 
> Los atacantes aprovechan servidores DNS que generan respuestas de gran tamaño (hasta **4000 bytes**) debido a características como IPv6 y seguridad.
> 
> **💥 Secuencia del ataque**
> 1. El atacante envía múltiples peticiones DNS falsificadas con la dirección de la víctima.  
> 2. Los servidores DNS seleccionados responden directamente a la víctima, generando una avalancha de tráfico mucho mayor al tráfico de origen. 

> ---

> **🔁 ¿Cómo se genera un bucle de tráfico?**
Si la víctima tiene activado el **servicio de eco**, puede entrar en un **bucle infinito** con el servidor DNS intermediario.  

---

## Ataque DDoS por amplificación

> **💥 ¿Qué es un Ataque DDoS por amplificación?**
> 
> *🔄 Similar al de reflexión*
> Se utilizan muchos intermediarios para amplificar el tráfico.
> 
> *📡 Dirección de broadcast*
> La petición inicial se dirige a la dirección de broadcast de una red, lo que hace que todos los hosts respondan.  
>  
> **Ejemplos**  
> - 🐸 **Smurf**
> 	Se utiliza un ping (ICMP) para amplificar el tráfico.
> - 💬 **Fraggle**
> 	Utiliza el servicio de eco (UDP) para amplificación.

> ---

> **⚡ Herramienta de ataque - Slowloris**
> El atacante abre múltiples conexiones HTTP al servidor y envía cabeceras incompletas.
> 
> Esto provoca que el servidor cree un hilo por cada petición. Si la petición tarda mucho, el servidor espera un tiempo de espera (timeout).
> 
> El atacante sigue enviando cabeceras incompletas para evitar el timeout. Cuando el servidor se queda sin hilos disponibles, se genera un DoS porque no puede manejar más conexiones.

---