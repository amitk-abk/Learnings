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

- Scala is a line-oriented language where statements may be terminated by semicolons (;) or newlines. Semicolon is usually optional unless there are multiple statements on single line e.g. val s = "go"; doThis(s)
> A semicolon at the end of a statement is usually optional.

- A multi-line string literal is a sequence of characters enclosed in triple quotes """ ... """. This is also called as "raw strings".

The sequence of characters is arbitrary, except that it may contain three or more consecutive quote characters only at the very end.

- The null value is of type scala.Null and is thus compatible with every reference type.

It denotes a reference value which refers to a special "null" object.

- Immutability is norm in Scala.

Entities are declared as **immutable** using **'val'**.  
e.g. **val PI = 3.14**  OR  **val PI:Double = 3.14** though type specification is optional.  
This declares immutable variable called PI.

  > Commonly used collections are immutable too.  
  > Modifying an immutable collection returns a new collection, leaving the original unchanged.

If you prefix a *val* definition with a *lazy* modifier, the initializing expression on the right-hand side will only be evaluated the first time the *val* is used.

```Scala
    def main(args: Array[String]): Unit = {
        lazy val x = { println("Initializing x"); 5}

        println("-------------------------------------")
        val y = { println("Initializing Y"); 15}
    }

    //prints "Initializing Y"
    //The initialization of x is deferred until the first time x is used
```

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
  String resides in java.lang package and rest others are part of scala package. Scala's basic types have exact same range as of corresponding java types.

- Scala does not support break or continue statement like Java does.

- String interpolation: It allows programmers to embed references, expressions to string variables inside string literals.

```Scala
    e.g. val greet = "hello"
    val name = "Mark"
    s "$greet $name, have a great day!"

    s "The answer to calculation is ${45 * 96.7}"
    Scala will substitute the values for $greet and $name.
```

You can place any expression after a dollar sign ($) in a processed string literal.  
Scala provides two other string interpolators by default: raw and f. The raw string interpolator behaves like s, except it does not recognize character literal escape sequences.  
The f string interpolator allows you to attach printf-style formatting instructions to embedded expressions.  
**In Scala, string interpolation is implemented by rewriting code at compile time.**

- you can instantiate objects, or class instances, using ***new***.  

- Most of the scala operators are just syntax for ordinary method calls e.g. 1 + 5 actually means 1.+(5). It also means, class Int contains a method named **+** that takes an **Int** and returns an **Int** result. Actually, Int contains several overloaded + methods that take different parameter types e.g. Long, float, double etc.

- In scala **any method call can be operator** as operators are not special language syntax so s.indexOf("abc") can be written in *operator notation* way as s indexOf "ABC" where indexOf is an operator.

- In Scala, the empty parenthesis can be left off e.g. *s.toLowerCase()* can be written as *s.toLowerCase* and also as *s toLowerCase* in *operator notation* form.

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

The if expression, in general, works like if in any other language.

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
Generally, a for expression is expressed as form: ***for(seq) yield expr***,.Here, seq is a sequence of *generators, definitions, and filters*, with semicolons between successive elements.  
A **for loop with *yield*** will 'yield' a collection of the return values of ***each iteration*** of the loop.

```Scala
var x = for (day <- daysOfWeekList) yield {
        day match {
          case "Mon" => "Monday, first day"
          case "sun" => "Sunday, last day"
        }
      }

Returns>> x: List[String] = List("Monday, first day", "Tue", "Wed", "Thur", "Fri", "Sat", "Sunday, last day")

Also,

def getFilesMatching(query: String, matcher: (String, String) => boolean) = {
    for (fileName <- filesListed; if matcher(fileName, query))
        yield fileName
}

Above function can be called as:
    def getFilesNameEndingWith(query: String) = getFilesMatching(query, _.endsWith(_))

    def getFilesNameContaining(query: String) = getFilesMatching(query, _.contains(_))
  
    def getFilesNameMatchingRegex(query: String) = getFilesMatching(query, _.matches(_))

Here, the function literal _.endsWith(_), used in the getFilesNameEndingWith method, means the same thing as:
    (fileName: String, query: String) => fileName.endsWith(query)

    The first underscore is a placeholder for the first parameter, the file name, and the second underscore a placeholder for the second parameter, the query string.

In following, for expression contains one generator, one definition and one filter:
    for (p <- persons; n = p.name; if (n startsWith "To"))
        yield n

    The same can be written as:
        for {
            p <- persons              // a generator
            n = p.name                // a definition
            if (n startsWith "To")    // a filter
        } yield n
```

