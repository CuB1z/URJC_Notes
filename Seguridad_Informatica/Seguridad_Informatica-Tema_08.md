---
tags: URJC URJC_SI
---

# Tema 8 - Seguridad Informática

---

## Tabla de Contenidos

1. [Introducción](#Introducción)
2. [Firewalls y DMZs](#Firewalls%20y%20DMZs)
3. [Honeypots](#Honeypots)
4. [Redes Privadas Virtuales (VPN)](#Redes%20Privadas%20Virtuales%20(VPN))
5. [IPSec](#IPSec)
6. [SSL/TLS](#SSL/TLS)
7. [Resumen](#Resumen)

---

## Introducción

> **🌐 Seguridad en la topología**
> Las **redes modernas** pueden adoptar diversas **topologías físicas y lógicas** (estrella, bus, anillo, malla, árbol...), cada una con ventajas y desafíos en cuanto a rendimiento y redundancia.
> 
> Sin embargo, **la seguridad debe estar garantizada sin importar el diseño**, a través de contramedidas específicas adaptadas a la estructura de red.
> 
> Algunos principios clave para una topología segura:
> 
> *🌍 Nivel de exposición*
> A mayor conectividad con internet, mayor debe ser la protección perimetral (firewalls, IDS/IPS, proxies, DMZ...).  
> 
> *🧱 Segmentación de redes*
> Dividir la red en **subredes separadas** ayuda a contener ataques y aplicar diferentes niveles de seguridad.
> 
> *🎯 Zonificación por función o sensibilidad*
> Por ejemplo, una red de usuarios comunes no debe tener acceso directo a servidores críticos o bases de datos sensibles.
> 
> *📊 Políticas de acceso adecuadas*
> Control de tráfico interno con listas blancas, VLANs, ACLs, y firewalls internos.
> 
> Una **topología segura no es solo física**, también debe contemplar aspectos lógicos y organizativos: control de accesos, monitoreo continuo y respuesta a incidentes en cada segmento de red.

---

## Firewalls y DMZs

> **🧱 ¿Qué es un Firewall?**
> Un **firewall** es un dispositivo físico o software que **filtra y controla el tráfico de red**, basado en un conjunto de reglas predefinidas.
> 
> Su función es decidir qué tráfico puede entrar o salir de una red según criterios como dirección IP, puertos o protocolos.
> 
> Se sitúa entre redes con distintos niveles de confianza (por ejemplo, entre **Internet y una red corporativa interna**).
> 
> Un error frecuente es dejar configuraciones por defecto, lo cual puede exponer servicios innecesarios o inseguros.

> ---

> **📋 Tipos de Firewalls**
> Según el nivel de análisis y control, podemos encontrar:
> 
> *📦 Packet Filtering*
> Filtra paquetes por campos simples como IP, puerto y protocolo. Es rápido, pero **muy limitado** en seguridad.
> 
> *🔄 Stateful Inspection*
> Mantiene el **estado de las conexiones** y permite decisiones más contextuales sobre el tráfico.
> 
> *🧍‍♂️ Proxy Firewall*
> Actúa como **intermediario** entre cliente y servidor. Analiza a nivel de aplicación (ej. HTTP, FTP).
> 
>*🧬 Deep Packet Inspection (DPI)*
>Analiza el **contenido interno de los paquetes**, detectando malware, intrusiones o patrones sospechosos.

> ---

> **📑 Reglas y políticas**
> Las reglas de firewall determinan qué tráfico es permitido o bloqueado. Existen dos enfoques generales:
> 
> *✅ Permisivas*
> Permiten todo excepto lo explícitamente prohibido.
> 
> *🔒 Restrictivas*
> Bloquean todo excepto lo explícitamente autorizado (**más seguras**).
> 
> Estas reglas pueden aplicarse en distintos niveles:
> *🧱 Firewalls de perímetro*
> Dispositivos de hardware entre la red interna y externa.
> 
> *🖥️ Firewalls de host*
> Software instalado en sistemas individuales que protege ese único nodo.

> ---

> **🕹️ Bastion Hosts y DMZs**
> Un **bastion host** es un equipo **altamente expuesto** que ha sido reforzado para resistir ataques. Suele ofrecer servicios a internet (como un servidor web) y tiene estrictas políticas de seguridad.
> 
> Una **DMZ (Demilitarized Zone)** es una red intermedia ubicada entre la red interna y la red externa:
> - Aísla los servicios expuestos al público (servidores web, correo, DNS) para evitar que un atacante los use como puente hacia la red privada.  
> - Protege la red interna incluso si un servidor público es comprometido.
> 
> **🏗️ Implementación común**
> *🔀 Firewall de tres interfaces*
> Una para la red interna, una para la DMZ y otra para Internet.
> 
> *🧩 Doble firewall*
> Uno externo para proteger la DMZ del mundo exterior y otro interno que aísla la DMZ de la red privada.
> 
> Firewalls y DMZs son herramientas esenciales dentro de una arquitectura de defensa en profundidad, combinadas con IDS/IPS, monitoreo, y segmentación de red.


---

## Honeypots

> **🍯 ¿Qué es un Honeypot?**
> Un **honeypot** es un sistema o recurso deliberadamente expuesto y vulnerable que **simula ser un activo real de la red** con el objetivo de atraer, detectar, estudiar y desviar a posibles atacantes.
> 
> Su principal finalidad no es evitar un ataque, sino **observar el comportamiento del atacante**, capturar información sobre métodos y herramientas usadas, y reforzar la seguridad general de la red.
> 
> Puede simular un servidor web, una base de datos, un servicio SSH o incluso una red completa, todo diseñado para ser lo suficientemente convincente como para atraer a un actor malicioso.

> ---

> **📊 Objetivos**
> Los honeypots son útiles en múltiples frentes de la seguridad ofensiva y defensiva:
> - *📈 Registrar intentos de acceso no autorizados* y comportamientos anómalos.  
> - *🔬 Estudiar técnicas y herramientas* utilizadas por los atacantes, incluyendo exploits o malware.  
> - *🧨 Detectar ataques 0-day* o nuevas variantes de amenazas aún no catalogadas.  
> - *🎯 Distraer a los atacantes* y ganar tiempo para responder mientras intentan vulnerar un sistema falso.

> ---

> **🧠 Buenas prácticas**
> Para que un honeypot sea efectivo (y no un riesgo), debe estar cuidadosamente diseñado:
> - 🧑‍💻 Debe **parecer legítimo**: debe simular servicios, tráfico, archivos o incluso usuarios reales.  
> - 🚫 Nunca usar **configuraciones por defecto** ni dejar huellas que indiquen que se trata de un señuelo.  
> - 🧱 Debe estar **completamente aislado** del entorno productivo para evitar que sea usado como puente para ataques internos.  
> - ❗ Nadie del personal debe usarlo, para evitar comprometerlo accidentalmente.

> ---

> **🔄 Según su propósito**
> *🏭 Producción*
> Usados en entornos operativos para detectar y ralentizar ataques reales.
> 
> *🧪 Investigación*
> Instalados por analistas y centros de ciberseguridad para **estudiar amenazas avanzadas** y nuevas técnicas de ataque.

> ---

> 🔌 **Según nivel de interacción**
> *🧊 Baja interacción*
> Simula uno o pocos servicios, muy seguro pero limitado en la información recolectada.
> 
> *⚙️ Media interacción*
> Simula múltiples servicios, con más capacidad para engañar al atacante.
> 
> *🧠 Alta interacción*
> Entorno real o casi real (máquinas virtuales completas), mayor riesgo pero también mayor detalle y aprendizaje.

> ---

> **🧪 Ejemplos destacados de Honeypots**
>
> - **🎯 Propósito general**  
>   - `Honeytrap`: analiza ataques TCP/UDP.  
>   - `Dionaea`: simula servicios comunes como SMB, HTTP, FTP o MSSQL.  
>   - `Cowrie`: simula un servidor con SSH/Telnet para observar comandos interactivos.  
>   - `Glastopf`: orientado a vulnerabilidades web comunes.  
>   - `Conpot`: emula entornos de sistemas industriales (ICS).  
>   - `EMobility`: simula una red de carga de vehículos eléctricos.
>
> - **🌐 Honeypots Web**  
>   - `Nodepot`: emula servidores Node.js vulnerables.  
>   - `Google Hack Honeypot`: simula sitios vulnerables para ser detectados por motores de búsqueda maliciosos.
>
> - **🛠️ Honeypots de Bases de Datos (BBDD)**  
>   - `ElasticHoney`: finge ser una instancia de Elasticsearch.  
>   - `HoneyMySQL`: simula un servidor de bases de datos MySQL.
>
> - **📡 Honeypots para IoT**  
>   - `HoneyThing`: orientado a dispositivos de red vulnerables.  
>   - `Kako`: diseñado para dispositivos domésticos conectados.
>
> - **🕸️ Honeynet**  
>   - Conjunto coordinado de honeypots de alta interacción que conforman una red realista para detección, análisis y respuesta ante ataques.

---

## Redes Privadas Virtuales (VPN)

> **🔐 ¿Qué es una VPN?**
> Una **VPN (Virtual Private Network)** es un sistema que permite crear un **canal seguro y cifrado** para transmitir datos a través de una red pública como Internet.
> 
> Gracias a este túnel virtual, se protege la confidencialidad e integridad de la información, incluso en entornos inseguros como redes Wi-Fi públicas.
> 
> Las VPN son esenciales para:
> - 📡 Acceso remoto a redes empresariales.  
> - 🛡️ Proteger conexiones personales contra espionaje o filtrado.  
> - 🌍 Evitar censura o restricciones geográficas.

> ---

> **🏗️ Tipos**
> Según su propósito o escenario de uso, existen distintos tipos de VPN:
> 
> *🧑‍💼Acceso remoto*
> Permite a empleados conectarse de forma segura a la red corporativa desde cualquier ubicación.
> 
> *🏢 Intranet VPN*
> Conecta oficinas o sedes geográficamente separadas de una misma empresa, creando una red privada extendida.
> 
> *🤝 Extranet VPN*
> Otorga acceso restringido a usuarios externos (como proveedores o clientes) a recursos concretos de la red.

> ---

> **⚙️ Protocolos usados**
> Los protocolos VPN definen cómo se cifra y transporta la información. Algunos de los más comunes incluyen:
> 
> *🔐 SSL/TLS*
> Utilizado frecuentemente en VPNs de acceso remoto vía navegador (SSL VPN).
> 
> *🔐 IPSec*
> Muy usado en redes corporativas, cifra paquetes IP y proporciona integridad y autenticación.
> 
> *📡 PPTP*
> Obsoleto y considerado inseguro.
> 
> *🔁 L2TP + IPSec*
> Combina encapsulamiento y cifrado robusto.
> 
> *🔄 SSTP*
> Túnel sobre HTTPS, útil cuando otros protocolos son bloqueados.
> 
> *🔁 MPPE*
> Usado en Microsoft Point-to-Point Encryption.
> 
> *🧪 SSH Tunneling*
> Menos común como VPN, pero útil para túneles cifrados.

> ---

> **🔓 Clasificación**
> 
> *🌐 VPN abierta*
> Los datos se cifran, pero no requiere autenticación fuerte o personalizada. Común en servicios comerciales simples.
> 
> *🔐 VPN cerrada*
> Requiere **autenticación y autorización específicas**, como certificados digitales, tokens o credenciales corporativas. Ofrece un mayor nivel de seguridad.

---

## IPSec

> **📡 ¿Qué es IPSec?**
> **IPSec (Internet Protocol Security)** es un conjunto de **protocolos diseñados para proteger el tráfico IP** mediante **cifrado, autenticación e integridad de datos**.
> 
> Es obligatorio en IPv6 y opcional en IPv4, y puede aplicarse tanto en modo extremo a extremo como entre gateways.
> 
> Se utiliza frecuentemente en **VPNs corporativas** y en la protección de redes internas con alta sensibilidad de datos.

> ---

> **🔒 Servicios ofrecidos**
> *🕶️ Confidencialidad*
> *🧾 Integridad*
> *👤 Autenticación del origen*
> *🚫 Control de acceso*
> *🧯 Rechazo de paquetes modificados o no autorizados*

> ---

> **📦 Componentes clave**
> 
> *🤝 SA (Security Association)*
> Acuerdo unidireccional entre dos partes sobre algoritmos y claves a usar.
> 
> *🔑 IKE (Internet Key Exchange)*
> Protocolo que negocia dinámicamente los parámetros de seguridad y las claves criptográficas.
> 
> *🧾 AH (Authentication Header)*
> Proporciona integridad y autenticación, pero **no cifra** el contenido.
> 
> *🔐 ESP (Encapsulating Security Payload)*
> Proporciona **cifrado, autenticación e integridad**. Es el más utilizado.
> 
> *🗂️ SAD (Security Association Database)* y *SPD (Security Policy Database)*
> Almacenan configuraciones y reglas que definen cómo manejar cada paquete.

> ---

> **🌐 Modos de funcionamiento**
> 
> *🔄 Modo transporte*
> Protege la carga útil del paquete IP, ideal para comunicación directa entre dos dispositivos (host a host).
> 
> *🚪 Modo túnel*
> Cifra todo el paquete IP original y lo encapsula en uno nuevo. Es común en VPNs entre dos routers o firewalls.

> ---

> **📥 Funcionamiento general**
> 
> IPSec **añade cabeceras adicionales** a los paquetes IP existentes (AH o ESP, o ambos).
>  
> Los dispositivos intermedios **no pueden distinguir fácilmente** si un paquete es IPSec o tráfico IP normal, lo que mejora la opacidad del tráfico.
> 
> Utiliza **cifrado simétrico** (como AES o 3DES) para proteger datos y **HMAC (Hash-based Message Authentication Code)** para verificar integridad.

---

## SSL/TLS

> **🔐 SSL (Secure Sockets Layer) / TLS (Transport Layer Security)**
> **SSL y TLS** son **protocolos criptográficos** que funcionan entre la capa de aplicación y la capa de transporte del modelo OSI.
> 
> Su objetivo es **proteger la confidencialidad, integridad y autenticación** de la comunicación en protocolos como:
> - 🌐 HTTPS (navegación segura)  
> - 📤 SMTP (correo)  
> - 📁 FTP (transferencia de archivos)  
> - 📞 VoIP y otros protocolos de red
> 
> ❗ SSL está obsoleto (SSLv3 y anteriores). Hoy en día se usa exclusivamente **TLS**, siendo TLS 1.3 la versión más reciente y segura.

> ---

> **🎯 Funciones de seguridad**
> - *✅ Autenticación* del servidor y, opcionalmente, del cliente mediante certificados digitales.
> - *🔐 Cifrado simétrico* para mantener la **confidencialidad** de los datos transmitidos.
> - *🧾 MACs (Message Authentication Codes)* para verificar la **integridad** de los mensajes.
> - *📉 Compresión opcional* antes del cifrado (deshabilitada en versiones modernas por seguridad).
> - *🔗 Establecimiento de un canal seguro y confiable* para aplicaciones.

> ---

> **🤝 Fases del Handshake**
> El proceso de establecimiento de sesión segura se llama **handshake**, y consta de varias fases:
> 
> 1. 👋 **ClientHello** y **ServerHello**: cliente y servidor intercambian versiones, suites criptográficas compatibles, identificadores y números aleatorios.  
> 2. 📜 El servidor **envía su certificado digital**, y opcionalmente solicita el del cliente.  
> 3. 🔑 El cliente responde con su certificado (si se solicita) y genera un **pre-master secret**, que cifra usando la clave pública del servidor.
> 4. 🔐 Ambos derivan un **master secret compartido** y generan claves de sesión.  
> 5. 🔄 Se intercambia un mensaje **ChangeCipherSpec**, y a partir de este punto, la comunicación va cifrada.
> 
> ✅ A partir del master secret, se generan claves simétricas para cifrado y autenticación en ambas direcciones.


---

## Resumen

> **🧩 Comparativa entre VPNs: IPSec vs SSL**
> 
> La siguiente tabla compara las características más relevantes de dos de los protocolos más utilizados para implementar VPNs seguras:
> 
> 
> | Característica              | **IPSec**                             | **SSL/TLS**                            |
> |----------------------------|----------------------------------------|----------------------------------------|
> | 🔗 **Capa**                | Red (nivel 3 del modelo OSI)          | Aplicación (nivel 7 del modelo OSI)   |
> | 🔒 **Cobertura**           | Todo el tráfico de red                | Tráfico web o aplicaciones específicas |
> | ⚙️ **Configuración**       | Más compleja (requiere coordinación)  | Más sencilla y accesible               |
> | 🔑 **Acceso otorgado**     | Total a la red tras autenticación     | Acceso granular por servicio           |
> | 💻 **Cliente requerido**   | Software VPN dedicado                 | Navegador o app compatible             |
> | 🚶‍♂️ **Ideal para...**      | Redes corporativas controladas        | Usuarios remotos o móviles             |

> ---

> 📌 **Conclusión**:  
> - IPSec es más adecuado para conexiones permanentes entre sedes o redes completas.  
> - SSL/TLS VPN es ideal para trabajadores móviles, conexión desde dispositivos personales o cuando se busca simplicidad y compatibilidad.

> ---

> **💬 Consideraciones finales**
> 🛡️ La **defensa en profundidad** es el enfoque más robusto en ciberseguridad: consiste en aplicar **múltiples capas de protección** para mitigar riesgos incluso si una de ellas falla.  
> 🔐 Este enfoque debe contemplar:
> 
> - 🧱 **Perímetro**: uso de **firewalls**, segmentación, DMZs.  
> - 👀 **Monitoreo**: sistemas de **detección de intrusiones (IDS/IPS)**.  
> - 🍯 **Engaño**: empleo de **honeypots** para distraer y analizar al atacante.  
> - 🔒 **Cifrado del tráfico**: implementación de **VPNs (IPSec, SSL/TLS)** para proteger datos en tránsito.  
> - 🧬 **Control de acceso**: autenticación multifactor, políticas de mínimos privilegios, certificados digitales.  
> - 🧠 **Concienciación y formación** del personal: la primera línea de defensa siempre es el usuario.
> 
> 📢 La ciberseguridad no es un producto único, sino un **proceso continuo** que debe adaptarse a las amenazas en evolución y a las necesidades cambiantes del entorno digital.

---