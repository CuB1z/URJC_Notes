---
tags: URJC, URJC_SI
---

# Tema 9 - Seguridad Informática

---

## Tabla de Contenidos

1. [Buenas Prácticas para el Usuario](#Buenas%20Prácticas%20para%20el%20Usuario)
2. [Buenas Prácticas para el Administrador](#Buenas%20Prácticas%20para%20el%20Administrador)
3. [Buenas Prácticas para el Desarrollador](#Buenas%20Prácticas%20para%20el%20Desarrollador)
4. [Metodologías de Desarrollo Seguro](#Metodologías%20de%20Desarrollo%20Seguro)
5. [Metodologías Completas de Seguridad](#Metodologías%20Completas%20de%20Seguridad)
6. [Seguridad en Aplicaciones Móviles](#Seguridad%20en%20Aplicaciones%20Móviles)

---

## Buenas Prácticas para el Usuario

> **👤 Usuario Final**  
> Los **usuarios finales** son el **objetivo más común** en los ataques de ingeniería social, phishing y malware.
> 
> Su **formación**, hábitos digitales y conciencia sobre los riesgos juegan un papel clave en la **prevención de brechas de seguridad**.

> ---

> **🔑 Buenas prácticas**
> - 🔐 Utilizar **contraseñas fuertes y únicas**, con al menos 12 caracteres, combinando letras, números y símbolos.  
> - 💼 Emplear **gestores de contraseñas** para mantenerlas seguras y evitar reutilizarlas.  
> - 🔄 Mantener **software, navegadores y sistemas operativos actualizados** frente a vulnerabilidades.  
> - 🦠 Usar un **antivirus confiable** y mantenerlo activado y actualizado.  
> - 🚫 **Evitar enlaces o archivos sospechosos** recibidos por correo, mensajería o redes sociales.  
> - 🔒 Activar **autenticación multifactor (MFA)** siempre que sea posible.
> 
> 🧠 La capacitación continua en **ciberhigiene digital** es una defensa fundamental.

---

## Buenas Prácticas para el Administrador

> **🧑‍💻 Administrador de Sistemas**  
> Los administradores tienen la responsabilidad de **diseñar, implementar y mantener entornos seguros**, garantizando tanto la **protección técnica** como la **concienciación del personal**.
> 
> Además de proteger la infraestructura, deben fomentar una **cultura de seguridad organizacional** que involucre a todos los niveles.

> ---
 
> **🛠️ Buenas prácticas**
> - 🔒 Asegurar la **infraestructura física** (servidores, hardware, accesos restringidos).  
> - 👥 Implementar **control de acceso basado en roles (RBAC)** para limitar privilegios.  
> - 🌐 Asegurar **accesos remotos mediante protocolos cifrados** (VPN, SSH).  
> - 🧠 Capacitar continuamente a usuarios sobre nuevas amenazas y políticas.  
> - 🧾 Aplicar políticas estrictas de seguridad:
>   - 📅 **Contraseñas caducables** y bloqueo tras intentos fallidos.  
>   - 🧍 **Principio de privilegio mínimo**: solo acceso a lo estrictamente necesario.  
>   - ❌ **Eliminación de cuentas obsoletas o inactivas**.  
>   - 🚫 **Restricción de shells** o accesos innecesarios.  
> - 🔑 Uso correcto de **criptografía**:
>   - 🧊 **Simétrica**: AES, rápida y eficiente para cifrado de grandes volúmenes.  
>   - 🔐 **Asimétrica**: RSA, útil para autenticación y transmisión segura de claves.

---

## Buenas Prácticas para el Desarrollador

> **💻 Codificación Segura**  
> El desarrollador es el **primer defensor del software**. Su trabajo determina la **resistencia estructural de las aplicaciones** frente a amenazas como inyecciones, desbordamientos, escalado de privilegios o fugas de información.
> 
> Un código mal diseñado o descuidado **puede convertirse en una puerta abierta para atacantes**, incluso si la infraestructura subyacente es segura.
> 
> 👨‍💻 La **seguridad debe integrarse desde el diseño**, no como un añadido posterior.

> ---

> **✔️ Validaciones clave**
> Aplicar validaciones correctas es esencial para evitar ataques como SQL Injection, XSS, o ejecución remota de comandos:
> 
> - 🧮 **Validar operandos y rangos** antes de su uso (especialmente en cálculos, bucles, accesos a arrays).  
> - 📥 **Verificar y sanear entradas externas**, tanto de usuarios como de APIs o archivos.  
> - 📂 **Canonizar rutas** y normalizar cadenas para evitar traversal o manipulaciones.  
> - 🚫 **Evitar mostrar trazas o errores detallados** que puedan revelar información sensible (rutas internas, estructuras de base de datos, versiones...).
> 
> 🧰 Usa librerías confiables y, si es posible, frameworks que integren validación de entrada automática.

> ---

> **🧠 Buenas costumbres**
> El desarrollo seguro también implica una serie de buenas prácticas generales que evitan errores comunes:
> 
> - ⚠️ **No ignorar excepciones** ni valores de retorno: capturar y gestionar adecuadamente cualquier fallo.  
> - 🧹 **Eliminar archivos temporales** y datos sensibles una vez ya no son necesarios.  
> - 🧼 **Liberar recursos correctamente**: memoria, sockets, hilos, conexiones a base de datos.  
> - 🎲 **Utilizar generadores aleatorios seguros** como `SecureRandom`, `/dev/urandom`, evitando funciones predecibles como `rand()`.  
> - 📚 **Conocer bien el lenguaje y sus vulnerabilidades comunes** (ej. errores de manejo de memoria en C/C++, manejo de objetos en Java, eval() en Python, etc).
> 
> 🧠 Adoptar el enfoque **DevSecOps** (Desarrollo + Seguridad + Operaciones) favorece la integración de seguridad en todas las fases del ciclo de vida del software.
> 
> 🏗️ El software seguro **no solo se ejecuta bien**, sino que **resiste ataques y no compromete los datos del usuario ni del sistema**.


---

## Metodologías de Desarrollo Seguro

> **🔍 Análisis Estático**
> El **análisis estático** revisa el código fuente **sin necesidad de ejecutarlo**, lo que permite detectar:
> - 🛠️ Errores comunes de sintaxis y lógica.
> - ⚠️ Problemas de estilo, complejidad y duplicación.
> - 🧨 Vulnerabilidades conocidas (buffer overflows, inyecciones, etc.).
> 
> Es una práctica recomendable en etapas tempranas del desarrollo, especialmente antes de la integración o despliegue.

> ---

> **🔧 Herramientas recomendadas**:
> 
> Algunas de las herramientas más utilizadas para análisis estático incluyen:
> 
> - 🧪 `FlawFinder` — analiza C/C++ en busca de llamadas inseguras.  
> - 🧹 `PMD` — útil para código Java, detecta errores y duplicación.  
> - 🧬 `LAPSE+` — plugin de análisis de seguridad para Java basado en OWASP.  
> - ☁️ `SonarCloud` — solución en la nube para análisis estático continuo.  
> - 🧰 `AppScan (IBM)` — análisis de vulnerabilidades en aplicaciones web.  
> - 🏗️ `Fortify (HP)` — análisis estático y dinámico para múltiples lenguajes.

> ---

> **📚 Guías y Estándares**
> 
> Para escribir código seguro y conforme a las mejores prácticas, existen guías y estándares ampliamente aceptados:
> 
> | 📘 Estándar | 🔎 Enfoque técnico |
> |------------|--------------------|
> | **ISO**    | Buenas prácticas para lenguaje Ada (sistemas críticos). |
> | **MISRA**  | Reglas para C en entornos industriales (automoción, aeroespacial). |
> | **CERT**   | Reglas de codificación segura para C, C++, Java. |
> | **OWASP**  | Guía rápida y concisa para desarrollo web seguro. |
> 
> Estos estándares ayudan a minimizar errores, fortalecer la arquitectura del software y mejorar su mantenibilidad.

> ---

> **🏆 Top 10 buenas prácticas CERT**
> 
> El equipo CERT (Carnegie Mellon) establece 10 reglas clave para un desarrollo seguro y responsable:
> 
> 1. ✅ Validar cuidadosamente **todas las entradas externas**.  
> 2. ⚠️ Corregir todos los **warnings del compilador**.  
> 3. 🏗️ Diseñar con **políticas de seguridad desde el inicio**.  
> 4. 🔧 Aplicar el principio **KISS** (*Keep It Simple, Stupid*).  
> 5. 🚫 Aplicar el principio de **negación por defecto** (deny by default).  
> 6. 🔒 Usar **privilegios mínimos** para cada proceso.  
> 7. 🧼 **Sanear salidas** hacia otros sistemas (bases de datos, redes...).  
> 8. 🛡️ Fomentar la **defensa en profundidad**.  
> 9. 🔬 Asegurar **testing y verificación continua**.  
> 10. 📏 Adoptar y respetar **estándares de codificación bien definidos**.

> ---

> **⚖️ Comparativa de Análisis**
> 
> | Tipo         | 🧪 Características principales |
> |--------------|-------------------------------|
> | **Estático**  | No ejecuta el código · Usa reglas predefinidas · Rápido · Automatizable |
> | **Dinámico**  | Ejecuta la aplicación · Detecta vulnerabilidades reales en tiempo de ejecución · Requiere entorno funcional |
> 
> Ambos enfoques son **complementarios** y deben combinarse dentro de una estrategia de desarrollo seguro (DevSecOps).


---

## Metodologías Completas de Seguridad

> **📈 Modelos de Ciclo Completo**  
> La seguridad no debe ser un añadido tardío, sino un proceso transversal en todo el ciclo de vida del software.

> ---

> **🧩 Modelos destacados**
> 
> | 🧱 Modelo     | 💬 Descripción |
> |--------------|----------------|
> | **BSIMM**    | Estudia prácticas reales en grandes empresas. Diagnóstico de madurez. |
> | **OWASP SAMM** | Modelo abierto y adaptable a cualquier empresa o proyecto. |
> | **SDL (Microsoft)** | Guía paso a paso con checklist para cada fase del desarrollo. |

---

> **🔗 Elementos en común**
>
> | 🧠 Elemento | 🌟 Descripción |
> |------------|---------------|
> | 🔁 Procesos repetibles | Estandarización de actividades seguras |
> | 📏 Resultados medibles | Indicadores de seguridad por fase |
> | 🔗 Trazabilidad | Historial de decisiones y cambios |
> | 🎓 Formación continua | Entrenamiento constante del equipo |
> | 🛠️ SD3+C | Seguridad por diseño, por defecto y con buena comunicación |

---

## Seguridad en Aplicaciones Móviles

> **📱 Contexto móvil moderno**  
> Las **aplicaciones móviles** operan en un entorno con características y desafíos propios.
> 
> A diferencia de los sistemas tradicionales, los móviles tienen:
> - 🔓 Menor control del usuario sobre el sistema operativo.  
> - 📦 Almacenamiento local más accesible y propenso a fuga de datos.  
> - 🧾 Permisos extensos que, mal gestionados, pueden ser explotados.  
> - 🕵️‍♂️ Entornos expuestos a ingeniería inversa y análisis forense por parte de atacantes.
> 
> 📌 Por ello, **la seguridad debe planificarse desde el diseño** de la aplicación (principio de seguridad por diseño) y mantenerse durante todo su ciclo de vida.

> ---

> **📉 Principales riesgos OWASP Mobile Top 10**
> 
> El proyecto **OWASP Mobile Top 10** identifica los riesgos más frecuentes en apps móviles:
> 
> - 💥 **Inyección de comandos**: mediante inputs maliciosos o APIs expuestas.  
> - 🧪 **Ingeniería inversa**: los atacantes analizan el APK/IPA para descubrir lógica interna, claves o vulnerabilidades.  
> - 🗄️ **Almacenamiento inseguro**: guardar contraseñas, tokens o datos sensibles sin cifrado adecuado.  
> - 🚪 **Fallas en autenticación y control de sesión**: tokens inseguros, sesiones no caducadas, mal uso de cookies.  
> - 🌐 **Comunicación insegura con APIs**: falta de TLS, certificados no verificados, APIs abiertas o mal protegidas.
> 
> 🧠 Conocer estos riesgos permite adoptar medidas específicas antes de que la app llegue al usuario.

> ---

> **🧰 Buenas prácticas específicas**
> 
> Para proteger eficazmente una aplicación móvil, se deben considerar prácticas como:
> 
> *🔐 Validar siempre del lado del servidor*
> Nunca confiar en los datos manipulables del cliente.
> 
> *🔒 Cifrar datos en reposo y en tránsito*
> Usar AES para almacenamiento y TLS 1.2+ para comunicación.
> 
> *🚫 Evitar permisos innecesarios*
> Solicitar solo los estrictamente requeridos para la funcionalidad.
> 
> *🧬 Ofuscar y proteger el código*
> Dificultar la ingeniería inversa con herramientas de ofuscación, firmas digitales, y detección de entornos modificados.
> 
> *📛 No almacenar secretos en el dispositivo*
> Como claves de API, certificados, contraseñas. Usar almacenamiento seguro o cifrado fuerte si es imprescindible.
> 
> *📲 Aplicar control de versiones y actualizaciones* regulares con parches de seguridad.
> 
> 📱 La seguridad móvil es un aspecto **crítico y dinámico**, ya que los atacantes constantemente prueban nuevas formas de vulnerar dispositivos, apps y usuarios.

---