The result includes all of the yielded values contained in a single collection. And, the type of the resulting collection is based on the kind of collections processed in the iteration clauses.  

The syntax of a for-yield expression is like: ***for clauses yield loop***.  

Every for expression starts with a generator.  
If there are several generators in a for expression, later generators vary more rapidly than earlier ones.  

```Scala
    for (x <- List(1, 2); y <- List("one", "two"))
         yield (x, y)

    Result:List[(Int, String)] = List((1,one), (1,two), (2,one), (2,two))
```

Basic **for expression:**  
e.g. for(item <- items>) println(item)  
Here, the println is applied to every item from items, both are on the either side of symbol <-  
You can say "in" for the <- symbol. You can read ***for (item <- items)*** , therefore, as "for item in items."  

Sometimes you don't want to iterate through a collection in its entirety; you want to filter it down to some subset. You can do this with a for expression by adding a filter, an if clause inside the for's parentheses.  
e.g. val filesHere = (new java.io.File(".")).listFiles  
    for (file <- filesHere if file.getName.endsWith(".scala"))  
      println(file)  

You can include more filters if you want.  

**While loop**
Scala's while loop behaves as in other languages. It has a condition and a body, and the body is executed over and over as long as the condition holds true.  
Scala also has a do-while loop.  
The while and do-while constructs are called "loops," not expressions, because they don't result in an interesting value.

> **Almost all of Scala's control structures result in some value.** Scala's ***if, for, try and match*** can result in value.

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
- Every function value is an instance of some class that extends one of several FunctionN traits in package scala, such as Function0 for functions with no parameters, Function1 for functions with one parameter, and so on.
- Function definitions start with **def**, the function's name is followed by a comma-separated list of parameters in parentheses. A type annotation must follow every function parameter, preceded by a colon (e.g. x: Int, y: Int), because the Scala compiler does not infer function parameter types. After that parameter list separated with : is return type (e.g. : Int).
- If the function you're calling performs an operation, use the parentheses. But if it merely provides access to a property, leave the parentheses off.

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

#### call-by-name parameter

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

##### Functions-with-named-arguments

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

