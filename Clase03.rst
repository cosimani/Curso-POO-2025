.. -*- coding: utf-8 -*-

.. _rcs_subversion:

Clase 03 - POO 2025
===================
(Fecha: 14 de marzo)


Registro en video de algunos temas de la clase de hoy
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

`Clases 2021 <https://www.youtube.com/watch?v=dH0WqMW3-_w>`_ 




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
	
	
