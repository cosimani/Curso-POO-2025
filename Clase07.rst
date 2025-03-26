.. -*- coding: utf-8 -*-

.. _rcs_subversion:

Clase 07 - POO 2025
===================
(Fecha: 26 de marzo)


Registro en video de algunos temas de la clase de hoy
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

`Dibujar a mano - QByteArray - Preprocesador 2021 <https://www.youtube.com/watch?v=8Gu5_ejipus>`_



Macro Q_OBJECT
^^^^^^^^^^^^^^

- Convierte a una clase cualquiera en una clase Qt.
- Una clase Qt permitirá trabajar con signals y slots.
- Incluir la macro Q_OBJECT en la primer línea de la definición de la clase.


QGridLayout
^^^^^^^^^^^

- Ubica los widgets en una grilla
- Con setColumnMinimumWidth() podemos setear el ancho mínimo de columna
- Separación entre widget con setVerticalSpacing( int )
- void addWidget( QWidget * widget, int fila, int columna, int spanFila, int spanCol )



QLineEdit
^^^^^^^^^

.. code-block::

	QLineEdit * le = new QLineEdit;
	le->setEchoMode( QLineEdit::Password );
	le->setEnabled( false );

	// QLineEdit::Normal  // Se visualizan al escribir
	// QLineEdit::NoEcho  // No se visualiza nada
	// QLineEdit::Password  // Se escribe como asteriscos
	// QLineEdit::PasswordEchoOnEdit  // Se escribe normal y al dejar de editar se convierten en asteriscos

**Señales**

.. code-block::

	// void returnPressed()  // Detecta cuando el usuario presiona Enter.

	// void editingFinished()  // Cuando pierde foco.

	// void textChanged( const QString & text )  // Texto modificado por código o por usuario desde la gui.

	// void textEdited( const QString & text )  // Sólo por el usuario.



Dibujar a mano sobre un QWidget
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block::

	// mapa.h
	#include <QWidget>

	class Mapa : public QWidget  {
	    Q_OBJECT

	public:
	    Mapa()  {  }

	protected:
	    void paintEvent( QPaintEvent * );

	};

	// mapa.cpp
	#include "mapa.h"
	#include <QPainter>

	void Mapa::paintEvent( QPaintEvent * )  {
	    QPainter painter( this );
	    painter.drawLine( 0, 0, this->width(), this->height() );
	}

**Clase QPainter**

- Pinta a bajo nivel sobre widgets.
- Debe ser utilizado dentro del método ``paintEvent( QPaintEvent * )``.

.. code-block::

	void drawEllipse( int x, int y, int ancho, int alto );
	void drawImage( int x, int y, QImage & image );
	void drawLine( int x1, int y1, int x2, int y2 );
	void drawText( int x, int y, QString & text );
	void fillRect( int x, int y, int ancho, int alto );





Ejercicio 5:
============

- En un Empty qmake Project
- En la función main crear un objeto de la clase QLabel y pegarle en el mismo objeto QLabel una imagen de alta resolución.
- Que la imagen se obtenga desde un archivo JPG del disco duro
- Mostrar el QLabel de forma maximizada y que la imagen no se deforme.
- Al cabo de 3 segundos, el QLabel y la aplicación se deberá cerrar


Ejercicio 6:
============

- Diseñar un login con QGridLayout.
- Usar asteriscos para la clave.
- Detectar Enter para simular la pulsación del botón.
- Definir la clase Formulario que será un QWidget
- Formulario tendrá QLabels y QLineEdits para Legajo, Nombre y Apellido, y un QPushButton
- Si la clave ingresada es admin:1111, se cierra Login y se muestra Formulario
- Si se ingresa otra clave se borrará el texto del QLineEdit de la clave.


Ejercicio 7:
============

.. figure:: imagenes/ejercicio_captcha.jpg


Ejercicio 8:
============

- Tener disponible un endpoint con FastAPI para validar usuarios.
- Registrar en MySQL algunos usuarios en una tabla con campos como: nombre, apellido, usuario, clave, mail




Aclaraciones:
=============

- Todos los ejercicios tienen que ser actualizados en un repositorio en GitHub en carpetas ejercicio01, ejercicio02, ...
- Que cada ejercicio debe contener todo lo necesario para poder compilarlo y ejecutarlo.
- Excluir los archivos y carpetas que no sean necesarios, como es el archivo con extensión .pro.user y la carpeta build-
- Escribir el README con instrucciones para la ejecución de los ejercicios
- Enviar un mail a cesarosimani@gmail.com con la URL del repositorio.







