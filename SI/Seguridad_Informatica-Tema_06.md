---
tags: URJC URJC_SI
---

# Tema 6 - Seguridad Informática

---

## Tabla de Contenidos

1. [Definición y características](#Definición%20y%20características)
2. [Tipos de Malware](#Tipos%20de%20Malware)
3. [Rentabilidad del Malware](#Rentabilidad%20del%20Malware)
4. [Contramedidas](#Contramedidas)
5. [Técnicas de detección](#Técnicas%20de%20detección)
6. [Conclusión](#Conclusión)

---

## Definición y características

> **📝 Definición de Malware**  
> El malware, o software malicioso, es cualquier tipo de software diseñado para infiltrarse o dañar un sistema sin el consentimiento del usuario. Su objetivo puede ser desde la alteración del funcionamiento de un dispositivo hasta el robo de información.  
> 
> Las características básicas del malware incluyen:  
> 
> *🔁 Replicación*
> Capacidad para duplicarse a sí mismo, como en los virus.
> 
> *🕵️ Métodos de ocultamiento*
> Utiliza técnicas como el cifrado o el polimorfismo para evadir la detección.
> 
> *🎬 Activación*
> Se activa mediante diferentes métodos, como un contador o un clic del usuario.
> 
> *⚠️ Manifestación*
> Produce efectos que alertan al usuario, como la modificación o eliminación de archivos.
> 
> *🔓 Explotación de privilegios*
> A menudo, el malware busca escalar privilegios para obtener más control sobre el sistema.

---

## Tipos de Malware

> **💻 Virus**  
> Un virus es un tipo de malware que se infiltra en el código de otros programas y se replica al ejecutarlos. Requiere la interacción del usuario para propagarse y puede afectar al funcionamiento de los sistemas o robar información.
> 
> El **CIH (Chernobyl)** es uno de los virus más conocidos, diseñado para destruir la información almacenada en el sistema.

> ---

> **🦠 Gusanos (Worms)**  
> Los gusanos son programas que se replican y se desplazan a través de redes sin necesidad de la intervención del usuario. No requieren que el usuario haga nada para propagarse, solo se distribuyen y infectan automáticamente otros equipos conectados a la red.
> 
> El gusano **Blaster** que explotaba vulnerabilidades en el sistema Windows XP.

> ---

> **🎭 Troyanos (Trojan Horses)**  
> Los troyanos se hacen pasar por programas inofensivos, pero contienen códigos maliciosos ocultos. Generalmente se utilizan para robar información confidencial o permitir el acceso remoto no autorizado.
> 
> **Zeus** es un troyano diseñado para robar credenciales bancarias.

> ---

> **🔐 Ransomware**  
> El ransomware es un malware que bloquea o cifra archivos del sistema y exige un rescate para liberarlos. A menudo se propaga mediante correos electrónicos fraudulentos y puede causar pérdidas graves si no se toman las medidas adecuadas.
> 
> **WannaCry**, un ataque de ransomware que afectó a miles de sistemas en todo el mundo, principalmente explotando vulnerabilidades de Windows.

> ---

> **👁️ Spyware**  
> El spyware es un software que espía la actividad del usuario sin su conocimiento, con el fin de robar información personal, como contraseñas, datos bancarios, y más.
> 
> Suele instalarse sin el consentimiento del usuario a través de descargas engañosas.
> 
> **Keyloggers** son un tipo común de spyware, que registran las pulsaciones del teclado.

> ---

> **📢 Adware**  
> El adware muestra anuncios no deseados o ventanas emergentes en el sistema de la víctima, lo que generalmente interrumpe la experiencia del usuario y puede ralentizar el rendimiento del dispositivo.
> 
> Muchos programas gratuitos instalan adware que muestra anuncios invasivos, como **Amonetize**.

> ---

> **🔒 Rootkits**  
> Los rootkits permiten a los atacantes obtener acceso persistente y oculto al sistema infectado, haciendo más difícil su detección y eliminación.
> 
> Pueden ocultar otros tipos de malware y dificultar la limpieza del sistema.
> 
> **TDSS** es un rootkit utilizado para instalar malware adicional en sistemas comprometidos.

> ---

> **⏳ Keyloggers**  
> Los keyloggers son programas diseñados para registrar las pulsaciones del teclado de un usuario, lo que permite a los atacantes robar contraseñas, números de tarjetas de crédito y otros datos sensibles.  
> 
> **Spybot** es un keylogger que monitoriza las pulsaciones y las almacena en un archivo.

---

## Rentabilidad del Malware

> **💸 La industria del Malware**  
> El desarrollo de malware ha evolucionado hacia una industria altamente rentable. Algunos ejemplos incluyen:  
> - **Click fraud**: Los atacantes alquilan botnets para generar clics fraudulentos y obtener ingresos.
> - **Extorsión**: El ransomware secuestra los archivos de las víctimas y exige dinero a cambio.
> - **Spam**: Las botnets también se utilizan para enviar grandes cantidades de correos electrónicos no deseados.
> - **Malware como servicio (MaaS)**: Los atacantes venden o alquilan su infraestructura de botnets a otros cibercriminales.
>  
> **MaaS** permite a los delincuentes alquilar herramientas de malware, como kits de exploits y botnets, sin necesidad de conocimientos técnicos.

---

## Contramedidas

> **🛡️ Estrategias de protección**  
> Para protegerse contra el malware, es esencial implementar las siguientes medidas:
> - Mantener actualizado el software y el sistema operativo.
> - Desinstalar programas que no se utilicen.
> - Evitar abrir correos electrónicos de remitentes desconocidos.
> - No descargar programas de fuentes no verificadas.
> - Utilizar software antivirus actualizado.
>  
> **⚠️ Otros consejos**  
> - No proporcionar información personal por correo electrónico o sitios web no confiables.
> - Usar contraseñas fuertes y autenticación de dos factores cuando sea posible.

> ---

> **🔍 Ejemplo de herramienta de detección**  
> 
> *🔎 VirusTotal*
> Una plataforma que permite analizar archivos y URLs en busca de malware utilizando múltiples motores antivirus.
> 
> *🛡️ Malwarebytes*
> Un antivirus especializado en la detección y eliminación de malware avanzado, incluyendo ransomware y adware.

---

## Técnicas de detección

> **🔍 Análisis estático**
> Este tipo de análisis examina el código del malware sin ejecutarlo. Su objetivo es identificar patrones conocidos, como cadenas de texto, firmas digitales, y comportamientos específicos.
> 
> El análisis estático permite examinar archivos sin poner en riesgo el sistema, pero puede ser limitado cuando el malware está ofuscado o empaquetado.

> ---

> **⚙️ Análisis dinámico**
> El análisis dinámico implica ejecutar el malware en un entorno controlado, como un **sandbox**, para observar su comportamiento en tiempo real.
> 
> Este enfoque es más efectivo para identificar acciones maliciosas que no se pueden ver con un análisis estático, como la modificación de archivos del sistema, el envío de información a servidores remotos o la explotación de vulnerabilidades.

> ---

> **🛠️ Herramientas útiles**  
> Existen múltiples herramientas utilizadas tanto en el análisis estático como dinámico para detectar y estudiar el malware. Algunas de las más importantes incluyen:
> 
> *🛡️ Antivirus*
> Los antivirus escanean archivos y procesos en busca de firmas de malware conocidas. Utilizan bases de datos de firmas que contienen fragmentos de código asociados con malware previamente identificado.
> 
> Sin embargo, los antivirus convencionales tienen limitaciones para detectar malware desconocido o aquellos que han sido modificados (polimorfismo o metamorfismo).
> 
> *🏖️ Sandboxing*
> Las herramientas de sandboxing permiten ejecutar el malware en un entorno aislado para estudiar su comportamiento sin poner en riesgo el sistema objetivo.
> 
> Ejemplos de herramientas de sandboxing son **Cuckoo Sandbox**, **Any.Run**, y **FireEye**.
> 
> Estos entornos permiten analizar cómo interactúa el malware con el sistema operativo, detectar posibles conexiones a servidores externos y observar cualquier modificación en los archivos o registros del sistema.
> 
> *🛠️ Ghidra*
> Herramienta avanzada de ingeniería inversa utilizada para descompilar y analizar binarios. Ghidra permite la inspección detallada de un archivo ejecutable sin necesidad de ejecutarlo.
> 
> Es muy útil cuando se trata de malware ofuscado, ya que permite estudiar el código y descifrar técnicas como el **polimorfismo** o **metamorfismo**.
>  
> *🔄 Radare2*
> Una suite de herramientas de análisis y forense digital que permite realizar ingeniería inversa en binarios. 
> 
> Al igual que Ghidra, Radare2 ofrece una amplia gama de funcionalidades para analizar malware sin ejecutarlo, con soporte para depuración y descompilación.

> ---

> **🔒 Ofuscación y técnicas de evasión**  
> Muchos tipos de malware emplean técnicas de **ofuscación** para evitar ser detectados por herramientas de análisis estático, como los antivirus.
> 
> La **ofuscación** es el proceso de modificar el código del malware para que sea difícil de entender o analizar, pero sin alterar su funcionalidad. Algunas técnicas comunes de ofuscación incluyen:
> 
> *🔐 Cifrado de código*
> El código del malware se cifra y solo se descifra cuando está en ejecución. Esto hace que el análisis estático sea muy difícil, ya que el código no está en su forma original.
> 
> *🔄 Polimorfismo*
> El malware se reescribe a sí mismo de manera que cambia su apariencia cada vez que se ejecuta, pero sigue funcionando de la misma manera. 
> 
> Los antivirus basados en firmas no pueden detectar polimorfismo porque la firma cambia en cada ejecución.
> 
> *💥 Metamorfismo* 
> Similar al polimorfismo, pero en este caso, el código del malware cambia completamente cada vez que se ejecuta, lo que hace aún más difícil la detección.
> 
> *📦 Técnicas de empaquetado*
> El malware se "empaqueta" con herramientas que lo comprimen o cifran, lo que dificulta que los escáneres antivirus detecten su código malicioso. 
> 
> Herramientas como **UPX (Ultimate Packer for eXecutables)** se utilizan comúnmente para empaquetar el malware y evitar la detección.

> ---

> **⚠️ Ejemplo de evasión de antivirus**  
> Los atacantes pueden utilizar herramientas como **Themida** o **VMProtect** para proteger el malware de la detección, asegurándose de que solo se ejecute correctamente en un entorno controlado o cuando el atacante lo decida. 
> 
> Estas herramientas dificultan que los antivirus analicen el malware al utilizar técnicas avanzadas de ofuscación y cifrado.

---

## Conclusión

> **🛡️ Prevención**  
> A medida que el malware se vuelve más sofisticado, es crucial que los usuarios y las organizaciones implementen medidas preventivas y técnicas de detección avanzadas para proteger sus sistemas. 
> 
> La actualización regular de software, la educación en ciberseguridad y el uso de herramientas de seguridad avanzadas como **Ghidra**, **Cuckoo Sandbox** y **Wireshark** son clave para mitigar los riesgos asociados con el malware.

---