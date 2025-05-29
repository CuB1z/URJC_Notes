---
tags: URJC URJC_DAW Angular Router SPA
---

# DAW - Angular Tema 4

---

## Tabla de Contenidos

1. [SPA con múltiples pantallas](#SPA%20con%20múltiples%20pantallas)
2. [Configuración del Router](#Configuración%20del%20Router)
3. [Navegación dentro de la App](#Navegación%20dentro%20de%20la%20App)
4. [Navegar al mismo componente con otros datos](#Navegar%20al%20mismo%20componente%20con%20otros%20datos)
5. [Funcionalidades Avanzadas](#Funcionalidades%20Avanzadas)
6. [Ejemplo: CRUD de Libros](#Ejemplo%20CRUD%20de%20Libros)
7. [Conclusión](#Conclusión)

---

## SPA con múltiples pantallas

> **🧩 Concepto**
>
> Aunque Angular crea *Single Page Applications*, podemos simular múltiples pantallas mediante el **Router**.
>
> Esto permite que la app tenga:
> - Una *estructura fija* (cabecera, pie de página).
> - Una zona dinámica que cambia según la URL mediante `<router-outlet>`.
> 
> [Documentación oficial de Angular Router](https://angular.io/docs/ts/latest/guide/router.html)

---

## Configuración del Router

> **⚙️ Definición de rutas**
>
> En `app.routing.ts` se define qué componente se muestra para cada URL.
>
> ```typescript
> const appRoutes = [
>   { path: 'book/:id', component: BookDetailComponent },
>   { path: 'books', component: BookListComponent },
>   { path: '', redirectTo: 'books', pathMatch: 'full' }
> ];
>
> export const routing = RouterModule.forRoot(appRoutes);
> ```

> ---

> **🧩 Integración en la app**
>
> Importa el módulo de rutas en `app.module.ts`:
>
> ```typescript
> imports: [ BrowserModule, FormsModule, HttpClientModule, routing ]
> ```

> ---

> **🖥️ Área dinámica**
>
> En el componente principal, `<router-outlet>` actúa como "contenedor" dinámico:
>
> ```typescript
> @Component({
>   template: `
>     <h1 class="title">Library</h1>
>     <router-outlet></router-outlet>
>   `
> })
> ```

---

## Navegación dentro de la App

> **🔗 Enlaces internos**
>
> Para navegar, utilizamos `[routerLink]` en lugar de `href`:
>
> ```html
> <a [routerLink]="['/book', book.id]">{{ book.title }}</a>
> ```

> ---

> **🧩 Acceso a parámetros**
>
> En el componente que recibe la navegación:
>
> ```typescript
> constructor(private route: ActivatedRoute) {
>   let id = route.snapshot.params['id'];
> }
> ```

> ---

> **🚀 Navegación programática**
>
> Desde el código, se navega con `Router`:
>
> ```typescript
> constructor(private router: Router) {}
> 
> this.router.navigate(['/books']);
> ```

---

## Navegar al mismo componente con otros datos

> **🔄 Reutilización de componentes**
>
> Cuando navegas al mismo componente con distintos parámetros:
>
> ```typescript
> this.route.params.subscribe(params => {
>   const id = params['id'];
>   this.book = this.service.getBook(id);
> });
> ```
> 
> Así el componente actualiza su contenido sin ser destruido y recreado. 🎯

---

## Funcionalidades Avanzadas

> **🛤️ Rutas hijas**
>
> Permiten estructurar pantallas complejas dentro de un componente específico.
>
> **⚠️ Protección de rutas**
>
> Verifica si el usuario tiene permisos antes de permitir la navegación.
>
> **💾 Prevención de pérdida de datos**
>
> Al salir de una página, podemos preguntar si desea guardar cambios antes de abandonar.
>
> **🧩 Lazy loading**
>
> Las pantallas solo se cargan al acceder, mejorando el rendimiento inicial de la app.
>
> **🎨 Animaciones**
>
> Mejora la experiencia de usuario añadiendo animaciones entre transiciones.

---

## Ejemplo: CRUD de Libros

> **📝 Funcionalidades esperadas:**
>
> - Visualización de todos los libros.
> - Formulario para crear un nuevo libro.
> - Detalle de cada libro.
> - Edición y eliminación de libros existentes.

> Se utiliza una API REST externa para gestionar la información de los libros.

---

## Conclusión

> **🚀 Resumen**
>
> Angular Router transforma una SPA en una aplicación *multipágina fluida*:
>
> - Mejora la organización mediante rutas claras.
> - Permite estructurar la app con componentes reutilizables.
> - Se integra fácilmente con servicios REST y navegación programática.
> 
> ¡Tu aplicación será profesional, ordenada y rápida! 🌟

> ---

> **📚 Recursos adicionales**
>
> - [Guía oficial de Angular Router](https://angular.io/docs/ts/latest/guide/router.html)

---