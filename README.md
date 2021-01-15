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
