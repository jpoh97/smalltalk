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

Los closures son bloques de código que no tienen un nombre asociado (en ocaciones se denominan funciones anonimas). Un bloque es un objeto que representa un conjunto de colaboraciones al igual que un metodo, la diferencia es que no esta relacionado a una clase y no tiene un nombre.

La función más importante de los closures es poder parametrizar código. Poder pasar como parametro en un mensaje un conjunto de colaboraciones de manera sencilla. En terminos de FP, los closures nos permiten tener funciones de alto orden (funciones que pueden recibir funciones como parametros).

C: Bloque
Lisp: Funciones lambdas
Closure: Funciones lambdas + binding lexicográfico

Los closures bindean al contexto de ejecución en el cual es instanciado.

Una de las limitaciones de las funciones lambda en Java (que viene heredado de las clases anonimas) es que no pueden modificar objetos del contexto en el cual la función lambda es instanciada. Esto es debido a que esa variable ya no puede vivir en el Stack sino en el Heap. No son closures, son funciones lambda (no son las mismas func. lambda de Lisp). Son syntactic sugar de las clases anonimas.

Un full closure es un closure que el return bindea al contexto de ejecución de donde ese closure esta siendo instanciado.

El sindrome maradoniano es cuando alguien se referencia a si mismo en tercera persona en vez de primera persona (en la clase True de Smalltalk, returnar true en vez de self).

En Smalltalk el mensaje if esta implementado con polimorfismo (en la clase True y False). Cuando se trabaja con objetos, uno intenta evitar el if y usar polimorfismo. Cuando utilizo polimorfismo las decisiones las termina tomando los objetos, cuando utilizo if las decisiones las toma el programador y las hardcodea en el código. Cuando necesito agregar condiciones, solo debo agregar objetos y no modificar la lógica de decisión, me da mayores opciones de ampliar mi diseño sin necesidad de modificar nada (no es un regla, no siempre aplica utilizar polimorfismo sobre if, hay limitantes).

En lenguajes tipo, algunas sintaxis son construcciones especiales (while, if, try, for, etc), cuando trabajamos en lenguajes consistentes como Smalltalk empezamos a verlo como un conjunto de colaboraciones.

Los lenguajes type recursive detectan y eliminan la cola de la recursión. No necesitan crear un nuevo contexto de ejecución para la implementación de un metodo recursivo (ej: Haskell).
