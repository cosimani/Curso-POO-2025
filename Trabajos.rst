.. -*- coding: utf-8 -*-

.. _tp1_visionai:

Trabajo Práctico Integrador - POO 2025
======================================

A continuación se proponen trabajos prácticos integradores para desarrollar durante el cuatrimestre.  
Está centrado en **C++ con Qt y Programación Orientada a Objetos**, y se combina con tecnologías como **FastAPI**, **AWS EC2**, **Docker**, **MySQL** y **APIs externas (OpenAI, entre otras)**.  


TP1 - Analizador Inteligente de Imágenes
----------------------------------------

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

TP2 - Analizador de CVs para selección de personal
--------------------------------------------------

**Cantidad de estudiantes:** 4

**Descripción general:**  
Aplicación de escritorio orientada a empresas para ayudar en procesos de selección de personal. Permite cargar múltiples CVs, analizarlos automáticamente, extraer la información relevante y generar un ranking sugerido para un perfil específico.

**Funcionalidades mínimas:**

- Carga de archivos de CV en texto o PDF.
- Login y autenticación usando FastAPI + MySQL.
- Campo para ingresar un perfil deseado (ejemplo: "desarrollador backend con experiencia en Python").
- Análisis automático de los CVs mediante la API de OpenAI, con extracción de información clave.
- Visualización en Qt de:
  
  - CV original cargado.
  - Perfil deseado.
  - Resumen generado por OpenAI.
  - Nivel de adecuación con respecto al perfil ingresado.
  - Ranking general de candidatos y exportación del shortlist como PDF o CSV.


TP3 - Analizador de reuniones grabadas
--------------------------------------

**Cantidad de estudiantes:** 3

**Descripción general:**  
Sistema que permite cargar transcripciones de reuniones o textos extensos, y genera automáticamente un acta resumida, lista de tareas y resúmenes por participante.

**Funcionalidades mínimas:**

- Carga de archivos `.txt` o `.docx` con la transcripción.
- Campo para ingresar el tema de la reunión.
- Uso de OpenAI para detectar participantes, extraer tareas asignadas y generar un resumen ejecutivo.
- Visualización en Qt de:
  
  - Transcripción original.
  - Acta generada automáticamente.
  - Lista de tareas por participante.
  - Exportación del acta y tareas en formato PDF.

TP4 - Planificador de tareas técnicas  
--------------------------------

**Cantidad de estudiantes:** 2

**Descripción general:**  
Aplicación que permite ingresar un texto que describe actividades o requerimientos generales de un proyecto de software, y devuelve un plan detallado con las tareas concretas a realizar, organizadas cronológicamente y clasificadas por tipo.

**Funcionalidades mínimas:**

- Campo para ingresar una descripción general de tareas técnicas o requisitos.
- Uso de OpenAI para:
  - Extraer tareas individuales.
  - Clasificar por categoría (frontend, backend, base de datos, testing, etc.).
  - Ordenarlas cronológicamente según dependencias implícitas.
- Visualización en Qt de:
  
  - Lista de tareas ordenadas.
  - Etiquetas o colores por tipo.
  - Exportación como PDF o CSV.


TP5 - Transcriptor inteligente de diálogos desde audio  
-----------------------------------------

**Cantidad de estudiantes:** 4

**Descripción general:**  
Aplicación que permite grabar o subir un archivo de audio con una conversación, entrevista o clase, y genera una transcripción estructurada que separa claramente los diálogos por hablante.

**Funcionalidades mínimas:**

- Grabación de audio desde la app o carga de archivo `.mp3` / `.wav`.
- Uso de OpenAI Whisper para transcripción.
- Procesamiento posterior con OpenAI para:
  - Separar por interlocutor (Persona 1, Persona 2, etc.).
  - Presentar el diálogo en formato tipo guion.
- Visualización en Qt de:
  
  - Transcripción separada por hablante.
  - Opcional: edición y corrección manual.
  - Exportación como texto, Word o PDF.


TP6 - Generador de imágenes a partir de descripción  
---------------------------------

**Cantidad de estudiantes:** 2

