# progreso-semanal-programacionFuncional

#SEMANA 4 PROGRAMACION FUNCIONAL

-Funciones de Orden Superior

    .Funcion que puede asignarse a un valor:
    (x:Double) => -Math.pow(x,2) + 8 * x - 12
    val f1 = (x:Double) => -Math.pow + 8 * x - 12
    f1(12)
    ((x:Double)) => (-Math.pow + 8 * x - 12)(12)
    
    .Funcion que se envía como parámetro:
    def integracion(a:int, b:int, f:Double => Double){
      val intermedio = ((a+b)/2.0)
      val fa = f(a)
      val fi = f(intermedio)
      val fb = f(b)
      (b-a) * (fa + 4 * fi + fb )/6 
    }
   
    .Funcion que devuelve otra funcion:

	def select(option: Char) : (Int, Int) => Double = {
		option match {   //Similar a un switch case
			case '+' => (a: Int, b: Int) => a + b
			case '-' => (a: Int, b: Int) => a - b
			case '*' => (a: Int, b: Int) => a * b
			case '/' => (a: Int, b: Int) => a / b.toDouble
			case _ => (a: Int, b: Int) => 0/(a+b) //Para que devuelva siempre 0, _ significa default
		}
	}

	select('+')(2, 1)
	val operation = select('+')
	operation(2, 1)


#Dada una lista de enteros [5, 6, 7, 8, 9] ¿Cuántos son pares?

val isEven = (k : Int) => if (k % 2 == 0) 1 else 0

def isEven(k : Int) : Int = (k % 2) match{
	case 0 => 1
	case _ => 0
}

//Ambas funciones son lo mismo, la funcion con nombre es mas funcional

def countEven(s : List[Int]) : Int = s.map(isEven).sum

//Resultado

-------------------------------------------------------------------------------------------------------

sum // método que calcula la suma de todos los números de la lista
map // Aplica a cada elemento y como resultado lo ubica en una nueva lista (nombre diferente)

List(1, 2, 3).map(x=> x * x + 100 * x)
res3: List[Int] = List(101, 204, 309)

val nums = List(1, 2, 3)
nums.map(x => x + 1) //Resultado (2, 3, 4)

def add1(a : Int) : Int = a + 1
nums.map(add1)

nums.map(x => add1(x))
nums.map(x => add1(_))

val suma2 = (a: Int, b: Int) => a+b
nums.map(x => sumaDos(x, x))

----------------------------------------------------------------------------------------------------------

val cedula = "1106765321"
cedula = "1106239138" //Al reasignar valores, produce error
var cedula = "1106765321" //Cambio correcto (var en lugar de val para cambiar valores)

f(x) = -x^2 + 8x - 12                        --------- Matematica
(x: Double) => -Math.pow(x, 2) + 8 * x - 12          -- Programacion
val f1 = (x: Double) => -Math.pow(x, 2) + 8 * x - 12 
f1(12) 							// Se invoca a la funcion aignada al valor f1
((x: Double) => -Math.pow(x, 2) + 8 * x - 12)(12)  	// Forma de invocar una funcion en una misma sentencia, "anonima" 

=> Simbolo de Mapeo, funciones sin nombre

------------------------------------------------------------------------------------------------------------

#Mapeo

El siguiente código determina la cantidad de numeros pares, de una lista de enteros en Scala:


def isEven(k:Int) : Int = (k % 2) match{
	case 0 => 1
	case_ => 0	
}

def countEven(s : List[Int]) : Int = x.map(isEven).sum

countEven(List(3, 4, 8, 14, 26))

-----------------------------------------------------------

//Alternativa al codigo de la parte superior

def countEven(s: List[Int]) : Int = {
	def isEven(k:Int): Int = (k % 2) match{
		case 0 => 1
		case_ => 0	
	}

	s.map(isEven).sum
}

##Mapear una lista de cadenas de texto a lista de enteros que representan la longitud del texto

val names : List[String] = List("Leo", "Cristiano", "Enner", "Felipe")
names.map(_.length)

##Dada una lista de enteros, desarrollar las fuciones necesarias que le permitan contar cuantos
elementos de la lista son numeros primos

val numbers = List(3, 4, 7, 11, 12)
val isPrime = (nro : Int) => (2 to nro - 1).forall(nro % _!= 0)

numbers.map(isPrime(_)match{
	case true => 1
	case false => 0
}).sum

Otras Operaciones
	-sum
	-product
	-map
	-forall
	-max
	-min
	-size
	-exists
	-filter
	-takeWhite

val numbers = List(6, 28, 15, 12, 11, 24)

numbers.max //28

number.min //6

numbers.size //6

Predicado: Devuelve un booleano(exists, filter, takeWhite)

forall: devuelve true si y solo si el predicado devuelve true para todos los valores de la lista
	val isPrime = (nro : Int) => (2 until nro).forall(nro % _!= 0)

exists: Devuelve true si y solo si el predicado devuelve true para por lo menos un valor de la lista
	val isPrime = (nro : Int) : Boolean = !(2 until nro).exists(nro % _= 0)	

filter: Devuelve una lista que unicamente contiene los valores que cumplen con el predicado
	List(1, 2, 3, 4, 5).filter(k => k % 3 =! 0) //Resultado: List(1, 2, 4, 5)

takeWhile: Trunca la lista cuando encuantra un valor que NO cumple con el predicado
	List(1, 2, 3, 4, 5).takeWhile(k => k % 3 =! 0) //Resultado: List(1, 2) llega al 3 (que devuelve false) y la lista se queda de esa manera


#Map/Reduce
Transforman una función, toma una lista y devuelve otra(map, filter).
Agregan, toma una lista y devuelve un unico valor(max, sum).

En big data se concatenan transformaciones y agregaciones, las cuales se conocen como map/reduce

Dada una lista de numeros enteros, desarrollar las funciones necesarias que permitan contar el numero de elementos de la lista que son
perfectos, deficientes o abundantes.


val numbers = List(6, 28, 15, 12, 11, 24)

val sumDiv = (n : Int) => (1 until n).filter(div => n % div == 0).sum

numbers.filter(nro => nro == sumDiv(nro)).size //Numeros perfectos
numbers.filter(nro => nro < sumDiv(nro)).size //Numeros deficientes 
numbers.filter(nro => nro > sumDiv(nro)).size //Numeros abundantes

Factorial escalonado:

def !!(n : Int) : Int = {
	n % 2 match{
		case 0 => (2 to n by 2).product 
		case_ => (1 to n by 2).product 
	}
} 


Dada una lista, cuente los numeros pares:

val numbers = (1 to 20).toList

numbers.filter(nro => nro % 2 == 0).size
numbers.count(nro => nro % 2 == 0) //Otra alternativa mas corta



Dada una lista, cuente los numeros impares:

val numbers = (1 to 20).toList

numbers.filter(nro => nro % 2 != 0).size
numbers.count(nro => nro % 2 != 0)



Dada una lista, cuente los numeros primos:

val numbers = (1 to 20).toList

def contarPrimos(nros : List[Int]) : Int{
	val isPrime = (n : Int) => (2 to nro - 1).forall(nro % _!= 0)
	nros.filter(isPrime).size
}

contarPrimos(numbers)



Presentar 3 factores:

def tresFactores(nros: List[Int]) : List[Int] = {
	val divisors = (n : Int) =>
}
