# Informe de Investigación Sobre Arquitectura de Computadoras

Electronica IV - Trabajo Práctico Nº2 - Arquitectura de Computadoras

Facundo Sonzogni

## Introducción

Una ***Computadora*** es una Máquina (electrónica y digital), que es capaz de realizar varias tareas, ejecutando una serie de instrucciones provenientes de un Programa, a través de una *Unidad Central de Procesamiento* que recibe datos de entrada, los cuales traslada, almacena y procesa para convertirlos en información que posteriormente se envía a los puertos de salida. Además una computadora puede Cambiar de programa (es decir, si se cambian las instrucciones, la computadora cambia de tarea).
La anterior NO es una definición rigurosa de una Computadora, pero es suficiente para comprender su funcioamiento y cuáles son los elementos básicos de la misma. A continuación se da una breve descripción de los elementos constitutivos de una Computadora:

![](Imagenes/Elementos_basicos_Computadoras.png)

**1) Puertos de Entrada y Salida:** En primer lugar, es claro que la computadora necesita poder interactuar con el mundo real. Esa interacción se realiza a través de los *Dispositivos E/S* (Dispositivos de Entrada/Salida), los cuales se comunican con el procesador a través de los Puertos de E/S incluídos en la computadora.
Los Dispositivos de entrada envían datos al CPU (el cuál, además recibe instrucciones de qué hacer con dichos datos), que los procesa y los transforma en Información que se envía a los dispositivos de Salida (como un Monitor, unos Auriculares o una Impresora).

**2) Buses de Interconexión:** Los datos de entrada, la información de salida y las instrucciones no son más que señales binarias que deben transmitirse entre los distintos componentes de la computadora. Luego, se necesitan Buses de interconexión que conectan los puertos de entrada/salida, la memoria principal y la CPU. Una computadora debe contar, al menos, con 3 buses:
  - *Bus de Datos:* Permite el intercambio de datos entre la Memoria Principal y la CPU. También es el bus que conecta los puertos de E/S con el CPU. Por éste, se le comunican las instrucciones al procesador y los datos con los cuales debe trabajar, los cuales provienen tanto de la Memoria Principal como de los dispositivos de entrada.
  - *Bus de Direcciones:* Cada dato y cada instrucción se guarda en una determinada ubicación dentro de la memoria. Cada ubicación es posee una dirección UNÍVOCA asociada. El bus de direcciones es un canal del microprocesador totalmente independiente del bus de datos donde se establece la dirección de memoria del dato en tránsito. 
  - *Bus de Control:* El bus de control se utiliza para transferir señales de control hacia y desde la CPU. Controla el funcionamiento interno y externo del procesador. Los buses de datos y de direcciones están compartidas por todos los componentes, por lo que la computadora debe contar con algún mecanismo que controle su utilización. Para ello, la CPU genera una serie de señales en el bus de control que permiten coordinar y sincronizar distintas operaciones.

**3) Memorias y Almacenamiento:** Es evidente que una Computadora tiene que ser capaz de almacenar los datos, y además debe tener la capacidad de volver a acceder a datos con los que ha operado anterirormente; Es decir, debe contar con algún elemento de Memoria. En una computadora típica, se usan diversos tipos de memoria y los principales son los siguientes:
  - *Memoria RAM:* Almacena temporalmente datos binarios y programas durante el procesamiento. Los datos son números y otros tipos de información mientras que los programas son listas de instrucciones. En una memoria RAM, pueden leerse y escribirse datos en cualquier momento. La RAM es volátil, lo que quiere decir que la información se pierde si se desconecta la alimentación o si ésta falla. Esta memoria constituye la Memoria PRINCIPAL de la computadora. (Floyd)
  - *Memoria ROM:* Los datos y programas que tengan que ser guardados, luego de retirar la alimentación, tienen que transferirse a una memoria no volátil. En la memoria ROM se guarda el programa, por ejemplo, puesto que es evidente que la serie de instrucciones no se debe borrar al desconectar la computadora. (NOTA: El término ROM hace referencia a "Read Only Memory", y se emplea para enfatizar el hecho de que el procesador, en general, SOLAMENTE DEBE LEER LAS INSTRUCCIONES DEL PROGRAMA, MÁS NO MODIFICARLAS. Sin embargo, es claro que si se desea cambiar de programa, se debe poder modificar lo contenido en esta memoria, por lo que en realidad NO se trata de una Memoria ROM, sino más bien de una Memoria FLASH, que permite escribir. El motivo de llamarla ROM es, justamente, que el Procesador solo LEE las instrucciones). (Floyd)
  - *Memoria Caché:* La memoria caché es una pequeña memoria RAM que se utiliza para almacenar una cantidad limitada de datos frecuentemente utilizados, a los que se puede acceder mucho más rápido que si estuvieran en la memoria RAM principal. La caché almacena información que debe “estar a mano” con el fin de poder volver a utilizarla rápidamente, sin tener que extraerla de nuevo de la memoria principal. (Floyd)
  - *Disco Rígido:* Se trata de una memoria No Volátil que permite almacenar un gran número de datos. En el disco rígido se suelen guardar los datos de más alto nivel y que deben mantenerse una vez retirada la alimentación, como ser el Sistema Operativo, el Software de Aplicación, etc. (Floyd)
  - *Almacenamiento Extraíble:* La mayoría de los sistemas informáticos cuentan con la posibilidad de extraer algunos datos de la computadora, a través de dispositivos como disquetes, discos Zip o discos CD (Compact Discs), los cuáles pueden ser CD-ROM (solo permiten su lectura) o CD-RW (permiten reescribirlos). (Floyd)

