---
tags: URJC, URJC_SI
---

# Tema 10 - Seguridad Informática

---

## Tabla de Contenidos

1. [Entornos Cloud](#Entornos%20Cloud)
2. [Blockchain](#Blockchain)
3. [Dispositivos móviles y BYOD](#Dispositivos%20móviles%20y%20BYOD)
4. [Amenazas Persistentes Avanzadas (APTs)](#Amenazas%20Persistentes%20Avanzadas%20(APTs))
5. [Ciberguerra](#Ciberguerra)
6. [Protección de Infraestructuras Críticas](#Protección%20de%20Infraestructuras%20Críticas)
7. [5G](#5G)
8. [IoT / Industria](#IoT%20/%20Industria)
9. [Deep Web y Dark Web](#Deep%20Web%20y%20Dark%20Web)
10. [Inteligencia Artificial en Ciberseguridad](#Inteligencia%20Artificial%20en%20Ciberseguridad)
11. [Deepfakes](#Deepfakes)

---

## Entornos Cloud

> **🧰 Modelos tecnológicos**
> El **cloud computing** es un modelo de prestación de servicios tecnológicos que permite el acceso remoto, escalable y bajo demanda a recursos de computación compartidos a través de internet.
> 
> Existen tres modelos principales:
> *🖥️ IaaS (Infrastructure as a Service)*
> Los proveedores ofrecen máquinas físicas o virtuales. El usuario instala y gestiona su sistema operativo, middleware y aplicaciones.
> 
> *🛠️ PaaS (Platform as a Service)*
> Proporciona un entorno de desarrollo completo sin tener que administrar la infraestructura subyacente.
> 
> *🧑‍💻 SaaS (Software as a Service)*
> Acceso directo a aplicaciones y bases de datos vía web, sin necesidad de instalar nada localmente.
> 
> Además, ha surgido el modelo **SECaaS (Security as a Service)**, donde proveedores ofrecen servicios de ciberseguridad como firewalls, gestión de accesos, detección de amenazas y más, directamente desde la nube.

> ---

> **⚠️ Retos de seguridad**
> La migración a la nube, aunque aporta flexibilidad y ahorro, trae consigo desafíos importantes:
> - **Dependencia de proveedores** externos para garantizar la confidencialidad, integridad y disponibilidad de la información.  
> - Los modelos tradicionales de **seguridad perimetral** pierden eficacia, ya que el acceso a los datos es remoto y desde múltiples ubicaciones.  
> - **Datos y aplicaciones de múltiples organizaciones** pueden residir en los mismos recursos físicos, generando riesgos de aislamiento inadecuado o filtraciones.

> ---

> **🔐 Medidas de protección**
> Para hacer frente a estos riesgos, las estrategias de seguridad en la nube deben ser robustas y actualizadas.
> 
> Usan **protocolos seguros de red** como HTTPS, VPN o IPsec.   y **cifrado de datos** en tránsito y en reposo.
> 
> Además, implementan sistemas de **gestión de identidades y accesos (IAM)** con el modelo **AAA**.
> 
> *🧾 Autenticación*
> Verificar que el usuario es quien dice ser.
> 
> *🚪 Autorización*
> Controlar el acceso a los recursos.
> 
> *📊 Auditoría*
> Registrar y supervisar todas las acciones realizadas.
> 
> Para evitar la gestión individual de múltiples credenciales, se recurre a **esquemas federados** de autenticación (como SAML o OpenID), donde un tercero confiable centraliza el proceso, reduciendo complejidad y aumentando seguridad.

---

## Blockchain

> **📜 Origen y concepto**
> Aunque comúnmente se relaciona con las criptomonedas como **Bitcoin**, el concepto de **blockchain** fue introducido en 1991 por Haber y Stornetta como una forma de proteger documentos digitales mediante técnicas criptográficas.
> 
> Es un **registro distribuido, consensuado e inmutable**, compuesto por bloques enlazados entre sí mediante funciones hash.
> 
> Cada bloque contiene:
> - Transacciones o registros válidos.
> - Información de control del bloque.
> - El hash del bloque anterior, lo que lo encadena y refuerza la integridad de todo el sistema.

> ---

> **🛡️ Seguridad por diseño**
> El diseño descentralizado del blockchain lo convierte en una de las tecnologías más resistentes y confiables:
> - 🗂️ Todos los nodos de la red almacenan una copia completa de la cadena → garantiza **alta disponibilidad**.  
> - 🔄 Para modificar un bloque se necesitaría alterar simultáneamente todas las copias → **resistencia a manipulaciones**.  
> - ✍️ Uso de **firmas digitales** y **certificados criptográficos** para validar transacciones.  
> - 🛑 Alta **resiliencia frente a ataques DoS**, ya que no existe un único punto de fallo.

> ---

> **🏥 Aplicaciones prácticas**
> 
> *🏥 Sanidad*
> Almacenaje seguro y universal del historial clínico de pacientes, accesible solo por usuarios autorizados.
> 
> *📄 Documentación legal*
> Verificación y validación de contratos, escrituras, compraventas, sin posibilidad de falsificación.
> 
> *🏭 Industria*
> Control de procesos logísticos, trazabilidad de productos, automatización de auditorías y cumplimiento.
> 
> Estas aplicaciones se benefician especialmente de las propiedades de inmutabilidad, transparencia y descentralización de la tecnología blockchain.

---

## Dispositivos móviles y BYOD

> **🏡 Auge del teletrabajo**
> A raíz de la pandemia en 2020, el **teletrabajo** se implementó de forma masiva, obligando a las empresas a replantear su infraestructura de seguridad.
> 
> Ahora los empleados acceden a recursos empresariales desde cualquier lugar, utilizando redes no seguras y dispositivos personales.
> 
> Este cambio implica:
> - Asegurar las **redes domésticas y públicas** desde donde se conectan.  
> - Garantizar la seguridad de **dispositivos móviles, tablets y laptops**.  
> - Abandonar el modelo de seguridad basado en el **perímetro corporativo tradicional**, ya que los datos están distribuidos.

> ---

> **📲 Riesgos del BYOD**
> El modelo **BYOD (Bring Your Own Device)** permite a los trabajadores utilizar sus propios dispositivos para tareas laborales.
>  
> Esto mejora la flexibilidad y reduce costos para la empresa, pero también introduce **graves riesgos de seguridad**:
> *🦠 Dispositivos infectados* con malware o aplicaciones no verificadas.  
> *🎯 Ataques dirigidos* a la red empresarial a través de accesos débiles desde dispositivos no gestionados.
> *⚠️ Falta de control* sobre actualizaciones, antivirus y cifrado en dispositivos personales.

> ---

> **🛠️ Medidas recomendadas**
> Las organizaciones deben implementar políticas claras y recursos técnicos que mitiguen estos riesgos:
> - Proveer **dispositivos corporativos** configurados con medidas de seguridad avanzadas.  
> - Aplicar políticas de **cifrado, autenticación multifactor y VPN** obligatorias.  
> - **Capacitar a los empleados** sobre buenas prácticas de ciberseguridad, uso de aplicaciones seguras y reconocimiento de amenazas.  
> - Usar herramientas MDM (Mobile Device Management) para controlar, limitar o borrar datos corporativos en caso de robo o pérdida.

---

## Amenazas Persistentes Avanzadas (APTs)

> **🎯 ¿Qué son?**
> Las **APTs (Advanced Persistent Threats)** son ataques cibernéticos extremadamente sofisticados que se caracterizan por su **persistencia en el tiempo** y su capacidad de mantenerse **ocultos dentro de sistemas críticos** durante meses o incluso años.
> 
> Están orquestados por **grupos organizados y con amplios recursos**, tales como agencias gubernamentales, mafias digitales, grupos terroristas o colectivos hacktivistas.
> 
> Su propósito suele ser el espionaje, robo de datos sensibles o control total del sistema comprometido.

> ---

> **🔎 Características**
> Estas amenazas son muy distintas de ataques comunes como virus o ransomware:
> *🔄 Persistencia*
> El malware se instala en múltiples máquinas para resistir reinstalaciones o cambios de hardware.
> 
> *🥷 Sigilo*
> Utilizan técnicas como cifrado, código ofuscado, evasión avanzada, y mecanismos para autodestruirse en caso de detección.
> 
> *🧬 Flexibilidad*
> Pueden adaptarse y reorganizarse rápidamente para evitar ser eliminadas.
> 
> *🧽 Eliminación de evidencias*
> Minimizan las huellas digitales mediante borrado de logs, tráfico cifrado, y ausencia de comentarios en el código.

---

## Ciberguerra

> **🌐 Definición**
> La **ciberguerra** se refiere al uso de **ataques digitales orquestados por un Estado** con el objetivo de dañar, desestabilizar o espiar infraestructuras críticas de otro país.
> 
> Estos ataques suelen realizarse de forma encubierta, lo que permite evitar sanciones o reacciones diplomáticas directas.
> 
> A diferencia de los conflictos armados convencionales, no requieren tropas ni armamento físico, pero pueden tener efectos devastadores.

> ---

> **💣 Implicaciones**
> *💸 Bajo coste*
> Una ciberguerra puede iniciarse con un equipo reducido de expertos y recursos mínimos comparado con una guerra tradicional.
> 
> *🕵️‍♂️ Anonimato*
> Es extremadamente difícil atribuir un ciberataque a un Estado concreto, lo que complica las represalias.
> 
> *🧠 Manipulación social*
> Algunos gobiernos podrían incluso involucrar indirectamente a su ciudadanía, aprovechando su capacidad de cómputo (ej. botnets sin saberlo).
> 
> *🧨 Impacto global*
> Un solo ataque bien ejecutado puede generar apagones, paralizar hospitales o colapsar sistemas financieros.
> 
> Además, la falta de regulación internacional clara hace que muchos países exploren este tipo de confrontaciones como una opción “segura” y efectiva.


---

## Protección de Infraestructuras Críticas

> **🧱 ¿Qué son?**
> Las infraestructuras críticas son aquellos sistemas físicos y digitales cuya interrupción, destrucción o fallo tendría un impacto severo en:
> - Salud pública  
> - Energía  
> - Economía y finanzas  
> - Transporte y comunicaciones
> 
> Estas infraestructuras son esenciales para el funcionamiento seguro y estable de la sociedad moderna.

> ---

> **🛡️ CNPIC**
> En España, el **Centro Nacional de Protección de Infraestructuras y Ciberseguridad (CNPIC)** es el organismo encargado de proteger estos activos estratégicos.
> 
> *🛑 Prevenir* ataques informáticos dirigidos a infraestructuras críticas.  
> *🧩 Reducir* la vulnerabilidad del país frente a ciberamenazas.  
> *🚑 Minimizar* los daños y mejorar la **recuperación** tras incidentes.

> ---

> **💥 Ejemplos de ataques**
> 📚 Casos reales que demuestran la vulnerabilidad de estas infraestructuras:
> - **2000 - Australia**: un exempleado provocó un vertido de aguas residuales en parques y ríos tras acceder al sistema de control de una empresa de agua.  
> - **2015 - Ucrania**: el grupo BlackEnergy causó un apagón masivo que dejó sin luz a millones de personas durante 6 horas.  
> - **2017 - Reino Unido**: el ransomware WannaCry paralizó hospitales del NHS, afectando el acceso a historiales médicos.  
> - **2021 - España**: el ransomware Zeppelin afectó al servicio en la nube de ASAC, dejando sin servicios a varios ayuntamientos y organismos estatales.



---

## 5G

> **🚀 Ventajas**
> La tecnología **5G** representa una **evolución clave** en las telecomunicaciones, mejorando tanto el rendimiento como la eficiencia en comparación con generaciones anteriores:
> 
> - ⚡ **Velocidad hasta 100 veces mayor** que 4G → ideal para transmisión de datos en tiempo real (ej. vídeo 4K, realidad aumentada).  
> - ⏱️ **Latencia ultra baja**, crucial para aplicaciones críticas como vehículos autónomos, cirugía remota o control industrial.  
> - 🔋 **Menor consumo energético**, lo que permite operar sensores IoT y dispositivos móviles por más tiempo.  
> - 🌐 **Gestión avanzada de conexiones simultáneas**, esencial para entornos de alta densidad como ciudades inteligentes y fábricas automatizadas.

> ---

> **⚠️ Puntos críticos**
> A pesar de sus ventajas, la adopción masiva de 5G también introduce **nuevos retos de ciberseguridad**:
> 
> - 🕳️ **Mayor superficie de ataque** debido al aumento en la cantidad de dispositivos conectados y nodos de acceso.  
> - 🧱 **Nodos críticos expuestos**: ciertos equipos de red se convierten en elementos estratégicos que, si se comprometen, afectan a toda la infraestructura.  
> - 🔗 **Dependencia tecnológica** de fabricantes y proveedores específicos, lo cual puede comprometer la **soberanía digital y el control nacional** sobre la infraestructura.

> ---

> **🧠 Riesgos futuros**
> 5G no solo revolucionará las telecomunicaciones, sino que se convertirá en la **infraestructura base** para servicios críticos:
> 
> - 🏥 **Sanidad conectada**  
> - 🚗 **Transporte autónomo y logístico**  
> - 🏙️ **Ciudades inteligentes**  
> - 🛡️ **Defensa y seguridad pública**
> 
> Esto requiere implementar:
> - **Medidas de protección proactivas** como **monitoreo continuo**, segmentación de red y detección de anomalías.  
> - **Blindaje contra amenazas distribuidas** como ataques DDoS o infiltraciones a través de dispositivos IoT comprometidos.
> 
> 📉 Un fallo en la infraestructura 5G podría tener **repercusiones graves a nivel económico, social y estratégico**.

---

## IoT / Industria

> **📊 Generalidades**
> El Internet de las Cosas (IoT) conecta una cantidad creciente de dispositivos que operan de forma autónoma sin intervención humana.
> 
> Incluye sensores industriales, sistemas de automatización urbana (smart cities) y dispositivos domésticos inteligentes.

> ---

> **🏭 Industria y ciudades**
> En el sector industrial, sensores controlan procesos clave como temperatura, presión o velocidad de producción.
> 
> En ciudades inteligentes, regulan servicios como el tráfico, climatización en edificios, transporte público o parkings.  
> 
> Un ataque puede paralizar operaciones o exponer datos sensibles.

> ---

> **🏥 Salud**
> Aplicaciones médicas: monitorización remota de pacientes, bio wearables, diagnóstico a distancia.
> 
> La información sanitaria es extremadamente sensible y debe protegerse contra accesos no autorizados.

> ---

> **🏠 Hogar y privacidad**
> El hogar es uno de los entornos con mayor implementación de IoT: cámaras, luces, cerraduras, termostatos, alarmas y vehículos conectados.
> 
> El principal riesgo: configuración por defecto y seguridad insuficiente → acceso fácil para atacantes.

> ---

> **🧰 Herramientas clave**
> *🔎 Shodan*
> Motor de búsqueda especializado en dispositivos conectados a internet (cámaras, routers, servidores).
> 
> *📡 Bluescanner*
> Rastrea dispositivos Bluetooth cercanos.
> 
> *🕵️ Bluesniff*
> Detecta redes Bluetooth ocultas y ataca a dispositivos vulnerables.

---

## Deep Web y Dark Web

> **🌐 Diferencias**
> El contenido que no es accesible mediante motores de búsqueda tradicionales se clasifica generalmente en dos categorías:
> 
> *🔍 Deep Web*
> Parte de internet que **no está indexada** por buscadores comunes. Incluye bases de datos académicas, cuentas personales (correo, banca online), intranets corporativas y servicios en la nube como Dropbox o Google Drive.
> 
> No es maliciosa por sí misma, simplemente está protegida o restringida.

> *🕸️ Dark Web*
> Subconjunto de la Deep Web al que **solo se puede acceder mediante herramientas específicas** como **Tor (The Onion Router)**, **I2P** u otras redes cifradas. Está diseñada para garantizar anonimato tanto a usuarios como a servidores.

> ---

> **⚠️ Actividades**
> Aunque existen usos legítimos (libertad de expresión en regímenes opresivos, periodismo, privacidad), la **Dark Web** también alberga múltiples actividades delictivas o altamente sensibles:
> 
>  *💰 Venta de datos*
>  Credenciales filtradas, exploits, información personal y corporativa robada.
>  
> *🧠 Foros técnicos clandestinos*
> Se debaten y comercializan vulnerabilidades 0-day antes de que sean conocidas públicamente.
> 
> *🕵️‍♂️ Filtraciones internas*
> Empleados descontentos o comprometidos filtran documentos confidenciales o venden accesos privilegiados.
> 
> *🏴 Actividades ilegales*
> Tráfico de armas, drogas, falsificación de documentos, servicios de hacking, etc.
> 
> 🧠 Por ello, muchas empresas implementan **sistemas de inteligencia de amenazas (Threat Intelligence)** para **monitorizar la Dark Web** en busca de posibles compromisos que involucren a su organización.
> 
> 📌 La vigilancia proactiva de estos entornos puede ayudar a **anticipar ataques, detectar filtraciones y proteger la reputación corporativa**.

---

## Inteligencia Artificial en Ciberseguridad

> **📈 Evolución**
> La **Inteligencia Artificial (IA)** se ha convertido en una herramienta fundamental en el ámbito de la ciberseguridad.
> 
> El mercado global de IA aplicada a seguridad crecerá de **8.800 millones de dólares (2019)** a más de **38.200 millones (2026)**.
> 
> 🧠 Esta tecnología se emplea en **todas las fases del ciclo de defensa**, desde la prevención hasta la respuesta ante incidentes.

> ---

> **🔍 Aplicaciones defensivas**
> Las soluciones basadas en IA son cada vez más eficaces para:
> - *🚨 Detectar amenazas en tiempo real* mediante análisis de logs, comportamiento y patrones anómalos.
> - *🤖 Automatizar respuestas* ante incidentes (bloqueo de IPs, cuarentena de archivos, revocación de accesos).
> - *📊 Analizar comportamiento de usuarios (UEBA)* para detectar accesos inusuales, fraudes o cuentas comprometidas.  
> - *🧪 Filtrar falsos positivos* en sistemas de detección de intrusos, mejorando la eficiencia del equipo de seguridad.

> ---

> **🧨 Uso ofensivo**
> La IA también puede ser usada por actores maliciosos con fines destructivos:
> - *🕵️‍♂️ Ciberespionaje asistido por IA*, capaz de filtrar grandes volúmenes de datos y priorizar objetivos.  
> - *🎣 Phishing automatizado* con mensajes altamente personalizados generados mediante NLP (Procesamiento del Lenguaje Natural).  
> - *🎯 Personalización de ataques* basada en datos recopilados de redes sociales y correos anteriores.  
> - *🦾 Creación de malware adaptativo*, que cambia su comportamiento para evadir mecanismos de detección.
> 

---

## Deepfakes

> **📺 Qué son**
> Los **deepfakes** son contenidos multimedia (principalmente vídeo y audio) manipulados mediante **inteligencia artificial** para hacer que una persona **aparente decir o hacer cosas que nunca ocurrieron**.
> 
> Son utilizados en contextos como:
> - Fake news y desinformación.  
> - Pornografía no consensuada.  
> - Manipulación política y electoral.  
> - Suplantación de identidad en fraudes.

> ---

> **🧠 Tecnología**
> La tecnología detrás de los deepfakes se basa en redes neuronales avanzadas, especialmente:
> - *🔁 Autoencoders* para mapear y reconstruir rostros.  
> - *🧠 GANs (Generative Adversarial Networks)*: redes que compiten entre sí (una genera, otra evalúa) hasta lograr resultados realistas.  
> - *📷 Few-shot learning*: sistemas como los de Samsung que permiten **crear un deepfake con solo unas pocas imágenes** del rostro.

> ---

> **🪦 Necromancia digital**
> La tecnología también se ha usado para **recrear a personas fallecidas**, generando vídeos o interacciones simuladas:
> - 🎬 En cine (ej. Star Wars).  
> - 🧬 En sitios web genealógicos como **MyHeritage**, donde familiares pueden "revivir" fotos de antepasados.

> ---

> **🤖 Identidades falsas**
> Con IA también se generan **rostros que nunca han existido**, como los de la web [thispersondoesnotexist.com](https://thispersondoesnotexist.com/).
> 
> Estos rostros sintéticos pueden ser usados para:
> - Crear perfiles falsos en redes sociales.  
> - Suplantar identidad en procesos de verificación.  
> - Generar evidencia falsa en fraudes complejos.
> 
> Es fundamental desarrollar tecnologías para **detectar y combatir deepfakes**, y fomentar la educación digital para evitar caer en sus engaños.

---