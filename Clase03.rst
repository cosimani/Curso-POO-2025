.. -*- coding: utf-8 -*-

.. _rcs_subversion:

Clase 03 - POO 2024
===================
(Fecha: 18 de marzo)


Registro en video de algunos temas de la clase de hoy
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

`Clases 2021 <https://www.youtube.com/watch?v=dH0WqMW3-_w>`_ 



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






Clases
======

.. code-block::

	class Poste  {
	    // Lista de miembros (generalmente funciones y datos)
	    // Los datos no pueden ser inicializados fuera del constructor 
	    // Si las funciones se definen fuera, se usa el operador :: 
	    // :: es el operador de acceso a ámbito
	};


.. code-block::

	class Poste;  // Esto es la declaración de una clase.

.. code-block:: c

	class Poste  {  // Esto es la declaración y definición de una clase.
	     
	};




**Ejemplo: Clase Poste**

.. code-block::

	#include <iostream>
	
	class Poste  {
	private:
	    int altura;
		
	public:
	    Poste() : altura( 0 )  {  }
	    int getAltura();
	};

	int Poste::getAltura()  {
	    return altura;
	}

	int main()  {
	    Poste poste;

	    std::cout << "Altura: " << poste.getAltura() << std::endl;
	    
	    return 0;
	}
	


**Cuestiones sobre declaraciones**

.. code-block::

	Poste poste;  // Llama al constructor sin parámetros. En esta última versión 
	              // de Poste, esto no serviría, ya que no hay constructor sin parámetros. 
	              // Si no se especifica un constructor, el compilador crea uno. 
	              // Por lo tanto, esta declaración sirve para una clase Poste 
	              // donde el programador no escriba constructor, o escriba uno sin recibir parámetros.

	Poste poste();  // Se entiende como el prototipo de una función sin parámetros que 
	                // devuelve un objeto Poste. Es decir, no sirve para instanciar un 
					// objeto con el contructor sin parámetros de Poste.

	Poste poste1( 12 );  // Válido


**Inicialización de objetos**

.. code-block::

	// Lo siguiente se permite y funciona casi siempre, (salvo cuando usemos const, que
	// veremos más adelante). Hay que tener presente que aquí, primero se reserva lugar 
	// en memoria para altura conteniendo basura y luego se le asignan los 
	// valores que vienen en los parámetros del constructor.
	Poste( int a )  {
	    altura = a;
	}

	// La siguiente sería la manera más correcta de inicializar los atributos de un 
	// objeto. En este caso, altura nunca contienen basura, sino que 
	// directamente se crean en memoria con el valor que viene en el parámetro del constructor.
	Poste::Poste( int a ) : altura( a )  {  }

	Poste::Poste() : altura( 0 )  {  }


**El puntero this**

- Es un puntero que ya se exite dentro del ámbito de una clase y apunta al propio objeto instanciado.
- Se utiliza para acceder a los atributos y métodos.

.. code-block::

	#include <iostream>
	
	class Poste  {
	private:
	    int altura;
		
	public:
	    Poste( int altura ) : altura( altura )  {  }
	    
	    int getAltura()  {
	        return this->altura;
	    }

	    void setAltura( int altura )  {
	        this->altura = altura;
	    }

	};


	int main()  {
	    Poste poste;

	    std::cout << "Altura: " << poste.getAltura() << std::endl;
	    
	    return 0;
	}
	

**Destructor**

.. code-block::

	Poste::~Poste()  {
	    this->altura = 0;
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

