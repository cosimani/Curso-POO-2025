.. -*- coding: utf-8 -*-

.. _rcs_subversion:

Clase 16 - POO 2025
===================
(Fecha: 21 de abril)



Registro en video de algunos temas de la clase de hoy
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

`Función virtual pura clase abstracta 2021 <https://youtu.be/LjxmhcdzZbs>`_

`SQLite, AdminDB y función virtual pura 2023 <https://youtu.be/sJu1Icc4rkQ>`_

`MD5 e independizar del SO 2021 <https://youtu.be/I4onYdM0Enk>`_

`Práctica con MD5 y base de datos 2021 <https://youtu.be/nLHdT_-8Afk>`_





Función virtual pura y clase abstracta
======================================

- No necesita ser definida, sólo se declara.
- Será definida en las clases derivadas

.. code-block:: c

	virtual void verValor( int a ) = 0;

- Una clase con al menos una función virtual pura la convierte en clase abstracta.
- Una clase abstracta no puede ser instanciada.
- Si en la clase derivada no se define la función virtual pura, significa que esta clase derivada también es abstracta.







Clase QCryptographicHash
^^^^^^^^^^^^^^^^^^^^^^^^

- Provee la generación de la clave hash 
- Soporta MD5, MD4 y SHA-1

.. code-block:: c

	enum Algorithm { Md4, Md5, Sha1 }

	QCryptographicHash(Algorithm metodo)

	void addData(const QByteArray & data)
	
	void reset()

	QByteArray result() const


**Método estático**

.. code-block:: c

	QByteArray hash( const QByteArray & data, Algorithm metodo )


**Otros métodos útiles**

.. code-block:: c

	QByteArray QByteArray::toHex()
	// Devuelve en hexadecimal
	// Útil para enviar por url una clave hash MD5
	// Hexadecimal tiene sólo caracteres válidos para URL

**Ejemplo**: Obtener MD5 de la clave ingresada en un QlineEdit:

.. code-block:: c

	QcryptographicHash::hash( leClave->text().toUtf8(), QCryptographicHash::Md5 ).toHex()
	


**Calculadora MD5 online**

http://www.md5.cz/



**Para independizar del SO**

.. code-block:: c

	AdminDB adminDB;
	QString nombreSqlite;

	#ifdef __APPLE__
	    nombreSqlite = "/home/cosimani/db/test";
	#elif __WIN32__
	    nombreSqlite = "C:/Qt/db/test";
	#elif __linux__
	    nombreSqlite = "/home/cosimani/db/test";
	#else
	    nombreSqlite = "/home/cosimani/db/test";
	#endif

	if ( adminDB.conectar( nombreSqlite ) )
	    qDebug() << "Conexion exitosa";


**Algunas explicaciones sobre base de datos** 


- `Crear base de datos <https://www.youtube.com/watch?v=U9iE6pM0bxM>`_

- `Crear tabla <https://www.youtube.com/watch?v=_-hKca2k784>`_

- `Insertar registro <https://www.youtube.com/watch?v=RggFhFZnCPU>`_

- `Consultar datos <https://www.youtube.com/watch?v=8emd37mvN2E>`_


**Ejemplo de método mostrarTabla para la clase AdminDB**

.. code-block:: c

	#ifndef ADMINDB_H
	#define ADMINDB_H

	#include <QObject>
	#include <QSqlDatabase>

	class AdminDB : public QObject
	{
	    Q_OBJECT
	public:
	    explicit AdminDB( QObject * parent = 0 );
	    ~AdminDB();

	    bool conectar( QString archivoSqlite );
	    QSqlDatabase getDB();
	    bool isConnected();
	    void mostrarTabla( QString tabla );

	private:
	    QSqlDatabase db;
	};

	#endif // ADMINDB_H


.. code-block:: c

	#include "admindb.h"
	#include <QDebug>
	#include <QSqlQuery>
	#include <QSqlRecord>

	AdminDB::AdminDB( QObject * parent ) : QObject( parent )  {
	    qDebug() << "Drivers disponibles:" << QSqlDatabase::drivers();

	    db = QSqlDatabase::addDatabase( "QSQLITE" );
	}

	AdminDB::~AdminDB()  {
	    if ( db.isOpen() )
	        db.close();
	}

	bool AdminDB::conectar( QString archivoSqlite )  {
	    db.setDatabaseName( archivoSqlite );

	    return db.open();
	}

	QSqlDatabase AdminDB::getDB()  {
	    return db;
	}

	bool AdminDB::isConnected()  {
	    return db.isOpen();
	}

	void AdminDB::mostrarTabla( QString tabla )  {
	    if ( this->isConnected() )  {
	        QSqlQuery query = db.exec( "SELECT * FROM " + tabla );

	        if ( query.size() == 0 || query.size() == -1 )
	            qDebug() << "La consulta no trajo registros";

	        while( query.next() )  {
	            QSqlRecord registro = query.record();  // Devuelve un objeto que maneja un registro (linea, row)
	            int campos = registro.count();  // Devuleve la cantidad de campos de este registro

	            QString informacion;  // En este QString se va armando la cadena para mostrar cada registro
	            for ( int i = 0 ; i < campos ; i++ )  {
	                informacion += registro.fieldName( i ) + ":";  // Devuelve el nombre del campo
	                informacion += registro.value( i ).toString() + " - ";
	            }
	            qDebug() << informacion;
	        }
	    }
	    else
	        qDebug() << "No se encuentra conectado a la base";
	}


Ejercicio 16
============

- Un Login con QtDesigner validando usuarios de una base de datos sqlite
- Que lea de la base de datos el último usuario logueado exitosamente y mantenerlo en el campo usuario luego de cerrar la aplicación.
- La clave en la base de datos deberá almacenarse en MD5.

 