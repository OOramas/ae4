# AE4 — Aplicación Web con base de datos en contenedores

En esta práctica voy a desplegar una aplicación web usando Docker Compose.

La aplicación tendrá cuatro servicios principales:

- PostgreSQL para la base de datos.
- pgAdmin para gestionar PostgreSQL.
- Django + Gunicorn como servidor de aplicaciones.
- nginx como servidor web y proxy inverso.

## Preparación del proyecto

Primero creé la carpeta de trabajo e inicié el repositorio Git:

```bash
mkdir -p ~/dpl/ae4
cd ~/dpl/ae4
git init
```

También configuré mi nombre y correo de Git para este repositorio.

## Material de la UT4

Descargué el material proporcionado en la unidad y copié al proyecto la aplicación Django y el fichero `db/init.sql`, que usaremos como base para el despliegue.

Por ahora he copiado principalmente:

```text
app/
db/init.sql
```

## Práctica previa de Docker

Antes de empezar esta práctica hice el laboratorio de Docker.

En él practiqué:

- crear y arrancar contenedores;
- publicar puertos;
- usar volúmenes;
- crear redes Docker;
- comunicar contenedores entre sí por su nombre;
- comprobar su funcionamiento con `docker ps`, `docker exec` y `curl`.

Ahora voy a aplicar esos mismos conceptos usando Docker Compose.

## Docker Compose

He preparado un primer `compose.yml` con los cuatro servicios de la AE4:

```text
db
pgadmin
app
nginx
```

También comprobé que el fichero tiene una sintaxis válida con:

```bash
sudo docker compose config -q
echo $?
```

El resultado fue:

```text
0
```

por lo que la configuración de Compose es válida.

## nginx

También añadí el fichero:

```text
nginx/default.conf
```

del material de la unidad.

De momento lo he dejado como viene en el material y más adelante lo adaptaré a la versión final de la AE4.

## Estado actual

Hasta ahora he preparado la estructura del proyecto, el material base y el fichero `compose.yml`.

El siguiente paso será empezar a levantar los servicios, comenzando por PostgreSQL y pgAdmin.
