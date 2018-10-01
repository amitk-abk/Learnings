# Scala

Scala, short for Scalable Language, is a hybrid functional programming language.  
It was created by Martin Odersky.  
Scala is a pure object-oriented language in the sense that every value is an object and every operation is a method call.  
It runs on the standard Java platform and interoperates seamlessly with all Java libraries.  
Scala is a kind of mix of object oriented and functional programming ideas in what is called as statically typed language.  
Scala is designed to be interoperable with Java & JVM -  Scala code can call Java methods, access Java fields, inherit from Java classes, and implement Java interfaces. And scala code makes heavy use of Java libraries and also heavily re-uses Java types e.g. Int, Scala arrays are mapped to java arrays.

## Why Scala

The central drive behind Scala is to make life easier and more productive for the developer. Scala does this with three principal techniques:

- It cuts down on boilerplate, so programmers can concentrate on the logic of their problems.
- It adds expressiveness, by tightly fusing object-oriented and functional programming concepts in one language
- And it protects existing investments by running on the Java Virtual Machine and interoperating seamlessly with Java.
- Scala brings unique fusion of functional programming and object oriented programming thereby making it possible to express new kinds of programming patterns and component abstractions.
- It deploys concise programming style and syntax - Scala programs tend to be short upto factor of 10 compared to java. It tends to avoid lot of boilerplate.
- Scala is statically typed language but it avoids verbosity by using type inference and gains flexibility by deploying pattern matching.

