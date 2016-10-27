#Tema 2

##Ejercicio 1

###Instalar alguno de los entornos virtuales de node.js (o de cualquier otro lenguaje con el que se esté famil 59iarizado) y, con ellos, instalar la última versión existente, la versión minor más actual de la 4.x y lo mismo para la 0.11 o alguna impar (de desarrollo).

Para la realización de de este ejercicio se usara la herramienta **virtualenv** usada para crear entornos virtuales de desarrollo aislados para Python.
En primer lugar instalamos **virtualenv** usando el instalador de paquetes Python **pip**.

![Instalando virtualenv](https://www.dropbox.com/s/w15xukb5l45cju8/Tema2_1.png?dl=1 "Instalando virtualenv")

Para crear un nuevo entorno virtual se utiliza el siguiente comando:

    $ virtualenv ENV

**ENV** es el directorio donde se alojara el nuevo entorno virtual(lib, include y bin).

Como ejemplo crearemos un entorno virtual para Python3 con el siguiente comando:

    virtualenv --python=python3 py3

![Creando entorno virtual con virtualenv](https://www.dropbox.com/s/e21xlwuug9wiw4x/Tema2_2.png?dl=1 "Creando entorno virtual con virtualenv")

Para activar el entorno virtual utilziamos el comando **source** de bash para que interprete el archivo **bin/activate** del nuevo entrono virtual.

![Acticando entorno virtual](https://www.dropbox.com/s/ycwr5yov4sta8mp/Tema2_3.png?dl=1)

Para salir del entorno virtual se usa el comando **deactivate**.


##Ejercicio 2

###Como ejercicio, algo ligeramente diferente: una web para calificar las empresas en las que hacen prácticas los alumnos. Las acciones serían 
* Crear empresa
* Listar calificaciones para cada empresa
* Crear calificación y añadirla (comprobando que la persona no la haya añadido ya) 
* Borrar calificación (si se arrepiente o te denuncia la empresa o algo)
* Hacer un ránking de empresas por calificación, por ejemplo. 
* Crear un repositorio en GitHub para la librería y crear un pequeño programa que use algunas de sus funcionalidades. 

Si se quiere hacer con cualquier otra aplicación, también es válido.



Para la realización de esta web he utilizado el framework Django, el código de la web se encuentra en [GitHub](https://github.com/adalsa91/IV_Calificar_Empresas)


##Ejercicio 3

###Ejecutar el programa en diferentes versiones del lenguaje. ¿Funciona en todas ellas?

El programa se desarrollo para Python 2.7.6, para la prueba que se pide en este ejercicio creé un entorno virtual con los requisitos del anterior pero para la versión 3.4.4 de Python, al ejecutar e intentar cargar la página web aparece un error al importar los modelos, este error se debe a que en Python 3 no se puede importar con rutas relativas implícitas dentro de los paquetes ([pep-0404](https://www.python.org/dev/peps/pep-0404/#imports)); para subsanar este problema basta con modificar la siguiente linea:
``` python
from models import Empresa, Alumno
```

por esta otra en la que se utiliza una ruta relativa explicita:

``` python
from .models import Empresa, Alumno
```
Una vez realizado este cambio la aplicación funciona correctamente.

##Ejercicio 4
###Crear una descripción del módulo usando package.json. En caso de que se trate de otro lenguaje, usar el método correspondiente.

En mi caso el lenguaje usado ha sido Python, por lo que utilizaré la biblioteca **SetupTools** para describir el módulo.


``` python

from setuptools import setup

setup(
    name='Calificar Empresas',
    version='0.1',
    description='Aplicación para valorar empresas de prácticas.',
    url='https://github.com/adalsa91/IV_Calificar_Empresas',
    author='Adrián Álvarez Sáez',
    author_email='adalsa91@gmail.com',

    license='GNU GPLv3',

    classifiers=[
        'Environment :: Web Environment',
        'Framework :: Django',
        'Framework :: Django :: 1.8',
        'Intended Audience :: Education',
        'Development Status :: 3 - Alpha',
        'Topic :: Internet :: WWW/HTTP',
        'Topic :: Internet :: WWW/HTTP :: Dynamic Content',
        'License :: OSI Approved :: GNU General Public License v3 (GPLv3)',
        'Operating System :: OS Independent',
        'Programming Language :: Python',
        'Programming Language :: Python :: 3',
        'Programming Language :: Python :: 3.4',

    ],
    install_requires=[
        'Django==1.8.5',
        'sqlite3',
    ],

    keywords='education companies students practice',
)

```

##Ejercicio 5
###Automatizar la generación de documentación de la librería que se cree.

Para este apartado he usado el generador de documentación [Sphinx](http://www.sphinx-doc.org/es/stable/index.html). Para empezar a trabajar con él podemos instalarlo con **pip**:

``` bash
	$ pip install Sphinx
```

Para que funcione correctamente al documentar un proyecto python debemos añadir las siguientes lineas al fichero de configuración **conf.py** de *Sphinx*:

```python
	from django.conf import settings
	settings.configure()

```

La documentación generada se alamacena en el directorio [docs](https://github.com/adalsa91/IV_Calificar_Empresas/tree/master/docs) del proyecto.

En la siguiente imagen se puede ver un ejemplod e la documentación generada.

![Ejemplo de documentación](https://github.com/adalsa91/EjercicioIV/blob/master/images/tema2/ejercicio5_1.png "Ejemplo de documentación generada con Sphinx")

##Ejercicio 6
###Para la aplicación que se está haciendo, escribir una serie de aserciones y probar que efectivamente no fallan. Añadir tests para una nueva funcionalidad, probar que falla y escribir el código para que no lo haga (vamos, lo que viene siendo TDD).

Para probar el funcionamiento de los tests he creado un test sobre los models utilizados en la aplciación.

``` python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

from django.test import TestCase
from calificaciones.models import Empresa
from calificaciones.models import Alumno


class EmpresaMethodTests(TestCase):

    def test_empresa_creation(self):
        emp = Empresa(nombre='Prueba')
        emp.save()

        empresas = Empresa.objects.all()
        self.assertEqual(empresas.count(), 1)

        self.assertEqual(emp.nombre, 'Prueba')
        self.assertEqual(str(emp), emp.nombre)


class AlumnoMethodTests(TestCase):

    def test_alumno_creation(self):
        emp = Empresa(nombre='Prueba')
        emp.save()
        alum = Alumno(nombre='John', empresa=emp, puntuacion='8')
        alum.save()

        alumnos = Alumno.objects.all()
        self.assertEqual(alumnos.count(), 1)

        self.assertEqual(alum.nombre, 'John')
        self.assertEqual(alum.puntuacion, '8')


```

Una vez escritos los test probamos que se ejecutan correctamente con el comando `test` de la utilidad `manage.py`.

![Resultados tests](https://github.com/adalsa91/EjercicioIV/blob/master/images/tema2/ejercicio5_2.png "Resultados tests")

Ahora creamos un test para una nueva funcionalidad, por ejemplo para obtener el nombre de la empresa mejor valorada.

```python
class MejorEmpresaTests(TestCase):

    def test_get_mejor_empresa(self):
        emp1 = Empresa(nombre='Empresa1')
        emp1.save()
        emp2 = Empresa(nombre='Empresa2')
        emp2.save()
        emp3 = Empresa(nombre='Empresa3')
        emp3.save()

        alum1 = Alumno(nombre='John', empresa=emp1, puntuacion='7')
        alum1.save()
        alum2 = Alumno(nombre='Peter', empresa=emp2, puntuacion='8')
        alum2.save()
        alum3 = Alumno(nombre='Sophie', empresa=emp3, puntuacion='9')
        alum3.save()

        mejor = calificaciones.views.mejor_empresa()
        self.assertEqual('Empresa3', mejor)
```

Si ahora intentamos pasar los tests obtenemos un error debido a que la función a testear no ha implementado todavía.

![Ejemplo test fallido](https://github.com/adalsa91/EjercicioIV/blob/master/images/tema2/ejercicio5_3.png "Ejemplo de test fallido")

Ahora implementamos la función para resolver el problema.

```python
def mejor_empresa():
    """Comprueba cual es la empresa con mayor puntuación.

    Busca cual es la empresa con mayor puntuación y devuelve su nombre.

    Returns:
    String con el nombre de la empresa con mejor puntuación.
    """
    puntuacion = 0
    for alumno in Alumno.objects.all():
        if alumno.puntuacion > puntuacion:
            puntuacion = alumno.puntuacion
            nombre = alumno.empresa.nombre

    return nombre

```

##Ejercicio 7
###Convertir los tests unitarios anteriores con assert a programas de test y ejecutarlos desde mocha, usando descripciones del test y del grupo de test de forma correcta. Si hasta ahora no has subido el código que has venido realizando a GitHub, es el momento de hacerlo, porque lo vas a necesitar un poco más adelante.

Django incluye su propio [marco de testeo](https://docs.djangoproject.com/es/1.10/topics/testing/tools/) gestionado desde la utilidad **manage.py** usando el comando **test** que ejecuta los **test.py** que encuentra en cada paquete.

```bash
	manage.py test
```