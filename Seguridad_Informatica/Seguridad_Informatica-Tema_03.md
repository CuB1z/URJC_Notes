---
tags: URJC URJC_SI
---

# Tema 3 - Seguridad Informática

---

## Tabla de Contenidos

1. [Anatomía de un Ataque](#Anatomía%20de%20un%20Ataque)
2. [Técnicas de Hacking](#Técnicas%20de%20Hacking)
3. [Fases de un Ataque](#Fases%20de%20un%20Ataque)
4. [Footprinting](#Footprinting)
5. [Fingerprinting](#Fingerprinting)
6. [Ingeniería Social](#Ingeniería%20Social)
7. [Phishing](#Phishing)
8. [Sniffing](#Sniffing)
9. [Scanning / Mapping](#Scanning%20/%20Mapping)
10. [Anonimato](#Anonimato)

---

## Anatomía de un Ataque  

> **📌 Tipos de Ataques**
> Los ataques pueden ser **activos** (modifican o afectan un sistema) o **pasivos** (se limitan a la observación).  
> 
> *⚠️ Intercepción*
> Espionaje o redirección de comunicaciones sin autorización (**pasivo**).  
> 
> *🎭 Fabricación*
> Creación de activos falsos para engañar a usuarios (**activo**).
> 
> *🚧 Interrupción*
> Bloqueo del funcionamiento de un activo o comunicación (**activo**).  
> 
> *✍️ Modificación*
> Alteración no autorizada de un activo (**activo**).  

> ---

> 🕵️ **Tipos de Atacantes**  
> 
> *🏴 Black Hat Hackers*
> Explotan vulnerabilidades sin informar y suelen actuar con fines maliciosos.  
> 
> *⚪ White Hat Hackers*
> Hackers éticos que reportan vulnerabilidades y colaboran en su corrección.  
> 
> *🎮 Script Kiddies*
> Aficionados sin conocimientos profundos que usan herramientas automáticas.  
> 
> *🔓 Crackers*
> Especializados en romper sistemas criptográficos.

---

## Técnicas de Hacking

> **🔍 Recopilación de Información**
> 
> *🖥️ Footprinting*
> Se centra en la recolección de información pública de Internet. Su uso no conlleva la vulnerabilidad de ninguna ley, y por lo tanto, no es delito.
> 
> *🕵️‍♂️ Fingerprinting*
> Consiste en recolectar información más específica y que no es pública, lo tanto **es delito**.
> 
> - **🎭 Ingeniería Social**
> 	Manipulación de personas para obtener información.  
> - **📧 Phishing**
> 	Correos electrónicos fraudulentos que buscan datos personales.
> - **📱 Smishing**
> 	Variante del phishing, pero a través de SMS.
> - **🖥️ Sniffing**
> 	Captura de datos en una red local.
> - **🌐 Scanning/Mapping**
> 	Análisis de redes y dispositivos conectados.

> ---

> **🌐 Ataques en Red**
> 
> *🔄 ARP Poisoning*
> Envenenamiento de cachés ARP para redirigir tráfico de red.  
> 
> *🎭 ARP Spoofing*
> Suplantación de identidad en la capa de enlace mediante mensajes ARP falsos.  
> 
> *👥 Man In The Middle (MiM)*
> Intercepción de comunicaciones sin que las víctimas lo sepan.  
> 
> *🔓 TCP Hijacking (Secuestro de sesión)*
> Control no autorizado de una conexión TCP para manipular tráfico.  
> 
> *🛠️ Ataques en la capa de aplicación*
> - **🌍 DNS Poisoning**
> 	Envenenamiento de registros DNS.
> - **✏️ Typosquatting**
> 	Suplantación de dominios aprovechando errores tipográficos.
> - **📊 Ataques DDoS**
> 	Saturación de recursos con peticiones masivas.
> 
> **📎 Enlace al temario**
> [Seguridad Informática - Tema 4](Seguridad_Informatica-Tema_4.md)

> ---

> **📦 Desbordamiento de Buffer**
> 
> *💥 Buffer Overflow*
> Ocurre cuando un programa no controla correctamente la cantidad de datos copiados en un buffer.
> 
> Puede sobrescribir datos adyacentes, causando vulnerabilidades graves.
> 
> **Ejemplo**
> Si un nombre de usuario tiene un límite de 8 caracteres, pero se ingresa un valor más largo, podría sobrescribirse código ejecutable con instrucciones maliciosas.
> 
> **📎 Enlace al temario**
> [Seguridad Informática - Tema 5](Seguridad_Informatica-Tema_5.md)

> ---

> **💉 Inyecciones**
> 
> *🖥️ Inyecciones en servidor*
> - **⚙️ Shell Injection**
> 	Permite ejecutar comandos del sistema en el servidor.
> - **📊 Inyección SQL**
> 	Manipulación de consultas SQL para extraer datos.
> - **📜 XPath Injection**
> 	Explotación de consultas XPath en bases de datos XML.
> 
> *🖥️ Inyecciones en cliente*
> - **📝  XSS (Cross-Site Scripting)**
> 	Inyección de código JavaScript malicioso en páginas web.
> - **🔳 XFS (Cross-Frame Scripting)**
> 	Manipulación de marcos de navegador para robar datos.
> - **📨 HTTP Response Split (CRLF Injection Attack)**
> 	Inyección de saltos de línea para alterar respuestas HTTP.
> 	
> **📎 Enlace al temario**
> [Seguridad Informática - Tema 5](Seguridad_Informatica-Tema_5.md)

> ---

> **🦠 Malware (Malicious Software)**  
> Software malicioso diseñado para dañar sistemas, robar información o generar ingresos ilícitos.
> 
> *📥 Métodos de Propagación*  
> - **📩 Descarga involuntaria**  
>   A través de correos electrónicos, torrents o software gratuito.  
> - **🌐 Enlaces engañosos**  
>   Sitios web fraudulentos que instalan malware sin consentimiento.  
> 
> *🔄 Tipos de Malware*  
> - **🔒 Ransomware**  
>   Bloquea o encripta archivos y exige un rescate.  
> - **🕵️ Spyware**  
>   Recopila información personal sin autorización.  
> - **📢 Adware**  
>   Muestra publicidad no deseada para generar ingresos.  
> 
> **📎 Enlace al temario**  
> [Seguridad Informática - Tema 6](Seguridad_Informatica-Tema_6.md)


---

## Fases de un Ataque

> **🔍 Modelo SANS Technology Institute**  
> 1. *🛰️ Reconocimiento*  
>    Identificar sistemas y redes para recopilar información.  
> 2. *📋 Enumeración*  
>    Obtener datos específicos del objetivo, como usuarios y servicios.  
> 3. *🚪 Brecha*  
>    Conseguir acceso al sistema explotando vulnerabilidades.  
> 4. *🎛️ Administración*  
>    Tomar control del sistema comprometido.  
> 5. *🧹 Limpieza*  
>    Eliminar evidencias para evitar la detección.  

> ---

> **💣 Modelo Lockheed Martin (Kill Chain)**  
> 1. *🔍 Reconocimiento*  
>    Investigar el objetivo para planear el ataque.  
> 2. *🛠️ Armamento*  
>    Desarrollar malware o exploits adecuados.  
> 3. *📤 Entrega*  
>    Transmitir el malware a través de correos, descargas o vulnerabilidades.  
> 4. *💥 Explotación*  
>    Aprovechar fallos de seguridad para ejecutar el ataque.  
> 5. *📌 Instalación*  
>    Garantizar que el malware se mantenga activo en el sistema.  
> 6. *📡 Comando y Control*  
>    Mantener acceso remoto para operar el ataque.  
> 7. *🎯 Acción sobre el objetivo*  
>    Robar información, cifrar archivos o comprometer la red.  

> ---

> **🛡️ Modelo NCSC (UK)**  
> 1. *🕵️ Encuesta*  
>    Investigar y analizar la información del objetivo.  
> 2. *📨 Entrega*  
>    Posicionarse para explotar una vulnerabilidad.  
> 3. *💻 Infracción*  
>    Ejecutar el ataque sobre el sistema objetivo.  
> 4. *🎭 Efecto*  
>    Modificar, robar o afectar el sistema comprometido.  

> ---

> **🔓 Modelo Infosec Institute**  
> 1. *🛰️ Reconocimiento*  
>    Identificar el objetivo y posibles vulnerabilidades.  
> 2. *🔍 Escaneo*  
>    Analizar puntos débiles en la red o dispositivos.  
> 3. *🔑 Acceso y escalamiento*  
>    Infiltrarse en el sistema y obtener más privilegios.  
> 4. *📤 Exfiltración*  
>    Extraer datos sensibles.  
> 5. *⚙️ Sostenibilidad*  
>    Mantenerse oculto dentro del sistema.  
> 6. *🔥 Asalto*  
>    Modificar o deshabilitar funciones críticas.  
> 7. *🧩 Ofuscación*  
>    Borrar rastros para evitar ser detectado.  

> ---

> **📌 Resumen General**  
> 1. *🛰️ Reconocimiento* $\to$ Recopilar información del objetivo. 
> 2. *🔍 Escaneo* $\to$ Identificar vulnerabilidades.  
> 3. *🔑 Obtener acceso* $\to$ Explotar fallos de seguridad.  
> 4. *📌 Mantener acceso* $\to$ Garantizar persistencia en el sistema.  
> 5. *🧹 Ocultación* $\to$ Eliminar evidencias del ataque.  

---

## Footprinting

> **🔍 ¿Qué es el footprinting?**
> Es un proceso de recopilación de información pública disponible en internet, sin infringir ninguna ley. 
> 
> Algunas fuentes comunes son:
>   - 🌐 Redes sociales, blogs, foros.
>   - 📰 Medios de comunicación, boletines oficiales.
>   - 📄 Metadatos ocultos en archivos compartidos.

> ---

> **📡 OSINT (Open Source Intelligence)**  
> Inteligencia de fuentes abiertas basada en información accesible públicamente.
> 
> 1. *📝 Requisitos*
> 	Definir los objetivos del análisis.
> 2. *📚 Identificación de fuentes*
> 	Especificar los sitios de interés.
> 3. *📥 Adquisición*
> 	Recopilar datos de las fuentes elegidas.
> 4. *⚙️ Procesamiento*
> 	Organizar y dar formato a los datos.  
> 5. *📊 Análisis*
> 	Relacionar datos y extraer conclusiones.
> 6. *📑 Presentación de inteligencia*
> 	Mostrar la información de manera clara y útil.

> ---

> **🔎 Búsquedas avanzadas con "dorks"**  
> Técnicas de refinamiento en motores de búsqueda:  
> 
> | Dork                 | Descripción                                        |
> | -------------------- | -------------------------------------------------- |
> | `""`                 | Coincidencia exacta.                               |
> | `site:`              | Buscar dentro de un sitio web específico.          |
> | `filetype:` / `ext:` | Encontrar archivos con una extensión concreta.     |
> | `intext:`            | Buscar texto dentro de una página.                 |
> | `intitle:`           | Resultados con una palabra clave en el título.     |
> | `OR` / `AND`         | Operadores lógicos.                                |
> | `-`                  | Excluir palabras de los resultados.                |
> | `cache:`             | Ver una versión almacenada en caché de una página. |

> ---

> **📷 IMINT - IMage INTelligence**
> Se pueden utilizar buscadores especializados para el análisis de imágenes:  
> 
> | Herramienta | Enlace |
> |--------------|---------|
> | TinEye | [https://tineye.com/](https://tineye.com/) |
> | Yandex | [https://yandex.com/](https://yandex.com/) |
> | Google Lens | [https://www.google.com/](https://www.google.com/) |
> | Google Images | [https://images.google.com/](https://images.google.com/) |

> ---

> **📂 Metadatos**  
> Los metadatos proporcionan detalles sobre un archivo, incluyendo:  
> 
> - 📅 *Fecha de creación/modificación*.
> - ✍️ *Autores del documento*.
> - 🖥️ *Aplicación y sistema operativo usados*.
> - 🌍 *Datos de geolocalización*.
> 
> 
> 📌 **Herramientas para analizar metadatos:**
> 
> | Herramienta | Enlace |
> |---------------|---------|
> | ElevenPaths | [https://www.elevenpaths.com/](https://www.elevenpaths.com/) |
> | ExifTool | [https://exiftool.org/](https://exiftool.org/) |

---

## Fingerprinting

> **🔍 ¿Qué es el Fingerprinting?**
> El fingerprinting es un proceso de recopilación de datos específicos que permite obtener información detallada sobre una red o sistema.
> 
> 📊 Datos que se pueden obtener:
> - *🌐 Topología de red y direcciones IP*.
> - *🔌 Estado de los puertos (abiertos/cerrados)*.
> - *🖥️ Versiones de software y sistemas operativos*.
> - *🛠️ Historial de actualizaciones y parches*.
> - *⚠️ Listado de vulnerabilidades*.
> 
> **📚 Técnicas muy extendidas**
> - 👥 Ingeniería social.
> - 🎣 Phishing.
> - 🐍 Sniffing.
> - 🧭 Scanning/mapping.

---

## Ingeniería Social

> **🎭 ¿Qué es la Ingeniería Social?**
> Técnicas basadas en la manipulación psicológica para obtener información valiosa de personas dentro de una organización.
> 
> 🎯 Objetivos comunes
> - *👨‍💼 Empleados sin conciencia sobre seguridad*.
> - *😠 Personal descontento con la organización*.
> - *🔓 Falta de políticas de seguridad adecuadas*.

> ---

> **🕵️‍♂️ Perfiles de atacantes en Ingeniería Social**
> 
> | Tipo |  Características |
> |--------|----------------|
> | Insider | Empleado con acceso privilegiado que filtra información por venganza, dinero o descontento. |
> | Ciberdelincuente | Hacker malintencionado con conocimientos técnicos que busca acceder a la red empresarial. |
> | Hacker Ético | Pentester autorizado que audita la seguridad de una empresa mediante técnicas controladas. |
> | Estafadores o timadores | Utilizan engaños para obtener información de víctimas. |
> | Espías | Manipulan objetivos para obtener información confidencial. |

> ---

> **🚨 Tipos de ataques de Ingeniería Social**
> 
> | Ataque | Descripción |
> |-----------|--------------|
> | Piggybacking | Uso de la sesión de otro usuario o acceso físico siguiendo a alguien a una zona restringida. |
> | Dumpster Diving | Búsqueda de información en la basura o en documentos desechados. |
> | Eavesdropping | Escucha de conversaciones privadas sin consentimiento. |
> | Shoulder Surfing | Observación disimulada de pantallas o teclados para obtener datos sensibles. |
> | Office Snooping | Acceso a equipos desbloqueados cuando el usuario se ausenta. |
> | Baiting | Dejar dispositivos infectados (USB, CD) para que la víctima los conecte a su equipo. |
> | Bribing | Soborno a empleados para obtener información confidencial. |
> | Ingeniería Social Inversa | Crear una situación en la que la víctima se acerque voluntariamente al atacante. |

---

## Phishing

> **🎣 ¿Qué es el Phishing?**
> El atacante se hace pasar por otra persona o entidad en la cual la víctima confía. Tiene puntos en común con la [Ingeniería Social](#Ingeniería%20Social).
> 
> El objetivo es extraer información confidencial enviando una comunicación confiable y legítima solicitando dicha información.

> ---

> **🦑 Tipos de Phishing**
> 
> *🛡️ Spear Phishing*
> Si el objetivo es un grupo determinado de personas.
> 
> *🐋 Whaling*
> Si el objetivo son los directivos de la organización.

> ---

> **📱 Tipos de ataque**
> 
> *📱 Smishing*
> Usando SMS, o apps de mensajería como Telegram o WhatsApp.
> 
> *📧 Phishing*
> Usando el correo electrónico.

---

## Sniffing

> **👀 ¿Qué es el Sniffing?**  
> Es una técnica que permite capturar todos los datos que circulan por una red de área local. No es necesariamente maliciosa.
> 
> Su alcance depende de los dispositivos de conmutación o segmentación en la red, de su correcta configuración y de la forma de acceso.
> 
> Es una técnica típica para conseguir **contraseñas**.

> ---

> **🖥️ Sniffers**  
> Software que configura las tarjetas de red en modo promiscuo, soportando los protocolos de interés y proporcionando mecanismos de filtrado adecuados.

---

## Scanning / Mapping

> **🔍 ¿Qué es el Scanning / Mapping?**  
> El scanning trata de analizar a través de diferentes herramientas el estado de una determinada red y de los dispositivos ubicados en ella.
> 
> Existen diferentes tipos dependiendo del nivel de profundidad y del objetivo del análisis:
> - *🔌 Escáner de puertos*.
> - *🛠️ Escáner de vulnerabilidades*.

---

## Anonimato

> **🐧 ¿Qué es Tails?**  
> Es un SO de software libre basado en Debian. Fuerza que todas las conexiones salientes sean a través de la red TOR.

> ---

> **🧅 ¿Qué es TOR (The Onion Router)?**  
> El objetivo de este proyecto es crear una red de comunicaciones distribuida y superpuesta al Internet convencional.
> 
> TOR implementa una técnica llamada *Onion Routing*, diseñada para proteger las comunicaciones en la Marina de los Estados Unidos.
> 
> La idea es cambiar el enrutado tradicional de Internet para garantizar el anonimato y la privacidad de los datos.  

> ---

> **🔒 Enrutado Clásico vs Onion Routing**
> 
> *🌐 Enrutado clásico*  
> Si alguien intercepta el paquete de datos (MiM), sabe de dónde vienen y a dónde van.
> 
> *🧅 Onion Routing*  
> Consiste en enviar los datos por un camino no directo utilizando nodos.
> 
> - El nodo A quiere mandar un mensaje al nodo B.  
> - Calcula una ruta más o menos aleatoria al destino.  
> - Luego, consigue las claves públicas de todos los nodos intermedios usando un directorio de nodos.  
> - Va cifrando el mensaje por "capas".

---