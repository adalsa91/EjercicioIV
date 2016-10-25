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
