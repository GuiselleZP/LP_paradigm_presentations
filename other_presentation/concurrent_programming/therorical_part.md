[Link del video en youtube](https://www.youtube.com/watch?v=Dyz6-8DV4Ho&feature=youtu.be)

# Programación Concurrente
###### Ejecución simultanea de tareas interactivas

Es un conjunto de técnicas que permiten la ejecución concurrente entre tareas que pueden interactuar entre sí, de esta forma se tiene un conjunto de procesos o hilos que se sincronizan y comunican entre sí

## Conceptos claves 
Los siguentes conceptos ayudan a entender como se funciona la concurrenca a nivel de proceso y a nivel de hilo.
* **Programa**: Conjunto de instrucciones  guardadas  en disco  que  se  deben  realizar  en una CPU.
* **Proceso**: Cuando una instancia de un programa se carga en memoria y es ejecutado en un procesador pasa a ser un *proceso*.
* **Hilos**: Representa la unidad básica de uso de  CPU  donde  un  proceso  se puede  componer  de  uno  o  más hilos  que  ejecutan  instrucciones del programa y se usan para poder utilizar concurrencia en un proceso singular, los hilos pueden compartir los mismos recursos(memoria y datos).
* **Procesadores**: Un  procesador es  el  chip  fisico que  hace  parte  del  computador que  contiene  la  CPU que  se define  como  el  hardware  que permite realizar instrucciones
* **Núcleos**: Cada  CPU puede  contener  uno  o más  núcleos los  cuales  son  los encargados  de  ejecutar  las instrucciones de cada proceso que llega a la CPU
* **Cambio de contexto**: Consiste  en  el  proceso  realizado por el Sistema Operativo de tomar un proceso o hilo ejecutándose en 
un  núcleo  de  CPU,  guardar  el estado  de  la  última  instrucción, detener su  ejecución, y finalmente colocar  otro  hilo  o  proceso en  el núcleo para su ejecución.

La concurrencia puede originar los siguentes problemas a nivel de sistema operativo:

* **Condición de carrera** (*condición de secuencias*): Se  usa cuando el resultado de la ejecución de un  proceso,  depende  del  orden  en  que se sucedieron eventos anteriores.(ej. Dos procesos que intentan acceder a una misma variable, el proceso A asigna un valor, luego el proceso B llega y altera el valor de la variable, cuando se retoma A el resultado de la ejecucion de este sería diferente al esperado.)
* **Sección Crítica** Secciones  del  código  de  los  procesos que  no  pueden  ser  ejecutadas  de forma  concurrente  ya  que  causaría errores  o  funcionamientos  inesperado al  tener  variables  o  recursos  que  son accedidos por más de un proceso a la vez (condición de carrera: Variables o recursos accedidos por mas de un proceso a la vez). 

Para solucionar el problema de las secciones criticas se usa la **Exclusion mutua** también  llamada  Mutex,  consiste  en inhabilitar  las  secciones  críticas  del código  cuando  la  ejecución  de  un proceso ha llegado a dicha seccion de codigo   y  volver  a  habilitarla  cuando se  termine  de  ejecutar  el  código  en dicha sección. La mayor parte de esos recursos son del tipo señales, contadores, colas y otros que se usan para realizar la exclusion entre procesos,  los principales son semáforos, monitoresm  y paso de mensajes

* **Semáforos** Son  indicadores  de  condición  que indican si un recurso está disponible o no, antes de ser accedido.
  * Semáforos binarios: son para proteger un único recurso, que puede estar diponible o no para ello se indica con los valores 1 o 0 respectivamente.
  * Semáforos generales: sirven para proteger un conjunto de resursos, funciona como una variable contadora la cual va decrementando a medida que los recursos estan siendo opupados por un proceso y aumentando a medida que el recurso vuelve aestar diponibles.
* **Monitores** Estructura  de  dato  abstracta compuesta  de  un  identificador,  un conjunto  de  variables  globales, conjunto  de  procedimientos  y  un bloque de inicialización.Pueden  ser  utilizadas  por  más  de  un hilo  ya  que  los  procedimientos  se ejecutan con exclusión mutua, es decir la estructura se encarga del proceso de asignación de los recursos.
Generalmente se implementan con semaforos ya que son una abstración de estos, para facilitar el desarollo de programas concurrentes.
* **Mensajes**: Son  cadenas  de  texto  transmitidas entre  procesos  que  permiten  la sincronización  y  comunicación  entre procesos. 
  * Mensajes directos: el proceso especifica emisot y receptor.
  * Mensajes indirectos: el mensaje no se envia a un receptor si no a otra estructura de datos denominada Buzon.
  * Mensajes implícitos: el emisor especifica quien es el receptor, pero el receptor no especifica cual es el proceso emisor.
* **Buzones**: Es una estructura de datos dedicada a almacenar  mensajes,  la  cual  tiene  un tamaño definido, ademas se especifica el nuemro max de mensajes y una lista de usuarios que pueden acceder o consultar dicho buzon.
  * Buzones propios de un proceso: el buzon existe mientras el proceso exista.
  * Buzones del Sistema operativo: existe mientras no se hafa un llamado a la instrución que destruye dicho buzon. 

## Ventajas y Desventajas
### Ventajas:
 * **Optimización** :  
    * Optimiza  los  recursos computacionales  de  procesamiento aprovechando  la  CPU  y  cada  uno  de sus núcleos al máximo.
    * Permite  un  menor  tiempo  de ejecución  que  un  programa  ejecutado
secuencialmente.
 * **Responsividad de usuario**:
    * La  concurrencia  le  permite  a  un programa  seguir  ejecutándose  incluso si  parte  de  él  está  realizando  una operación que lleva tiempo.Así  el  programa  esta  ocupado  pero sigue estando responsivo al usuario.
 * **Escalabilidad**: 
    * En  un  sistema  multiprocesador  las ventajas  se  multiplican  ya  que  se  puede combinar  la  concurrencia  con 
paralelización  y  permitir  a  varios  hilos ejecutarse  paralelamente  en  varios núcleos  sin  necesidad  de  cambiar demasiado la implementación de los hilos.
### Desventajas: 
 * **Implementación:** 
    * Es  necesario  examinar  cuidadosamente el  programa  para  encontrar  qué  tareas pueden dividirse en hilos concurrentes.
    * Una  concurrencia  mal  implementada podría aumentar el tiempo de ejecución de un programa, ya que aumentaria el número de cambios de contexto y esto tienen cierto tiempo de ejecución.
 * **Pruebas y depuración** : 
    * Un  programa  que  se  ejecuta concurrentemente  puede  ejecutarse  en 
diferentes  órdenes  generando  muchas posibilidades de ejecución. Esto dificulta el trabajo del programador a la hora de realizar testing y depuración del 
código
 * **Manejo de datos**: 
    * Se  pueden  generar  error  cuando  varios  hilos comparten  los  mismos  datos  y  estos  intentan acceder a estos al mismo tiempo. Asimismo  la  modificación  de  datos  combinado con  el  orden  en  el  que  se  modifican  pueden generar errores no esperados.
 
## Lenguajes de Programación 
Algunso lenguajes en los que se puede trbajar este paradigma Java, c++, python 
*Java*
* Java  permite  realizar  programación concurrente a través de hilos (threads).
* Los hilos son procesos ligeros, que se ejecutan fuera de la línea de flujo actual.
* Los  cambios  de  contexto  son  menos  costosos en tiempo de ejecución.

*C++*
* Al  igual  que  java  puede  realizar  concurrencia por medio de hilos, aunque no de forma nativa.
* Cuando se creó el estándar inicial de C++, el mecanismo  de  concurrencia  fue  excluído  de forma explícita porque C no tenía uno.
* Actualmente  existe  una  librería  “thread”  que permite programar concurrentemente.

*Python*
* Python no es realmente multitarea.
* Python  tiene  librerías  que  le  permiten  realizar programación paralela y concurrente por medio de hilos y procesos.
* Python  tiene  una  librería  “threading”  que permite programar concurrentemente.

## Aplicaciones
* Servidores Web
* Sistema multimedia
* Cálculo númerico
* Interacción por GUI
* Sistemas gestores de bases de datos
* Sistemas Operativos
* Sistemas de control
* simulacipon 
* Video Juegos





# Rust 

[Link del video en youtube ](https://www.youtube.com/watch?v=tfOBPsWxzYE)

[Link notebook 2019-II ](https://hub-binder.mybinder.ovh/user/futureun-rusttutorial-dts7k0cs/tree)

Rust es un lenguaje de programación de sistemas de paradigmas múltiples centrado en la seguridad, especialmente la concurrencia segura.Rust es sintácticamente similar a C ++, pero está diseñado para proporcionar una mejor seguridad de la memoria mientras se mantiene un alto rendimiento.

