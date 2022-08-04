# I7Arrays
Entrega de I7 Arquitectura de computadoras UAM-C 2022

Para compilar una biblioteca estatica debemos:

1.	Primero debemos obtener el código objeto de los archivos que queremos, en este caso los comandos serían 
g++ -c .\src\borrarElemento.cc -o .\obj\borrarElemento.o -I .\include
g++ -c .\src\insertarElemento.cc -o .\obj\insertarElemento.o -I .\include
g++ -c .\src\leeCadena.cc -o .\obj\leeCadena.o -I .\include
g++ -c .\src\leeCantidadElem.cc -o .\obj\leeCantidadElem.o -I .\include
g++ -c .\src\muestraCadena.cc -o .\obj\muestraCadena.o -I .\include
Tenemos que -c es para obtener el código objeto del archivo que se encuentra en la carpeta .\src\nombre del archivo.cc, mientras que -o indica la salida, ósea que la salida es se guardará en el directorio .\obj\Nombre del archivo.o, y -I indica los directorios donde se encuentran las cabeceras.

2.	Posteriormente se utiliza el comando ar crs .\lib\static\arrays.lib .\obj\*.o que sirve para compactar los archivos objetos creados anteriormente en un único archivo .lib

3.	Con el siguiente comando se realiza la compilación del ejecutable para una biblioteca estática g++ main.cc -o app\test -I .\lib\include -L .\lib\static -larrays donde main.cc es el archivo a compilar.
4.	Finalmente se ejecuta el ejecutable con el comando .\app\test.exe
y después los parámetros que se usarán para el funcionamiento de la aplicación.


Para compilar una biblioteca dinamica debemos:

1.	Primero debemos obtener el código objeto de los archivos que queremos, en este caso los comandos serían 
g++ -c .\src\borrarElemento.cc -o .\obj\borrarElemento.o -fPIC
g++ -c .\src\insertarElemento.cc -o .\obj\insertarElemento.o -I .\include
g++ -c .\src\leeCadena.cc -o .\obj\leeCadena.o -I .\include
g++ -c .\src\leeCantidadElem.cc -o .\obj\leeCantidadElem.o -I .\include
g++ -c .\src\muestraCadena.cc -o .\obj\muestraCadena.o -I .\include
donde -fPIC sirve para indicarle al compilador que las direcciones de estos objetos no van a depender del código que invoque esta biblioteca.

2.	Para crear la biblioteca dinámica a partir de los códigos objetos que se hayan diseñado se utiliza el comando g++ -shared .\obj\.o -o arrays.dll donde -share es compartido, los archivos objeto que en este ejemplo fueron usados se encuentran en el directorio  .\lib\obj\ y como todos tienen la extensión .o se coloca \lib\obj\.o, por último -o arithmetic.dll será el nombre de la biblioteca con .dll siendo la extensión de una biblioteca dinámica

3.	para compilar el ejecutable con una biblioteca dinámica se usa el comando g++ .\main.cc -o executable -L .\lib\dinamic -l arrays donde -L es para indicar la ruta donde se encuentra la biblioteca que contiene las funciones que se están invocando y -l es para indicar el nombre de la biblioteca.

4.	Finalmente se ejecuta el ejecutable para ambos casos, tanto para la biblioteca dinámica como para la estática con el comando .\executable.exe y después los parámetros que se usarán para el funcionamiento de la aplicación.