For more details check: [Why-Scala](https://www.lightbend.com/blog/why-scala)

### Scala Basics: General

- Scala is a line-oriented language where statements may be terminated by semicolons (;) or newlines.
> A semicolon at the end of a statement is usually optional.

- A multi-line string literal is a sequence of characters enclosed in triple quotes """ ... """.

The sequence of characters is arbitrary, except that it may contain three or more consecutive quote characters only at the very end.

- The null value is of type scala.Null and is thus compatible with every reference type.

It denotes a reference value which refers to a special "null" object.

- Immutability is norm in Scala.

Entities are declared as **immutable** using **'val'**.  
e.g. **val PI = 3.14**  OR  **val PI:Double = 3.14** though type specification is optional.  
This declares immutable variable called PI.

  > Commonly used collections are immutable too.  
  > Modifying an immutable collection returns a new collection, leaving the original unchanged.

- Mutable data items are created using 'var' e.g. var thisCanChange = 10

- Multiple assignments:  
 Scala supports multiple assignments.  
 If a code block or method returns a Tuple (Tuple − Holds collection of Objects of different types), the Tuple can be assigned to a val variable.  
 e.g. val (myVar1, myVar2) = Pair(40, "Foo") OR val (myVar1: Int, myVar2: String) = Pair(40, "Foo")

- Scala uses ***type inference*** to determine the type of the data, it helps scala to infer what kind of storage unit or data item is.  
 When you assign an initial value to a variable, the Scala compiler can figure out the type of the variable based on the value assigned to it.  
 Still, You can define any type of Scala variable by mentioning its data type as:  
    var myVar :Int;
    val myVal :String;

- Value types in scala are mostly wrapper over java's:  
  **Byte, Short, Char, Int, Long, Float, Double, Boolean and Unit.**

- Scala does not support break or continue statement like Java does.

- String interpolation:	It allows programmers to embed references to string variables inside string literals.

```Scala
    e.g. val greet = "hello"
    val name = "Mark"
    s "$greet $name, have a great day!"

    Scala will substitute the values for $greet and $name.
```

- you can instantiate objects, or class instances, using ***new***.

#### Expression v/s statements

Scala favors expressions over statements. Anything that evaluates to a value is an expression. An object is an expression also.

- When expression is assigned to a data item is when we get statement.
- Expressions can be chained together, they can be composed. They can be rvalue (of statement).
- Expressions support functional programming paradigm while statements do not.
- Expressions are block of codes that do return a value while statements not.

```Scala
      e.g.
      expression- List("Mon", "Tue", "Wed", "Thur", "Fri")
      statement- val weekDays = List("Mon", "Tue", "Wed", "Thur", "Fri")
```

> Statements are scares in scala, as far as possible avoid them and use expressions instead.

Expression blocks are enclosed in {}, last expression in the block is the return value.

```Scala

  val radius = 10
  val area = {
  val PI = 3.14;
    PI*radius*radius -------------> return value
  }
```

Expression blocks can be nested, each has it's own scope hence same named variable will have scope specific value.
**The return value from the outer scope (before inner scope) is ignored.**

***if/else, for loops (but not while loop), pattern matching*** (similar to switch statement in java) are few of major constructs that are statements in java but are expressions in scala. **It means they are rvalue in an expression, and they can be functionally composed (can be chained together)**:

```Scala
  val value1 = if (boolean expression) { expression block 1 } else { expression block 2 )
```

```Scala
  val number = 22
  val denom = 7
  val PI = if (denom != 0) { numer/denom } else { None }
```

Here, ***if*** can be present without ***else*** clause and in that case the expression returns Nothing if boolean condition evaluates to false.

***For loop*** in scala are both statements and expression. Adding keyword **yield** on for loop transforms it to expression from statement.
A **for loop with *yield*** will 'yield' a collection of the return values of each iteration of the loop.

```Scala
var x = for (day <- daysOfWeekList) yield {
        day match {
          case "Mon" => "Monday, first day"
          case "sun" => "Sunday, last day"
        }
      }

Returns>> x: List[String] = List("Monday, first day", "Tue", "Wed", "Thur", "Fri", "Sat", "Sunday, last day")
```

Basic **for expression:**  
e.g. for(item <- items>) println(item)  
Here, the println is applied to every item from items, both are on the either side of symbol <-  
You can say "in" for the <- symbol. You can read ***for (item <- items)*** , therefore, as "for item in items."

##### Function and Expressions

A function is really just a named, reusable expression block.
Both function and expression blocks in scala:

- Can be passed into functions and returned from functions.
- Can be stored in values and variables.
- Can have nested scopes.
- While expression blocks do not have parameters, functions have.

#### Functions in Scala

**Functions are *first class citizens* of scala.**

- Scala allows functions to be stored in a variable or in a value.
- The return value of the function can be a function: Scala treats function as first class citizens.
- A parameter of a function can be a function.
- closures - Functions that retain the referencing environment.
- parameter groups - logical groups of parameters to a function.
- Function is of type &lt;function1&gt;, &lt;function2&gt; (until &lt;function23&gt; & hence upto 23 arguments to max) family of **traits**.
- Function definitions start with **def**, the function's name is followed by a comma-separated list of parameters in parentheses. A type annotation must follow every function parameter, preceded by a colon (e.g. x: Int, y: Int), because the Scala compiler does not infer function parameter types. After that parameter list separated with : is return type (e.g. : Int).

``` Scala
Function example:
  def calculate(x: Int, y: Int): Int = {
      (x + y) * 5
  }

Another example:
  def max(x: Int, y: Int) = if (x > y) x else y

One More example:
  val getArea = (radius : Double) => {
    val PI = 3.14
    PI * radius * radius
  } : Double      ------------------> Double mentions return type of function, can be omitted for scala to work it out.
```

**Assigning the method to function variable:**

``` Scala
Method 1: Using the signature of the method
    def getPI() = {PI}
        the signature of this method is () => Double

    val calPI: ()=>Double = getPI

Method 2: Using eta expansion (_)
    val calPI = getPI _


Another example:
    def getRectangleArea(len : Double, b : Double) : Double = { len * b}

    The signatuer is:
        (Double, Double) => Double

    val getArea: (Double, Double) => Double = getRectangleArea
                    OR
    val getArea = getRectangleArea _
```

#### Function literal

A function literal is typically part of function that is main and is without name part. The syntax for a function literal is a **list of named parameters**, in parentheses (e.g. (x: Int, y: Int)), **a right arrow**, and then the **body of the function** (e.g. x * y).  
e.g. (x: Int, y: Int) => x * y

#### Functions and methods

A Scala method is a part of a class which has a name, a signature, optionally some annotations, and some bytecode.  
A **function** in Scala is a **complete object** which **can be assigned to a variable**.</br>
A function definition can appear anywhere in a source file and Scala permits **nested function** definitions.</br>
Scala function's name can have characters like +, ++, ~, &,-, --, \, /, :, etc.

**Functions are objects but methods are not.**

Methods are defined with the **def** keyword. def is followed by a name, parameter lists, a return type, and a body.  

```Scala
Method example:
    def getArea(radius: Double) : Double = {
       val PI = 3.14
       PI*radius*radius
    }
```

- Method are non value type - can not serve as l-values.
- Methods are not objects but can easily be converted into function objects.
- Methods are always associated with some class.

**Function example:**

```Scala
  val getArea = (radius: Double) => {
     val PI = 3.14
     PI*radius*radius
  }: Double

   Here getArea is a function object.
```

- Functions are value type - can be stored in val and var storage units.
- Functions are first class entities in scala and are not associated with any class.
- Functions are objects in scala.

A function, that does not return anything can return a Unit that is equivalent to void in Java and indicates that function does not return anything.

```Scala
e.g.
    object Hello{
       def printMe( ) : Unit = {
           println("Hello, Scala!")
        }
    }
```

**Anonymous Function:**  
You can define an anonymous function (i.e. no name) that returns a given integer plus one:  

```Scala  
(x: Int) => x + 1
```

On the left of => is a list of parameters. On the right is an expression involving the parameters.

**You can also name functions:**

```Scala
val add = (x: Int, y: Int) => x + y
println(add(1, 2))
```

#### call-by-name parameter:

A ***call-by-name*** mechanism passes a code block to the call and each time the call accesses the parameter, the code block is executed and the value is calculated.  
It is used if we need to write a function that accepts as a parameter an expression that we don't want evaluated until it's called within our function.  
**Call by name parameter** is not evaluated until it is called and not when it is passed & they are evaluated every time they are encountered.  

```Scala
e.g.
    object Demo {
       def main(args: Array[String]) {
           delayed(time());
       }

    def time() = {
       println("Getting time in nano seconds")
       System.nanoTime
    }

    def delayed( t: => Long ) = {
       println("In delayed method")
       println("Param: " + t)
    }
}
```

Another high level example:

```Scala
    class ui {
       def updateUIElements() {
           runInThread {
                applyDiscountToBasket(basket)
                updateCustomerBasket(basket)
            }

           runInThread {
                updateOfferFor(customer)
            }
        }

        def runInThread(function: => Unit) {
            new Thread() {
               override def run(): Unit = function
           }.start()
        }
    }
```

##### Functions-with-named-arguments:

Named arguments allow you to pass arguments to a function in a different order.   
The syntax is simply that each argument is preceded by a parameter name and an equals sign.

```Scala
e.g.
	object Demo {
	   def main(args: Array[String]) {
		  printInt(b = 5, a = 7);
	   }

	   def printInt( a:Int, b:Int ) = {
		  println("Value of a : " + a );
		  println("Value of b : " + b );
	   }
}
```

##### Functions with variable arguments

Array[String] can be written as String*

e.g. def main(args: String*)  is same as def main(args: Array[String])

##### Default parameter values for function

Scala lets you specify default values for function parameters.
The argument for such a parameter can optionally be omitted from a function call, in which case the corresponding argument will be filled in with the default.

```Scala
e.g.
def main(args: Array[String]) {
  println( "Returned Value : " + addInt() );
 }

 def addInt( a:Int = 5, b:Int = 7 ) : Int = {
  var sum:Int = 0
  sum = a + b
  sum
 }
```

##### Higher order function

- A function whose return value is a function.
- A function with a parameter that is a function.

```Scala
e.g.
	object Demo {
	   def main(args: Array[String]) {
		  println( apply( layout, 10) )
	   }

	   def apply(f: Int => String, v: Int) = f(v)

	   def layout[A](x: A) = "[" + x.toString() + "]"
	}
```

Also,  
apply(a, b) -> object(a, b)  
while,  
unapply(object(a, b)) -> a, b

##### Currying

Group parameters to a function and then specify values to some of them.  
Currying transforms a function that takes multiple parameters into a chain of functions, each taking a single parameter.  

```Scala
e.g.
	Syntax
		def strcat(s1: String)(s2: String) = s1 + s2

	Calling
		strcat("foo")("bar")
```

>f(a, b) -> a + b for this statement the same can be mentioned as f(a) that returns a function f' such that f'(b) -> a + b
so to say that f(a) returns function f' which is applied on second argument b and so on for rest of the arguments (if there are more arguments)
the same can be represented (by removing f') as f(a)(b) where f(a) can be visualized as returning f' making this as f'(b).
Scala supports this currying by returning a function f' on first argument so as to maintain equation intact.

```Scala
Another Example:
class ui {
	def updateUiElements() {
		runInThreadGroup("basket") {
			applyDiscountToBasket("basket")
			updateCustomerBasket("basket")
		}

		runInThreadGroup("customer") {
			updateOfferFor("customer")
		}
	}

	def runInThreadGroup(group: String)(function: => Unit) {
		new Thread(new ThreadGroup(group), new Runnable() {
			def run(): Unit = function
		}).start()
	}
}
```

### Scala Class

The class name works as a class constructor which can take a number of parameters.
Following is a simple syntax to define a basic class in Scala.

- This class defines two variables x and y and a method: move, which does not return a value.
- You can create objects using a keyword new and then you can access class fields and methods.

``` Scala
    class Point (xc: Int, yc: Int) {
        var x: Int = xc
        var y: Int = yc

    def move(dx: Int, dy: Int) {
        x = x + dx
        y = y + dy

        println("X location:" + x)
        println("Y location:" + y)
     }
   }

   object Demo {
       def main(args: Array[String]]) {
          val pt = new Point(10, 20)
          pt.move(10,10)
       }
  }
```

Anonymous way to instantiate class:

```Scala
   val discountedCustomer: DiscountedCustomer = new DiscountedCustomer {
       private final val basket = new ShoppingBasket

    def total: Double = {
       basket.value*0.90
    }
}
```

#### Classes and Objects

All fields and methods in a class are by default **public**.  
You can instantiate objects, or class instances, using ***new***.  

```Scala
e.g. val str = new Array[String](3)  
        OR
     val str: Array[String] = new Array[String](3)
```

```Scala
e.g.

class Customer(val name: String, val address: String) {	} 

    //This is primary constructor with two parameters.
    //If no modifier is specified then the field is public
    //The fields name and address  are called as class parameters, when class parameters are difined with val or var they are converted into class fields.
    //It is possible to have default values for class parameter.

object Customer {
    def main(args: Array[String]) {
        val eric = new Customer("Eric", "29 Acacia Road")
    }
}

```

1. If **val** is used for variable, then **public getter** is created but **no setter** is created, the value can be set by constructor.
2. If **var** is used for variable, then **both public getter and setter** are created, the value can be set by setter or by constructor.
3. If **neither val or var** is used then **no methods** are generated and the value can only be used within scope of the **primary constructor**.

**To override the generated names:**

1. Rename the field
2. Make it as private
3. Recreate setter and getter.

> ***Primary constructor is the only constructor that can invoke a base class constructor.***

#### Auxiallary constructor

Use of ***this*** to create auxiallary constructor

```Scala
    def this(first: String, last: String) {
       this(first, "", last)
    }

    -----OR------

    def this(first: String, last: String) = this (first, "", last)
```

#### Companion Objects

You can combine classes and objects in scala.  
When you **create class and object** with ***same name in same source file*** then object is known as companion object.  
You use companion objects where you would mix static and non static.  

```Scala
class Customer(val name: String, val address: String) {
    private val id = Customer.nextId()
}

object Customer {
    private var sequenceOfIds = 0

    private def nextId() {
       sequenceOfIds += 1
       sequenceOfIds
   }
}
```

Companion objects are used to distinguish between methods and functions but keep the related functions close to a class they are related to.

#### Extending class

You can extend a base Scala class and you can design an inherited class in the same way you do it in Java (use extends key word), but there are two restrictions:

- method overriding requires the override keyword.
- only the primary constructor can pass parameters to the base constructor.

e.g.

```Scala

class Point (xc: Int, yc: Int) {
      var x: Int = xc
      var y: Int = yc

      def move(dx: Int, dy: Int) {
        x = x + dx
        y = y + dy

        println("X location:" + x)
        println("Y location:" + y)
      }
    }

    class Location (override val xc: Int, override val yc: Int, val zc: Int) extends Point(xc, yc) {
      var z: Int = zc

      def move(dx: Int, dy: Int, dz: Int) {
        x = x + dx
        y = y + dy
        z = z + dz

        println("X location:" + x)
        println("Y location:" + y)
        println("Z location:" + z)
      }
    }

    object demo {
      def main(args: Array[String]]) {
        val loc = new Location(10, 20, 15)
        loc.move(10, 10, 10)
      }
    }
```

#### Singleton Objects

Scala is more object-oriented than Java because in Scala, we cannot have static members. Instead, Scala has singleton objects.

  You create singleton using the keyword **object** instead of class keyword. It is language feature now.

  Since you can't instantiate a singleton object, you can't pass parameters to the primary constructor.

  Objects are single instances of their own definitions. You can think of them as singletons of their own classes.  
  You can define objects with the object keyword.

  ```Scala

    object IdFactory {
        private var counter = 0
        def create(): Int = {
           counter += 1
           counter
        }
    }
```

Scala does not have static keyword but **members of singleton object are effectively static**.  
***Functions generally belong to singleton objects rather than class.***

### Inheritance

Inheritance in scala can be from class or from traits.  
Like java a scala class can have only a single super class, but it can mix in as many traits as required.  

```Scala
class DiscountedCustomer(name: String, address: String) extends Customer(name, address) {
        override def total: Double = {
           super.total * 0.90
        }
}

//The base class constructor Customer(name, address) is invoked by primary constructor of the derived class DiscountedCustomer(name: String, address: String)

object DiscountedCustomer {
    def main(args: Array[String]) {
        val joe = new DiscountedCustomer("Joe", "128, mark road")
        joe.add(new Item {
            def price = 2.5
        })

        joe.add(new Item {
           def price = 3.5
        })

        println("Joe's basket costs $ " + joe.total)
    }
}
```

In scala you can use the keyword ***abstract*** to denote the class that can not be instantiated but you don't need to qualify methods as such, just leave the implementation off. No implementation here means it is just abstract.

```Scala
        abstract class AbstractCustomer {
            def total : Double  ---------------> Un-implemented method
        }

        class DiscountedCustomer extends AbstractCustomer {
           private final val basket = new ShoppingBasket

           def total: Double = {
                basket.value*0.90
            }
       }
```

### Traits in scala ~= Interfaces in java

```Scala
    //java
    public interface Readable {
       public int read(CharBuffer buffer);
    }

    //scala
    trait Readable {
       def read(buffer: CharBuffer): Int
    }

    //To implement this trait in scala, use extends keyword e.g.:

    class FileReader(file: File) extends Readable with AutoCloseable{
        def read(buffer: CharBuffer): Int = {
            val readLines: Int = 0
            //....
            readLines
        }

    def close(): Unit = ???

    //In scala, you use 'with' keyword to add additional traits (& then add additional methods)
}
```

Traits can have both abstract and concrete methods and have state.  
A class can implement any number of traits just as a class can implement any number of interfaces.  
Traits can not have constructor arguments.  

Scala allows class to extend more than one trait and uses **process of linearization** to resolve duplicate methods in traits:

- specifically scala puts all the traits in a line and resolves calls to super while going from right to left along the line.
- which means that the order you define traits in a class definition is important.

#### Default implementation in trait

```Scala

   trait Sortable[A <: Orderd[A]] extends Iterable[A] {
     //Generic type A must be subtype of Ordered, symbol <: indicates upperbound.
       def sort: Seq[A] = {
           this.toList.sorted
       }
    }

usage:
    class Customers extends Sortable[Customer] {
        private val customers = mutable.Set[Customer]()

        def add(customer: Customer) = customers.add(customer)
        def Iterator: Iterator[Customer] = customers.iterator
   }
```

### Types & Type Inference

Scala employs *local type inference*, that helps scala to guess or infer the type of the variable in code.
It helps programmers to not specify the types of variables, function return types, type parameters to generic functions.

Everything in scala: all values and variables are instances of a class.

***Any*** is universal base class in scala.  
**Any** is the supertype of all types, also called the **top type**.  
It defines certain universal methods such as **equals**, **hashCode**, and **toString**.  
**Any** has two direct subclasses: **AnyVal** and **AnyRef**.

***AnyVal*** descends from **Any** and is base for all *Java value types.*  
**AnyVal** represents value types.
There are nine predefined value types and they are non-nullable: *Double, Float, Long, Int, Short, Byte, Char, Unit, and Boolean*.  

**Unit** is a value type which carries no meaningful information it is equivalent to **void**.
All functions must return something so sometimes Unit is a useful return type.

***AnyRef*** also descends from **Any** and is base for *all Java reference types*. It is an alias for **java.lang.Object.**  
These two are interchangeable, it supplies default implementation for toString, Equals and hashCode for all reference types.  
**AnyRef** represents reference types. All non-value types are defined as reference types.  
Every user-defined type in Scala is a subtype of **AnyRef**.

***None*** is a value in scala (not type) while ***Nothing*** is a type (not value) that is inherited from **Any**

***Scala.Null*** is at bottom of all reference hierarchy. **Null** extends all reference types.  
***Scala.Nothing*** is at bottom of all value types (Short, Char, Int etc), it extends all value types and **Scala.Null** as well.

== will delegate the call to equals().
> i.e. new String("A") == new String("A") same as *new String("B").equals(new String("B"))*

For more details [refer this.](https://docs.scala-lang.org/tour/unified-types.html)

**Emptiness in Scala:**

- **null** : same as in java, this is for reference type only and not for value type. It itself is a value and not a type.
- **Null** : It is a type, it is a trait and not a value. *null* is a type of **Null**.
- **Nothing** : It is a type, it is a trait. **Nothing** can never be instantiated. **Nothing extends everything in Scala** as it is bottom of all types & reference.
- **Nil** : It is a special value associated with an empty List. Nil is a singletone instance of List[Nothing]  
 Lists are internally implmented as singly linked list. Nil is used to signify the end of the list e.g. while (listIter != Nil) .......
- **None** : None is a special value associated with an Option (Option is a type safe way of representing in scala that a value may or may not be present)
- **Unit** : It is same as **void** in java.

### Options

- Used to indicate presence or absence of a value.  
- If value is absent then Option will take special value None.
- If value is present then Option will be instance of Some. **Some** and **None** are both values that can be tested against using pattern matching or other mechanism in scala.  
- In order to extract a value from the result of an Option, the programmer must specify a plan B

```Scala
val piOption = fraction(22, 7)
val pi = piOption getOrElse "Oops, pi should be 3.14"
```

- Another way of extracting the value is via a match statement

```Scala
piOption match
{
case Some(pi) => pi
case None => "Something bad happened"
}
```

#### Pattern matching

There is no switch statement in scala, it uses match expressions instead. It is match expression, hence like other expressions it can be rvalue
and can be chained.
It is similar to switch statements.</br>
There is no fall through so at most one pattern matches.</br>
There are no break statements in scala.</br>
Matches can be on type, value or condition.</br>

It looks like this:

```Scala
value match {
    case pattern guard => expression
    case ...
    case ...
}
```

Each case is made up of **patterns**, optionally a **guard condition** and **an expression** to evaluate on successful match.

```Scala
val typeOfDay = dayOfWeek match {
        case "Monday" => "First day of week"
        case "Tuesday" | "Wednesday" | "Thursday" | "Friday" => "Mid week days"
        case "Saturday"|"Sunday" => "Weekend"
   }

The second and third case are OR-ed expressions, they form compound ORed condition.
```

If no value matches then error would occur (Scala.MatchError), so need to set up catch-all.

**Value binding pattern:**
When none of existing case expressions match the input the value binding pattern can be used :

```Scala
val typeOfDay = dayOfWeek match {
    case "Monday" => "First day of week"
    case "Saturday"|"Sunday" => "Weekend"
    case someOtherDay => {
        someOtherDay
    }
    case _ => {
        println("Error")
    }
}
```

**case expression on type of variable:**
The expression in case evaluates to true if the type of the variable matches to that in case.

```Scala
    val radius: Any = 10
    val typeOfRadius = radius match {
        case radius: Int => "Integer"
        case radius: String => "String"
        case radius: Double => "Double"
        case _ => "Any"
    }
```

### Scala Containers: Tuples, Lists, Maps, Options, Arrays, Mutable Collections

**Immutable collections:**
Neither collection length nor can it's contents be changed.

**Mutable Collections:**
Collection length as well as contents can be changed.  
They reside in **scala.collection.mutable** namespace.

**Arrays:**

Fixed length, however contents can be modified.  
Arrays are simply instances of classes like any other class in Scala.  
Both mutable and immutable collections implement java **iterable** interface.  
Arrays in Scala are accessed by placing the index inside parentheses.

```Scala
Array example: val greetStrings = new Array[String](3)

//Accessing array:
greetStrings(0) = "Hello"
greetStrings(1) = ", "
greetStrings(2) = "world!\n"

//Iterating array
for(i <- 0 to 2) println(greetStrings(i))
```

When you apply parentheses surrounding one or more values to a variable, Scala will transform the code into an invocation of a method named apply on that variable. So **greetStrings(i)** gets transformed into **greetStrings.apply(i)**. Thus accessing an element of an array in Scala is simply a method call like any other.

#### Tuples

- They are same as tuples in math. They are bunch of values enclosed within parentheses.
- They are ordered containers of values of same or different types.
- They are not technically collections.
- Tuples are indexed starting with 1 and not 0.
- Tuples are immutable, any transformation on it results in new tuple.
- Tuples implement traits Tuple1, Tuple2 .....

```Scala
   e.g.
       val personInfo = ("Vitthal", "Srinivasan", 36, "M")
       val genderPair = "Vitthal" -> "M"  //This is key value pair forming a Tuple.
```

- Two value tuple is nothing but a pair which can be created using **->**
- Scala's type inference identifies the type of elements in tuple.
- Tuples are created for ease of creating them and to pass around.

**Accessing element in Tuple:**

1. In order to access the individual element in tuple, ._ (dot underscore) notation is used.

```Scala
e.g.
    personInfo._1 gives "Vitthal"
    personInfo._2 gives "Srinivasan"
```

2.Tuple can be assigned to list of variables on left side.

```Scala
e.g.
val (firstName, lastName, age, gender) = personInfo
```

You can use placeholder _ to ignore any specific value:

```Scala
e.g.
val (firstName, lastName, _, gender) = personInfo    ------------- age is ignored
```

**Iterating Tuples:**  
Since tuple is not a collection per say, the syntax to iterate it is different.
You need to use &lt;&lt;tupleName&gt;&gt;.productIterator.foreach{&lt;&lt;&gt;&gt;} syntax

```Scala
e.g.
personInfo.productIterator.foreach{i => println("value:" + i)}
```

**To get number of elements in tuple:**  
Use **productArity**

```Scala
e.g. personInfo.productArity     --------------------- gives 4
```

**Passing tuples to functions:**  
Call the .tupled() method on the function object.

```Scala
e.g.
val genderPair = "Vitthal" -> "M"
def printPersonGender(name: String, gender: String) = println(s"Name is $name and gender is $gender")

To call it using tuple:
            (printPersonGender _).tupled(genderPair)
            //here method is converted
            //to function object with _
```

#### Lists

- Lists are usually immutable collections but they can be mutable as well.
- Immutable lists are of fixed length and the objects i.e. elements inside the list can not be changed once list is created.
- They are singly linked list and terminated with Nil (special value, technically it is list of nothing i.e. List[Nothing]).
- Lists are indexed starting from 0.

**Ways of creating list:**

1. Cons (constructor operator ::) operator

```Scala
e.g. val weekDays = "Mon" :: "Tue" :: "Wed" :: "Thurs" :: "Fri" :: Nil
```

  It is right associative i.e. it starts at extreme right and works to left i.e. it starts with Nil and keeps on adding elements to its right making it.  
as *Mon -> Tue -> Wed -> Thurs -> Fri -> Nil*  (it is like add element to head of singly linked list)
  It takes element on it's right and add on it to its left.
  This approach is not elegant as it exposed underlying implementation.  
  If the method name ends in a colon, the method is invoked on the right operand. Therefore, in *"Sat" :: weekEndDays*, the :: method is invoked on weekEndDays, passing in "Sat", like this: *weekEndDays.::("Sat")*.

2. Prefered way  

Using List() directly to create List.
> val weekDays = List("Mon", "Tue", "Wed", "Thurs", "Fri")

3. Creating a list by concatinating two lists:

3.1. Using ::: operator  
    This is also right associative  

```Scala
   e.g. val days = weekDays ::: weekendDays
```

3.2. Using ++ operator  

```Scala
   e.g. val days = weekDays ++ weekendDays
```

> The operator ++ can be used with all collections (Traversable elements) not just list.  
> The difference between above methods is ::: operator works only with lists but ++ operator works with any Traversable.

3.3. Using flatten method  
It takes list of lists and combine or squeeze, or flatten all those elements into one single large list

```Scala
val daysAgain = List(weekDays, weekendDays).flatten
```

3.4. Using zip method : list of tuples  

```Scala
    dayIndices zip dayIndices
    creates list like List((1,1), (2,2), (3,3), (4,4))
```

Each element is a tuple of the corresponding elements of the two lists.  

> Class List does offer an "append" operation — it's written **:+**
> But this operation is rarely used, because the time it takes to append to a list grows linearly with the size of the list, whereas prepending with :: takes constant time.

**List Methods:**  

- **.head** : returns the element at head of the list (weekDays.head)
- **.tail** : returns the list of all elements in original list except the first i.e. all elements except head element.
- **.size** : returns the size of the list.
- **.reverse** : gives back another list but elements in reverse order.
- **.drop &lt;count&gt;** : drops count number of elements starting from left (e.g. weekDays drop 2)
- **.distinct** : returns distinct values (weekDays.distinct)
- **.slice** : returns a new list, subset of the old one (e.g. weekDays slice (2, 4) returns Wed, Thurs 2 is non inclusive and 4 is inclusive)
- **.splitAt** : returns 2 new lists (weekDays.splitAt(2) returns (Mon, Tue) and (wed, Thur, Fri))
- **.take** : returns a new list starting at the head (e.g. weekDays take 2 returns (Mon, Tue))
- **.sorted** : returns a new list sorted in "natural" order (e.g. weekDays.sorted)
- **.contains**
- **.startsWith**
-	**.endsWith**
- **.sum**
- **.product**
- **.min**
- **.max**

**Higher order methods:**
- **foreach**
- **map**
-	**reduce**
-	**filter**
-	**partition**
-	**sortBy**
-	**fold**
-	**scan**

##### Scan family: scan, scanRight, scanLeft
Takes two parameters, first being the initial value and second being the reduce function.  

**Scan right:**
- Scan right is right associative, the initial value is considered as right most & first value in consideration and then subsequently given reduce
- operation is applied moving into list from it's right most values towards first item in list (i.e. nth item towards 1st item in list)
- Initial value provided remains as is as last value (right most) in resultant list.
```Scala
val numbers = List(10, 20, 30, 40, 50, 60)
val result = numbers.scanRight(0)(_ - _)
println(result)	======> List(-30, 40, -20, 50, -10, 60, 0)
```

**Scan left:**
- Scan left is left associative, the initial value is considerd as left most and first value in consideration, and then subsequently given reduce.
- operation is applied movied into list from it's left most values towards right end (1st to nth item in list).
- Initial value provided remains as is as first value (left most) in resultant list.
```Scala
val numbers = List(10, 20, 30 , 40, 50, 60)
val result = numbers.scanLeft(0)(_ - _)
println(result) ======> List(0, -10, -30, -60, -100, -150, -210)
```

**Scan:**
- Is mostly used from optimization perspective and it does not make any gurantee about scan direction, all is left for compiler to decide.

##### Fold family: fold, foldRight, foldLeft 

They can be considered as functions returning the last value of corresponding scan operation.  

**foldRight:**
- provides the last value from scanRight operation.
- As scanRight starts from right most value and moves towards left, the left most value (i.e. in 1st position) in resultant list is the answer.
```Scala
e.g.
val numbers = List(10, 20, 30, 40, 50, 60)
val result = numbers.foldRight(0)(_ - _)        ========> -30
```

**foldLeft:**
- provides the last value from scanLeft operation.
- As scanLeft starts from right most value and moves towards right, the right most value (i.e. in last position) in resultant list is the answer.
```Scala
e.g.
val numbers = List(10, 20, 30, 40, 50, 60)
val result = numbers.scanLeft(0)(_ - _)			=========> -210
```

**fold:**
Is mostly used from optimization perspective and it does not make any gurantee about scan direction. All is left for compiler to decide.

##### Reduce family: reduce, reduceLeft, reduceRight

- Conceptually very close to scan and fold
- Reduce does not take initial value, the operation is carried out between first two (for left reduce) (or last two - for right reduce) elements in list.
- The result is single value as per fold family.

```Scala

e.g.
val numbers = List(10, 20, 30, 40, 50, 60)
val result = numbers.reduceRight(_ - _)   ========> -30

e.g.
val numbers = List(10, 20, 30, 40, 50, 60)
val result = numbers.reduceLeft(_ - _)    =========> -190

```

#### Maps

- Immutable associative containers (associatve because they contain key value pair & key is used to look up the associated value in map).
- Maps in Scala are not language syntax. They are library abstractions that you can extend and adapt.
- Maps are essentially collections of two element tuples i.e. key-value pairs.
- Maps in scala are library abstractions that can be extended per user needs.
- There can be various particular implementations like HashMap, TreeMap or ParMap (Parallel Map - obtained by invoking par method)
- There is base **Map trait** in **scala.collection** package and **mutable trait** in **scala.collection.mutable** and **immutable trait** in **scala.collection.immutable** both **extending** trait in base package.
- Concrete implmentation like HashMap can extend either the mutable or immutable trait.

##### Creating Map

```Scala

val statesCodes = Map("California" -> "CA", ("Vermont", "VT"))

Mutable Map example:
    import scala.collection.mutable

    val pizzaIngredients = Map[Int, String]()
    pizzaIngredients += (1 -> "Pizza Base")
    pizzaIngredients += (2 -> "Sauce")
    pizzaIngredients += (3 -> "Cheese")
    pizzaIngredients += (4 -> "Toppings")
    println(pizzaIngredients)
    println("3rd item:" + pizzaIngredients(3))

    The scala compiler transforms a binary operation expression like 1 -> "Pizza Base" into (1).->("Pizza Base") so here you are calling method named "->" on integer with value 1, passing the string "Pizza Base".

    The method "->" you can invoke on any object in Scala program. It returns a two-element tuple containing the key and value.
    Here, that tuple is passed to "+=" method of the map object: pizzaIngredients.

```

The resulting object is a **scala.collection.immutable.Map**

**Accessing element in Map:**  
*statesCodes("California") returns "CA"*  
If key does not exists in the map then exception is thrown. so check if the element is present before accessing it.  

**contains** : If element is present in the map collection.  
**e.g. statesCodes.contains("California") returns true**

**foreach:**

```Scala

stateCodes.foreach((p: (String, String)) => println(p._1 + "=" + p._2))
returns:
    California=CA
    Vermont=VT

```

**Creating map using two lists:**  
*val stateCodes = (states zip codes).toMap*  
where states and codes are lists with state names and state codes.  

Here, zip will take these two lists and create a third list where every element is a tuple of corresponding elements from two lists: first being key and second being value. Then toMap will convert that list of tuples into map.

**Getting the list of keys from map:**  
val states = stateCodes.keySet.toList

**Getting the list of values from map:**  
val codes = stateCodes.values.toList

#### Sets

Sets are very much similar to that of lists but they are unordered and have uniqueness constraint.  
The Scala API contains a base trait for sets. Scala then provides two subtraits, one for mutable sets and another for immutable sets.  
Concrete set classes in the scala API e.g. HashSet, either extends mutable or immutable Set trait.

Lists, Sets and Maps are all immutable collections. They can not grow or shrink neither the collection elements can be changed/modified.  
There are corresponding mutable set of collections for each of them, they can shrunk/grow and their elements can be modified too.  

```Scala
Set Heirarchy:
scala.collection.immutable.Set <<trait>> extends scala.collection.Set
scala.collection.mutable.Set <<trait>> extends scala.collection.Set

scala.collection.immutable.HashSet extends scala.collection.immutable.HashSet
scala.collection.mutable.HashSet extends scala.collection.mutable.HashSet
```

```Scala
Adding element to mutable set:
example:
   var carSet = Set("Merc", "BMW")
   carSet += "Toyota"               //Use + to add new element to a set.

   As shown here, you can create the Set in scala by invoking apply() on companion object for scala.collection.immutable.set which is same as Set("Merc", "BMW")
   So by default the immutable set gets created.

example: To create a concret Set
    import scala.collection.immutable.HashSet

    val pizzaSet = HashSet("Pizza Base", "Sause")
    pizzaSet += "Cheese"
    println(pizzaSet)
```

On both mutable and immutable sets, the + method will create and return a new set with the element added.  
Although mutable sets offer an actual += method, immutable sets do not.

#### creating mutable collections

>val someNumbers = collection.mutable.Buffer(10, 20, 30, 40, 50, 60)  
>val stateCodes = collection.mutable.Map("California" -> "CA")  
>val stateSet = collection.mutable.Set("California", "Vermont")  

#### To convert the mutable collections to immutable collection

>val someNumbersImmutable = someNumbers.toList  
>val stateCodesImmutable = stateCodes.toMap  
>val stateSetImmutable = stateSet.toSet  

#### Arrays

Fixed lenght but elements can be changed.  
Creating array: val daysOfWeek = Array("Mon", "Tue", "Wed", "Thur", "Fri")  

#### util.Try

To check for success or failure (exception)

```Scala

e.g.
val stateCodes = Map("California" -> "CA", "Vermont" -> "VT")
val stateCodes = util.Try(stateCodes("California"))

stateCode match {
case util.Success(code) => code
case util.Failure(error) => "Something terrible happened!"
}

```

#### Higher Order methods

Higher order methods of collections take in function objects and then go ahead and apply those function objects to the contents of our collection.  

**Categories:**

1. Higher order functions acting one iteam at a time e.g. Map, foreach, filter
2. Higher order functions operating on multiple elements at a time e.g. Scan, Fold, Reduce.


### Exceptions

All exceptions in scala are **runtime exceptions**. Catching exceptions uses pattern matching.  

```Scala

try {
    val url = new URL("http://badwebsite.com")
    val reader = new BufferedReader(new InputStreamReader(url.openStream))
    try {
        var line = reader.readLine
        while(line != null) {
           line = reader.readLine
           println(line)
        }
    } finally {
       reader.close
    }
    } catch {
        case e: MalformedURLException => println("Bad url")
        case e: IOException => println("Problem reading data : " + e.getMessage)
    }

```

### Generics or Type parameter

In java: List&lt;Customer&gt; customers = new ArrayList<>();  

In scala: val customers: List[Customer] = List()

**Generic method:**  
In java: public &lt;A&gt; void add(A a) { ...... }

In scala: def add[A](a: A) { ....... }

**Another example with interface:**  

```Scala

In java:
    public interface Stack&lt;T&gt; {
        T push (T t);
        T pop();
    }

In scala:
    trait Stack[T] {
        def push(t: T): T
        def pop: T
    }

Implementation:
    class ListStack[T]() extends Stack[T] {
        private var elements: List[T] = List()

        override def push(t: T): T = {
            elements = t +: elements
            //as scala's list is immutable, we replaced list instance with new list with element prepended
            t
        }

        override def pop: T = {
            if(elements.isEmpty)
                throw new IndexOutOfBoundsException

            val head = elements.head
            elements = elements.tail
            head
        }

        def main(args: String*) {
            val stack = new ListStack[String]
            stack.push("c")
            stack.push("d")
            stack.push("a")
            val element: String = stack.pop
        }
    }

Also,
    trait Sortable[A <: Ordered[A]] extends Iterable[A] {
        def sort: Seq[A] = {
           this.toList.sorted
        }
    }

```

### Faking function calls

Example of **apply method**

When you apply parentheses surrounding one or more values to a variable, Scala will transform the code into an invocation of a method named **apply** on that variable.  
Any application of an object to some arguments in parentheses will be transformed to an **apply** method call if that type of object actually defines an **apply** method.  
**THIS APPLY METHOD IS DEFINED ON COMPANION OBJECT**

```Scala

Example:
    val str = new Array[String](3)
    val g = str(0) ------> same as str.apply(0)

Another example:
    class Customer(name: String, address: String)
        object Customer {
            def apply(name: String, address: String) = new Customer(name, address)

        def main(args: Array[String]) {
            Customer.apply("First", "Address1")-----|
            Customer("Second", "Address2")     -----|//Both are same, you can drop apply method.
        }
    }

```

There can be multiple apply methods.  
Apply methods can be used as factory methods. They can make any method call look like a function call.  

Apply method can be called on class as well:  
e.g. val add = new Adder()  
     add.apply(1, 3)  
     //apply can be dropped to make it add(1, 3) it makes it look like we are calling add function.

```Scala

Another example:

    class Directory {
        private val numbers = scala.collection.mutable.Map(
            "Rajesh" -> "986532147874",
            "Kedar"  -> "801234578612",
            "Vinay"  -> "782345182690"
        )

        def apply(name: String) = {
            numbers.get(name)
        }
    }

    object Directory {
        def main(args: Array[String]) {
            val yellowPages = new Directory()
            println("Kedar's number is:" + yellowPages("Kedar"))
            println("Vinay's number is:" + yellowPages.apply("Vinay"))
        }
    }

```

val numbers = Array("Zero", "One", "Two")  
Here, actually **apply** method is getting called such as:  
val numbers = Array.apply("Zero", "One", "Two")  
This **apply** method creates and returns a new array. 



Example of **update method**

When an assignment is made to a variable to which parentheses and one or more arguments have been applied, the compiler will transform that into an invocation of an update method that takes the arguments in parentheses as well as the object to the right of the equals sign.

e.g. instance(a) = b is translated as instance.update(a, b)  

Another example: To update a number we can implement an update method and call it directly. With scala's shorthand, using just assignment operator (=), it will call update method directly without calling it implicitly.  
i.e. either yellowPages.update("Vinay","9966558877")  
OR yellowPages("Vinay") = "7788556611"

```Scala

Example:
    val str = new Array[String](3)
    str(0) = "Greetings" -------> Same as str.update(0, "Greetings")

Another Example:
    class Directory {
        private val numbers = scala.collection.mutable.Map(
           "Rajesh" -> "986532147874",
           "Kedar"  -> "801234578612",
           "Vinay"  -> "782345182690")

        def apply(name: String) = {
            numbers.get(name)
        }

        def update(name: String, number: String) = {
            numbers.update(name, number)
        }
    }

    object Directory {
        def main(args: Array[String]) {
            val yellowPages = new Directory
            println("Kedar's number is:" + yellowPages("Kedar"))
            println("Vinay's number is:" + yellowPages.apply("Vinay"))

            yellowPages.update("Vinay","9966558877")
            println("Vinay's 1st updated number is:" + yellowPages("Vinay"))
            yellowPages("Vinay") = "7788556611"
            println("Vinay's 2nd updated number is:" + yellowPages("Vinay"))
        }
    }

```

#### Faking language constructs in Scala

**Curly braces** rule:  
In any method call, in which you pass in exactly one argument, you can use curly braces to surround that argument instead of parentheses.

```Scala

e.g. val numerals = List("I", "II", "III", "IV", "V")  
you can write  
        numerals.foreach(println(_))  
        as well as  
        numerals.foreach{  
            println(_)  
        }

```

### Map - Map is transforming function

For collections, it iterates over the collection applying some function similar to foreach method.

But unlike foreach, map will collect values from the function into **new collection and return it**.  

Map transforms the collection optionally i.e. it will if collection has values and it will not if collection is empty, prevents null checks.

```Scala

Map function example:
    import java.util.Calendar

    def age(birthYear: Int) = {
        Calender.getInstance.get(Calendar.YEAR) - birthYear
    }

    val birthDays = List(1990, 1977, 1988, 1980)
    birthDays.map(age)

    -------OR-------
    birthDays.map(year => Calender.getInstance.get(Calendar.YEAR) - year)

```

Given Collection[A]  

```Scala

map(f: A => B): List[B]  
flatMap(f: A => List[B]): List[B]

def ages(birthYear : Int): List[Int] = {
    val today = Calendar.getInstance.get(Calendar.YEAR)
    List(today - 1 - birthYear, today - birthYear, today + 1 - birthYear)
}

```

birthDays.map(ages)  //This returns List[List[Int]]

flatMap flattens the resultant list so that result is List[Int] (& it removes None from the collection so resultant is some value for sure)

birthDays.flatMap(ages)  //This returns List[Int]

**flatMap maps and then flattens the result.**

#### For comprehensions

```Scala

    object CustomerDatabase {
        val customers = Customers()
        val albertz = Customer("Albert", Some(Address("1a Bridge rd", None))
        val berts = Customer("Berts", None)
        val carol = Customer("Carol", Some(Address("1a Finac rd", Some("AL1"))
        val sherlock = Customer("Sherlock", Some(Address("21b Baker st", Some("6XE"))

        customers.add(albertz)
        customers.add(berts)
        customers.add(carol)
        customers.add(sherlock)
    }

    object Example {
        val all = Set("Albert","Berts","Carol","Sherlock","John","Erin")

        def generateShippingLabels() = {
            all.flatMap {
                name => customers.find(name).flatMap {
                    customer => customer.address.flatMap {
                        address => address.postCode.map {
                           postCode => shippingLabel(name, address.street, postCode)
                        }
                    }
                }
            }
        }

        def main(args: Array[String]) {
            println(generateShippingLabels())
        }
    }

The above can be implemented using for syntax as:

    def generateShippingLabels() = {
        for {
            name <- all                             //flatMap
            customer <- customers.find(name)        //flatMap
            address <- customer.address             //flatMap
            postCode <- address.postCode            //map
        } yield {
            shippingLabel(name, address.street, postCode)  //mapping function
        }
    }

```

### Case Classes

Scala has a special type of class called a “case” class. By default, **case classes are immutable and compared by value**.  

e.g. **case class Point(x: Int, y: Int)**  

You can instantiate case classes without new keyword.

```Scala

    val point = Point(1, 2)
    val anotherPoint = Point(1, 2)
    val yetAnotherPoint = Point(2, 2)

```

And they are compared by value.

```Scala

    if (point == anotherPoint) {
        println(point + " and " + anotherPoint + " are the same.")
    } else {
        println(point + " and " + anotherPoint + " are different.")
    }

```

### Multi-threading

Java comes with a rich, thread-based concurrency library. Scala programs can use it like any other Java API.

However, Scala also offers an additional library that essentially implements Erlang's actor model.

Actors are **concurrency abstractions** that can be implemented on top of threads.
They communicate by **sending messages** to each other.
An actor can perform two basic operations: **message send** and **receive**.  

The **send** operation is denoted by ! (exclamation mark) and it sends message to an Actor e.g. messageReceiver ! msg, here messageReceiver is an Actor.  
A **send is asynchronous**; that is, the sending actor can proceed immediately, without waiting for the message to be received and processed.


Every **actor has a mailbox** in which incoming messages are queued. An actor handles messages that have arrived in its mailbox via a **receive** block.

```Scala

def receive {
    case Msg1 => ... // handle Msg1
    case Msg2 => ... // handle Msg2
    // ...
}

```

A receive block can contain number of cases that each query the mailbox with a pattern - message pattern. As per pattern matching, the first message in the mailbox that matches the case is selected and associated action to it is performed.  
Once all messages in mailbox are processed, actor suspends and wait for new incoming messages.

### Functional programming

In functional programming, the methods should not have any **side effects**. They should communicate with their surrounding only by accepting the input and providing the result.  
Such methods can be called as Referentially transparent - meaning that for any given input the method call could be replaced by it's result without affecting the semantics of the program.  
Functional languages encourage immutable data structures and referentially transparent methods.  
A method's only act should be to compute and return a value without any side effect (following SRP - Single Responsibility Principle). That way methods become reliable and reusable.

If you are using vars in code, it is probably not in functional style.  
A function with Unit as a return type could be the function with side effects: If a function is not returning any interesting value then the only way the function can make difference is through some kind of side effect.
