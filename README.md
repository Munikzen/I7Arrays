# I7Arrays
Entrega de I7 Arquitectura de computadoras UAM-C 2022

Esta biblioteca nos va a permitir manejar un arreglo a través de 3 funciones, para poder utilizar estas, se pide al usuario que en su programa principal un arreglo de tamaño predefinido por el usuario. 

Una biblioteca dinamica nos va a permitir usarla en diferentes ejecutables a la vez, mientras se añada en la cabecera en el codigo de nuestro programa, para que este funcionamiento se cumpla, nuestra biblioteca se debe agregar a las carpeta system32 de windows o en sus variables de entorno.

Para compilar una biblioteca estatica debemos:

1.	Primero debemos obtener el código objeto de los archivos que queremos, en este caso los comandos serían: 

g++ -c .\src\borrarElemento.cc -o .\obj\borrarElemento.o -I .\include
g++ -c .\src\insertarElemento.cc -o .\obj\insertarElemento.o -I .\include
g++ -c .\src\llenarCadena.cc -o .\obj\llenarCadena.o -I .\include

Tenemos que -c es para obtener el código objeto del archivo que se encuentra en la carpeta .\src\nombre del archivo.cc, mientras que -o indica la salida, ósea que la salida es se guardará en el directorio .\obj\Nombre del archivo.o, y -I indica los directorios donde se encuentran las cabeceras.

2.	Posteriormente se utiliza el comando ar crs .\lib\static\arrays.lib .\obj\*.o que sirve para compactar los archivos objetos creados anteriormente en un único archivo .lib

3.	Con el siguiente comando se realiza la compilación del ejecutable para una biblioteca estática g++ main.cc -o app\test -I .\lib\include -L .\lib\static -larrays donde main.cc es el archivo a compilar.

4.	Finalmente se ejecuta el ejecutable con el comando .\app\test.exe

Para compilar una biblioteca dinamica debemos:

1.	Primero debemos obtener el código objeto de los archivos que queremos, en este caso los comandos serían: 

g++ -c .\src\borrarElemento.cc -o .\obj\borrarElemento.o -fPIC
g++ -c .\src\insertarElemento.cc -o .\obj\insertarElemento.o -fPIC
g++ -c .\src\llenarCadena.cc -o .\obj\llenarCadena.o -fPIC

donde -fPIC sirve para indicarle al compilador que las direcciones de estos objetos no van a depender del código que invoque esta biblioteca.

2.	Para crear la biblioteca dinámica a partir de los códigos objetos que se hayan diseñado se utiliza el comando g++ -shared .\obj\*.o -o arrays.dll donde -share es compartido, los archivos objeto que en este ejemplo fueron usados se encuentran en el directorio  .\lib\obj\ y como todos tienen la extensión .o se coloca \lib\obj\*.o, por último -o arrays.dll será el nombre de la biblioteca con .dll siendo la extensión de una biblioteca dinámica

3.	para compilar el ejecutable con una biblioteca dinámica se usa el comando g++ .\main.cc -o executable -L .\lib\dinamic -l arrays donde -L es para indicar la ruta donde se encuentra la biblioteca que contiene las funciones que se están invocando y -l es para indicar el nombre de la biblioteca.

4.	Finalmente se ejecuta el ejecutable para ambos casos, tanto para la biblioteca dinámica como para la estática con el comando .\executable.exe y después los parámetros que se usarán para el funcionamiento de la aplicación.

Arbol del directorio:
    *.
	
	├── app
	
	├── include
	
	│   └── arrays
	
	├── lib
	
	│   └── static
	
	├── main.cc
	
	├── obj
	
	└── src
	
    		├── borrarElemento.cc
		
    		├── insertarElemento.cc
		
    		├── llenar.cc
		
 Para ejemplificar el siguiente codigo:
 
 ~~~
 int main()
{
    int n[5];

    llenar(5, n, 3);
    insertarElemento(5, n, 30, 2);
    borrarElemento(5, n, 3);
    for (int i = 0; i < 5; i++)
    {
        std::cout << "n[" << i << "]:" << n[i] << std::endl;
    }

    return 0;
}
~~~
