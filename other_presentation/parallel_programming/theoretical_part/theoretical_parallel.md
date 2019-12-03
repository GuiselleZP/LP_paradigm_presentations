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
	* **dependencia de datos:** Una tarea no puede ser ejecutada antes de la
	otra.
	* **dependencia de control:** Sucede cuando hay una sentencia que evalúa
	una condición y otras sentencias cuya ejecución dependen del resultado de 
	dicha evaluación.
* **Datos**
