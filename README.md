# smalltalk

## Episodio 1

"unarios"
10 factorial.

"binarios"
10 + 20.
10 >=20.

"keywords"
10 gcd: 20.
10 raisedTo: (3 gcd: 2) modulo: 4.

Array with:10 with:10 with:10.

FixedGregorianDate yearNumber: 2020 monthNumber: 3 dayNumber: 24.
March/24/2020 at: 19:50.
3/24/2020.

"
En sintaxis C este seria un if
if(numero.even()) {
	System.out.println('es par'); }
else {
	System.out.println('es impar'); }
"
numero := (FillInTheBlankMorph  request: 'Ingresa un numero') asNumber.
numero even ifTrue: [self informBlockingUI: 'es par'] ifFalse: [self informBlockingUI: 'es impar'].

"
while(numero.even()) {
	System.out.println('ingresar numero impar');
	numero := (FillInTheBlankMorph  request: 'Ingresa un numero') asNumber.
}
"
[numero := (FillInTheBlankMorph  request: 'Ingresa un numero') asNumber.	
numero even] whileTrue: [
	self informBlockingUI: 'ingresar un numero impar'.].
  
## Episodio 2

"
o m |
(o m) |
v := o |
[...] |
^ a
"

11 even ifFalse: [5].
11 even ifFalse: [] ifTrue: [].

[] whileFalse: [].
[] whileTrue: [].
[] whileNil: [].

"
Mensajes -> qué
Metodos -> cómo
"
"
Clasificacion
Objeto instancia de clase
"

10 class.
'Hola' class.
$a class.
false class.

[10 factorial] value. "value es el mensaje para ejecutra el closure o bloque, equivale a 10 factorial."

'hola' = ('ho','la'). "equals"
'hola' == ('ho','la'). "=="

Object subclass: #Customer 
	instanceVariableNames: 'name dateOfBirth' 
	classVariableNames: '' 
	poolDictionaries: '' 
	category: 'Webinar'.
	
"lenguaje dinamicamente tipado"
aCustomer := Customer new.
aCustomer name: 'Pepe'.
aCustomer dateOfBirth: March/24/2020.

aCustomer := Customer2 named: 'pepe' bornOn: March/27/2020.

"La subclasificacion en Java solo vale desde el punto de vista de instanciancias pero no de clases, en smalltalk se puede en ambas"

"Un lenguaje de programacion es el estado del conocimiento de las personas que lo desarrollan"
"Los closures se hicieron famosos porque Java no los tenia"

"Vimos la diferencia entre instancia en clase. Jugamos con el browser, inspector y debuger. Podemos ir modificando un programa mientras esta funcionando"

## Episodio 3

Del Episodio 03: Aprendiendo Smalltalk con Hernan Wilkinson

Lo importante de TDD es escribir tests que nos interesen a los programadores, sin importar si son unitarios, de integración, funcionales, etc

Técnica de desarrollo basada en las características de aprendizaje (no es técnica de testing, se usan tests como herramienta)
* Iterativa e incremental
* Con feedback inmediato

Como side-effect:
* Recuerda todo lo aprendido
* Y permite asegurarnos de no haber "desaprendido"

Incluye análisis, diseño, programación y testing (no en este orden).

¿Cómo se hace TDD?
1. Escribir un test
* Debe ser el mas sencillo que se nos ocurra
* Debe fallar al correrlo
2. Correr todos los tests
* Implementar la solución más simple (no debe abarcar mas que el caso que estamos testeando) que haga pasar el/los test/s
* GOTO 2 hasta que todos los tests pasen
3. Reflexiono - ¿Se puede mejorar el código?
* Si - Refactorizar. GOTO 2
* No - GOTO 1
Este paso es la parte artística de TDD, en donde hacemos que la aplicación se vea bien. No se puede agregar ni sacar funcionalidad, solo refactorizar (no cambia la ejecución del sistema)

Se hacen tests de caja negra que permitan construir la funcionalidad. 

