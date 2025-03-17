.. -*- coding: utf-8 -*-

.. _rcs_subversion:

Clase 04 - POO 2025
===================
(Fecha: 17 de marzo)


Problema para las próximas semanas
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

:Una empresa que se dedica al desarrollo de software ofrece soluciones y utiliza las siguientes tecnologías y herramientas:
		- QtCreator como IDE
		- Biblioteca Qt con C++ para aplicaciones Desktop
		- MySQL para base de datos y phpmyadmin para su gestión
		- FastAPI en Python para la API
		- Y se desea implementar en contenedores

Necesidad 
^^^^^^^^^

- Se desea una aplicación desktop en Qt que tenga un login de usuarios 
- Cuando un usuario en la aplicación desktop ingrese un usuario válido obtendrá un access token desde la API desarrollada con FastAPI
- Cuando se obtiene el access token, el usuario ya estará logueado, y podrá utilizar este token para próximas consultas a la API
- Los usuarios se almacenarán en una tabla usuarios en MySQL
- Se quiere montar todo esto en el localhost o en la nube para tener un entorno de desarrollo y testing



Para profundizar
^^^^^^^^^^^^^^^^

:Manejo de Autenticación y Seguridad en APIs:
		- Implementación de OAuth2 con FastAPI y generación de tokens JWT.
		- Seguridad en almacenamiento de contraseñas: uso de hashing con bcrypt.
		- Configuración de permisos y roles en la API.
		- Conexión y Manejo de Base de Datos en Qt con MySQL

:Creación de un Dockerfile para FastAPI y MySQL:
		- Configuración de docker-compose para el despliegue del entorno.
		- Persistencia de datos en contenedores: volúmenes en Docker.
		- Despliegue en AWS o similar y configuración del servidor

:Consumo de APIs en Qt:
		- Uso de QNetworkAccessManager para realizar peticiones HTTP.
		- Manejo de respuestas JSON en Qt y parseo con QJsonDocument.
		- Implementación de manejo de errores y reintentos en solicitudes a la API.

