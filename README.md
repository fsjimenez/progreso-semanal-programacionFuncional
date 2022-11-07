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