Cada test debe agregar un valor funcional.

Si me demoro mucho en cada paso puede significar que estoy abarcando un test muy grande, que no empecé por el mejor lugar, q el diseño del sistema no es bueno, etc.

En ese ultimo caso significa que debo hacer mas refactors.

REGLA 1: Si el test no falla la primera vez que corre es porque:
a. Estamos testeando algo ya testeado
b. Nos adelantamos en el paso 2

La implementación no debe estar relacionada con datos de prueba sino con casos de prueba.

Casos de prueba = Conjunto de datos de prueba.

Cuando diseñamos un sistema con papel, nosotros estamos corriendo ese sistema en nuestra cabeza. Intentamos ser computadoras pero no lo somos.

Debemos diseñar a alto nivel antes de empezar para particionar el problema funcionalmente. No debemos anticiparnos a crear todo el diseño, el diseño debe surgir ya que así funciona el ciclo de aprendizaje.

Los getter y setter rompen el encapsulamiento.

Lo que no se ejecuta no son mantenibles en el tiempo. UML es muy útil para transmitir conocimiento.

REGLA 2: Sensar el tiempo que nos lleva realizar cada paso.

Esto nos va a dar feedback.

"Programar es el arte de nombrar cosas"

Testing no es una técnica formal para verificar código. No te asegura nada de las cosas que no estas testeando.

El nombre de los tests deben representar reglas de negocio.

Implementación rápida de un algoritmo que factoriza un número:
	
	calculate
		| primeFactors numberToFactorize divisor |
		primeFactors  := OrderedCollection new.
		numberToFactorize := self
		divisor := 2.

		[ numberToFactorize > 1 ] whileTrue: [
			[numberToFactorize isDivisibleBy: divisor] whileTrue: [
					primeFactors add: divisor. 
					numberToFactorize :=  numberToFactorize / divisor].
				divisor := divisor + 1].

		^primeFactors
## Episodio 4

Todas los tests de performance, escalabilidad, seguridad, etc. no son tests que nosotros escribimos con TDD. Son tests que se escriben cuando el sistema/código ya esta hecho, TDD es un proceso de desarrollo.

Los closures son bloques de código que no tienen un nombre asociado (en ocasiones se denominan funciones anónimas). Un bloque es un objeto que representa un conjunto de colaboraciones al igual que un método, la diferencia es que no esta relacionado a una clase y no tiene un nombre.

La función más importante de los closures es poder parametrizar código. Poder pasar como parámetro en un mensaje un conjunto de colaboraciones de manera sencilla. En términos de FP, los closures nos permiten tener funciones de alto orden (funciones que pueden recibir funciones como parámetros).

C: Bloque
Lisp: Funciones lambdas
Closure: Funciones lambdas + binding lexicográfico

Los closures bindean al contexto de ejecución en el cual es instanciado.

Una de las limitaciones de las funciones lambda en Java (que viene heredado de las clases anónimas) es que no pueden modificar objetos del contexto en el cual la función lambda es instanciada. Esto es debido a que esa variable ya no puede vivir en el Stack sino en el Heap. No son closures, son funciones lambda (no son las mismas func. lambda de Lisp). Son syntactic sugar de las clases anónimas.

Un full closure es un closure que el return bindea al contexto de ejecución de donde ese closure esta siendo instanciado.

El sindrome maradoniano es cuando alguien se referencia a si mismo en tercera persona en vez de primera persona (en la clase True de Smalltalk, retornar true en vez de self).

En Smalltalk el mensaje if esta implementado con polimorfismo (en la clase True y False). Cuando se trabaja con objetos, uno intenta evitar el if y usar polimorfismo. Cuando utilizo polimorfismo las decisiones las termina tomando los objetos, cuando utilizo if las decisiones las toma el programador y las hardcodea en el código. Cuando necesito agregar condiciones, solo debo agregar objetos y no modificar la lógica de decisión, me da mayores opciones de ampliar mi diseño sin necesidad de modificar nada (no es un regla, no siempre aplica utilizar polimorfismo sobre if, hay limitantes).