Another example: (This is also example of loan pattern or execute around pattern)
    def withPrintWriterForFile(fileToProcess: File)(fileOperation: PrintWriter => Unit) = {
        val writer = new PrintWriter(fileToProcess)
        try {
            fileOperation(writer)
        } finally {
            writer.close()
        }
    }

    Calling:
        val fileToProcess = new File("timestamp.txt")
        withPrintWriterForFile(fileToProcess) { writer => writer.println(new java.util.Date)
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

**To override the default implementation in class**: Use **override** modifier in front of a method definition.

```Scala
    class Adder(x: Int, y: Int) {
        override def toString() = "Adding " + x + " and " + y
    }
```

Scala has two **namespaces**:  

1. values: For fields, methods, packages and singleton objects.
2. types: For class and trait names

Scala places fields and methods into the same namespace and that is why user can override a parameterless method with a *val*

#### Classes and Objects

All fields and methods in a class are by default **public**.  
You can instantiate objects, or class instances, using ***new***.  
Scala classes do not have "static" members.  
In Scala, you can define classes and singleton objects inside other classes and singleton objects.  

```Scala
e.g. val str = new Array[String](3)  
        OR
     val str: Array[String] = new Array[String](3)
```

```Scala
e.g.

class Customer(val name: String, val address: String) { }

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

The **private** constructor:

The primary constructor can be hidden by declaring class parameter list as private & adding private modifier in front of the class parameter list. It makes the constructore as private: it can be accessed only from within the class itself and its companion object.

```Scala

    class Person private (private val name: String, private val age: Int)

    //It privents call of constructor to create object. Following gives error: val p: Person = new Person("A", 20)
    //So use auxiliary constructor instead.
```

#### Auxiliary constructor

Constructors other than the primary constructor are called auxiliary constructors.  
Use ***this*** to create Auxiliary constructor.  
Auxiliary constructors in Scala start with ***def this(...)***.

```Scala
    def this(first: String, last: String) {
       this(first, "", last)
    }

    -----OR------

    def this(first: String, last: String) = this (first, "", last)
```

Every auxiliary constructor must have call to another constructor of the same class as its first statement. The invoked constructor can be main or another auxiliary one.  
In scala, only primary constructor can invoke the superclass constructor.

#### Companion Objects

You can combine classes and objects in scala.  
When you **create class and object** with ***same name in same source file*** then object is known as companion object. And the class is called as **companion class** of the singleton object.  
You use companion objects where you would mix static and non static.  

> **A class and its companion object can access each other's private members.**

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

#### Object Equality

To compare two objects for equality, you can use either == or its inverse !=. These operations actually apply to all objects, not just basic types.

```Scala

    e.g. you can use == to compare lists:
    List(1, 2, 3) == List(1, 2, 3)

    you can compare two objects that have different types
    e.g. 1 == 1.0, List(1, 2, 3) == "hello"
```

**Scala provides a facility for comparing reference equality, as well, under the name eq.  

The equality operation == in Scala is designed to be transparent with respect to the type's representation. For value types, it is the natural (numeric or boolean) equality. For reference types other than Java's boxed numeric types, == is treated as an alias of the equals method inherited from Object.

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
A singleton object definition looks like a class definition, except instead of the keyword class you use the keyword object.

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

> One difference between classes and singleton objects is that singleton objects cannot take parameters, whereas classes can: you can't instantiate a singleton object with the new keyword, so you have no way to pass parameters to it.

### Scala Application

To run a scala program, provide the name of standalone singleton object with a main function that takes Array[String] as parameter and has a return type of Unit.

```Scala
example:
    object adder {
        def main(args: Array[String]): Unit = {
            var sum = 0
            for (arg <- args>)
                sum += arg
            println(sum)
        }
    }
```

> Scala implicitly imports members of packages **java.lang** and **scala**, as well as the members of a singleton object named **Predef** (which resides in package *scala*), into every Scala source file.

And,
> In contrast to java, the name of the file can be anything with extension being fixed as .scala. So you can name .scala files anything you want irrespective of the code that goes in it. Though recommended practise is as followed in java source file naming convention.

And,
> Scala distribution typically include fsc (fast scala compiler daemon).

Running either of **scalac** or **fsc** commands will produce Java class files that you can then run via the scala command

### Inheritance

Inheritance in scala can be from class or from traits.  
Like java a scala class can have only a single super class, but it can mix in as many traits as required.  
Like java in scala, user can add ***final*** modifier keyword before member to ensure that it can not be overridden by subclasses.  
To ensure that an entire class not be subclassed, add a ***final*** modifier to the class declaration.  

```Scala
class Customer(name: String, address:String) {
    def total: Double = {
        1.0
    }

    final def printDetails(): Unit = {
        println("Customer name:" + name)
        println("Customer address:" + address)
    }
}

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

In scala you can use the keyword ***abstract*** to denote the class that can not be instantiated but you don't need to qualify methods as such, just leave the implementation off. No implementation here means it is just abstract (which is unlike java).

```Scala
        abstract class AbstractCustomer {
            def total : Double  ---------------> Un-implemented method *declared* here
        }

        class DiscountedCustomer extends AbstractCustomer {
           private final val basket = new ShoppingBasket

           def total: Double = {
                basket.value*0.90
            }
       }

    Here the method total is defined as without any parameters, it is called as parameterless-method.
    The recommended convention is to use a parameterless method whenever there are no parameters.
    In principle it's possible to leave out all empty parentheses in Scala function calls.
```

>Abstract method declarations may be implemented by both concrete method definitions and concrete *val* definitions.

### Traits in scala ~= Interfaces in java

Traits in scala are considered very much in line with interfaces (java 8 onwards) in Java. They form a basic unit of code reuse.  
Trait encapsulates method and field definitions, which can be reused by mixing them into classes (a class can mix in any number of traits using with or extends keywords).  

```Scala
    A trait definition looks like a class definition in scala. Following is comparision of trait definition and java interface definition.

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
You can use the ***extends*** keyword to mix in a trait; in that case you implicitly inherit the trait's superclass.  
If you wish to mix a trait into a class that explicitly extends a superclass, you use extends to indicate the superclass and ***with*** to mix in the trait.  

Scala allows class to extend more than one trait and uses **process of linearization** to resolve duplicate methods in traits:

- specifically scala puts all the traits in a line and resolves calls to ***super*** while going from right to left along the line.
- which means that the order you define traits in a class definition is important.
- The ***super*** calls in trait are dynamically bound.
- When you instantiate a class with *new*, Scala takes the class, and all of its inherited classes and traits, and puts them in a *single, linear order*. Then, whenever you call *super* inside one of those classes, the invoked method is the next one up the chain. If all of the methods but the last call super, the net result is stackable behavior.

A trait can ***extend*** another class, which means it declares that class as it's ***superclass*** (superclass to the trait). This declaration means that, this trait can only be mixed into a class that also ***extends*** the ***same class***.

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

***Any*** is universal base class in scala. Every class inherits from this class.  
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
***Scala.Nothing*** is at bottom of all value types (Short, Char, Int etc), it extends all value types and **Scala.Null** as well. Nothing is a subclass of every other class in scala heirarchy. One use of Nothing is that it signals abnormal termination.  

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
and can be chained. It always results in a value.  
It is similar to switch statements from java.  
There is no fall through so at most one pattern matches.  
There are no break statements in scala.  
Matches can be on type, value or condition.  
In match, any kind of constant as well as other things, can be used in cases in scala, not just the integer-type, enum or string constants.  

It looks like this:

```Scala
value match {
    case pattern guard => expression
    case ...
    case ...
    case _ => ......  //This is catch-all (like default)
}

The syntax is: selector match { alternatives }
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
Arrays are simply instances of classes like any other class in Scala. Arrays in Scala are represented as Java arrays.  
Both mutable and immutable collections implement java **iterable** interface.  
Arrays in Scala are accessed by placing the index inside parentheses.  
The ++ operation concatenates two arrays.  

```Scala
Array example: val greetStrings = new Array[String](3)

//Accessing array:
greetStrings(0) = "Hello"
greetStrings(1) = ", "
greetStrings(2) = "world!\n"

//Iterating array
for(i <- 0 to 2) println(greetStrings(i))
```

When you apply parentheses surrounding one or more values to a variable, Scala will transform the code into an invocation of a method named **apply** on that variable. So **greetStrings(i)** gets transformed into **greetStrings.apply(i)**. Thus accessing an element of an array in Scala is simply a method call like any other.

> Scala treats arrays as nonvariant (rigid). So Array[String] is not considered to conform to an Array[Any]

**ArrayBuffer:**

It is similar to Array but addition and removal of elements from beginning and end of the sequense is possible. These operations are constant to linear time on average.  
It is part of scala.collection.mutable package.  
When you create an ArrayBuffer, you must specify a type parameter.  
An element can be appended to it using += method.  
An element can be prepended to it using +=: method.

```Scala
    import scala.collection.mutable.ArrayBuffer

    val numBuff = new ArrayBuffer[Int]()

    //Append operation
    numBuff += 1
    numBuff += 2
    numBuff += 3

    //Prepend operation
    -1 +=: numBuff
    -2 +=: numBuff
    -3 +=: numBuff

    println(numBuff)
    //prints ArrayBuffer(-3, -2, -1, 1, 2, 3)
```

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
- Like Arrays Lists are homogeneous i.e. all the elements of the lists are of same type.
- The lists in scala are covariant i.e. for each pair of types A and B, if A is subtype of B then List[A] is subtype of List[B]. e.g. List[String] is subtype of List[Object].
- The type of empty list is List[Nothing]. Also, List[Nothing] is a subtype of List[T] for any given type T.
- Lists support fast addition and removal of items to the beginning of the list, but they do not provide fast access to arbitrary indexes because the implementation must iterate through the list linearly.  
- Lists are not "built-in" as a language construct in Scala; they are defined by an ***abstract class List*** in the *scala* package, which comes with two subclasses for :: and Nil.

**Ways of creating list:**

1. Cons (constructor operator ::) operator

```Scala
e.g. val weekDays = "Mon" :: "Tue" :: "Wed" :: "Thurs" :: "Fri" :: Nil
```

  It is right associative i.e. it starts at extreme right and works to left i.e. it starts with Nil and keeps on adding elements to its right (head i.e. at the beginning) making it as *Mon -> Tue -> Wed -> Thurs -> Fri -> Nil*  (it is like add element to head of singly linked list)
  It takes element on it's right and add on it to its left.
  This approach is not elegant as it exposed underlying implementation.  
  If the method name ends in a colon, the method is invoked on the right operand. Therefore, in *"Sat" :: weekEndDays*, the :: method is invoked on weekEndDays, passing in "Sat", like this: *weekEndDays.::("Sat")*.
  x :: xs is treated as ::(x, xs) like infix operator. The class ***scala.::*** builds non-empty lists. So, :: exists twice in Scala, once as a name of a class in package scala and again as a method in class List. The effect of the method :: is to produce an instance of the class scala.::.

2.Prefered way  

Using List() directly to create List.
> val weekDays = List("Mon", "Tue", "Wed", "Thurs", "Fri")

3.Creating a list by concatinating two lists:

3.1. Using ::: operator  
    This is also right associative  

```Scala
   e.g. val days = weekDays ::: weekendDays
```

    This is implemented as method in class List.

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

    Array(1, 2, 3) zip Array("a", "b")
    creates Array((1, "a"), (2, "b"))
```

Each element is a tuple of the corresponding elements of the two lists.  
If one of the two operand arrays is longer than the other, zip will drop the remaining elements.  

> Class List does offer an "append" operation — it's written **:+**
> But this operation is rarely used, because the time it takes to append to a list grows linearly with the size of the list, whereas prepending with :: takes constant time.

**Sorting** the list:

It can be denoted by operation ***lst sortWith before***, where lst is the list, sortWith is the method and before is a function that can be used to compare two elements of the list lst.

```Scala
val numList = List(4, 5, 9, 1, 2, -9, -3, -5, 0)
val sortedList = numList sortWith (_ < _)
//Generates List(-9, -5, -3, 0, 1, 2, 4, 5, 9)
```

> The method sortWith performs merge sort.

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
- **.endsWith**
- **.sum**
- **.product**
- **.min**
- **.max**

**Higher order methods:**

- **foreach**
- **map**
- **reduce**
- **filter**
- **partition**
- **sortBy**
- **fold**
- **scan**

***map*** returns a list of lists, ***flatMap*** returns a single list in which all element lists are concatenated.

#### Scan family: scan, scanRight, scanLeft

Takes two parameters, first being the initial value and second being the reduce function.  

**Scan right:**

- Scan right is right associative, the initial value is considered as right most & first value in consideration and then subsequently given reduce
- operation is applied moving into list from it's right most values towards first item in list (i.e. nth item towards 1st item in list)
- Initial value provided remains as is as last value (right most) in resultant list.

```Scala
val numbers = List(10, 20, 30, 40, 50, 60)
val result = numbers.scanRight(0)(_ - _)
println(result) ======> List(-30, 40, -20, 50, -10, 60, 0)
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
val result = numbers.scanLeft(0)(_ - _) =========> -210
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

#### Mutable Lists: ListBuffer

It is mutable list from scala.collection.mutable package.  
ListBuffer provides constant time append and prepend operations.  
Elements can be ***appended*** using += operator and ***prepended*** with +=: operator.  
A List can be obtained by calling toList on ListBuffer.

```Scala
    import scala.collection.mutable.ListBuffer

    val numBuff = new ListBuffer[Int]

    //Append operation
    numBuff += 1
    numBuff += 3
    numBuff += 7

    //Prepend operation
    -1 +=: numBuff
    -5 +=: numBuff
    -7 +=: numBuff

    val primeNumList = numBuff.toList

    //Gets List(-7, -5, -1, 1, 3, 7)
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
The behavior of this try-catch expression is the same as in other languages with exceptions.  
Throwing an exception in Scala looks the same as in Java. You create an exception object and then throw it with the throw keyword.  
Technically, an exception throw has type Nothing.  
As with most other Scala control structures, try-catch-finally results in a value (unlike java which does not result in a value)

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

Example of try-catch-finally returning the value:

    def getUrl(path: String) = {
        try {
            new URL(path)
        } catch {
            case e: MalformedURLException => new URL("http://wikipedia.com/correctURL")
        }
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
Classes with ***case*** modifier are called case classes.  

e.g. **case class Point(x: Int, y: Int)**  

Using the modifier makes the Scala compiler add some syntactic conveniences to your class.  

1. It adds a factory method with the name of the class, which means you can skip ***new*** from class creation e.g. Point p = Point(4, 5)
2. All arguments in the parameter list of a case class implicitly get a val prefix, so they are maintained as fields. So you can access as p.x and p.y
3. The compiler adds "natural" implementations of methods toString, hashCode, and equals to class. In scala, **==** always delegates to ***equals*** so the elements of case class are always compared structurally e.g. p1 ==p2
4. Compiler adds a copy method to class for making modified copies. This method is useful for making a new instance of the class that is the same as another one except that one or two attributes are different e.g. p.copy(4, 5)

```Scala
    You can instantiate case classes without *new* keyword.

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

Case classes are Scala's way to allow pattern matching on objects without requiring a large amount of boilerplate.  

### Implicit Conversions

Implicits are a powerful, code-condensing feature of Scala.  
Implicit definitions are the ones that compiler can insert in the program in order to fix any of type errors that it may encounter.  
For example, if ***t1 - t2*** fails to perform due to type check error, then compiler is allowed to change it to ***transform(t1) - t2***, where ***transform*** does *implicit conversion*. If ***transform*** alters *t1* such that it now has **-** method onto it, then this change may fix the problem so that now it is type compatible to perform ***t1 - t2*** and overall program runs fine.  

The ***implicit*** keyword is used to mark the declarations that compiler can use to perform conversions and use them as implicits. It can be used for any variable, object definition and function.

This inserted implicit conversion must be associated with the source or target type of the conversion so that scala will consider implicit conversions which are in scope (that includes companion object). And at a time only one implicit conversion is inserted. But, if the code is valid per type check in first place, no implicit converion is performed.  

1. Implicit conversions to an expected type let user use one type in a context where a different type is expected.
    Whenever the compiler sees an X, but needs a Y, it will look for an implicit function that converts X to Y.

    ```Scala
        implicit def doubleToInt(x: Double) = x.toInt
        val x: Int = 3.5
    ```

2. Conversions of the receiver let user adapt the receiver of a method call (i.e., the object on which a method is invoked), if the method is not applicable on the original type.

3. Simulating new Syntax: For example in map creation using -> e.g. Map(1 -> "one", 2 -> "two", 3 -> "three"). The symbol -> is actually a method of the class ArrowAsoc from scala.Predef (i.e. scala preamble). In case of Map creation, scala compiler inserts implicit conversion from 1 (Int) to ArrowAssoc to satisfy the type check needed for use of ->. This is also known as "rich wrappers".

```Scala
    Implicit method example:

    trait Action {
        def performAction(): Unit
    }

    abstract class ActionPerformer extends Action {  
    }

    class Item {
        private var performer: Action = _

        def addPerformer(performerInp: Action) {
            performer = performerInp
        }

        def perform(): Unit = {
            performer.performAction()
        }  
    }

    class TestImplicit {
        def doIt() : Unit = {
            val item = new Item
            item.addPerformer(new ActionPerformer() {
                def performAction(): Unit = { println("Item action is performed") }
            })
            item.perform()
        }

        implicit def function2ImplicitActionPerformer (performAction1: Unit => Unit) = {
            new ActionPerformer() {
                def performAction(): Unit = performAction1()
            }
        }

        def doItImplicit(): Unit = {
            val item = new Item
            item.addPerformer(function2ImplicitActionPerformer((_: Unit) => println("Implicit item action is performed")))
            item.perform()
        }
    }

    object TestImplicit {
        def main(args: Array[String]) : Unit = {
            val testImplicit = new TestImplicit
            testImplicit.doIt()
            testImplicit.doItImplicit()
        }
    }
```

#### Implicit Class

An implicit class is preceded by Implicit keyword.  
Compiler generates an implicit conversion from class's constructor to the class itself.  
Such classes are used for "rich wrappers".  
An implicit class cannot be a case class, and its constructor must have exactly one parameter.  
An implicit class must be located within some other object, class, or trait.  

#### Choosing between conversions

>If there are more than one implicit conversions applicable then if one of the available conversions is strictly more specific than the others, then the compiler will choose the more specific one.

To be more precise, one implicit conversion is more specific than another if one of the following applies:

1. The argument type of the former is a subtype of the latter's.
2. Both conversions are methods, and the enclosing class of the former extends the enclosing class of the latter.

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

### Scala imports

In scala the *package* keyword is used to define the package to which the code belongs and *import* is used to import the piece of information required. This is very much like java.  
But in scala the import can rename the object. The renaming clause is used for the same. This renaming clause is always in the form "{original-name => new-name}"  
e.g. import companies.{google => alphabet}. This offers a benefit of avoiding name collesions in case of having same named import from scala and java.  

In scala you can exclude something from importing as well e.g. import org.comp.intro.{detailed => _}, here the detailed object is excluded from import.  

The catch-all import is presented by _. e.g. import org.mycomp.rules._ it imports all the rules.  

There are some (following) implicit imports (done by default) in each scala program:

    1. java.lang._
    2. scala._      Contains standard scala library. The scala import overshadows the java.lang import.
    3. Predef._     Contains many definitions of types, methods, and implicit conversions that are commonly used on Scala programs.

### Functional programming

In functional programming, the methods should not have any **side effects**. They should communicate with their surrounding only by accepting the input and providing the result.  
Such methods can be called as Referentially transparent - meaning that for any given input the method call could be replaced by it's result without affecting the semantics of the program.  
Functional languages encourage immutable data structures and referentially transparent methods.  
A method's only act should be to compute and return a value without any side effect (following SRP - Single Responsibility Principle). That way methods become reliable and reusable.

If you are using vars in code, it is probably not in functional style.  
A function with Unit as a return type could be the function with side effects: If a function is not returning any interesting value then the only way the function can make difference is through some kind of side effect.

#### Immutable Object

Immutable objects provide no way to alter object state once they are constructed. They can be freely passed around without having any fear of threads accidently altering their states. They form excellent choices as keys for hashtables as they would stay the same without alterations and bring predictability for corresponding object value to be found.
