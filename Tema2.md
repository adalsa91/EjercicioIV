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
