.. -*- coding: utf-8 -*-

.. _rcs_subversion:

Clase 28 - POO 2025
===================
(Fecha: 28 de mayo)



Primer Parcial
==============

Instrucciones generales
-----------------------
- Todos los ejercicios deben resolverse utilizando **C++** con la biblioteca **Qt**.
- La clase base principal debe ser **QWidget**. No se permite el uso de **QMainWindow**.
- Se debe utilizar **SIGNAL()** y **SLOT()** explícitamente para conectar señales y slots.
- No se permite el uso de **lambdas** ni punteros a funciones en **connect(...)**.
- No se debe usar **QPixmap**. Usar exclusivamente **QImage**.
- No se deben usar rutas absolutas.

Ejercicio 1 – Reloj mundial con zonas horarias
-----------------------------------------------
Objetivo: Implementar una aplicación que muestre la hora actual en diferentes zonas del mundo utilizando clases personalizadas y networking.

Requisitos:

- Una clase `RelojZona` (archivos `relojzona.h`, `relozjona.cpp`, `relozjona.ui`) que contenga:

  - Un QLabel para mostrar la hora.
  - Un QLabel para mostrar el nombre de la ciudad.
  - Un método `actualizarHora(QString zona)` que obtenga la hora actual de una API pública de tiempo como http://worldtimeapi.org/api/timezone.
  - Un temporizador que actualice la hora cada 30 segundos.

- La interfaz principal debe tener un QGridLayout con al menos 3 relojes de zonas distintas:

  - Buenos Aires
  - New York
  - Madrid

- El acceso a la hora debe realizarse mediante `QNetworkAccessManager`.

- Dibujar un pequeño ícono analógico del reloj usando `paintEvent` y `QImage`, dentro de cada `RelojZona`.

Ejercicio 2 – Tablero interactivo de figuras geométricas
---------------------------------------------------------
Objetivo: Implementar una aplicación que permita agregar y visualizar distintas figuras geométricas utilizando herencia, polimorfismo y dibujo con paintEvent.

Requisitos:

- Crear una clase abstracta `FiguraGeometrica` con:

  - Posición (`x`, `y`).
  - Color.
  - Método virtual puro `dibujar(QPainter&)`.

- Implementar al menos dos clases derivadas:

  - `Circulo`: dibuja un círculo con `QPainter`.
  - `Rectangulo`: dibuja un rectángulo con `QPainter`.

- La aplicación debe permitir:

  - Elegir el tipo de figura a agregar mediante un `QComboBox` (Círculo o Rectángulo).
  - Elegir el color de la figura en RGB.
  - Un botón “Agregar figura” que la coloca en una posición aleatoria del tablero.
  - Un widget personalizado que actúe como el "tablero de dibujo", usando `paintEvent`.

- Todas las figuras deben almacenarse en una lista de punteros a `FiguraGeometrica` y dibujarse iterando con polimorfismo en `paintEvent`.

- Agregar un botón para limpiar todas las figuras del tablero.