**4) Unidad Central de Procesamiento:** La computadora necesita una unidad que se encargue de recibir las isntrucciones y los datos, para poder ejecutar una serie de pasos de manera secuencial para poder cumplir con lo especificado en el programa. La unidad encargada de ello es la CPU: La CPU es un microprocesador con una serie de circuitos asociados que controla los programas software de la computadora. Básicamente, la CPU obtiene (extrae) cada instrucción de programa de la memoria y lleva a cabo (ejecuta) dicha instrucción. que constituye el "cerebro" de la computadora. Una idea muy general de su funcionamiento es el siguiente:
  1. En primer lugar, la CPU coloca una dirección en el bus de direcciones, en la cual se encuentra la instrucción que debe ejecutar.
  2. Dicha instrucción, junto con los datos provenientes de la memoria y de los dispositivos de entrada se envían al procesador a través del bus de datos.
  3. Luego, la CPU ejecuta internamente dicha instrucción y genera una salida de información, la cuál se envía a los dispositivos de salida a través del bus de datos.
  4. Posteriormente, el procesador vuelve a enviar una dirección por el bus de direcciones que le permite acceder a la siguiente instrucción y repetir el procedimiento anterior.

De esta manera, la CPU consigue ejecutar todas las instrucciones del programa en forma secuencial (NOTA: Recordar que para realizar todas estas operaciones, el procesador envía señales por el bus de control, para así coordinar todo lo anterior). Finalmente, para formar una idea de cómo el procesador es capaz de ejecutar las instrucciones, es preciso comprender un poco de su funcionamiento interno:

![](Imagenes/Partes_Microprocesador.png)

  *a) Decodificador de Instrucciones:* Las instrucciones llegan a la CPU a través del bus de datos, por lo que llegan en forma de una cadena de bits binarios. Luego, para poder interpretar esas instrucciones, el procesador debe contar con un Decodificador de dichas instrucciones, que las transforme en algo que el mismo "comprenda".

  *b) Unidad Aritmética Lógica:* Cualquier instrucción, si se analiza desde un bajo nivel, puede realizarse simplemente a través de operaciones aritméticas (suma, resta, multiplicación, división) y/o operaciones lógicas (NOT, AND, OR, XOR, inversiones, desplazamientos y rotaciones). Luego, el procesador debe contar con una unidad capaz de realizar todas estas operaciones, en función de cuál sea la instrucción que le llega, denominada ALU (Unidad Aritmética Lógica).

  *c) Matriz de Registros:* Para poder ejecutar las instrucciones, muy probablemente, el procesador deberá tener que guardar datos, por lo que necesita alguna forma de memoria interna. La matriz de registros es una colección de registros contenida en el microprocesador.Durante la ejecución de un programa, los datos y las direcciones de memoria se almacenan temporalmente en los registros que forman esta matriz. La ALU puede acceder a esos registros muy rápidamente, lo que permite que el programa se ejecute de forma más eficiente que si tuviera que acceder a la memoria principal de la computadora. 

  *d) Unidad de Control:* Una vez que las instrucciones han sido decodificadas, alguna unidad dentro del procesador debe encargarse de su procesamiento. La Unidad de Control sigue la dirección de las posiciones en memoria que contienen la instrucción que el computador va a realizar en ese momento; recupera la información poniéndola en la ALU para la operación que debe desarrollar. Transfiere luego el resultado a ubicaciones correspondientes en la memoria. Una vez que ocurre lo anterior, la unidad de control va a la siguiente instrucción. Además, esta unidad es la encargada de enviar las señales de sincronización y control por el bus de control de la computadora.

  *e) Buses Internos del Procesador:* Internamente, la CPU también debe contar con buses que permitan conectar las diferentes unidades. Cuenta, también con buses de datos e instrucciones, buses de direcciones y buses de control.

