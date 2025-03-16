# Guía Completa de Comandos de Docker

Este archivo contiene una lista de los comandos de Docker más utilizados, con explicaciones detalladas de cómo funcionan. También incluye detalles sobre cómo escribir un `Dockerfile` para construir imágenes personalizadas. Es una referencia rápida para gestionar contenedores, imágenes y redes en Docker.

---

## Índice

1. [Comandos Básicos de Docker](#comandos-básicos-de-docker)
2. [Comandos de Gestión de Contenedores](#comandos-de-gestión-de-contenedores)
3. [Comandos de Gestión de Imágenes](#comandos-de-gestión-de-imágenes)
4. [Comandos de Redes y Volúmenes](#comandos-de-redes-y-volúmenes)
5. [Comandos de Docker Compose](#comandos-de-docker-compose)
6. [Otros Comandos Útiles](#otros-comandos-útiles)
7. [Estructura Básica de un Dockerfile](#estructura-básica-de-un-dockerfile)

---

## Comandos Básicos de Docker

1. **`docker --version`**  
   Muestra la versión de Docker instalada en tu máquina.

2. **`docker info`**  
   Muestra información detallada sobre el sistema Docker y su configuración.

3. **`docker version`**  
   Muestra información sobre la versión del cliente y servidor de Docker.

4. **`docker help`**  
   Muestra una lista de todos los comandos de Docker disponibles con una breve descripción.

---

## Comandos de Gestión de Contenedores

1. **`docker run <imagen>`**  
   Ejecuta un contenedor basado en una imagen especificada. Si la imagen no está en el sistema local, Docker la descarga desde Docker Hub.

   - **Ejemplo:**
     ```bash
     docker run ubuntu
     ```
     Esto ejecuta un contenedor de Ubuntu y lo deja corriendo de manera interactiva en la terminal.

2. **`docker run -d <imagen>`**  
   Ejecuta un contenedor en segundo plano (detached mode). Esto es útil si no quieres que el contenedor se ejecute en tu terminal actual y prefieres que Docker lo ejecute en segundo plano.

   - **Ejemplo:**
     ```bash
     docker run -d nginx
     ```
     Esto ejecuta un contenedor de Nginx en segundo plano.

3. **`docker ps`**  
   Muestra una lista de todos los contenedores en ejecución. Solo muestra los contenedores activos.

4. **`docker ps -a`**  
   Muestra todos los contenedores, incluyendo los que están detenidos.

5. **`docker stop <id del contenedor>`**  
   Detiene un contenedor en ejecución.

6. **`docker start <id del contenedor>`**  
   Inicia un contenedor detenido.

7. **`docker restart <id del contenedor>`**  
   Reinicia un contenedor en ejecución.

8. **`docker rm <id del contenedor>`**  
   Elimina un contenedor detenido.

9. **`docker exec -it <id del contenedor> <comando>`**  
   Ejecuta un comando dentro de un contenedor en ejecución. Por ejemplo, puedes acceder a un contenedor con un shell interactivo usando `bash`.

   - **Ejemplo:**
     ```bash
     docker exec -it <id del contenedor> bash
     ```
     Esto abrirá una terminal interactiva dentro del contenedor.

10. **`docker logs <id del contenedor>`**  
    Muestra los logs de un contenedor en ejecución.

11. **`docker pause <id del contenedor>`**  
    Pausa un contenedor en ejecución (congelando todos los procesos dentro del contenedor).

12. **`docker unpause <id del contenedor>`**  
    Despausa un contenedor previamente pausado.

13. **`docker container prune`**  
    Elimina todos los contenedores detenidos.

14. **`docker container prune -f`**  
    Elimina todos los contenedores detenidos sin solicitar confirmación.

---

## Comandos de Gestión de Imágenes

1. **`docker build -t <nombre-imagen> <directorio>`**  
   Construye una imagen Docker a partir de un Dockerfile en el directorio especificado.

2. **`docker pull <imagen>`**  
   Descarga una imagen de Docker desde Docker Hub.

3. **`docker push <imagen>`**  
   Sube una imagen Docker a Docker Hub o a un repositorio privado.

4. **`docker images`**  
   Muestra una lista de todas las imágenes locales.

5. **`docker rmi <id de imagen>`**  
   Elimina una imagen Docker del sistema local.

6. **`docker tag <imagen> <repositorio>/<nombre-imagen>:<etiqueta>`**  
   Asigna una etiqueta a una imagen para facilitar su identificación y uso.

7. **`docker history <imagen>`**  
   Muestra el historial de una imagen, es decir, todas las capas de la imagen y sus cambios.

8. **`docker inspect <id o nombre de imagen>`**  
   Muestra información detallada sobre una imagen, como configuraciones, etiquetas, y más.

9. **`docker images prune`**  
   Elimina todas las imágenes no utilizadas.

10. **`docker images prune -a`**  
    Elimina todas las imágenes no utilizadas, incluyendo las que no tienen etiquetas.

11. **`docker images prune -af`**  
    Elimina todas las imágenes no utilizadas sin pedir confirmación.

12. **`docker builder prune`**  
    Elimina datos no utilizados por el builder de Docker (como capas intermedias no necesarias).

13. **`docker builder prune -a`**  
    Elimina todas las capas de build que no se están utilizando.

---

## Comandos de Redes y Volúmenes

1. **`docker network ls`**  
   Muestra una lista de todas las redes Docker.

2. **`docker network create <nombre-red>`**  
   Crea una nueva red Docker.

3. **`docker network rm <nombre-red>`**  
   Elimina una red Docker.

4. **`docker volume ls`**  
   Muestra una lista de todos los volúmenes Docker.

5. **`docker volume create <nombre-volumen>`**  
   Crea un nuevo volumen Docker.

6. **`docker volume rm <nombre-volumen>`**  
   Elimina un volumen Docker.

7. **`docker run -v <volumen>:/<directorio>`**  
   Monta un volumen en un contenedor en el directorio especificado.

8. **`docker inspect <nombre-volumen>`**  
   Muestra información detallada sobre un volumen.

9. **`docker volume prune`**  
   Elimina volúmenes no utilizados.

---

## Comandos de Docker Compose

1. **`docker-compose up`**  
   Inicia todos los servicios definidos en un archivo `docker-compose.yml`. Si las imágenes no existen, las construye automáticamente.

2. **`docker-compose up -d`**  
   Inicia los servicios en segundo plano (modo detached). Esto es equivalente a usar `-d` en `docker run`.

3. **`docker-compose down`**  
   Detiene y elimina los contenedores, redes y volúmenes definidos en un archivo `docker-compose.yml`.

4. **`docker-compose build`**  
   Construye las imágenes definidas en el archivo `docker-compose.yml`.

5. **`docker-compose logs`**  
   Muestra los logs de los contenedores gestionados por Docker Compose.

6. **`docker-compose exec <servicio> <comando>`**  
   Ejecuta un comando dentro de un contenedor gestionado por Docker Compose.

7. **`docker-compose ps`**  
   Muestra el estado de los contenedores gestionados por Docker Compose.

8. **`docker-compose restart`**  
   Reinicia los servicios gestionados por Docker Compose.

---

## Otros Comandos Útiles

1. **`docker stats`**  
   Muestra estadísticas de uso de recursos (CPU, memoria, red, etc.) para los contenedores en ejecución.

2. **`docker top <id del contenedor>`**  
   Muestra los procesos en ejecución dentro de un contenedor.

3. **`docker cp <id del contenedor>:<ruta> <directorio-local>`**  
   Copia archivos desde un contenedor a tu sistema local.

4. **`docker cp <directorio-local> <id del contenedor>:<ruta>`**  
   Copia archivos desde tu sistema local a un contenedor.

5. **`docker stats <id del contenedor>`**  
   Muestra estadísticas de uso de recursos para un contenedor específico.

6. **`docker system prune`**  
   Elimina todos los contenedores detenidos, imágenes sin usar, redes no utilizadas y volúmenes no utilizados.

7. **`docker system prune -a`**  
   Elimina todos los recursos no utilizados (contenedores detenidos, imágenes no etiquetadas, etc.) sin preguntar.

8. **`docker info`**  
   Muestra información del sistema Docker, como contenedores en ejecución, imágenes, y configuraciones.

---

### Estructura Básica de un Dockerfile

```bash
# Usar una imagen base
FROM <imagen-base>

# Establecer el directorio de trabajo
WORKDIR /app

# Copiar archivos locales al contenedor
COPY <directorio-local> <directorio-en-contenedor>

# Instalar dependencias o software
RUN <comando-de-instalar>

# Exponer puertos
EXPOSE <puerto>

# Comando por defecto que se ejecuta cuando el contenedor inicia
CMD ["<comando>", "<argumentos>"]

