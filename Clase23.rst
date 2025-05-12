.. -*- coding: utf-8 -*-

.. _rcs_subversion:

Clase 23 - POO 2025
===================
(Fecha: 12 de mayo)



Registro en video de algunos temas de la clase de hoy
=====================================================


`inline 2021 <https://youtu.be/HbI7Dws-sYg>`_



Funciones inline
================

- Cuando decimos que llamamos a una función es porque salta, ejecuta y retorna.
- Una función inline inserta su código.
- Ventaja de ejecutarse más rápidamente.
- Como desventaja tenemos un programa generado más extenso.

.. code-block:: c

	#include <QDebug>
	#include <QApplication>

	inline int calculo( int a, int b )  {
	    return a/2+b;
	}

	int main( int argc, char ** argv )  {
	    QApplication a( argc, argv );

	    int x=2, y=3, z=0;
	    z = calculo( x, y );

	    return 0;
	}

**Funciones miembro inline dentro de clases**

- Un método se declara dentro del cuerpo de la clase y se puede definir dentro o fuera
- Si se declara y define dentro, se denomina función inline. En este caso, no hace falta indicar con inline (está implícito).
- Si se define fuera, deberá indicar inline. De lo contrario será offline.
- Se recomienda usar funciones inline para funciones pequeñas y de uso frecuente.

.. code-block:: c

	#include <QDebug>
	#include <QApplication>

	class ClaseA  {
	private:
	    int x;
	    int y;

	public:
	    ClaseA() : x( 10 ), y( 20 )  {  }
	    int getX()  {  return x;  }     // inline implícito
	    int getY();
	};

	inline int ClaseA::getY()  {
	    return y;
	}

	int main( int argc, char ** argv )  {
	    QApplication a( argc, argv );

	    ClaseA cA;
	    qDebug() << cA.getX();
	    qDebug() << cA.getY();

	    return 0;
	}
	



Ejercicio 22:
=============

Inline en acción — Simulador de Sensor Inteligente
--------------------------------------------------

Implementar una clase que simule un sensor, aplicando funciones frecuentes tanto en versión ``inline`` como ``offline``, y luego comparar el rendimiento al ejecutar esas funciones **millones de veces**.


Parte 1: Diseño de la clase ``Sensor``
--------------------------------------

Implementar una clase ``Sensor`` con las siguientes características:

**Atributos:**

- ``int valorActual`` → puede inicializarse con un valor aleatorio entre 0 y 1023.

**Métodos:**

- ``int getValorBruto()`` → devuelve el valor actual sin modificar. Definir **dentro de la clase** (será ``inline`` implícito).
- ``int getValorBrutoOffline()`` → igual que el anterior, pero definir **fuera** de la clase sin usar ``inline`` (será una función normal).
- ``double getValorNormalizado()`` → devuelve ``valorActual / 1023.0``. Definir como ``inline`` explícito.
- ``double getValorNormalizadoOffline()`` → igual que el anterior, pero sin ``inline``.


Parte 2: Benchmark de rendimiento (Prueba de rendimiento)
---------------------------------------------------------

Utilizar ``QElapsedTimer`` para medir el tiempo de ejecución de:

- Ejecutar **10 millones de veces** la llamada a ``getValorBruto()``.
- Ejecutar **10 millones de veces** la llamada a ``getValorBrutoOffline()``.
- Ejecutar **10 millones de veces** la llamada a ``getValorNormalizado()``.
- Ejecutar **10 millones de veces** la llamada a ``getValorNormalizadoOffline()``.

Mostrar los tiempos en consola con ``qDebug()``.