En lenguajes tipo C, algunas sintaxis son construcciones especiales (while, if, try, for, etc), cuando trabajamos en lenguajes consistentes como Smalltalk empezamos a verlo como un conjunto de colaboraciones.

Los lenguajes type recursive detectan y eliminan la cola de la recursión. No necesitan crear un nuevo contexto de ejecución para la implementación de un método recursivo (ej: Haskell).

## Episodio 5

Smalltalk te permite hacer todos, el limite es tu imaginación (incluso puedes debugear el debuger). No leemos archivos o usamos herramientas para las dependencias, solo trabajamos con objetos. Smalltalk fue creado por científicos que te dan todas las libertades, Java evita que te puedas equivocar y por ello te restringen tus libertades (no puedes modificar las clases que vienen con el JDK).

El padre de todos los objetos es ProtoObject que tiene los mensajes mínimos que debe tener un objeto. Object hereda de ProtoObject.

Cuando un objeto recibe un mensaje que no sabe responder, el retorna el mensaje el mensaje doesNotUnderstand. En lenguajes tipados el compilador no te permite enviar mensajes que el objeto no sabe responder.

El patrón MVC fue creado en Smalltalk como un framework. Este resolvía el problema de la interacción hombre maquina con user interface, mouse y teclado. Cada modelo podía tener múltiples vistas. Este framework utiliza lo que hoy en día conocemos como el patrón observer.

Los 23 patrones que vienen del libro de GOF fueron deducidos de soluciones que proponía Smalltalk, pero usaron para los ejemplos a C++. 

Cuando Alan Kay pensó en Smalltalk no pensó en un lenguaje de programación, pensó en una computadora. Smalltalk es mucho mas que un lenguaje.

De Number hereda Integer, Fraction y Float. Se podría trabajar sin float, solo con fraction pero es un poco mas lento. En Smalltalk estamos trabajando con números reales, no tenemos las limitaciones, overflow, problemas de precisión, etc que usualmente tenemos en Java y tampoco es necesario definir el tipo del numero ya que es un lenguaje dinámicamente tipado.

La mayoría de lenguajes de programación tiene implementada solamente la parte aritmética de la matemática, no nos permiten trabajar algebraicamente. El problema es que los números no tienen semántica, son símbolos que representan una abstracción. ¿Qué significa 5? es diferente a decir ¿Qué significa 5 metros? Es la manera de darle semántica a un número.

No debemos quedarnos nunca con lo que el lenguaje de programación nos da. Si el lenguaje no tiene una representación o abstracción que necesitamos, debemos crearla o implementarla. Debemos ir más allá.

Gracias a la extensibilidad de Smalltalk (open close principle), podemos adicionar estas representaciones que el lenguaje no trae y necesitamos. 

En Java no podemos tener nombres de mensajes que sean operadores, de hecho los operadores no son mensajes.

Nil es un objeto global que puede representar infinidad de cosas (de allí viene el problema de tenerlo).

Todas las colecciones vienen de la clase Collection. Puedes crear un array #(10 25 31) o {10 factorial. 3+5. 'hola'} o Array with: 10 factorial with: 3+5 with: 'hola'.

Se usa el mensaje at: para acceder a las posiciones de un array. No existe esa sintaxis [], todo se resuelve por mensajes y objetos.

El for seria asi:

Sintaxis C: for (int i = 0; i < 10; i++) { ... }

En Smalltalk: 0 to 9 do: [ :aNumber | aNumber + 1 ]

0 to 9 crea un intervalo que es una colección.

El mensaje sum lanza un mensaje de error si la colección es vacía. Se puede usar un closure ifEmpty: para manejar el caso en que sea vacía la colección. Se puede hacer reject, collect, select, sum, etc.

