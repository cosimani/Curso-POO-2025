.. -*- coding: utf-8 -*-

.. _rcs_subversion:

Clase 05 - POO 2025
===================
(Fecha: 19 de marzo)



Registro en video de algunos temas de la clase de hoy
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

`Función genérica 2021 <https://www.youtube.com/watch?v=PkmAW31KuV0>`_ 

`Función genérica - arrays - string - punteros 2022 <https://www.youtube.com/watch?v=gdrMyvjf7M4>`_ 

`getDatos de Poste - Convenciones 2021 <https://www.youtube.com/watch?v=7l0QZzqbQjI>`_

`Introducción a Qt 2021 <https://www.youtube.com/watch?v=JYADonAlKPc>`_

`Primer aplicación en Qt 2021 <https://www.youtube.com/watch?v=krfWC8mWTQM>`_



Cadena de caracteres
^^^^^^^^^^^^^^^^^^^^

- Al estilo C	

.. code-block::

	#include <string.h>

	char cadena1[ 30 ], cadena2[ 30 ];
	strcpy( cadena1, "Hola" );
	cin >> cadena2;
	
- Con C++ usamos   

.. code-block::

	#include<string>

	Asignación       s1 = s2    s1 = "Hola"
	Concatenación    s1 = s2 + s3	
	Comparación      if ( s1 == s2 )
	Subcadenas       s1.substr( 3, 5 )
	Longitud         s1.length()    s2.size()  // Son lo mismo
	Acceso a char    s1[ 2 ]    s2.at( 2 )  // Lanza out_of_range
	Limpiar          s1.clear()
	Busca cadena     s1.find( "cadena" );    s1.find( s2 );
	Puntero a char   const char *c = s1.c_str()



Punteros
========

**Declaración**

.. code-block::

	int * entero;     // entero es un puntero a int
	char * caracter;  // puntero a char

	entero      es el puntero
	*entero     es el contenido


**Punteros a variables**

.. code-block::

	int entero;         // entero es una variable int
	int * pEntero;      // pEntero es un puntero a int
	pEntero = &entero;  // &entero es la dirección de memoria donde se almacena entero

**Arrays y punteros**

.. code-block::

	int miArray[ 10 ];	// miArray es como un puntero al primer elemento
	int* puntero;

	puntero = miArray;  // similar a:  puntero = &miArray[0];
	( *puntero )++;     // equivale a miArray[0]++;  // incrementa
	puntero++;          // equivale a &miArray[1];   // se mueve una posición

	puntero = puntero + 3;  // se desplaza 3 posiciones int






Función Genérica
================

- Supongamos que debemos implementar una función que imprima en la salida los valores de un array de enteros:

.. code-block::

	void imprimir ( int v[], int cantidad )  {
	    for ( int i = 0 ; i < cantidad ; i++ )
	        std::cout << v[ i ] << " ";
	    std::cout << std::endl;
	}

	int main( int, char ** )  {
	    int v1[ 5 ] = { 5, 2, 4, 1, 6 };
	    imprimir( v1, 3 );

	    return 0;
	}

- Ahora necesitamos la impresión de un array de float

.. code-block::

	void imprimir( float v[], int cantidad );

- Vemos que las versiones se diferencian por el tipo de datos del array. Entonces podemos utilizar lo siguiente:

.. code-block::

	template < class T > void imprimir ( T v[], int cantidad )  {
	    for ( int i=0 ; i < cantidad ; i++ )
	        std::cout << v[ i ] << " ";
	    std::cout << std::endl;
	}

	int main( int, char ** )  {
	    int v1[ 5 ] = { 5, 2, 4, 1, 6 };
	    float v2[ 4 ] = { 2.3, 5.1, 0, 2 };

	    imprimir( v1, 5 );  // qué pasa si pongo cantidad 10 -> Publica basura
	    imprimir( v2, 2 );

	    return 0;
	}

- El compilador utiliza el código de la función genérica como plantilla para crear automáticamente dos funciones sustituyendo T por el tipo de dato concreto.

.. code-block::

	Con T = int     utiliza -->     void imprimir( int v[], int cantidad )

	Con T = float   utiliza -->     void imprimir( float v[], int cantidad )

- Aquí, la única operación que realizamos sobre los valores de tipo T es:

.. code-block::

	std::cout << v[ i ]

- Esto pone una restricción, ya que sólo se admitirá los tipos de datos para los que se puedan imprimir en pantalla con:

.. code-block::

	std::cout <<




Convenciones para escribir nuestro código
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- Los nombres de las clases, structs y enum comienzan con mayúsculas (usando ``UpperCamelCase``).
- Nombres de variables, funciones y métodos comienzan con minúsculas (usando ``lowerCamelCase`` y con palabras separadas con guión bajo).

- Ejemplos para nombres de clases: ``Persona`` - ``PrimeraClase`` - ``Ventana``
- Ejemplos para nombres de variables y funciones: ``velocidad`` - ``sumarNumeros`` - ``alto_imagen`` - ``anchoImagen``