**Descripción general:**  
Aplicación que permite ingresar una descripción en lenguaje natural y seleccionar un estilo visual para generar una imagen digital ilustrativa a partir del texto.

**Funcionalidades mínimas:**

- Campo para escribir una escena o descripción (ej: “una ciudad futurista iluminada por neones”).
- Selector de estilo artístico: Ghibli, Pixar, Art Nouveau, Moebius
- Uso de OpenAI (DALL·E) o similar para generar la imagen.
- Visualización en Qt de:
  
  - Imagen generada.
  - Opción de guardar o compartir.
  - Historial de imágenes creadas.



TP7 - Asistente de resolución de problemas de programación
-----------------------------------------------------------

**Cantidad de estudiantes:** 2

**Descripción general:**  
Sistema que permite al usuario pegar código fuente en C++, Python u otros lenguajes y recibir sugerencias de mejora, solución de errores o explicaciones detalladas.

**Funcionalidades mínimas:**

- Campo de texto para pegar código.
- Selector de lenguaje (C++, Python, etc.).
- Envío del código y una pregunta opcional a la API de OpenAI.
- Visualización en Qt de:
  
  - Código original.
  - Explicación o sugerencia generada.
  - Historial por lenguaje y búsqueda por error.



Criterios de evaluación – Trabajos Prácticos (TP)
=================================================

1. Diseño orientado a objetos (POO) – 30 puntos
-----------------------------------------------

- El modelo de clases refleja correctamente las entidades principales del sistema – 5 puntos  
- Se aplican principios de abstracción y encapsulamiento (uso adecuado de atributos privados y métodos públicos) – 10 puntos  
- Se utiliza herencia o polimorfismo de forma coherente y justificada – 10 puntos  
- Cada clase tiene una única responsabilidad clara y está bien separada del resto del sistema – 5 puntos  

2. Diseño y funcionalidad de la interfaz de usuario (GUI con Qt u otra tecnología) – 35 puntos
-----------------------------------------------------------------------------------------------

- La interfaz permite realizar todas las acciones requeridas de forma clara, completa y funcional – 10 puntos  
- El diseño visual es intuitivo, limpio y estéticamente cuidado – 5 puntos  
- Se implementan funcionalidades específicas de interacción, como *drag & drop*, accesos rápidos, atajos de teclado, etc., de forma robusta – 10 puntos  
- Se contempla el manejo de errores en la interfaz (fallos de red, validaciones, archivos incorrectos, etc.) – 10 puntos  

3. Uso de tecnologías externas – 15 puntos
------------------------------------------

- Se implementa un backend funcional (FastAPI, Flask, etc.) con endpoints bien definidos – 3 puntos  
- Se utiliza una base de datos relacional o no relacional con estructura adecuada y persistencia asegurada – 3 puntos  
- Se implementa almacenamiento local o sincronización eficiente con el backend – 3 puntos  
- La comunicación con APIs externas (por ejemplo OpenAI u otras) funciona correctamente – 3 puntos  
- Se utiliza Docker y Docker Compose para facilitar la ejecución y portabilidad del sistema – 3 puntos  

4. Valor agregado y creatividad – 20 puntos
-------------------------------------------

- El sistema incluye funcionalidades adicionales no requeridas explícitamente (exportaciones, mejoras de UX, accesibilidad, integración con otras herramientas, etc.) – 10 puntos  
- La presentación final del proyecto demuestra creatividad en la forma de comunicar el trabajo: storytelling, demo estructurada, identidad visual, etc. – 10 puntos  




Grupos de estudiantes por TP
============================

**TP1 - VisiónAI**
- Brasca, Borsotti, Delgado, Merino

**TP2**
- Becerra, Calviño, Lafuente, Cassini

**TP3**
- Caffa, Casado, Jimenez

**TP4**
- Sapa Matias, Frache Valentino

**TP5**
- Brizuela Bautista, Aghem Agustín

**TP6**
- Iván Acevedo, Sofía Coniglio, Tristan Nores, Gregorio Olmedo

**TP7**
- Santiago Juri Nam, Luciano Lucas