# 🚀 Proyecto Docker Compose: MySQL + phpMyAdmin 🐬

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

## ⚙️ Archivo .env.example 🧪

Crea un archivo `.env` en la raiz del proyecto con las siguientes variables (puedes cambiar los valores según necesites):

```env
MYSQL_ROOT_PASSWORD=root
MYSQL_DATABASE=testdb
MYSQL_USER=user
MYSQL_PASSWORD=changeme
PHPMYADMIN_PORT=8080
```


## 🗂️ Estructura del proyecto
.
├── docker-compose.yml
├── init.sql
└── .env

---

## 📝 Notas
Este entorno es para uso local o pruebas.

En producción, asegúrate de:

Cambiar las contraseñas por defecto.

Limitar acceso desde IPs específicas.

Usar almacenamiento persistente seguro y respaldos.

---

## 📌 Inspirado en

** Khezen/compose-postgres
** Docker Hub - phpMyAdmin
** Docker hub - MySQL

---

## 5. **Badges (opcional pero cool 😎)**

```markdown
![Docker](https://img.shields.io/badge/docker-compose-blue?logo=docker)
![MySQL](https://img.shields.io/badge/mysql-8.0-orange?logo=mysql)
![phpMyAdmin](https://img.shields.io/badge/phpMyAdmin-UI-yellow?logo=phpmyadmin)