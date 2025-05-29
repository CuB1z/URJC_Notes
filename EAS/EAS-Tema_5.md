---
tags: URJC URJC_EAS
---

# Tema 5 - Evolución y Adaptación Software

---

## Tabla de Contenidos

1. [Introducción General](#Introducción%20General)
2. [Principios SOLID](#Principios%20SOLID)
3. [Relación con Patrones de Diseño](#Relación%20con%20Patrones%20de%20Diseño)
4. [Principios RCC – Cohesión de Paquetes](#Principios%20RCC%20–%20Cohesión%20de%20Paquetes)
5. [Principios ASS – Acoplamiento y Estabilidad](#Principios%20ASS%20–%20Acoplamiento%20y%20Estabilidad)
6. [Inversión de Control (IoC) y Técnicas Relacionadas](#Inversión%20de%20Control%20(IoC)%20y%20Técnicas%20Relacionadas)
7. [Conclusión](#Conclusión)

---

## Introducción General

> **📘 Diseño Sostenible**  
> El diseño de software orientado a objetos moderno busca garantizar la *escalabilidad*, *mantenibilidad* y *flexibilidad* ante los cambios. Los principios que guían este diseño se resumen en tres grandes grupos:
> - Principios **SOLID**, aplicables a nivel de clases.
> - Principios **RCC/ASS**, aplicables a nivel de paquetes/componentes.
> - Patrones y estrategias como **IoC** o **DIP**, a nivel arquitectónico.

---

## Principios SOLID

> **🔑 SRP – Principio de Responsabilidad Única**
> *“Una clase debe tener un solo motivo para cambiar.”*
> 
> Significa que una clase debe tener **una única responsabilidad** dentro del sistema.
> 
> **📚 Detalles**
> - Cada clase representa un *actor* del sistema.
> - Si hay más de una razón para cambiar, deben separarse en clases diferentes.
> - Conecta con el principio de cohesión.

> ---

> **🚪 OCP – Principio Abierto-Cerrado**
> *“Las entidades de software deben estar abiertas a extensión, pero cerradas a modificación.”*
> 
> Es decir, el comportamiento se puede extender sin modificar el código existente.
> 
> **🛠 Técnicas**  
> - Abstracción con clases base e interfaces.
> - Polimorfismo.
> - Patrón `Strategy`, `Template Method`, etc.

> ---

> **🔄 LSP – Principio de Sustitución de Liskov**  
> *“Las subclases deben poder ser usadas en lugar de sus clases base sin alterar el funcionamiento del programa.”*
> 
> **⚠️ Peligro**  
> Violaciones del LSP son *violaciones ocultas del OCP*, que afectan el polimorfismo y la reutilización.
> 
> **Ejemplo clásico**: el dilema “Círculo vs Elipse” muestra cómo la herencia mal aplicada puede romper este principio.

> ---

> **📎 ISP – Principio de Segregación de Interfaces**  
> *“Los clientes no deben depender de interfaces que no utilizan.”*
> 
> **Solución**  
> - Interfaces pequeñas y específicas por cliente.
> - Aplicar múltiples interfaces en lugar de una única interfaz grande.

> ---

> **🔁 DIP – Principio de Inversión de Dependencias**  
> *“Los módulos de alto nivel no deben depender de los de bajo nivel. Ambos deben depender de abstracciones.”*
> 
> **Claves**
> - Abstraer dependencias usando interfaces o clases abstractas.
> - El código de alto nivel no debe conocer detalles concretos de bajo nivel.
> - Fomenta el uso de IoC e Inyección de Dependencias.

---

## Relación con Patrones de Diseño

> **🏗️ Conexiones prácticas**
> Los principios SOLID conducen a patrones OO ampliamente usados:
> 
> | Problema | Patrón Recomendado |
> |----------|---------------------|
> | Crear objetos sin conocer clase concreta | `Factory Method`, `Abstract Factory` |
> | Extender funcionalidad sin modificar código | `Decorator`, `Strategy`, `Template Method` |
> | Separar políticas de implementación | `Bridge`, `Command`, `Observer` |
> | Sustitución sin acoplamiento fuerte | `Adapter`, `Proxy` |

---

## Principios RCC – Cohesión de Paquetes

> **🔁 REP – Principio de Equivalencia Reutilización/Revisión**  
> *Los elementos reutilizados juntos deben vivir juntos y distribuirse juntos.*
> 
> **Claves**
> - Paquetes = unidad de reutilización + revisión.
> - Requiere herramientas de gestión de versiones.

> ---

> **♻️ CRP – Principio de Reutilización Común**  
> *No se debe forzar a los clientes a depender de clases que no usan.*
> 
> **Consecuencias**
> - Cambios en el paquete afectan a todos los clientes.
> - Divide paquetes que agrupan funcionalidades no cohesionadas.

> ---

> **🔒 CCP – Principio de Cierre Común**
> *Agrupar clases que cambian por las mismas razones.*
> 
> **Ejemplo**  
> Reglas de negocio sujetas a la misma ley deben estar juntas para que un cambio afecte solo un paquete.

---

## Principios ASS – Acoplamiento y Estabilidad

> **📉 ADP – Principio de Dependencias Acíclicas**  
> *La estructura de dependencias entre paquetes debe ser acíclica.*
> 
> **Peligros de los ciclos**
> - Dificultan mantenimiento y pruebas.
> - Complican despliegue e integración.

> ---

> **🏗️ SDP – Principio de Dependencias Estables**  
> *Un paquete debe depender solo de paquetes más estables que él.*
> 
> **Medida de estabilidad**  
> - Ca = clases externas que dependen de él (responsabilidad).
> - Ce = clases internas que dependen de otros (dependencia).
> - I = Ce / (Ca + Ce)

> ---

> **🧱 SAP – Principio de Abstracciones Estables**  
> *Los paquetes estables deben ser abstractos para permitir su extensión.*
> 
> **Relación estabilidad-abstracción**
> - Estabilidad alta → debe ser más abstracto.
> - Paquetes muy estables y concretos → rígidos y peligrosos.

---

## Inversión de Control (IoC) y Técnicas Relacionadas

> **🔁 IoC – Inversión de Control**
> Cambia el flujo tradicional del programa. En lugar de que el código controle sus dependencias, delega en un *framework* o contenedor.

> ---

>  **🧩 Patrones Relacionados**
> 
> *🔧 Template Method*
> Define la estructura de un algoritmo en una clase abstracta. Subclases implementan los pasos concretos.
> 
> *🧠 Strategy*
> Permite cambiar el comportamiento de una clase en tiempo de ejecución a través de la inyección de algoritmos.
> 
> *🧩 Otros relevantes*
> - `Adapter`
> - `Decorator`
> - `Plugin`
> - `Observer`

---

## Conclusión

> **🎯 Síntesis**
> - **SOLID** mejora el diseño orientado a objetos.
> - **RCC y ASS** permiten una organización modular a gran escala.
> - **DIP + IoC** ofrecen una arquitectura flexible y desacoplada.
> 
> **⚙️ Beneficios**
> - Reducción del acoplamiento
> - Aumento de la cohesión
> - Mejora en pruebas, mantenimiento y extensibilidad
> 
> **📚 Recomendaciones**
> - *Clean Architecture* – Robert C. Martin  
> - *Agile Software Development* – R. Martin  
> - *Domain-Driven Design* – Eric Evans

---