Existen Dictionary que permite representar clave y valor (no usarlo cuando se necesita un abstracción).

Tenemos el Set que no permite crear elementos repetidos dentro del Array. Tenemos los Bag que si lo permite y cuenta cuantos elementos hay de cada uno.

String subclasifica Collection. Es una colección de caracteres. Todos los mensajes que tiene una colección los puedo utilizar en un String.

Gemstorm reduce la complejidad accidental que normalmente tenemos con otras bases de datos.

## Episodio 6

Codigo repetido no es texto repetido, son patrones de colaboración repetido. Para sacar codigo repetido se copia a un lugar, parametrizo lo que cambia, contextualizo los nombres y lo empiezo a utilizar.

Para parametrizar codigo, se necesita usar closures o lambdas en caso de Java.

"Una linea en Smalltalk equivale a 5 o 6 lineas en C++"

"[Smalltalk] became the exampler of the new computing, in part, because we were actually trying for a qualitative shift in belief structures--a new Kuhnian paradigm in the same spirit as the invention of the printing press--and thus took highly extreme positions that almost forced these new styles to be invented" - Alan Kay

* Software -> Modelo
* Construir software -> Modelar -> Aprender sobre lo que se modela -> Aprendizaje constructivista
* "millions of potencial users meant that the user interface would have to become a lerning environment along the lines of Montessori and Brunet" -  Alan Kay
* "and needs for large scope, reduction in complexity, and end-user literacy would require that data and control structures be done away within favor of a more biological scheme of protected universal cells interaction only through messages that could mimic any desired behavior" - Alan Kay
* "El lenguaje no es nada, los objetos son todos"

Ej:
* Algebra de Boole - ifTrue:
* Iteraciones - whileTrue:
* Excepciones - on:do: -> redefinir handles:

* "The biggest hit for me while at SAIL in late '69 was to really understand LISP. Of course, every student knew about car, cdr, and cons, but... no one had penetrated the mysteries of eval and apply. I could hardly believe how beautiful and wonderful the idea of LISP was [McCarthy 1960]" - Alan Kay
* "... there were deep flaws in its logical foundations. By this, I mean that the pure language was supposed to be based on functions, but its most important components--such as lambda expressions, qoutes, and conds--were not functions at all, and instead were called special forms" - Alan Kay
* "The actual beauty of LISP came more from the promise of its metastructures than its actual model. I spent a fair amount of time thinking about how objects could be characterized as universal computers without having to have any exceptions in the central metaphor. What seemed to be needed was complete control over what was passed in a message send; in particular, when and in what environment did expressions get evaluated?" - Alan Kay

Meta-xxx: Que habla sobre, que define a, xxx
Ejemplo:
* Una clase es un Meta-objeto porque define su comportamiento
* El español es un "meta-lenguaje" porque puede predicar sobre "si mismo". Ejemplo: "La palabra casa tiene 4 letras"

Sistema computacional: Sistema que actúa y razona sobre un dominio
Casual connection: Propiedad que asegura que cambios en el dominio se ven reflejados en el modelo y viceversa
Mesa-sistema: Sistema cuyo dominio es otro sistema
Sistema Reflexivo: Meta-sistema "casually connected" consigo mismo

![](snapshots/ep6-1.png)

Reflexión: Habilidad integral de una entidad para representar, operar sobre y tratar consigo mismo en la misma manera que representa, opera sobre y trata con su sujeto primario
Introspection: La habilidad de un programa de razonar acerca de si mismo y/o la implementación del lenguaje de programación (read)
Intercession: La habilidad de un programa de "actuar" sobre las reificaciones de si mismo y la implementación del lenguaje de programación (write)
Reflexión estructural: La habilidad de un programa de acceder a su representación estructural y la implementación del lenguaje de programación
Reflexión de Comportamiento (Behavioral Reflection): Habilidad de un ptrograma de acceder a la representación dinámica de si mismo, esto es a la ejecución operacional del programa y de la implementación del lenguaje de programación
