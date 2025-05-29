---
tags: URJC URJC_DAW Angular REST API RxJS
---

# DAW - Angular Tema 3

---

## Tabla de Contenidos

1. [Cliente REST en Angular](#Cliente%20REST%20en%20Angular)
2. [Inyección de Dependencias](#Inyección%20de%20Dependencias)
3. [Ejemplo: Buscador de Libros](#Ejemplo%20Buscador%20de%20Libros)
4. [Buenas Prácticas: Uso de Servicios](#Buenas%20Prácticas%20Uso%20de%20Servicios)
5. [Observables en Servicios](#Observables%20en%20Servicios)
6. [Servicios Stateless vs Stateful](#Servicios%20Stateless%20vs%20Stateful)
7. [Pipe Async](#Pipe%20Async)
8. [Conclusión](#Conclusión)

---

## Cliente REST en Angular

> **🔌 Integración directa**
>
> Angular incluye un cliente REST: *HttpClient*.
> 
> _Ejemplo básico de uso:_
> ```typescript
> this.httpClient.get(url).subscribe(
>   response => console.log(response),
>   error => console.error(error)
> );
> ```
> 
> El método `subscribe()` recibe dos funciones:
> - Una para manejar respuestas exitosas.
> - Otra para manejar errores. ⚠️

> ---

> **📦 Respuestas JSON**
> 
> Si la API REST devuelve JSON, automáticamente se convierte en un objeto de JavaScript listo para usar.

> ---

> **🤔 ¿Cómo obtenemos el HttpClient?**
>
> No se crea manualmente con `new`.
> Angular utiliza *inyección de dependencias* para suministrarlo.
>
> Esto permite:
> - Hacer tests más fácilmente con objetos `mock`.
> - Desacoplar la lógica de red de los componentes.
>
> **Importante**
> ```typescript
> import { HttpClientModule } from '@angular/common/http';
> @NgModule({
>   imports: [HttpClientModule]
> })
> export class AppModule { }
> ```

---

## Inyección de Dependencias

> **🧩 Principio clave**
>
> Angular **inyecta automáticamente** dependencias como `HttpClient` en los componentes:
>
> ```typescript
> constructor(private httpClient: HttpClient) {}
> ```
>
> Así Angular construye el componente con el servicio ya configurado.
>
> **📚 Beneficios**
> 
> - Mejora la organización.
> - Facilita el testeo.
> - Permite reutilizar servicios en múltiples componentes.

---

## Ejemplo: Buscador de Libros

> **🔍 Búsqueda de libros con Google Books API**
>
> **Interfaz sencilla**
> ```html
> <input #title type="text">
> <button (click)="search(title.value); title.value=''">Buscar</button>
> <p *ngFor="let title of titles">{{title}}</p>
> ```
>
> **Funcionalidad**
> ```typescript
> search(title: string) {
>   let url = "https://www.googleapis.com/books/v1/volumes?q=intitle:" + title;
>   this.httpClient.get(url).subscribe(response => {
>     this.titles = response.items.map(item => item.volumeInfo.title);
>   });
> }
> ```

> ---

> **🧩 Peticiones POST / PUT**
>
> ```typescript
> this.httpClient.post(url, data).subscribe(...);
> this.httpClient.put(url, data).subscribe(...);
> ```

---

## Buenas Prácticas: Uso de Servicios

> **🚫 Problema**
>
> Acoplar la lógica de peticiones HTTP en los componentes los hace complejos y difíciles de mantener.
>
> **✅ Solución**
>
> *Crear un servicio especializado* para manejar la comunicación con la API.
>
> **Ejemplo de servicio básico**
> ```typescript
> @Injectable({ providedIn: 'root' })
> export class BooksService {
>   getTitles(title: string) {
>     return this.httpClient.get(url);
>   }
> }
> ```

> ---

> **🧩 Uso del servicio en un componente**
> 
> ```typescript
> constructor(private booksService: BooksService) {}
> 
> search(title: string) {
>   this.booksService.getTitles(title).subscribe(...);
> }
> ```

---

## Observables en Servicios

> **💡 ¿Por qué usar Observables?**
>
> - Manejan respuestas *asíncronas*.
> - Transforman datos fácilmente.
> - Permiten múltiples emisiones de datos.

> ---

> **🧩 Transformación de respuestas**
>
> ```typescript
> getTitles(title: string): Observable<string[]> {
>   return this.httpClient.get(url).pipe(
>     map(response => this.extractTitles(response as any))
>   );
> }
> ```
>
> Así entregamos directamente un array de títulos al componente.

> ---

> **🛑 Manejo de errores elegante**
>
> ```typescript
> catchError(error => throwError('Error del servidor'))
> ```

> ---

> **📦 RxJS: Biblioteca de Observables**
>
> Angular la incluye por defecto para potenciar el trabajo con datos reactivos.

---

## Servicios Stateless vs Stateful

> **🚀 Stateless (sin estado)**
>
> - No guardan información interna.
> - Cada petición obtiene los datos directamente del servidor.
> - *Más fáciles de implementar.*

> ---

> **💾 Stateful (con estado)**
>
> - Mantienen datos en memoria.
> - Mejoran la eficiencia evitando peticiones repetidas.
> - *Requieren sincronización con el backend.*

> ---

> **🧭 Herramientas para gestión de estado**
> 
> - NgRx: [https://ngrx.io/](https://ngrx.io/)
> - Akita: [https://datorama.github.io/akita/](https://datorama.github.io/akita/)
> - NGXS: [https://www.ngxs.io/](https://www.ngxs.io/)

---

## Pipe Async

> **⚡️ Simplifica la suscripción a observables en la plantilla**
>
> ```html
> <p *ngFor="let title of ($titles | async)">{{ title }}</p>
> ```
>
> Angular se encarga automáticamente de la suscripción y la actualización de la vista.

> ---

> **📌 Con la sintaxis `as` podemos crear una variable local:**
>
> ```html
> <div *ngIf="$titles | async as titles; else loading">
>   <p *ngFor="let title of titles">{{ title }}</p>
>   <p>{{ titles.length }} libros encontrados</p>
> </div>
>
> <ng-template #loading>
>   <p>Cargando...</p>
> </ng-template>
> ```

---

## Conclusión

> **🔍 Recapitulando:**
> 
> - Angular facilita la integración con APIs REST gracias a `HttpClient`.
> - Los servicios permiten separar responsabilidades y mejorar el mantenimiento del código.
> - RxJS y los observables añaden poder para manejar datos asíncronos.
> - El uso de *Async Pipe* simplifica las vistas y hace el código más limpio.
> 
> ¡Con estas prácticas, tendrás aplicaciones web profesionales, mantenibles y escalables! 🚀

> ---

> **📚 Recursos recomendados**
> 
> - [Documentación oficial de Angular](https://angular.io/docs)
> - [RxJS](https://rxjs.dev/)
> - [API HttpClient](https://angular.io/api/common/http/HttpClient)

---