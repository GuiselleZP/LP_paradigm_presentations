[link de la presentación en youtube](https://www.youtube.com/watch?v=Qb0_xnTgibI)
# Programación Paralela

## Introducción

Surge porque es natural pensar en paralelo en ciertos procesos cotidianos.

## Filosofía del paradigma

**Serializar:** Dividir un problema muy grande en tareas a las que se le asigna
un número de secuencia y son atendidas una destrás de la otra por un procesador

**Parametrizar:** Dividir un problema muy grande en problemas más pequeñas que
puedan ser ejecutadas concurrentemente, que a su vez son divididos en tareas
más pequeñas y son ejecutadas por varios procesadores en un mismo periodo de
tiempo. Los recursos pueden estar asignados de 2 formas distintas:

* Una única máquina ejecutando procesos en 8 nucleos distintos.
* Un número arbitrario de máquinas conectadas entre sí a través de una red.

## Conceptos clave

Lo fundamental en un algoritmo son:

* **Tareas:** Opera sobre los datos (modificandolos o creandolos), en la
computación paralela deben ser administradas y coordinadas, se debe tener
cuidado con la **dependencia** entre los datos y las de control
	* **Dependencia de datos:** Una tarea no puede ser ejecutada antes de la
	otra.
	* **Dependencia de control:** Sucede cuando hay una sentencia que evalúa
	una condición y otras sentencias cuya ejecución dependen del resultado de 
	dicha evaluación.
* **Datos:** 
* **Hilos:** Son un proceso liviano que ayuda a la realización de un proceso
más pesado, se comunican entre ellos a través una memoria global. 
* **Granularidadi:** Se refiere al tamaño de cada tarea y la granularidad entre
ellas.
	* **Granularidad gruesa:** Pocas tareas que tienen mucho trabajo entre 
	ellas, hay poca dependencia entre las tareas. No necesita gran 
	sincronización.
	* **Granularidad fina:** Muchas tareas que tienen poco trabajo y hay mucha
	dependencia entre ellas. Necesitan gran sincronización.
* **Sincronización:** En qué momento realizo las tareas para satizfacer las
dependencias.
* **Scheduling:** Si hay varios procesos que se pueden realizar inmediatamente
se le deben asignar los recursos computacionales necesarios, este trabajo lo
realiza el scheduling.
* **Grafo computacional y sección crítica:** El grafo computacional es un grafo
que representa la secuencia de las tareas a realizar en un programa y la
sección critica es el camino más largo que existe y que debe ser recorrido a la
hora de ejecutar el programa.
* **Ley de ahmdal:** Indica que tanto se puede mejorar la velocidad de 
ejecución de un programa, limitandolo con el porcentaje del programa que pueda
ser ejecutado en paralelo.
* **Condiciones de carrera:** Busca evitar que dos tareas que se ejecutan al
tiempo quieran escribir en el mismo espacio de memoria al mismo tiempo.

## Ventajas y Desventajas
