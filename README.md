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
* Ingresa al directorio con el siguiente,  `cd compose-mysql`
* Ejecuta el siguiente comando `docker-compose up -d`

## ⚙️ Archivo .env.example 🧪

Este archivo compose contiene las siguientes variables de entorno:

* `MYSQL_ROOT_PASSWORD`  El valor por defecto es **root**
* `MYSQL_DATABASE`  El valor por defecto es **testdb**
* `MYSQL_USER`  El valor por defecto es **user**
* `MYSQL_PASSWORD`  El valor por defecto es **changeme**
* `PHPMYADMIN_PORT`  El valor por defecto es **8080**

Crear un archivo `.env` en la raiz del proyecto con las siguientes variables (puedes verificar en el archivo .env.example y observar como cambiar los datos):

* `MYSQL_ROOT_PASSWORD`
* `MYSQL_DATABASE` 
* `MYSQL_USER`  
* `MYSQL_PASSWORD`  
* `PHPMYADMIN_PORT`

## 🗂️ Estructura del proyecto
```text
.
├── docker-compose.yml   # Define los servicios MySQL y phpMyAdmin
├── init.sql             # Script SQL de inicialización con privilegios
├── .env.example         # Plantilla para crear tu archivo .env
└── README.md            # Documentación del proyecto
```
---

## 🌐 Acceso a los servicios
- 🐬 Acceso a MySQL:
  - Host: `localhost`
  - Puerto: `3306`
  - Usuario: `${MYSQL_USER:-user}`
  - Contraseña: `${MYSQL_PASSWORD:-changeme}`
  - Base de datos: `${MYSQL_DATABASE:-testdb}`
    
- 🧭 Acceso a phpMyAdmin:
  - URL: `http://localhost:8080`
  - Host del Servidor MySQL: `mysql`
  - Usuario: `${MYSQL_USER:-user}`
  - Contraseña: `${MYSQL_PASSWORD:-changeme}`
    - Usuario raiz: `root`
    - Contraseña de root: `root`

---

## 📝 Notas
- Este entorno es para uso local o pruebas.

- En producción, asegúrate de:

  - Cambiar las contraseñas por defecto.

  - Limitar acceso desde IPs específicas.

  - Usar almacenamiento persistente seguro y respaldos.

---

## 📌 Inspirado en 😎

- [Khezen/compose-postgres](https://github.com/khezen/compose-postgres)
- [Docker Hub - phpMyAdmin](https://hub.docker.com/_/phpmyadmin)
- [Docker Hub - MySQL](https://hub.docker.com/_/mysql)
