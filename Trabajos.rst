.. -*- coding: utf-8 -*-

.. _tp1_visionai:

Trabajo Práctico Integrador - POO 2025
======================================

A continuación se proponen trabajos prácticos integradores para desarrollar durante el cuatrimestre.  
Está centrado en **C++ con Qt y Programación Orientada a Objetos**, y se combina con tecnologías como **FastAPI**, **AWS EC2**, **Docker**, **MySQL** y **APIs externas (OpenAI, entre otras)**.  


TP1 - Analizador Inteligente de Imágenes
----------------------------------------

**Nombre sugerido:** VisiónAI  
**Cantidad de estudiantes:** 4  

**Descripción general:**  
Una aplicación de escritorio que permite al usuario cargar imágenes y obtener descripciones automáticas, análisis semántico o etiquetas generadas por la API de OpenAI.  
El sistema permite al usuario escribir su propio *prompt*, el cual define qué tipo de análisis desea que realice OpenAI sobre la imagen cargada.

**Funcionalidades mínimas:**

- Carga de imágenes desde Qt usando *drag & drop*.
- Login y autenticación usando FastAPI + MySQL.
- Persistencia local en SQLite para almacenar el último usuario logueado y las últimas imágenes analizadas.
- Campo editable en la GUI para ingresar un *prompt* personalizado. Este texto es enviado junto con la imagen a la API de OpenAI.
- Visualización en Qt de:
  
  - Imagen original.
  - Prompt ingresado por el usuario.
  - Descripción o respuesta generada por OpenAI.
  - Historial de análisis almacenado por usuario en la base de datos MySQL (imagen, prompt, resultado, timestamp).

Criterios de Evaluación – TP1: VisiónAI (100 puntos)
-----------------------------------------------------

**1. Diseño Orientado a Objetos (POO) – 40 puntos**

- El modelo de clases refleja correctamente las entidades del sistema (Usuario, Imagen, Análisis, Prompt, etc.) – 15 puntos
- Se aplican principios de abstracción y encapsulamiento (uso adecuado de atributos privados y métodos públicos) – 5 puntos
- Se utiliza herencia o polimorfismo de forma coherente para representar tipos de análisis o entidades extendidas – 10 puntos
- Se implementa al menos un patrón de diseño relevante (estrategia, fábrica, etc.) – 10 puntos

**2. Diseño y funcionalidad de la interfaz de usuario (Qt GUI) – 25 puntos**

- La interfaz permite realizar todas las acciones requeridas de forma clara y funcional: login, carga de imagen, ingreso de prompt, análisis, visualización de resultados – 10 puntos
- El diseño visual de la GUI es intuitivo, limpio y estéticamente cuidado – 5 puntos
- El sistema permite cargar imágenes mediante *drag & drop* de forma robusta – 5 puntos
- Se implementa manejo de errores en la interfaz para eventos como fallos de red, archivos no válidos o errores de autenticación – 5 puntos

**3. Uso de tecnologías externas – 25 puntos**

- El backend en FastAPI está correctamente implementado y permite autenticación, almacenamiento y análisis – 8 puntos
- Se utiliza MySQL con una estructura de tablas bien definida y se almacena correctamente la información – 5 puntos
- Se implementa persistencia local en SQLite para guardar últimos accesos e imágenes – 4 puntos
- La comunicación con la API de OpenAI funciona correctamente y devuelve descripciones útiles – 5 puntos
- Se usa Docker y Docker Compose para levantar el backend y la base de datos de forma reproducible – 3 puntos

**4. Valor agregado y creatividad – 10 puntos**

- El equipo define un enfoque temático original e interesante para el análisis de imágenes (arte, industria, salud, etc.) – 4 puntos
- El sistema incluye funcionalidades adicionales no requeridas explícitamente (sugerencias de prompt, exportación de resultados, integración con otras APIs, accesibilidad, etc.) – 3 puntos
- La presentación final del proyecto demuestra creatividad en la forma de comunicar el trabajo: uso de storytelling, demo bien estructurada, identidad visual, etc. – 3 puntos


TP2 - Próximamente
----------------------------------------


TP3 - Próximamente
----------------------------------------


TP4 - Próximamente
----------------------------------------


TP5 - Próximamente
----------------------------------------


TP6 - Próximamente
----------------------------------------


TP7 - Próximamente
----------------------------------------