### Arquitectura de Computadoras

Hasta este punto, se ha discutido brevemente las partes de una computadora y sus principal funcionamiento. Sin embargo, debemos notar que hay diferentes maneras de realizar la interconexión del hardware de una computadora,las cuales dependerán de su funcionalidad, de su eficiencia y de los costos. Luego, es preciso distinguir entre las distintas maneras en las que puede estar constituído internamente un sistema de cómputo y realizar MODELOS que permitan estudiar como interactúa la CPU con los elementos de memoria; Estos modelos constituyen lo que llamamos ***Arquitectura de Computadoras***.

Establecer una única definición para lo que entendemos por "Arquitectura de una Computadora" resulta una tarea complicada, por varios motivos. En primera instancia, debido a la gran variedad de sistemas que hoy en día se agrupan en la denominación “computadora”; por otro lado, debido al ritmo vertiginoso al que cambian todos estos sistemas, tanto en lo que se refiere a la tecnología como al diseño, y la complejidad de las técnicas empleadas en la actualidad (Beltrán, Guzmán). A continuación se citan algunas definiciones dadas por diversos autores:

- *“Es la estructura de una computadora que debe conocer un programador en lenguaje máquina para escribir programas correctos para esa máquina”* (Familia 360 de IBM).
- *“Son los atributos de una computadora tal y como los ve un programador en lenguaje ensamblador, comprende la estructura conceptual y el modelo funcional (modelo de programación)”* (Amdhal, Blaaw y Brooks en 1964).
- *“Computer architecture refers to those attributes of a system visible to a programmer or, put another way, those attributes that have a direct impact on the logical execution of a program”* (Stallings William).
- *“The architecture is the programmer’s view of a computer. It is defined by the instruction set (language), and operand locations (registers and memory)”* (Harris, Harris).
- *“La arquitectura de computadoras, también llamada arquitectura de ordenadores en algunos casos, es el diseño conceptual y la estructura operacional fundamental de un sistema de computadoras.​ Es decir, es un modelo y una descripción funcional de los requerimientos y las implementaciones de diseño para varias partes de una computadora, con especial interés en la forma en que la unidad central de proceso (CPU) trabaja internamente y accede a las direcciones de memoria.”* (Wikipedia).

A partir de estas definiciones (y de muchas otras), se observa que en todos los casos, la arquitectura de computadoras se basa en una descomposición de la computadora en diferentes niveles que den una idea de su descricpción jerárquica. Luego, dependiendo de cuál sea la descomposición que se realice, se tendrá una descripción diferente de la máquina, lo cual se traduce en que cada arquitectura tendrá sus reglas de diseño, sus leyes de funcionamiento y su lenguaje de representación. Se trata, entonces, de una materia estrechamente
relacionada con el estudio de la estructura y organización de la computadora y con las relaciones entre
sus componentes. (Beltrán, Guzmán).
Así, es importante conocer la arquitectura de una computadora para comprender como se debe programar un determinado microprocesador. Asímismo, si se desea diseñar una computadora, se debe tener en cuenta su finalidad para poder elegir la arquitectura más adecuada.
---------------------------------------------------------------------------------------------------------------

Al realizar la descripción de una computadora, usualmente es necesario realizar una distinción entre lo referido a su **Arquitectura**, de lo que relacionado a su **Microarquitectura** (u Organización). Además, ambos conceptos deben distinguirse del **Software** de la computadora: 

