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
