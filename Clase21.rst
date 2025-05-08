.. -*- coding: utf-8 -*-

.. _rcs_subversion:

Clase 21 - POO 2025
===================
(Fecha: 7 de mayo)



Registro en video de algunos temas de la clase de hoy
=====================================================

`const 2025 <https://youtu.be/-z9BhQSPHJg>`_ 

`const 2021 <https://youtu.be/UqXE4GeFd_s>`_ 


const
=====

- Una variable definida como const no podrá ser modificada a lo largo del programa (se crea como sólo lectura)
- Se puede aplicar a cualquier tipo:

.. code-block:: c	

	const float pi = 3.14;
	const peso = 67;  // Si no se indica el tipo entonces es int
	                  // Aunque sólo en compiladores viejos



const con punteros
^^^^^^^^^^^^^^^^^^

.. code-block:: c	

	int x = 10;
	int * px = &x;  // normal

	const int y = 10;
	int * py = &y;  // El compilador dirá: "invalid conversion from const int*
	               // to int*". La inversa sí se permite

	int y = 10;
	const int * py = &y;  // permitido (pero el contenido es de sólo lectura)

	*py = 6;  // No permitido. El contenido apuntado es de sólo lectura

	int z = 10;
    const int * const pz = &z;  // Analizar


const en parámetros de funciones
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- Cuando los parámetros son punteros, decimos que no podrá modificar los objetos referenciados

.. code-block:: c	

	int funcion( const char * ch )


- Lo mismo sucede con referencias

.. code-block:: c	

	int funcion( const char& ch )


const en clases
^^^^^^^^^^^^^^^

.. code-block:: c	

	class ClaseA  {
	    const int i;
	    int x;

	public:
	    int funcion( ClaseA cA, const ClaseA &c )  {
	        cA.x = 1;
	        cA.i = 2;  // No compila. i es de sólo lectura.
	        c.x = 3;   // No compila. El objeto c es de sólo lectura.

	        return cA.x;
	    }
	}; 


.. code-block:: c	

	// A la variable i sólo la puede inicializar el constructor y sólo con la forma:
	ClaseA() : i( 8 )  {  }   

	// Si en el cuerpo del constructor se hace:
	ClaseA()  { 
	    i = 8;  // Compila? i es de solo lectura o no
	}   


- Aplicado a métodos de una clase no permite modificar ninguna propiedad de la clase

.. code-block:: c	

	class ClaseB  {
	    int x;

	    void funcion( int i ) const  {
	        x = x + i;  // Compila?
	    }
	};




Ejercicio 8 (... aquí continúa, y continuará ...):
============

- (anteriormente) Tener disponible un endpoint con FastAPI para validar usuarios.
- (anteriormente) Registrar en MySQL algunos usuarios en una tabla con campos como: nombre, apellido, usuario, clave, mail
- Desarrollar un login en Qt que permita loguearse mediante una solicitud HTTP POST a una endpoint de FastAPI enviando las credenciales en el cuerpo de la petición.
- Si las credenciales son válidas, el servidor devolverá un token JWT en la respuesta.
- El token debe almacenarse en memoria durante el uso de la aplicación Qt y utilizarse en las siguientes peticiones HTTP como Authorization: Bearer <token>.