El concepto de *Arquitectura de Computadoras* se relaciona con el coportamineto funcional de un sistema de computación que son VISIBLES PARA EL PROGRAMADOR, que inclue aspectos como el tamaño de los diferentes tipos de datos, los tipos de operaciones que se pueden realizar, los formatos de instrucciones, los registros y fundamentalmente, el acceso de la CPU a la memoria de datos y la memoria de instrucciones. En cambio, la *Microarquitectura de Computadoras* se refiera a las relaciones estructurales que NO SON VISIBLES AL PROGRAMADOR, como el arreglo específico de registros, memorias y ALU's del CPU, las interfaces hacia los dispositivos periféricos, la frecuencia de reloj, entre otros. (Un ejemplo sencillo para comprender esta diferencia podría ser el siguiente: Decidir si un procesador tendrá la opción de realizar una instrucción de una multiplicación está relacionado con su Arquitectura, mientras que es un problema de Organización (o mircroarquitectura) el determinar el mecanismo o la forma mediante el cual el procesador realizará la multiplicación). Esta distinción es muy importante puesto que muchos diseñadores de computadoras ofrecen máquinas que poseen la misma arquitecura, pero una organización diferente, que poseen diferentes atributos. (Stallings W.) (Harris, Harris) (Murdocca)
En contraposición, el *Software de una Computadora* abarca todo lo intangible relacionado con el funcionamiento de la máquina y es, finalmente, lo que permite que el hardware realice una tarea útil. El Estándar 729 de IEEE define el Software como el conjunto de los programas de cómputo, procedimientos, reglas, documentación y datos asociados, que forman parte de las operaciones de un sistema de computación. Las dos categorías principales de software usado
en una computadora son:
 - *Software del Sistema:* Constituye el Sistema Operativo y es lo que permite que el Usuario interactúe con la computadora: Se encarga de a) gestionar todo el hardware y el software de aplicación dentro de una computadora y b)Proporcionar una interfaz coherente entre el software de aplicación y el hardware. (Floyd)
 - *Software de Aplicación:* Se utiliza para realizar una tarea o trabajo específico. Para cada aplicación de una computadora, se debe diseñar un software que interaccione con el hardware para realizar alguna función.
Es importante notar que la Arquitectura de Computadoras no sólo se encarga de los elementos hardware sino también de los elementos software. Esto se debe a que en muchos casos ambos aspectos se hallan estrechamente relacionados y no se pueden estudiar por separado. (Beltrán, Guzmán).

## Clases de arquitectura de computadora

> Fundamentando con citas bibliográficas:
>
> - Explica brevemente los tipos de arquitectura de computadora que hayas encontrado en la bibliografía
> - Discute para cada tipo sus características distintivas, ventajas y desventajas
> - Considera *al menos* lo siguiente: máquina de pila, máquina de registros y máquina de acumulador; RISC y CISC; Von Newmann y Harvard
> - Sitúa en este contexto la arquitectura ARMv7M

## Partes de una arquitectura de computadora

> Fundamentando con citas bibliográficas:
>
> - Explica las distintas partes de una arquitectura de computadora
> - Analiza a la luz de lo desarrollado la arquitectura ARMv7M

## Conclusiones

> En este capítulo debes exponer con tus palabras lo siguiente
>
> - ¿Qué es, para tí, una arquitectura de computadoras?
> - Si descomponemos un sistema de cómputo en capas ¿Qué posición ocupa la arquitectura?
> - ¿Cuál es la función que cumple una arquitectura de computadora?
> - ¿Qué considerarías a la hora de elegir una arquitectura de computadora?
>
> *Nota:* El contenido de este capítulo expone lo que aprendiste durante la investigación para desarrollar este práctico. Es un espacio para tu propia reflexión. Intenta exponer tus propias ideas, tal vez sea bueno hacerlo luego de apartarte unas horas del material de referencia para evitar seguir demasiado de cerca una fuente particular.

## Bibliografía

- Floyd, T.L. (2006). *Fundamentos de Sistemas Digitales*. (9na ed.). Pearson Pretince Hall.
- Beltrán, M., Guzmán A. (2010). *Diseño y Evaluación de Arquitecturas de Computadoras*. Pearson Pretince Hall.
- Stallings, W. (2016). *Computer Organization and Architecture*. (10ma ed.). Pearson Pretince Hall.
- Harris, D.M., Harris S.L. (2007). *Digital Design and Computer Architecture*. (1ra ed.). Morgan Kaufmann.
- Murdocca, M.J., Heuring, V.P. (2002). *Principios de Arquitectura de Computadoras*. Pearson Pretince Hall.
- Stallings, W. (2005). *Organización y Arquitectura de Computadores*. (7ma ed.). Pearson Pretince Hall.
- Hennessy, J.L., Patterson, D.A. (1993). *Arquitectura de Computadores. Un enfoque cuantitativo*. McGraw-Hill.
- Tanenbaum, A.S. (2000). *Organización de Computadoras. Un enfoque estructurado*. (4ta ed.). Pearson Pretince Hall.
- Hennessy, J.L., Patterson, D.A. (2021). *Computer Organization and Design*. (2da ed.). Morgan Kaufmann.
- Pestano Herrera, J.M. (2018). *Microcontrolador STM32. Programación y Desarrollo*. Ra-Ma.

