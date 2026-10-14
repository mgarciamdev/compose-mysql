# 🐬 Proyecto Docker Compose: MySQL + phpMyAdmin 

Este proyecto levanta un entorno de base de datos MySQL con una interfaz gráfica phpMyAdmin utilizando Docker Compose. Tambien incluye configuración para varaibles de entorno y un script de inicialización para otorgar permisos al usuario.

---

## 📦 Servicios Incluidos

- **MySQL 8**: Motor de base de datos.
- **phpMyAdmin**: Panel web para administrar la base de datos gráficamente.

---

## 🧾 Requisitos

- Docker
- Docker compose

---

## ⚙️ Guia de Inicio
* Clonar o descargar este repositorio
* Ingresa al directorio del proyecto:
  
  ```
  cd compose-mysql
  ```
* Creat tu archivo `.env` a partir de la plantilla:
  
  ```bash
  cp .env.example .env
  ```
* Levanta los servicios:
  
  ```
  docker compose up -d
  ```
* Verifica que estén corriendo:
  
  ```
  docker compose ps
  ```
---

## 🧪 Variables de entorno

Las variables se definen en el archivo `.env` (puedes basarte en `.env.example` y cambiar los valores):

| Variable              | Valor por defecto | Descripción                          |
| --------------------- | ----------------- | ------------------------------------ |
| `MYSQL_ROOT_PASSWORD` | `root`            | Contraseña del usuario root          |
| `MYSQL_DATABASE`      | `testdb`          | Base de datos que se crea al iniciar |
| `MYSQL_USER`          | `user`            | Usuario de la aplicación             |
| `MYSQL_PASSWORD`      | `changeme`        | Contraseña del usuario de la app     |
| `PHPMYADMIN_PORT`     | `8080`            | Puerto local de phpMyAdmin           |

---

## 🗂️ Estructura del proyecto

```text
.
├── docker-compose.yml   # Define los servicios MySQL y phpMyAdmin
├── init.sh              # Otorga al usuario permisos solo sobre su base de datos
├── .env.example         # Plantilla para crear tu archivo .env
├── .gitignore           # Evita subir el archivo .env
├── .gitattributes       # Mantiene los saltos de línea LF en los scripts .sh
└── README.md            # Documentación del proyecto
```

---

## 🌐 Acceso a los servicios

- 🐬 **MySQL**
  - Host: `localhost`
  - Puerto: `3306`
  - Usuario: el valor de `MYSQL_USER` (por defecto `user`)
  - Contraseña: el valor de `MYSQL_PASSWORD` (por defecto `changeme`)
  - Base de datos: el valor de `MYSQL_DATABASE` (por defecto `testdb`)

- 🧭 **phpMyAdmin**
  - URL: `http://localhost:8080` (o el puerto definido en `PHPMYADMIN_PORT`)
  - Host del servidor MySQL: `mysql`
  - Usuario y contraseña: los mismos de `MYSQL_USER` y `MYSQL_PASSWORD`
  - Usuario root: `root` con la contraseña de `MYSQL_ROOT_PASSWORD` (solo para desarrollo local)

---

## 🔐 Permisos y seguridad

- El usuario `MYSQL_USER` recibe permisos únicamente sobre `MYSQL_DATABASE` (principio de mínimo privilegio). Lo configura el script `init.sh`.
- El puerto 3306 solo es accesible desde tu máquina (`127.0.0.1`).
- El archivo `.env` está en `.gitignore`: nunca subas credenciales reales al repositorio.

---

## 🛠️ Comandos útiles

```bash
docker compose up -d        # Levantar los servicios
docker compose ps           # Ver el estado de los servicios
docker compose logs mysql   # Ver los logs de MySQL
docker compose down         # Detener (conserva los datos)
docker compose down -v      # Detener y borrar los datos
```

---

## 📝 Notas

- Este entorno es para uso local o pruebas.
- Los scripts de inicialización solo se ejecutan la primera vez, cuando el volumen está vacío. Para reiniciar desde cero (borra todos los datos): `docker compose down -v`.
- En Windows, `init.sh` debe usar saltos de línea LF; de lo contrario el contenedor mostrará el error `\r: command not found`.
- En producción, asegúrate de:
  - Cambiar las contraseñas por defecto.
  - Limitar el acceso desde IPs específicas.
  - Usar almacenamiento persistente seguro y respaldos.

---

## 📌 Inspirado en 😎

- [Khezen/compose-postgres](https://github.com/khezen/compose-postgres)
- [Docker Hub - phpMyAdmin](https://hub.docker.com/_/phpmyadmin)
- [Docker Hub - MySQL](https://hub.docker.com/_/mysql)
