.. -*- coding: utf-8 -*-

.. _rcs_subversion:

Clase 01 - POO 2025
===================
(Fecha: 10 de marzo)


Metodología didáctica
=====================

- A continuación se resume el conjunto de estrategias, procedimientos y acciones para facilitar el aprendizaje y el logro de nuestros objetivos. 

:Teoría: 
	- En la primer parte de cada clase se expondrán los contenidos teóricos.
	- Este contenido también está disponible en grabaciones de años anteriores, cuyos links se colocarán a medida que se avance en las clases.

:Práctica: 
	- La segunda parte de cada clase estará destinado a la resolución de ejercicios e incorporación de esos contenidos.

:Regularidad, promoción y examen final: 
	- Primer y segundo parcial: Problema para resolver en 2 horas
	- La materia se promociona bajo la modalidad de la UBP.
	- El examen final sigue `esta modalidad <https://github.com/cosimani/Curso-POO-2025/blob/main/Desafios.rst>`_ .

:Meet y WhatsApp para comunicaciones: 
	- `https://meet.google.com/vyf-bsai-uvq <https://meet.google.com/vyf-bsai-uvq>`_
	- `https://chat.whatsapp.com/IDRbj8NFaut77I95Ov9Obb <https://chat.whatsapp.com/IDRbj8NFaut77I95Ov9Obb>`_

	
Registro en video de algunos temas de la clase de hoy
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

`Library, Librería, Biblioteca 2021 <https://www.youtube.com/watch?v=k9ZZSSWuX6E>`_ 

`std C y std C++ 2021 <https://www.youtube.com/watch?v=GrOLHLHcZqg>`_ 



Instalación de herramientas
===========================

:QtCreator: 
	- Instalar 'Biblioteca de Qt', 'Qt Creator' y 'MinGW 64-bit'

:OpenSSL: 
	- Descargar instalador desde la `Página de descarga <https://slproweb.com/products/Win32OpenSSL.html>`_
	- Seleccionar el instalador `Win64 OpenSSL v3.4.1 <https://slproweb.com/download/Win64OpenSSL-3_4_1.exe>`_


Biblioteca estándar de C++
==========================

- Está en el espacio de nombres ``std``
- En la biblioteca estándar de C, los archivos de cabecera X.h se reemplazan por cX o X. Por ejemplo:

.. code-block::

	#include <stdlib.h>                   #include <cstdlib>    

	    int atoi( const char * )  // Convierte a int un número expresado en cadena
	    int abs( int )            // Devuleve el valor absoluto
	    int rand()                // Devuelve un número pseudo aleatorio entre 0 y 32767


	#include <stdio.h>                   #include <cstdio>    

	    // Borra un archivo. Devuelve 0 o un código de error.
	    int remove( const char * filename )

	    // Imprime por pantalla. Recibe un número indefinido de argumentos.
	    int printf( const char * format, ... )

	#include <iostream.h>                   #include <iostream>    

	    cout
	    cin
	    endl



