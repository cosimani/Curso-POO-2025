.. -*- coding: utf-8 -*-

.. _rcs_subversion:

Clase 22 - POO 2025
===================
(Fecha: 9 de mayo)



Repositorio base
----------------



📦 https://github.com/cosimani/poo-api-db

El entorno incluye:
- Base de datos MySQL 8.0 accesible en el puerto 3306
- Interfaz phpMyAdmin en el puerto 8080
- API FastAPI en el puerto 8000

Estructura general
------------------

El proyecto contiene la siguiente estructura:

::

    poo-api-db/
    ├── app/                  # Código de la API en FastAPI
    ├── docker-compose.yml    # Definición de los servicios
    ├── Dockerfile            # Configuración del contenedor
    ├── .env                  # Variables sensibles (no subir al repo)
    ├── .gitignore
    └── README.md             # Documentación del entorno

Indicaciones para estudiantes
-----------------------------

- Este entorno es entregado para su **uso y adaptación libre** en los trabajos prácticos de la cátedra.
- Se espera que cada estudiante o grupo personalice la API según el problema que se proponga resolver.
- El backend puede ser utilizado para gestionar usuarios y otras tablas según los objetivos del proyecto final.


Instrucciones básicas
---------------------

1. Clonar el repositorio:
::

    git clone https://github.com/cosimani/poo-api-db.git
    cd poo-api-db

2. Crear un archivo `.env` con los datos de la base:
::

    MYSQL_ROOT_PASSWORD=****
    MYSQL_DATABASE=poo_db
    MYSQL_USER=****
    MYSQL_PASSWORD=****
    SECRET_KEY=****
    ACCESS_TOKEN_EXPIRE_MINUTES=60

3. Levantar los servicios:
::

    docker compose up --build -d

4. Acceder a:
- `http://localhost:8000/docs` para ver la API
- `http://localhost:8080` para gestionar la base con phpMyAdmin

