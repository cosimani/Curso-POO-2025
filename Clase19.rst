.. -*- coding: utf-8 -*-

.. _rcs_subversion:

Clase 19 - POO 2025
===================
(Fecha: 30 de abril)


Registro en video de algunos temas de la clase de hoy
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

`Sobrecarga de operadores 2021 <https://youtu.be/QGTNAjeRdNg>`_

`Singleton 2021 <https://youtu.be/RNAZ0pu-Ybc>`_


Sobrecarga de operadores 
========================

- Supongamos los siguientes objetos de la clase Poste:

.. code-block:: c

	Poste p1;  // Su único miembro dato es un float para la altura del Poste
	Poste p2;

- Necesitamos unir estos Postes para obtener un único Poste con sus alturas sumadas.
- ¿Podemos hacer lo siguiente?

.. code-block:: c

	Poste unidos = p1 + p2;

**Otro ejemplo**

.. code-block:: c

	class Cliente  {
	private:
	    int saldo;

	public:
	    Cliente() : saldo( 0 )  {
	    }

	    void operator+( int sumando )  {
	        this->saldo += sumando;
	    }

	    void operator-( int sustraendo )  {
	        this->saldo -= sustraendo;
	    }

	    bool operator<( Cliente otroCliente )  {
	        if ( this->saldo < otroCliente.saldo )
	            return true;
	        return false;
	    }
	};

	int main( int argc, char ** argv )  {
	    Cliente juan;

	    Cliente carlos;

	    juan + 50;  // Suma 50 a su cuenta

	    carlos + 100;  // Quita 100 a carlos

	    if ( juan < carlos )  {
	        qDebug() << "juan tiene menos";
	    }

	    return 0;
	}




Singleton
=========

- Un singleton es un patrón de diseño que restringe la creación de instancias de una clase a una única instancia.


Ejemplo de AdminDB como singleton
=================================

.. code-block:: c

	#ifndef ADMINDB_H
	#define ADMINDB_H

	class AdminDB  {

	private:
	    static AdminDB * instancia;
	    AdminDB();

	public:
	    static AdminDB * getInstancia();

	    void conectar();
	};

	#endif // ADMINDB_H


.. code-block:: c

	#include "admindb.h"
	#include <QDebug>

	AdminDB * AdminDB::instancia = nullptr;

	AdminDB::AdminDB()  {
	}

	AdminDB * AdminDB::getInstancia()  {
	    if( instancia == nullptr )  {
	        instancia = new AdminDB;
	    }
	    return instancia;
	}

	void AdminDB::conectar()  {
	    qDebug() << "La base se encuentra conectada...";
	}


.. code-block:: c

	#include "admindb.h"

	int main( int, char ** )  {

	    AdminDB::getInstancia()->conectar();

	    return 0;
	}





Ejercicio 19:
=============


Simulacro de Parcial - Gestión de medicamentos por Obra Social
---------------------------------------------------------------

Desarrollar una aplicación de escritorio con C++ y Qt que permita gestionar las cajas de medicamentos entregadas a una *única obra social* (por ejemplo: **"APROSS"**), respetando un límite máximo de **1000 dosis en total**.

La aplicación debe ser realizada únicamente con **QWidget** (no usar QMainWindow), y debe almacenar la información en una base de datos SQLite. La clase que gestiona la base de datos (`AdminDB`) debe implementarse como **singleton**.

Requisitos
^^^^^^^^^^

- Clase `CajaMedicamento`:
  
  - Atributos:
    - `int id` → autogenerado por la base de datos
    - `float dosisTotales`
  
  - Métodos:
    - Constructor para crear una nueva caja (sin ID)
    - Constructor para cargar una caja desde la base (`id`, `dosis`)
    - `CajaMedicamento operator+(const CajaMedicamento & otra) const` → suma de dosis
    - `bool operator==(const CajaMedicamento & otra) const` → compara si tienen misma cantidad de dosis
    - `QString toString() const` → retorna una cadena del estilo:
      
      .. code-block:: cpp

         CajaMedicamento [ID: 4, Dosis: 250.0]

- Clase `AdminDB` (singleton):
  
  - Métodos requeridos:
    - `void conectar();`
    - `bool insertarCaja(float dosis);` → solo si la suma total no excede 1000
    - `QList<CajaMedicamento> obtenerTodas();`
    - `float obtenerTotalDosis();`

- Base de datos SQLite:
  
  Tabla `cajas_medicamentos` con la siguiente estructura:

  .. code-block:: sql

     CREATE TABLE cajas_medicamentos (
       id INTEGER PRIMARY KEY AUTOINCREMENT,
       dosis_totales REAL NOT NULL
     );

- Interfaz gráfica:
  
  - Ingreso de cantidad de dosis por caja (`QDoubleSpinBox`)
  - Botón **Agregar**:
    - Verifica que la dosis ingresada no exceda el total permitido (1000)
    - Si se excede, muestra advertencia con `QMessageBox`
  - Lista de cajas cargadas (`QListWidget`)
  - Botón **Sumar**:
    - Combina dos cajas seleccionadas (usando `operator+`)
    - Solo permite agregar si la suma no excede 1000
  - Botón **Comparar**:
    - Compara si dos cajas seleccionadas tienen la misma cantidad (usa `operator==`)
    - Muestra resultado por consola con `qDebug()`

Restricciones
^^^^^^^^^^^^^

- ❌ No usar `QMainWindow`
- ❌ No usar `QPixmap`
- ❌ No usar lambdas ni punteros a funciones para `connect()`
- ✅ Usar `SIGNAL()` y `SLOT()` para señales y slots
- ✅ Usar `QWidget` como contenedor principal
- ✅ Usar `AdminDB` como singleton
- ✅ Usar SQLite con `QSqlDatabase`
