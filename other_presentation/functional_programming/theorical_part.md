[Link del video en youtube](https://www.youtube.com/watch?v=_axwVUoq1Yg)

# Programación Funcional

La programación funcional es un paradigma de programación **declarativo**, que tiene como núcleo el concepto matemático de *función*. 

En este paradigma se utilizan las funciones para dar orden y estructura a los problemas planteados. Un *función* es la relación de dos conjuntos, es decir una asociación de cada elemento de un conjunto a otro.

[](./images/image1.png)

El concepto de funcion en este paradigma, es totalmente diferente a los otros donde se definen las funciones como procedimientos, operaciones, metodos o rutinas. 

[](./images/image1.png)

Dentro del paradigma de programación funcional  las funciones pueden afectar el estado de un programa, permitiendo que al evaluar una función se obtengan valores diferentes en diferentes evaluaciones(sin embargo esto no se debe dar en la prog funcional), dentro de este paradigma se define el concepto de transferencia referencial para indicar que cada valor de entrda siempre va a tener la misma salida; otros conceptos que son definidos dentro del paradigma son composicion de funciones y funciones de orden superior (admiten como entrada o como salida funciones).

**transferencia referencial** :una expresión puede ser sustituida directamente por su valor sin que esto afecte a la ejecución del programa.

*Para diferencia las funciones declaradas en este paradigma que pueden tener problemas de coherencia para tratar los datos, se les conoce a las funciones matematicas como funciones puras y estas deben evitar el uso de efectos secundarios*.

#### Efectos secundarios (visibles fuera del contexto de ejecucion de una función)
* **Operaciones de entrada y salida** : Ej. imprimir el resultado de una operación (funcion *imprimir* externa de la funcion que se esta declarando)
* **La generación de números aleatorios.**
* **cambio de estado global o local**.

## Principios 
(Uno de los principios del paradigma es hacer que las funciones sean lo más específicas posible. De esta manera se cumple otro de los principios de este paradigma: la reutilizacion de código -pues, como veremos, las funciones retornarán lo mismo siempre a lo largo de toda la ejecución del programa-.)

* El programa es una funcion.
* Nada de estado compartido: Ya no habrán variables globales ni parámetros accesibles a cualquier función, todo va a depender de las entradas de las funciones.
* Las estructuras de datos son inmutables: No se tendrian estructuras del tipo lista, porque serian su uso ocasionaria efectos secundarios y el programa no seria predecible.
* Los efectos secundarios deben ser aislados y encapsuldos.
* Las funciones deben ser tratadas como ciudadanos de primera clase.

#### Funciones de primera clase.

Una entidad de un lenguaje de programación es considerada de primera clase si cumple con estas condiciones:
* Puede ser argumento de una función.
* Puede ser el valor retornado por una función.
* Puede ser declarado como variable.
* Puede ser comparado con otras entidades		
    
### Calculo Lambda 
###### (formulado por Alonzo Church - 1930) *base fundamental del paradigma*

[](./images/image3.png)

se basa en tres reglas
* Uso de variables.
* Abstracion: forma de definir funciones (en la imegen la funcion recibe un parámetro x  y retorna un valor M )
* Aplicación:  cuando se encuentran dos expresiones lambda consecutivas se entiende como la primera es una función que puede tomar como parámetro las siguentes.

En el ejemplo se lee como lamda recibe dos valores x,y  y retorna la suma de estos 

El sistema lambd puede codificar valores logicos en programación.

Esta demostrado que el calculo lambda es universal y puede expresr cualquier calculo 

Que problemas soluciono church con el calculo lamda: El problema de la parada*
	
Calculo lambda y maquina de computacion(turing)son equivalentes.

El paradigma funcional se empezó a desarrollar por el matemático John McCarthy en 1956, para programar los primeros proyectos de inteligencia artificial sobre un computador IBM 704 durante su desarrollo este crea el lenguaje de programcion lisp en 1958.

Lisp fue creado originalmente como una notación matemática práctica para los programas de computadora, basada en el cálculo lambda de Alonzo Church. apesar de no ser un lenguaje puramente funcional Se convirtió rápidamente un lenguaje de programación pionero en la investigación de la inteligencia artificial (AI) estableciendo las bases de lo que se conoceria hoy como el paradigma funcional

### Currificacion
###### (Matemático Haskel Curry) trabajo en la matemática combiantoria  que es el fundamento en los lenguajes de programación funcional.

Consiste en tomar una función con varios argumentos una n-tupla y tranformarla en una secuencia de funciones que toma un solo argurmento.


``` [language]
// funcion suma tome tres argumentos y son son transformados en una secuencia de funciones que cada una regesa otra función.
const sum = (a, b, c) => a + b +c;
const curriedSum = a => b => c => a + b + c;

console.log(sum(1, 2, 3)) // 6
console.log(curriedSum(1)(2)(3))// 6
```
La currificación es un concepto util en la aplicación parcial en la que se currifica una funcion y est es aplicada hasta cierto punto, para obtener un comportamiento nuevo.
``` [language]
//
const sum = (a, b) => a + b +c;
const incrementBy = a => b => sum(a, b);

const increment = incrementBy(1); //partially applied
console.log(incrementBy(5)) // 2
console.log(incrementBy(100))// 101
```

## Ventajas 
* Código más depurable, dado que es modular.
* Uso más natural de conceptos.
* Menor cantidad de código.
* Evita problemas de congruencia y facilta paralelismo 
* Se promueve la reutilzación de código 

## Desventajas 
* La pila de llamadas hace que se neceste más memoria.
* La creación de estructuras inmutables es más costosa.
* Ata barrera de entrada ata curva de aprendaje .
* Dificultad de lectura a medida que aumenta el nivel de abstracción

### Lenguajes:

Lenguajes funcionales puros, cabe destacar a Haskell y Miranda.Scala, Lisp, Clojure, Scheme, Ocaml, Erlang, R también es un lenguaje funcional dedicado a la estadística, Recientemente Microsoft Research está trabajando en el lenguaje F# (Functional#).

Entre otros lenguajes que se podrían utilizar para programación funcional se podrían incluir Python, java, Swift, php, kotlin, C#.

**Ejemplos:**
* Calcular el factorial de un número 
Haskell
``` Haskell
//Calcular el factorial de un numero 
fact :: Int -> Int
fact 0 = 1
fact n = n = * fact (n-1)
factorial n = product[1..n]
main = do 
    putStrLn (show(fact 4, factorial 4))
```
Clojure
``` Clojure
(defn factorial [n]
  (reduce *(range 1 (inc n))))
(factorial 4)
```
Scheme
``` Scheme
(define (fact n)
  (if(= n 0)
    1
    (* n (fact(- n 1))))
 (fact 4)
```

Java: contar los numeros mayores a 15.

``` Java
import java.util.List;

class Main{
  public static void main (String[] args){
  java.util.List<Integer>numberList = List.of(18,15,21,16,17,2,5,109,6,3,75,16);
  
  //Imperativo
  int count = 0;
  for(int number: numberList){
    if (number>15){
      count++;
    }
  }
  System.out.println("Imperativo: "+count);
  
  //Declarativo
  Long ans = numberList.stream().filter(n -> n>15).count();
  System.out.println("Declarativo: "+ans);
  
  }
}
```

### Aplicación

* Framework de desarrollo web.
* Manejo de informacion escañable.
* Parser.
* Inversión en bolsa.