**CamelCase**: Es escribir con la forma de jorobas de camello con las mayúsculas y minúsculas.

UpperCamelCase: La primera letra de cada palabra es mayúscula. Ejemplo: ``EjemploDeUpperCamelCase``.
lowerCamelCase: Igual a UpperCamelCase con excepción de la primer palabra. Ejemplo: ``ejemploDeLowerCamelCase``


Primer aplicación en Qt con interfaz gráfica
============================================

- Qt 
	- Biblioteca para desarrollo de software de Quasar Technologies
	- Se llamó también Trolltech
	- Biblioteca multiplataforma
	- En el 2008 lo compró Nokia
	- Aplicaciones escritas con C++ (Qt)
		- KDE
		- VLC Media Player
		- OBS Studio
		- VirtualBox
		- Google Earth 
		- Wireshark
		- Blender 
		- Cura
		- MATLAB 
	- En 2012, Digia compra Qt y comercializa las licencias 
	- Digia desarrolló herramientas para usar Qt en iOS y Android.
	- En 2014, Digia separó Qt en un empresa independiente llamada The Qt Company.
	- Disponible en C++, en Python (con PyQt o PySide) y en Javascript (con QML).
		

**Ejemplo**

- Creación de una aplicación Qt

.. code-block::

	#include <QApplication>	
	// - Administra los controles de la interfaz
	// - Procesa los eventos
	// - Existe una única instancia
	// - Analiza los argumentos de la línea de comandos

	int main( int argc, char** argv )  {	
	    // app es la instancia y se le pasa los parámetros de la línea
	    // de comandos para que los procese.
	    QApplication app( argc, argv ); 

	    QLabel hola( "<H1 aling=right> Hola </H1>" );
	    hola.resize( 200, 100 );
	    hola.setVisible( true );

	    app.exec();  // Se le pasa el control a Qt
	    return 0;
	}




Ejercicio 1:
============

- Instalar Qt. Lo cual incluye las herramientas de compilación C++ (MinGW 64 bits), la biblioteca Qt y Qt Creator.
- Crear un primer programa que muestre por la consola de QtCreator 10 números aleatorios en el intervalo [ 2, 20 ]
- Cada vez que se ejecute el programa, los números deberán ser aleatorios y distintos en cada ejecución.


Ejercicio 2:
============

- Definir una clase Poste con dos atributos: altura (int, en metros) y diametro (float, en cm).
- Crear un vector para almacenar varios objetos de la clase Poste.
- Cargar al menos 5 postes con diferentes alturas y diámetros.
- Ordenar los postes de menor a mayor según su altura.
- Mostrar en consola la lista de postes antes y después ordenarlos.
- Resolver únicamente con las clases, funciones y estructuras vistas hasta el momento en la asignatura y en asignaturas anteriores.


Ejercicio 3:
============

- Elija un nombre para su propio espacio de nombres.
- Defina una función dentro de ese namespace para devolver el número de versión junto con la fecha de la última actualización de la biblioteca
- Suponer que dentro de ese espacio de nombres se agregan funciones y clases, y que formarán parte de la versión de esta biblioteca propia.
- Definir un mecanismo para colocar la versión de la biblioteca y que exista la siguiente función que devuelva la versión.

.. code-block::

	QString getVersion();  // Devuelve un texto como "v0.0.1 - 20240318"


Ejercicio 4:
============

- Crear un std::vector para contener punteros a int
- Cargar 30 valores pseudo aleatorios entre 1 y 15
- Publicar la moda


Ejercicio 5:
============

- Crear un std::vector para contener objetos de la clase std::string
- Cargar 5 expresiones idiomáticas, como por ejemplo: pan comido
- Publicar por consola ordenado alfabéticamente sin considerar los espacios


Ejercicio 6:
============

- En un Empty qmake Project
- Crear una nueva clase (que no sea Persona, ni Cliente, ni Poste). Invente una clase.
- Agregar uno o más constructores, agregar sus métodos y sus atributos
- Crear algunos objetos de esta clase en la función main
- Utilizar un vector para almacenar estos objetos.
- Agregar tantos objetos hasta consumir 200 MB de RAM. Cuando alcance esto, no incoporar más objetos y publicar la cantidad de objetos agregados.
- Resolver únicamente con las clases, funciones y estructuras vistas hasta el momento en la asignatura y en asignaturas anteriores.



Aclaraciones:
=============

- Todos los ejercicios serán actualizados en un repositorio en GitHub
- Escribir el README con contenido para poder ejecutar los ejercicios
- Cada ejercicio tendrá su propia carpeta ejercicio01, ejercicio02, ...
- Que cada ejercicio debe contener todo lo necesario para poder compilarlo y ejecutarlo.
- Excluir los archivos y carpetas que no sean necesarios, como se el archivo con extensión .pro.user y la carpeta build-



