---
tags: URJC URJC_DAW Angular TypeScript SPA
---

# DAW - Angular Tema 1

---

## Tabla de Contenidos

1. [Taxonomía de las Webs](#Taxonomía%20de%20las%20Webs)
2. [Angular: El Framework Estrella](#Angular%20El%20Framework%20Estrella)
3. [Estructura de un Proyecto Angular](#Estructura%20de%20un%20Proyecto%20Angular)
4. [Empezando con Angular](#Empezando%20con%20Angular)
5. [TypeScript: El Motor de Angular](#TypeScript%20El%20Motor%20de%20Angular)
6. [Java vs TypeScript: La Comparativa](#Java%20vs%20TypeScript%20La%20Comparativa)
7. [Conclusión](#Conclusión)

---

## Taxonomía de las Webs

> **🧭 Panorama de la Web**
> 
> Existen *varios tipos de webs* dependiendo de cómo usan las tecnologías de cliente y servidor:
> 
> **🧱 Página Web Estática**  
> *Contenido fijo*, servido directamente desde el disco.
> 
> **⚙️ Página Web Interactiva**  
> Añade *dinamismo* mediante JavaScript.
> 
> **💡 Aplicación Web con Cliente Estático**  
> La lógica de la aplicación reside *principalmente* en el servidor.
> 
> **🚀 Aplicación Web Interactiva**  
> El cliente y servidor colaboran activamente.
> 
> **📡 Aplicación Web con AJAX**  
> *Comunicación asíncrona*, sin recarga de página.
> 
> **🧩 SPA (Single Page Application)**  
> Una sola página con navegación fluida y experiencia inmersiva.

---

## Angular: El Framework Estrella

> **🚀 ¿Qué es Angular?**
> 
> *Angular* es un framework pensado para desarrollar *SPA*, donde la experiencia de usuario es rápida y fluida.
> 
> Permite extender HTML con etiquetas y comportamientos personalizados, y se recomienda usar con *TypeScript* para aprovechar al máximo sus capacidades.
> 
> **🔗 [Ver documentación oficial](https://angular.io/)**

> ---

> **🛠️ Funcionalidades que enamoran**
>
> - *Composición de componentes* para construir interfaces ordenadas.
> - *Inyección de dependencias* que facilita la reutilización del código.
> - *Cliente HTTP integrado* para consumir APIs REST.
> - *Animaciones* y *SEO friendly* con renderizado del servidor.
> - *Testing robusto* con soporte para pruebas unitarias y e2e.
> 
> *¡Una herramienta todoterreno para proyectos web modernos!* 🌍

> ---

> **💡 Herramientas integradas**
> 
> *Angular CLI*
> 
> - Generar proyectos automáticamente.
> - Compilar y actualizar la app al vuelo.
> - Preparar la distribución con build.

---

## Estructura de un Proyecto Angular

> **🧩 ¿Qué encontrarás en un proyecto?**
> 
> - `src/` → *Fuente principal de la aplicación.*
> - `node_modules/` → *Librerías descargadas.*
> - `app/` → *Componentes principales.*
> - `assets/` → *Recursos estáticos como imágenes o estilos.*
> - `index.html` → *Página inicial.*
> - `angular.json`, `package.json` → *Configuraciones clave del proyecto.*
> 
> _Todo organizado para que el desarrollo sea eficiente y escalable._ 🧭

> ---

> **💻 Editores recomendados**
> 
> *Visual Studio Code* 🖥️ es la estrella por:
> - Extensiones especializadas.
> - Integración nativa con Angular y TypeScript.
> 
> También puedes usar Sublime Text o WebStorm si lo prefieres.

---

## Empezando con Angular

> **🧩 Crear y lanzar un proyecto**
> 
> ```bash
> $ ng new mi-proyecto
> $ cd mi-proyecto
> $ ng serve
> ```
> 
> *¡Y listo!* La aplicación se actualizará automáticamente cada vez que guardes cambios. 🔥

> ---

> **📦 Optimiza tu flujo**
> 
> _Ahorra espacio reusando carpetas `node_modules`:_
> 
> ```bash
> $ mv proyecto1/node_modules proyecto2/node_modules
> ```

> ---

> **🔍 Descargar ejemplos listos**
> 
> ```bash
> git clone https://github.com/codeurjc/curso-angular
> cd curso-angular/ejem1
> npm install
> ng serve
> ```
> 
> *¡Explora ejemplos reales y empieza a experimentar!* 🎯

---

## TypeScript: El Motor de Angular

> **💡 ¿Por qué usar TypeScript?**
> 
> - Es *JavaScript mejorado* con tipado opcional 🧩
> - Detecta errores antes de ejecutar 💡
> - Compatible con todos los navegadores 🎯
> - Favorece proyectos grandes y mantenibles 🧑‍💻
> 
> [🔗 Documentación oficial](http://www.typescriptlang.org/)

> ---

> **🚀 Ventajas que destacan**
> 
> - Inferencia de tipos que evita definirlos constantemente.
> - Herramientas inteligentes que completan código y ayudan a refactorizar.
> - Permite migrar desde JavaScript fácilmente, incluso combinarlos.
> 
> _¡Perfecto si vienes del mundo de Java o C#!_

---

## Java vs TypeScript: La Comparativa

> **👨‍💻 Similitudes clave**
> 
> - Las clases en TypeScript se exportan explícitamente con `export`.
> - Se usan `:` para definir tipos:  
> 
> ```typescript
> private salario: number;
> ```

> ---

> **🧩 Constructores eficientes**
> 
> En TypeScript, puedes declarar e inicializar atributos directamente en el constructor:
> 
> ```typescript
> constructor(private nombre: string, private salario: number) {}
> ```

> ---

> **💡 Operaciones con listas y funciones**
> 
> - `push()` en vez de `add()`.
> - Sintaxis elegante con *arrow functions*:  
> 
> ```typescript
> empleados.forEach(emp => console.log(emp.getNombre()));
> ```
> 
> _Las lambdas de Java se llaman arrow functions en TypeScript, pero funcionan igual o mejor 😎_

> ---

> **🧩 Extras de TypeScript**
> 
> - Type guards como `instanceof`, `typeof`.
> - Objetos literales tipados para estructuras claras.
> - Uniones de tipos flexibles: `string | number`.
> - Soporte para sobrecarga de métodos.

---

## Conclusión

> **🚀 Angular + TypeScript**
> 
> Combinan potencia y flexibilidad para crear aplicaciones modernas, rápidas y escalables.
> 
> *TypeScript* aporta seguridad y eficiencia.
> *Angular* te da la arquitectura y herramientas para brillar.
> 
> **🧩 ¡La combinación perfecta para el desarrollo web profesional!**

> ---

> **📚 Recursos recomendados**
> 
> - [Angular Oficial](https://angular.io/start)
> - [TypeScript Docs](https://www.typescriptlang.org/docs/)

---