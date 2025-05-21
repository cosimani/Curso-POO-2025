.. -*- coding: utf-8 -*-

.. _rcs_subversion:

Clase 25 - POO 2025
===================
(Fecha: 21 de mayo)


Simulacro de examen parcial
===========================


Instrucciones generales
=======================

- Todos los ejercicios deben resolverse utilizando **C++ con la biblioteca Qt**.
- La clase base principal debe ser **QWidget**. No se permite el uso de `QMainWindow`.
- Se debe utilizar `SIGNAL()` y `SLOT()` explícitamente para conectar señales y slots.
- No se permite el uso de lambdas ni punteros a funciones en `connect(...)`.
- No se debe usar `QPixmap`. Usar exclusivamente `QImage`.
- No se deben usar rutas absolutas.


Ejercicio 1 – Login con Avatar desde internet
=============================================

**Objetivo**: Implementar una aplicación de inicio de sesión que descargue una imagen de avatar desde Internet y almacene la sesión localmente.

Requisitos:

1. Una clase Login (en los archivos login.h, login.cpp y login.ui) con:

   - Dos `QLineEdit` para ingresar el usuario y clave.
   - Un botón `Iniciar sesión`.
   - Una clase `Image` en la cual se deberá dibujar una imágen (un avatar) con paintEvent.
   - Esta imagen deberá aparecer cuando el usuario completa su nombre de usuario y sale del QLineEdit de campo usuario.
   - Usar `QGridLayout` para confeccionar el Login.
   - El objeto de la clase Imagen deberá eetá promocionada dentro del layout.

2. El avatar será una imagen obtenida desde el sitio: https://robohash.org

   Ejemplo: Si el usuario ingresa "lucas" en el campo usuario, se descarga:
   https://robohash.org/lucas.png

3. Descargar la imagen utilizando `QNetworkAccessManager` y mostrarla en el objeto de la clase Imagen.

4. Al iniciar sesión correctamente, almacenar el nombre del usuario y la fecha/hora en una base de datos SQLite. Usar la tabla usuarios.

5. Cuando un usuario se valida correctamente con la base de datos, se ocultará el login y se mostrará una nueva ventana vacía.



Ejercicio 2 – Galería de imágenes local con etiquetas
======================================================

**Objetivo**: Implementar una galería de imágenes locales, clasificadas por etiquetas, utilizando herencia y polimorfismo.

Requisitos:

1. Diseñar una clase abstracta `ImagenConEtiqueta` con:

   - Ruta de la imagen.
   - Etiqueta textual.
   - Método virtual puro `mostrar()`.

2. Implementar dos clases derivadas:

   - `ImagenNormal`: muestra la imagen normalmente.
   - `ImagenConMarco`: dibuja la imagen con un marco usando `paintEvent()`.

3. Interfaz gráfica:

   - Una grilla de 3x3 para mostrar 9 imágenes.
   - Botón en cada celda de la grilla para agregar imagen.
   - Campo `QLineEdit` para ingresar etiqueta.
   - widget personalizado para mostrar la imagen.
   - `QFileDialog` para seleccionar la imagen.

5. Dibujar imágenes utilizando `QImage` y `paintEvent`.

6. Resolver en la interfaz de qué manera elegir ImagenNormal o ImagenConMarco en cada celda.
