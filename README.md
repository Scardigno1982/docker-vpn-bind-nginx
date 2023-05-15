# Docker Compose para Hosting de Aplicaciones

Este proyecto utiliza Docker Compose para gestionar una serie de servicios que incluyen BIND9 para DNS, Nginx como proxy inverso, Let's Encrypt para certificados SSL, PHP y Node.js para aplicaciones backend, y dos aplicaciones web servidas con Nginx.

## Estructura del Proyecto

El archivo `docker-compose.yml` define los siguientes servicios:

- `bind9`: un servidor DNS basado en la imagen `ubuntu/bind9:latest`.
- `nginx-proxy`: un servidor proxy inverso Nginx utilizando la imagen `jwilder/nginx-proxy`.
- `letsencrypt-nginx-proxy-companion`: un servicio que automatiza la creación y renovación de certificados SSL Let's Encrypt utilizando la imagen `jrcs/letsencrypt-nginx-proxy-companion`.
- `php`: un servicio de backend PHP utilizando la imagen `php:8.0-fpm`.
- `node`: un servicio de backend Node.js que se encarga de construir y servir una aplicación Next.js.
- `app1` y `app2`: dos servicios Nginx que sirven aplicaciones web estáticas.

## Cómo Utilizar

1. Clona este repositorio en tu servidor local o de producción.
2. Navega al directorio del repositorio.
3. Ejecuta `docker-compose up -d` para iniciar todos los servicios en modo "detached" (esto significa que los servicios seguirán ejecutándose en segundo plano).

## Notas

El servicio `node` está configurado para utilizar Next.js con la opción de "output: export", lo que significa que la aplicación Next.js se compila en un sitio web estático. Esta aplicación estática se sirve utilizando el paquete `serve`. Si prefieres utilizar un servidor de producción completo, como Nginx, para servir tu aplicación, tendrás que modificar la configuración correspondiente.
