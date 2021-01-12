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
