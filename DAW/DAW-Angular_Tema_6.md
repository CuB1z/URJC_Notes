---
tags: URJC URJC_DAW Angular SPA Deploy
---

# DAW - Angular Tema 6

---

## Tabla de Contenidos

1. [Desarrollo vs Producción](#Desarrollo%20vs%20Producción)
2. [Arquitectura de Publicación](#Arquitectura%20de%20Publicación)
3. [Generar la App para Producción](#Generar%20la%20App%20para%20Producción)
4. [Publicar en un Servidor Web](#Publicar%20en%20un%20Servidor%20Web)
5. [Publicación con Spring Boot](#Publicación%20con%20Spring%20Boot)
6. [SPA y Navegación con Router](#SPA%20y%20Navegación%20con%20Router)
7. [Publicación en Ruta Específica](#Publicación%20en%20Ruta%20Específica)
8. [Conclusión](#Conclusión)

---

## Desarrollo vs Producción

> **💡 Modo desarrollo**
>
> Durante el desarrollo, usamos `ng serve` para arrancar la aplicación con:
>
> - *LiveReload*: Guarda y actualiza automáticamente el navegador.
> - Código optimizado para depuración.
>
> ```bash
> ng serve
> ```

> ---

> **🚀 Modo producción**
>
> Antes de publicar, es necesario *optimizar* la aplicación:
>
> - Minificación de CSS, JS e imágenes.
> - Eliminación de código no usado.
> - Mejor rendimiento en el navegador.

---

## Arquitectura de Publicación

> **🖥️ Frontend + Backend**
>
> Las aplicaciones SPA tienen:
>
> - *Frontend* con Angular.
> - *Backend* con tecnologías como Java, Node.js, PHP o Python.
>
> El backend se suele empaquetar hoy en día con **Docker**, facilitando la portabilidad y despliegue.

> ---

> **🔗 Comunicación**
>
> - API REST (HTTP)
> - WebSockets
> - Server-Side Events

---

## Generar la App para Producción

> **⚙️ Comando clave**
>
> Para preparar el frontend para producción:
>
> ```bash
> ng build --prod
> ```
>
> Los archivos optimizados se generan en:
> ```
> /dist/<app-name>
> ```
> 
> Estos archivos incluyen HTML, CSS, JS e imágenes y recursos estáticos

---

## Publicar en un Servidor Web

> **🌐 Opciones para servir la app**
>
> - Servidor HTTP exclusivo (NGINX, Apache, http-serve)
> - Usar el mismo backend para servir el frontend (ej. Spring Boot)

> ---

> **🚀 Usando http-serve (rápido y sencillo)**
>
> 1. Instala http-serve:
> ```bash
> sudo npm install -g http-serve
> ```
>
> 2. Publica la aplicación:
> ```bash
> http-serve dist/<app-name>
> ```
> 
> Accede en http://127.0.0.1:8080

---

## Publicación con Spring Boot

> **🔄 Proxy para desarrollo**
>
> Configura el proxy para redirigir peticiones del frontend al backend:
>
> ```bash
> ng serve --proxy-config proxy.conf.json
> ```
>
> **proxy.conf.json**
> ```json
> {
>   "/books/*": {
>     "target": "http://localhost:8080",
>     "secure": false,
>     "logLevel": "debug",
>     "changeOrigin": true
>   }
> }
> ```
> 
> **📂 Copiar archivos de producción**
>
> ```bash
> ng build --prod
> cp dist/ejem23/* ../ejem23_backend/src/main/resources/static
> ```
> 
> Accede a la aplicación publicada en http://localhost:8080.

---

## SPA y Navegación con Router

> **🚨 Problema común**
>
> Cuando refrescas una URL interna como `/books`, el servidor no la reconoce.
>
> La solución es que el servidor devuelva siempre `index.html`.

> ---

> **🧩 Configuración en Spring Boot**
>
> ```java
> @Controller
> public class SPAController {
>     @GetMapping("/**/{path:[^\\.]*}")
>     public String redirect() {
>         return "forward:/";
>     }
> }
> ```
>
> Esto asegura que Angular maneje la navegación correctamente.

---

## Publicación en Ruta Específica

> **💡 Cuando tu app no se despliega en la raíz**
>
> Especifica la ruta base durante el build:
>
> ```bash
> ng build --prod --base-href="/spa/"
> ```
> 
> Copia los archivos:
>
> ```bash
> cp dist/ejem24/* ../ejem24_backend/src/main/resources/static/spa
> ```

> ---

> **🚦 Configuración Spring Boot para ruta específica**
>
> ```java
> @Controller
> public class SPAController {
>     @GetMapping({"/spa/**/{path:[^\\.]*}", "/{path:spa[^\\.]*}"})
>     public String redirect() {
>         return "forward:/spa/index.html";
>     }
> }
> ```

---

## Conclusión

> **🚀 Resumen final**
>
> - La publicación de aplicaciones Angular requiere optimización previa con `ng build --prod`.
> - Puedes usar servidores dedicados o integrar con el backend.
> - Configurar correctamente el servidor es clave para soportar rutas internas con Angular Router.
> Una correcta publicación garantiza rendimiento, estabilidad y una experiencia fluida para el usuario final. 🌟

> ---

> **📚 Recursos útiles**
>
> - [Angular CLI - build](https://angular.io/cli/build)
> - [http-serve](https://www.npmjs.com/package/http-serve)
> - [Angular Deployment](https://angular.io/guide/deployment)

---