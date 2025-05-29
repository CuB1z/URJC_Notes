---
tags: URJC URJC_SI
---

# Tema 7 - Seguridad Informática

---

## Tabla de Contenidos

1. [Introducción](#Introducción)
2. [Criptografía Clásica](#Criptografía-Clásica)
3. [Criptografía Moderna](#Criptografía-Moderna)
4. [Modelos Criptográficos](#Modelos-Criptográficos)
5. [Cifrado Simétrico (Clave Secreta)](#Cifrado-Simétrico-(Clave-Secreta))
6. [Cifrado Asimétrico (Clave Pública)](#Cifrado-Asimétrico-(Clave-Pública))
7. [Mecanismos de Autenticación](#Mecanismos-de-Autenticación)
8. [Firma Digital](#Firma-Digital)
9. [Certificados Digitales](#Certificados-Digitales)
10. [Esteganografía](#Esteganografía)
11. [Conclusión](#Conclusión)

---

## Introducción

> **🔐 ¿Qué es la Criptografía?**
> La criptografía es la disciplina encargada de proteger la información transformándola en algo ilegible para quienes no poseen la clave adecuada. Se usa en comunicaciones, almacenamiento de datos, contraseñas, autenticación, etc.
>
> La criptografía es fundamental para garantizar:
> *🔒 Confidencialidad*
> Sólo el destinatario debe leer el mensaje.
> 
> *🧾 Integridad*
> Asegurar que el mensaje no ha sido alterado.
> 
> *🧑‍⚖️ Autenticidad*
> Verificar la identidad del emisor.
> 
> *🙅 No repudio*
> El emisor no puede negar haber enviado el mensaje.

---

## Criptografía Clásica

> **🔄 Transposición**
> Reordena los caracteres del mensaje sin cambiarlos. Ejemplo: escítala espartana. Aunque simple, la transposición por sí sola no ofrece gran seguridad hoy en día.

> ---

> **🔤 Sustitución**
> Cambia cada letra por otra. Hay dos tipos:
> - Monoalfabética (César): cada letra siempre se reemplaza por la misma.
> - Polialfabética (Vigenère): se usan múltiples alfabetos, lo que dificulta el análisis de frecuencia.

> ---

> **🧠 Análisis de Frecuencia**
> Técnica que explota la frecuencia de letras en un idioma. Por ejemplo, en español, "E" es muy común. Esto permite romper cifrados monoalfabéticos fácilmente si el texto cifrado es suficientemente largo.

> ---

> **🔧 Máquina Enigma**
> Máquina alemana usada en la II Guerra Mundial. Usaba rotores, cables y mecanismos complejos. Su seguridad se basaba en la configuración de sus componentes, que se cambiaban a diario. Fue descifrada por matemáticos polacos y luego por Turing y su equipo en Bletchley Park.

---

## Criptografía Moderna

> **📚 Fundamentos**
> La criptografía moderna se basa en matemáticas avanzadas y teoría de la información. Incluye el uso de algoritmos que aseguran el secreto aún si el método es conocido, confiando únicamente en la clave.

> ---

> **📐 Principio de Kerckhoffs**
> Propuesto en 1883, establece que un sistema criptográfico debe seguir siendo seguro incluso si todo el sistema es conocido, excepto la clave. Es un principio clave para la seguridad de algoritmos como AES, RSA, etc.

> ---

> **🧠 Claude Shannon: Padre de la teoría de la información**
> Claude Shannon es considerado el **padre de la teoría de la comunicación** y una figura clave en la criptografía moderna.
> 
> En su artículo **“A Mathematical Theory of Cryptography”** (también conocido como *A Communications Theory of Secrecy Systems*), Shannon sentó las bases matemáticas para evaluar la seguridad de los sistemas criptográficos.
>
> Su enfoque transformó la criptografía de un arte empírico a una **ciencia basada en teoría matemática y estadística**.

> ---

> **🧩 Conceptos clave introducidos por Shannon**
> 
> *🔀 Difusión*
> Un pequeño cambio en el mensaje original debe provocar múltiples cambios en el mensaje cifrado, para ocultar patrones.
> 
> *🧪 Confusión*
> La relación entre la clave y el mensaje cifrado debe ser lo más compleja posible para evitar su deducción.
> 
> Estos dos principios se aplican en algoritmos como AES y DES, para maximizar la resistencia frente a ataques de análisis criptográfico.

> ---

> **📏 Máximas de diseño de Shannon**
> Según Shannon, un sistema de cifrado robusto debe cumplir las siguientes características:
> 
> *👀 El enemigo conoce el sistema*
> También llamada la *máxima de Shannon*, implica que la seguridad no debe depender del secreto del algoritmo, sino exclusivamente de la clave.
> 
> *⚖️ Esfuerzo proporcional a la seguridad*
> Los recursos necesarios para cifrar y descifrar deben adecuarse al nivel de protección requerido.
> 
> *🔄 Simplicidad operativa*
> Los mecanismos de cifrado/descifrado y la generación de claves deben ser simples de implementar.
> 
> *💡 Implementación sencilla*
> El algoritmo debe ser fácil de programar sin inducir errores.
> 
> *🔚 Tolerancia a errores*
> Un fallo en un bloque cifrado no debe comprometer el resto del mensaje.
> 
> *📦 Eficiencia en tamaño*
> El mensaje cifrado no debe ser significativamente más grande que el mensaje original.
> 
> Estas directrices han sido fundamentales para el desarrollo de estándares modernos de cifrado y siguen vigentes hoy en día en la ingeniería de seguridad.


---

## Modelos Criptográficos

> **🧾 Criptosistema**
> Representado por la tupla $(K, M, C)$ donde:
> - $K$: espacio de claves
> - $M$: mensajes posibles
> - $C$: textos cifrados posibles
>
> Funciones fundamentales:
> - $E(k, m) = c$: cifra el mensaje con clave $k$
> - $D(k, c) = m$: descifra con la misma clave $k$
>
> Debe cumplirse que: $D(k, E(k, m)) = m$

> ---

> **❌ Operador XOR**
> Muy usado en cifrados modernos. Es un "o exclusivo" que cumple:
> - $0 \oplus 0 = 0$, $1 \oplus 1 = 0$, $1 \oplus 0 = 1$
> - Conmutativo: $A \oplus B = B \oplus A$
> - Asociativo: $A \oplus (B \oplus C) = (A \oplus B) \oplus C$
> - Autoinverso: $A \oplus B \oplus B = A$

---

## Cifrado Simétrico (Clave Secreta)

> **📑 One-Time Pad (OTP)**
> El **One-Time Pad** es un sistema de cifrado **teóricamente perfecto**, ya que ofrece **seguridad absoluta** bajo ciertas condiciones:
> - Se usa una **clave completamente aleatoria**.  
> - La clave debe ser **igual de larga que el mensaje**.  
> - Cada bit o carácter del mensaje se combina con la clave usando **XOR** (en binario) o una tabla de sustitución (en texto).

> ---

> **🎲 Cifrado de Flujo**
> El **cifrado de flujo** es una técnica de cifrado simétrico que procesa el mensaje bit a bit (o byte a byte), generando una **secuencia pseudoaleatoria de bits (keystream)** a partir de una clave corta.
> 
> Cada bit del mensaje se combina con el flujo usando una operación XOR, generando el texto cifrado.
> 
> Es especialmente útil para cifrar **datos en tiempo real** (como transmisiones por red) debido a su baja latencia y eficiencia.
> 
> **🔑 Ejemplos de algoritmos**
> *⚠️ RC4*
> Extremadamente rápido, fue muy utilizado en SSL y WEP, pero hoy está considerado **inseguro** por múltiples debilidades criptográficas.
> 
> *🔥 Salsa20 / ChaCha20*
> Cifradores modernos, seguros y eficientes, usados ampliamente en protocolos actuales como **TLS**, **VPNs**, y **aplicaciones móviles** por su excelente rendimiento en hardware limitado.

> ---

> **🧱 Cifrado por Bloques**
> El **cifrado por bloques** es una técnica de cifrado simétrico donde el mensaje se divide en bloques de tamaño fijo (por ejemplo, 64 o 128 bits), y cada bloque se cifra por separado mediante una clave compartida.
> 
> **🔄 Modos de operación más comunes**
> *🧊 ECB (Electronic Codebook)*
> Cada bloque se cifra de forma independiente. ❌ **Inseguro**, ya que produce los mismos bloques cifrados para bloques de texto idénticos → permite identificar patrones. 
> 
> *🔗 CBC (Cipher Block Chaining)*
> Cada bloque se mezcla con el bloque anterior usando XOR antes de cifrarse, lo que elimina patrones repetitivos.
> 
> *🔁 CFB, OFB, CTR*
> Transforman el cifrado por bloques en un **cifrado de flujo**, útil para transmisiones en tiempo real o cifrado de tamaños variables.
> 
> **🔐 Algoritmos típicos**
> *🔒 AES (Advanced Encryption Standard)*
> Estándar actual, rápido, seguro y ampliamente adoptado. Ofrece longitudes de clave de 128, 192 y 256 bits.
> 
> *🧱 3DES (Triple DES)*
> Mejora del antiguo algoritmo DES aplicando tres rondas de cifrado, pero hoy considerado **obsoleto** por su lentitud y vulnerabilidades.
> 
> El uso correcto del modo de operación es **tan importante como el algoritmo** para garantizar la seguridad del cifrado.


---

## Cifrado Asimétrico (Clave Pública)

> **🔐 Concepto**
> El **cifrado asimétrico** se basa en el uso de **dos claves distintas pero matemáticamente relacionadas**.
> 
> *🔑 Clave pública*
> Se distribuye libremente y se utiliza para **cifrar** la información.
> 
> *🔐 Clave privada*
> Se mantiene en secreto y se utiliza para **descifrar** lo recibido.

> ---

> **✅ Ventajas clave**
> No requiere el intercambio previo de claves, lo que reduce el riesgo en la comunicación inicial. Además, permite implementar sistemas de **firma digital**, garantizando la autenticidad e integridad de los mensajes.
> 
> Facilita la creación de canales seguros sobre redes inseguras como Internet.
> 
> Aunque es más seguro en muchos contextos, es **computacionalmente más lento** que el cifrado simétrico, por lo que a menudo se usa en combinación con este.

> ---

> **🔁 Algoritmos más conocidos**
> En el cifrado asimétrico existen varios algoritmos ampliamente utilizados, cada uno con fundamentos matemáticos distintos:
> 
> *🔐 RSA (Rivest–Shamir–Adleman)*
> Se basa en la **dificultad de factorizar números enteros grandes**. Es uno de los algoritmos más antiguos y ampliamente usados en navegadores, firmas digitales y cifrado de correos.
> 
> *📉 ElGamal*
> Su seguridad se fundamenta en el **problema del logaritmo discreto**. Es probabilístico (el mismo mensaje cifrado puede dar diferentes resultados) y se utiliza en sistemas como GPG/PGP.
> 
> *🧮 ECC (Elliptic Curve Cryptography)*
> Utiliza propiedades matemáticas de las **curvas elípticas** sobre campos finitos. Proporciona **la misma seguridad con claves mucho más pequeñas**, lo que lo hace ideal para dispositivos móviles o con recursos limitados.
> 
> Estos algoritmos son esenciales en protocolos como TLS/SSL, firmas digitales, blockchain, autenticación y más.

> ---

> **⚠️ Limitaciones**
> Más lento que el simétrico. Se usa comúnmente para cifrar claves simétricas que luego se usan para cifrar los datos (modelo híbrido).

---

## Mecanismos de Autenticación

> **👤 ¿Qué autentica?**
> La **autenticación** es el proceso mediante el cual un sistema verifica la **identidad de un usuario o entidad**.
> 
> Es fundamental en cualquier sistema seguro para evitar accesos no autorizados.

> ---

> **🔐 Factores de autenticación**
> *🧠 Algo que sabes*
> Contraseñas, PINs, preguntas de seguridad.
> 
> *📱 Algo que tienes*
> Tokens físicos, llaves USB, aplicaciones móviles de autenticación (ej. Google Authenticator).
> 
> *🧬 Algo que eres*
> Datos biométricos como huellas dactilares, reconocimiento facial, iris o voz.
> 
> Los sistemas más seguros combinan varios factores (**autenticación multifactor - MFA**) para fortalecer el proceso.

> ---

> **🛡️ Kerberos**
> **Kerberos** es un protocolo de autenticación en red que utiliza **criptografía de clave simétrica y tickets** para autenticar de forma segura a los usuarios sin enviar contraseñas por la red.
> 
> Se basa en un modelo de confianza centralizado y consta de tres componentes principales:
> *🔐 AS (Authentication Server)*
> Verifica la identidad del usuario inicialmente.
> 
> *🎫 TGS (Ticket Granting Server)*
> Emite tickets para acceder a servicios tras la autenticación inicial.
> 
> *📜 TGT (Ticket Granting Ticket)*
> Prueba temporal que permite solicitar acceso a servicios sin reautenticarse.
> 
> Es ampliamente utilizado en entornos corporativos, especialmente en sistemas de **Active Directory de Microsoft**, donde facilita el inicio de sesión único (**Single Sign-On - SSO**).
> 
> Kerberos mejora la seguridad en redes internas, evitando el envío de contraseñas y reduciendo el riesgo de ataques de intermediario (MITM).

---

## Firma Digital

> **🔍 ¿Qué hace?**
> La **firma digital** es un mecanismo criptográfico que permite **verificar la identidad del emisor** y la **integridad del contenido**, aportando una capa esencial de confianza en entornos digitales.
> 
> Permite garantizar tres propiedades clave:
> *✅ Autenticidad*
> Confirma que el mensaje fue generado por quien dice haberlo enviado.
> 
> *🔒 Integridad*
> Asegura que el contenido **no ha sido modificado** desde su emisión.
> 
> *🧾 No repudio*
> Impide que el emisor **niegue posteriormente** haber enviado el mensaje o documento.

> ---

> **⚙️ Funcionamiento**
> La firma digital utiliza criptografía asimétrica combinada con funciones hash. El proceso básico es:
> 1. 📑 Se aplica una **función hash** al contenido del mensaje para obtener un resumen único (digest).  
> 2. 🔐 El emisor **cifra ese hash con su clave privada**, generando así la firma digital.  
> 3. 📩 El mensaje se envía junto con la firma.  
> 4. 🧾 El receptor **descifra la firma usando la clave pública** del emisor y calcula el hash del mensaje recibido.  
> 5. ✅ Si ambos hashes coinciden, se confirma la autenticidad e integridad.
> 
> 🔄 Es un proceso eficiente, ya que solo se firma el resumen del mensaje, no el mensaje completo.

> ---

> **📎 Casos de uso**
> La firma digital es una herramienta clave en el mundo actual. Algunos de sus usos más comunes incluyen:
> - **📧 Firmar correos electrónicos** para asegurar al destinatario que el mensaje proviene realmente del remitente.  
> - **📝 Firmar documentos oficiales y legales** (como contratos electrónicos, informes, formularios administrativos).  
> - **💳 Autenticar transacciones bancarias** y operaciones en plataformas de pago digital.
> 
> También se utiliza en sistemas de blockchain, certificados digitales, software y actualizaciones de firmware para validar su procedencia.

---

## Certificados Digitales

> **📄 ¿Qué es un certificado?**
> Un **certificado digital** es un **documento electrónico** que vincula la **identidad de una entidad** (persona, empresa, servidor, etc.) con una **clave pública**.
> 
> Es emitido y firmado digitalmente por una **Autoridad de Certificación (CA)** confiable, lo que permite garantizar la autenticidad de la clave pública.
> 
> La mayoría de los certificados actuales siguen el estándar **X.509**, utilizado en protocolos como **HTTPS, TLS, S/MIME, VPNs, etc.**

> ---

> **🔐 Contenido del certificado**
> - *🧑 Nombre del titular*
> - *🔑 Clave pública*
> - *📅 Fecha de emisión y expiración*
> - *✍️ Firma digital de la CA*
> 
> También puede incluir otros datos como el número de serie, el algoritmo de firma, uso del certificado (firma, cifrado, autenticación), entre otros.

> ---

> **🏛️ Confianza en la CA**
> La **confianza en los certificados** se basa en la **cadena de confianza**:
> - El sistema operativo o navegador incluye una lista de **CA raíz confiables**.  
> - Si un certificado es emitido por una CA intermedia, esta debe estar encadenada hacia una CA raíz reconocida.  
> - Si **una CA es comprometida** o emite certificados fraudulentos, toda la cadena asociada queda en riesgo.
> 
> Por ello, las CA están sujetas a estrictas auditorías y políticas de revocación (CRL, OCSP) para mantener la integridad del ecosistema de seguridad digital.
> 
> Sin certificados digitales, no existiría la **confianza básica en Internet**, como la que permite conexiones seguras a sitios web mediante HTTPS.

---

## Esteganografía

> **🕵️ Definición**
> La **esteganografía** es el arte de **ocultar información dentro de otro archivo o medio digital** (como una imagen, un audio o un vídeo), de manera que **su existencia pase desapercibida**.
> 
> No busca proteger el contenido mediante cifrado, sino **esconder el hecho de que existe un mensaje**.
> 
> Aunque no sustituye a la criptografía, puede complementarla eficazmente: por ejemplo, cifrar un mensaje y luego ocultarlo esteganográficamente.

> ---

> **🧪 Ejemplos comunes**
> *🖼️ LSB (Least Significant Bit)*
> Modifica los bits menos significativos de los píxeles en una imagen para almacenar datos ocultos.  
> 
> *🎧 Audio esteganográfico*
> Altera frecuencias inaudibles o la fase de una señal para insertar información.
> 
> *📂 Metadatos*
> Oculta datos en los encabezados de archivos como documentos o imágenes, sin afectar su funcionamiento aparente.
> 
> *🎞️ Vídeos*
> Se pueden insertar datos en ciertos cuadros sin que se perciban visualmente.
> 
> Existen herramientas específicas como **Steghide**, **OpenStego** o incluso métodos caseros con compresión y renombrado de archivos.

> ---

> **🎯 Criptografía vs Esteganografía**
> Aunque ambas técnicas buscan proteger la información, lo hacen de formas distintas y complementarias:
> 
> *🔒 Criptografía*
> Transforma el mensaje para que **no pueda ser comprendido** por terceros, aunque sepan que existe.
> 
> *🕳️ Esteganografía*
> Oculta el mensaje en otro medio**, de forma que nadie sospeche que está allí.
> 
> En conjunto, usar esteganografía sobre un mensaje previamente cifrado proporciona un **doble nivel de protección**: uno lógico (contenido ilegible) y otro visual (contenido invisible).

---

## Conclusión

> **📌 Puntos clave**
> La **criptografía moderna** es un pilar esencial en la protección de la información digital. Está presente en prácticamente todos los entornos donde circula información sensible:
> - 🌐 Redes y conexiones seguras (HTTPS, VPNs)  
> - 💾 Almacenamiento cifrado de archivos  
> - 📧 Correo electrónico seguro  
> - 🧑‍💻 Autenticación de usuarios  
> - 📄 Firma y validación de documentos
> 
> 🔎 Más allá del cifrado, también se integran técnicas complementarias como la **autenticación fuerte**, el uso de **certificados digitales confiables**, y **estrategias de esteganografía** para ocultar información crítica.

> ---

> **🔐 Para un sistema seguro necesitamos:**
> Una combinación equilibrada de tecnologías, buenas prácticas y conciencia del riesgo.
> 
> Aquí algunos elementos imprescindibles:
> 
> - *🧠 Algoritmos criptográficos fuertes y auditados* como AES, RSA, ECC, con actualizaciones constantes.  
> - *🔑 Manejo adecuado de claves*: generación segura, almacenamiento cifrado, rotación periódica y revocación si es necesario. 
> - *👥 Autenticación robusta*: uso de múltiples factores (contraseña + biometría + token).  
> - *📜 Certificados válidos y confiables*: emitidos por Autoridades de Certificación seguras.  
> - *🕵️‍♂️ Conciencia sobre esteganografía*: tanto para proteger como para detectar su uso malicioso.
> 
> En resumen, **la seguridad informática no es un producto, sino un proceso continuo**. Requiere formación, adaptación a nuevas amenazas, y una cultura de prevención a todos los niveles.

---