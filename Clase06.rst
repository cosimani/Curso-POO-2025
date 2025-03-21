.. -*- coding: utf-8 -*-

.. _rcs_subversion:

Clase 06 - POO 2025
===================
(Fecha: 21 de abril)




Registro en video de algunos temas de la clase de hoy
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

`Función genérica 2021 <https://www.youtube.com/watch?v=PkmAW31KuV0>`_ 

`Help signal slot QSlider QSpinBox 2021 <https://www.youtube.com/watch?v=BHog8TPjnos>`_



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



Ejercicio 1:
============

- Definir una clase Poste con dos atributos: altura (int, en metros) y diametro (float, en cm).
- Crear un vector para almacenar varios objetos de la clase Poste.
- Cargar al menos 5 postes con diferentes alturas y diámetros.
- Ordenar los postes de menor a mayor según su altura.
- Mostrar en consola la lista de postes antes y después ordenarlos.
- Resolver únicamente con las clases, funciones y estructuras vistas hasta el momento en la asignatura y en asignaturas anteriores.


Ejercicio 2:
============

- Crear un std::vector para contener objetos de la clase std::string
- Cargar 5 expresiones idiomáticas, como por ejemplo: pan comido
- Publicar por consola ordenado alfabéticamente sin considerar los espacios


Ejercicio 3:
============

- En un Empty qmake Project
- Crear una nueva clase (que no sea Persona, ni Cliente, ni Poste). Invente una clase.
- Agregar uno o más constructores, agregar sus métodos y sus atributos
- Crear algunos objetos de esta clase en la función main
- Utilizar un vector para almacenar estos objetos.
- Agregar tantos objetos hasta consumir 200 MB de RAM. Cuando alcance esto, no incoporar más objetos y publicar la cantidad de objetos agregados.
- Resolver únicamente con las clases, funciones y estructuras vistas hasta el momento en la asignatura y en asignaturas anteriores.




Signals y slots
===============

- signal y slot son funciones.
- Las signals de una clase se comunican con los slots de otra.
- Se deben conectar con la función connect de QObject.
- Un evento puede generar una signal.
- Los slots reciben estas signals.
- SIGNAL() y SLOT() son macros (convierten a cadena).
- emisor y receptor son punteros a QObject

.. code-block::
	
	QObject::connect( emisor, SIGNAL( signal ), receptor, SLOT( slot ) );

	
- Se puede remover la conexión:

.. code-block::

	QObject::disconnect( emisor, SIGNAL( signal ), receptor, SLOT( slot ) );

**Ejemplo:** QPushButton para cerrar la aplicación.

.. code-block::

	#include <QApplication>
	#include <QPushButton>

	int main( int argc, char** argv )  {
	    QApplication a( argc, argv );
	    QPushButton* boton = new QPushButton( "Salir" );

	    QObject::connect( boton, SIGNAL( pressed() ), &a, SLOT( quit() ) );
	    boton->setVisible( true );
		
	    return a.exec();
	}



Ejercicio 4:
============

- Usar el código del ejemplo del control de volumen
- Cuando el valor del QSlider se modifique, colocar como título de la ventana el mismo valor que tiene el QSlider. 



	
**Ejemplo:** Control de volumen

.. code-block::

	#include <QApplication>
	#include <QWidget>
	#include <QHBoxLayout>
	#include <QSlider>
	#include <QSpinBox>

	int main( int argc, char** argv )  {
	    QApplication a( argc, argv );

	    QWidget * ventana = new QWidget;  // Es la ventana padre (principal)
	    ventana->setWindowTitle( "Volumen" ); 
	    ventana->resize( 300, 50 );

	    QSpinBox * spinBox = new QSpinBox;
	    QSlider * slider = new QSlider( Qt::Horizontal );
	    spinBox->setRange( 0, 100 );
	    slider->setRange( 0, 100 );

	    QObject::connect( spinBox, SIGNAL( valueChanged( int ) ), slider, SLOT( setValue( int ) ) );
	    QObject::connect( slider, SIGNAL( valueChanged( int ) ),  spinBox, SLOT( setValue( int ) ) );

	    spinBox->setValue( 15 );

	    QHBoxLayout * layout = new QHBoxLayout;
	    layout->addWidget( spinBox );
	    layout->addWidget( slider );
	    ventana->setLayout( layout );
	    ventana->setVisible( true );	

	    return a.exec();
	}
	




