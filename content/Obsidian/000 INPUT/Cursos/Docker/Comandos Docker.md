

Construir una imagen a partir de un archivo Dockerfile

```bash
docker build -t <nombre_de_imagen>
```

Construir una imagen desde un archivo Dockerfile sin la caché

```bash
docker build -t <nombre_de_imagen> . -no-cache
```

Listar imágenes locales

```bash
docker images
```

Eliminar una imagen

```bash
docker rmi <nombre_imagen>
```

Eliminar todas las imágenes no utilizadas

```bash
docker image prune
```

Inicie sesión en Docker

```bash
docker login -u <nombredeusuario>
```

Publica una imagen en Docker Hub

```bash
docker push <nombre_usuario>/<nombre_imagen>
```

Buscar una imagen en Hub

```bash
docker search <nombre_imagen>
```

Extraer una imagen de un Docker Hub

```bash
docker pull <nombre_imagen>
```

---

Crea y ejecuta un contenedor a partir de una imagen, con un nombre personalizado:

```bash
docker run --name <nombre_contenedor> <nombre_imagen>
```

Ejecutar un contenedor con y publicar un puerto(s) del contenedor al host.

```bash
docker run -p <puerto_host>:<puerto_contenedor> <nombre_imagen>
```

Ejecutar un contenedor en segundo plano

```bash
docker run -d <nombre_imagen>
```

Iniciar o detener un contenedor existente:

```bash
docker start|stop <nombre_del_contenedor> (o <id_del_contenedor>)
```

Eliminar un contenedor detenido:

```bash
docker rm <nombre_del_contenedor>
```

Abrir un shell dentro de un contenedor en ejecución:

```bash
docker exec -it <nombre_del_contenedor> sh
```

Obtener y seguir los logs de un contenedor:

```bash
docker logs -f <nombre_contenedor>
```

Inspeccionar un contenedor en ejecución:

```bash
docker inspect <nombre_del_contenedor> (o <id_del_contenedor>)
```

Para listar los contenedores actualmente en ejecución:

```bash
docker ps
```

Listar todos los contenedores docker (en ejecución y parados):

```bash
docker ps --all
```

Ver las estadísticas de uso de recursos

```bash
docker container stats
```