---
tags: URJC URJC_DAW Angular Components UI Bootstrap Design
---

# DAW - Angular Tema 5

---

## Tabla de Contenidos

1. [Introducción](#Introducción)
2. [Frameworks CSS](#Frameworks%20CSS)
3. [Librerías de Componentes JavaScript](#Librerías%20de%20Componentes%20JavaScript)
4. [ng-bootstrap](#ng-bootstrap)
5. [Angular Material](#Angular%20Material)
6. [Otras Librerías Interesantes](#Otras%20Librerías%20Interesantes)
7. [Plantillas Profesionales](#Plantillas%20Profesionales)
8. [Conclusión](#Conclusión)

---

## Introducción

> **💡 Angular y los Componentes**
>
> Angular por sí solo no ofrece componentes de alto nivel para las interfaces.  
> Sin embargo, existen *muchas librerías* que complementan el diseño y la funcionalidad:
>
> - Frameworks CSS 🎨
> - Librerías específicas para Angular 📦
> - Gráficas y charts 📊
> - Carga de archivos 📂
> - Plantillas profesionales para admin dashboards 🖥️

---

## Frameworks CSS

> **💡 Mejora el diseño fácilmente**
>
> Angular permite integrar cualquier framework que sea puramente CSS.
>
> **Ejemplos populares:**
> - [Bootstrap](http://getbootstrap.com/)
> - [Material Design Lite (MDL)](http://www.getmdl.io/)
> - [Semantic UI](http://semantic-ui.com/)

> ---

> **🚀 Integrar Bootstrap en Angular**
>
> 1. Instala Bootstrap:
> ```bash
> npm install --save bootstrap
> ```
> 
> 2. Añade en `angular.json`:
> ```json
> "styles": [
>   "node_modules/bootstrap/dist/css/bootstrap.min.css",
>   "src/styles.css"
> ]
> ```
> 
> ¡Listo! Ya puedes usar clases de Bootstrap como `btn btn-primary`. 🎉

---

## Librerías de Componentes JavaScript

> **⚠️ Importante**
>
> Evita usar librerías que manipulen directamente el DOM, como:
> 
> - **jQuery**
> - **Bootstrap JavaScript puro**
>
> *¿Por qué?*  
> Angular necesita tener el control total del DOM para funcionar de manera eficiente y sin conflictos.
>
> **✅ Recomendación**
>
> Utiliza librerías **adaptadas a Angular**, que respeten el flujo de trabajo del framework.

---

## ng-bootstrap

> **✨ Bootstrap para Angular**
>
> [ng-bootstrap](https://ng-bootstrap.github.io/) es la adaptación oficial de Bootstrap para Angular.
>
> **Instalación rápida:**
> ```bash
> ng add @ng-bootstrap/ng-bootstrap
> ```

> ---

> **📦 Componentes disponibles**
>
> - Alertas, botones y modales
> - Tabs, acordeones y tooltips
> - Datepicker, timepicker y más 🎉

> ---

> **🧩 Ejemplo sencillo de tabs**
>
> ```html
> <ul ngbNav #nav="ngbNav" class="nav-tabs">
>   <li ngbNavItem>
>     <a ngbNavLink>Tab 1</a>
>     <ng-template ngbNavContent>
>       <p>Contenido de la tab 1</p>
>     </ng-template>
>   </li>
>   <!-- Más tabs... -->
> </ul>
> <div [ngbNavOutlet]="nav"></div>
> ```

---

## Angular Material

> **💡 La opción oficial**
>
> [Angular Material](https://material.angular.io/) es mantenido por el equipo de Angular y sigue las guías de Material Design de Google.
>
> **Instalación**
> ```bash
> ng add @angular/material @angular/flex-layout
> ```

> ---

> **📦 Componentes incluidos**
>
> - Tablas dinámicas 📊
> - Cards visuales 🧩
> - Diálogos personalizados 💬
> - Iconos y temas personalizables 🎨
>
> **Ejemplo tabla**
> ```html
> <mat-table [dataSource]="dataSource">
>   <ng-container matColumnDef="title">
>     <mat-header-cell *matHeaderCellDef> Title </mat-header-cell>
>     <mat-cell *matCellDef="let element"> {{element.title}} </mat-cell>
>   </ng-container>
>   <!-- Más columnas... -->
> </mat-table>
> ```

---

## Otras Librerías Interesantes

> **🎯 Teradata Covalent**
>
> *Pensada para entornos corporativos*, esta librería amplía Angular Material con componentes adicionales, ofreciendo un diseño limpio y profesional.
>
> 👉 Explora sus componentes en [Covalent](https://teradata.github.io/covalent/)

> ---

> **💎 PrimeNG**
>
> Una de las colecciones más completas del ecosistema Angular.  
> PrimeNG ofrece desde botones hasta componentes de alto nivel, además de *plantillas premium* para interfaces empresariales atractivas.
>
> 👉 Descubre más en [PrimeNG](http://www.primefaces.org/primeng/)

> ---

> **📊 Visualización avanzada de datos**
>
> Si tu proyecto necesita *tablas o gráficos complejos*, estas librerías son ideales:
>
> - **ag-Grid:** Potente para grandes volúmenes de datos y funcionalidades avanzadas de tablas.
> - **ngx-charts:** Perfecta para añadir gráficos de líneas, barras y más, basados en D3.
>
> 👉 Ejemplos interactivos en [ag-Grid](https://www.ag-grid.com/) y [ngx-charts](https://swimlane.github.io/ngx-charts/)

> ---

> **🚀 Ecosistema de Valor Software**
>
> Valor Software ha creado un ecosistema completo para Angular:
>
> _Desde tablas hasta carga de archivos y gráficos sencillos_, sus librerías están bien integradas y mantenidas.
>
> 👉 Echa un vistazo al catálogo de [Valor Software en GitHub](https://github.com/valor-software?q=ng2-)

> ---

> **📂 Soluciones para carga de archivos**
>
> Si tu aplicación necesita subir documentos o imágenes de forma elegante, esta librería te será útil:
>
> 👉 Prueba la demo en [Advanced File Upload](https://kzrfaisal.github.io/#/afu)

---

## Plantillas Profesionales

> **🌟 Dale personalidad a tu proyecto**
>
> Las plantillas profesionales para Angular son una excelente manera de arrancar con estilo y eficiencia.
>
> Estas plantillas ofrecen interfaces modernas, diseños bien estructurados y funcionalidades listas para usar, acelerando el desarrollo de tu aplicación.

> ---

> **📌 Recomendaciones clave**
>
> Asegúrate de que sean compatibles con *AOT* (Ahead-Of-Time Compilation) y *angular-cli* para un rendimiento óptimo.
> 
> Evita aquellas que dependan de *jQuery*, ya que puede generar conflictos con Angular y limitar la escalabilidad.
>
> **Elige siempre plantillas actualizadas y bien mantenidas para garantizar la mejor experiencia de desarrollo.** 🚀

> ---

> **🌟 Algunas plantillas que valen la pena explorar:**
>
> *PrimeNG Omega*: Estética limpia y profesional.  
> 👉 [Ver plantilla](http://www.primefaces.org/layouts/omega-ng)
>
> *Fury Angular Material*: Basada en Angular Material, ideal para dashboards empresariales. 
> 👉 [Descubrir Fury](https://themeforest.net/item/fury-angular-2-material-design-admin-template/19325966)
>
> *SB Admin Angular*: Plantilla gratuita y de código abierto, perfecta para empezar proyectos rápidamente.
> 👉 [Explorar SB Admin](https://github.com/start-angular/SB-Admin-BS4-Angular-8)

---

## Conclusión

> **🚀 Resumen final**
>
> - Angular no trae componentes visuales de alto nivel por defecto, pero existen *librerías potentes* que complementan tu proyecto.
> - Usar librerías adaptadas para Angular mejora el rendimiento y la mantenibilidad.
> - La personalización estética y funcional está a un solo comando de distancia.
>
> ¡Elige tu herramienta y lleva tu aplicación al siguiente nivel!💡

> ---

> **📚 Recursos adicionales**
>
> - [Angular Material](https://material.angular.io/)
> - [ng-bootstrap](https://ng-bootstrap.github.io/)
> - [PrimeNG](http://www.primefaces.org/primeng/)

---