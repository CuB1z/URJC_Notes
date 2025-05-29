---
tags: URJC URJC_DAW Angular Components
---

# DAW - Angular Tema 2

---

## Tabla de Contenidos

1. [Introducción](#Introducción)
2. [Crear un Componente](#Crear%20un%20Componente)
3. [Plantillas y Vistas](#Plantillas%20y%20Vistas)
4. [Interacción y Eventos](#Interacción%20y%20Eventos)
5. [Data Binding](#Data%20Binding)
6. [Templates Avanzados](#Templates%20Avanzados)
7. [Conclusión](#Conclusión)

---

## Introducción

> **🧩 Definición de Componente**
> En Angular, un **componente** es una pieza clave que combina:
> - **Una vista**, representada mediante una plantilla HTML con elementos especiales.
> - **Una lógica**, desarrollada en una clase TypeScript vinculada a la vista.
> 
> Los componentes permiten crear nuevas etiquetas HTML personalizadas, facilitando la construcción de interfaces dinámicas.
>
> **🗂️ Estructura básica**
> - Archivo `.html` → define la vista.
> - Archivo `.ts` → define la lógica del componente.

---

## Crear un Componente

> **⚙️ Configuración inicial**
> Para comenzar, se copia el contenido de la carpeta `src/app` de un proyecto base (ejem1).
>
> El archivo `index.html` incluye la etiqueta personalizada del componente mediante el **selector** definido en la clase.
> 
> **💡 Ejemplo**
> ```html
> <body>
>   <app-root></app-root>
> </body>
> ```

> ---

> **📦 Módulo Principal (`app.module.ts`)**
> Define:
> - Componentes declarados
> - Módulos importados
> - Componente principal que se carga al iniciar la aplicación
> 
> ```typescript
> @NgModule({
>   declarations: [AppComponent],
>   imports: [BrowserModule, FormsModule],
>   bootstrap: [AppComponent]
> })
> export class AppModule { }
> ```

---

## Plantillas y Vistas

> **🖼️ Integración de la vista**
> La plantilla HTML se puede definir directamente en la clase usando backticks (\`), permitiendo escribir HTML multilínea.
>
> ```typescript
> @Component({
>   selector: 'app-root',
>   template: `
>     <h1>My First Angular App</h1>
>   `
> })
> ```

> ---

> **🔍 Visualización de variables**
> La vista refleja el estado de las variables definidas en la clase.
>
> ```typescript
> name = 'Anybody';
> imgUrl = 'assets/img.png';
> ```
> ```html
> <h1>Hello {{name}}!</h1>
> <img [src]="imgUrl"/>
> ```

> ---

> **🗂️ Recursos de la App**
> Los recursos como imágenes o fuentes deben almacenarse en `src/assets`.

---

## Interacción y Eventos

> **🖱️ Manejo de eventos**
> Podemos ejecutar métodos desde la vista mediante eventos del DOM.
>
> ```html
> <button (click)="setName('John')">Hello John</button>
> ```
> ```typescript
> setName(name: string) {
>   this.name = name;
> }
> ```

> ---

> **⚡ Sintaxis del template**
> - `{{ attr }}` → Interpolación de atributos en el texto.
> - `[prop]="attr"` → Enlace de atributos a propiedades del elemento.
> - `(event)="method()"` → Ejecución de métodos al ocurrir un evento.

---

## Data Binding

> **🔗 Enlace bidireccional**
> Se utiliza `[(ngModel)]` para sincronizar campos de entrada con atributos de la clase.
>
> ```html
> <input type="text" [(ngModel)]="name">
> <h1>Hello {{name}}!</h1>
> ```
> 
> **🎯 Ventaja**
> Cualquier cambio en el input se refleja automáticamente en la variable de la clase.

---

## Templates Avanzados

> **🧩 Visualización condicional**
> Con `*ngIf` podemos controlar la visualización de elementos.
>
> ```html
> <p *ngIf="visible">Visible Text</p>
> <p *ngIf="num === 3">Num is 3</p>
> ```

> ---

> **🔁 Repetición de elementos**
> Usando `*ngFor` para iterar sobre listas:
>
> ```html
> <div *ngFor="let elem of elems">{{elem.desc}}</div>
> ```
> ```typescript
> elems = [
>   { desc: 'Elem1', check: true },
>   { desc: 'Elem2', check: true },
>   { desc: 'Elem3', check: false }
> ];
> ```

---

## Conclusión

> **🧩 Resumen**
> - Los componentes son la base de Angular, combinando vista y lógica.
> - La interacción entre plantilla y clase permite construir aplicaciones dinámicas y reactivas.
> - Angular facilita la gestión de recursos, eventos y datos enlazados para el desarrollo eficiente de aplicaciones web.

> ---

> **📚 Recursos adicionales**
> - [Documentación oficial de Angular](https://angular.io/docs/ts/latest/guide/template-syntax.html)

---