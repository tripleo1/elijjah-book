# Elijjah (programming language)

**Elijjah** is a [multi-paradigm](https://en.wikipedia.org/wiki/Multi-paradigm_programming_language "Multi-paradigm programming language") [systems and applications programming language](https://en.wikipedia.org/wiki/Systems_programming_language "Systems programming language") with an emphasis on making the programmer's life easier. It is statically typed while using type deduction where possible and it supports both functional and object oriented paradigms.

It is intended to provide the power of C++, the expressibility of Python, and the utility of Java.  The code the reference compiler generates if C/C++ or Java is intended to complement each and every one of those in any combination.  It can reliably interact with Java libraries or C/C++ libraries like Swing/JavaFX, SWT, boost, or gtk and Qt.

## Contents

*   [1 History](#History)
*   [2 Philosophy](#Philosophy)
*   [3 Syntax](#Syntax)
*   [4 Memory safety](#Memory_safety)
*   [3 Syntax](#Syntax)
    *   [3.1 Design and Features](#design-and-features)
    *   [3.2 Ownership](#Ownership)
    *   [3.3 Types and polymorphism](#Types_and_polymorphism)
    *   [3.4 Main Entry Point](#main-entry-point)
    *   [3.5 Extension Methods](#extension-methods)
    *   [3.6 Operator Overloading](#operator-overloading)
    *   [3.7 Higher Order Functions](#higher-order-functions)
*   [4 Tools](#Tools)
*   [5 Unimplemented Things](#unimplemented-things)

## History

In the early 2000s the author became disillusioned with the then current state of the language landscape.  Namely the frustrating complexity of C++ and the frustrating simplicity of Java, arguably the two most popular languages at the time.

Due to unforseen circumstances, the compiler is just now being produced and released, hopefully to widespread acclaim or niche acceptance.  The author hopes that Elijjah can achieve what Java, D and Vala could not.

The language has evolved over time from a simple JavaScript clone to a full-fledged programming language fit to challenge today's top contenders.  

## Philosophy

The author states that Elijjah is designed to be an industrial strength object-oriented language, and a better language that C++ and Java, but to still be interoperable with either, allowing programmers to make a gradual transition to Elijjah.

Semicolons are optional as a statement terminator , though whilespace is ignored in the current compiler,  eventually a newline should be enough to deduce that the statement has ended.

## Syntax

The concrete syntax of Elijjah is similar to C/C++ and Java with hints from JavaScript, Python, and Eiffel.  Blocks of code are delimited by curly braces and control flow keywords such as `if`, `else`, and `while` are allowed.  As of now `for` is not supported and `foreach` is available as `iterate`.

A function is composed of expressions and statements.  Everything other than a function call or a variable assignment is a statement.  A function need not end with a return statement (if enabled), but the return value must be assigned to a special variable `Result`.

## Memory safety

Elijjah has an option for using a [garbage collector](https://en.wikipedia.org/wiki/Garbage_collection_%28computer_science%29#AUTOMATIC "Garbage collection (computer science)") of the prrogrammer's choice whwen using C/C++ backend, otherwise it uses the default model of its backend.

[Resource acquisition is initialization](https://en.wikipedia.org/wiki/Resource_acquisition_is_initialization "Resource acquisition is initialization") (RAII), and optional reference counting are both supported. 

Overall, the memory safety of your program depends on the backend used and the non-abuse of features like `C.Pointer` and `Pointer` (and unsafe if implemented.)

### Syntax

***************************

Class members are public by default and classes themselves are open by default, though member access control can be fine grained, and classes can be prevented from derivarion by using the @Sealed annotation.

In addition to classes and methods (called member functions in Elijjah) of OOP, Elijjah also supports the use of functions without class instantiation using namespaces.  This can be useful when interacting with C.

Semicolons are optional as a statement terminator; in most cases a newline is sufficient for the compiler to deduce that the statement has ended.

Elijjah variable declarations and parameter lists have the data type (optionally, and then inferred) come after the variable name (and with a colon), similar to Pascal.

Variables in Elijjah can be immutable, declared with the `val` keyword, or mutable, declared with the `var` keyword.

### Design and Features  

It is hoped that Elijjah will be useful in concurrent systems though at this time no features specially exist to facilitate this,  The main safety feature of Elijjah is a more evolved type system using `datatype` and `match` and providing the now popular Option type. (called Maybe).

Maybe the language will evolve concurrency and safety features present in other languages like Rust and Erlang.  The programmer has fine-grained control of memory layout (using `struct`s) where applicable (meaning largely using the C/C++ backends, though transparent access to C/C++ objects is supported).  Performance of idiomatic Elijjah is comparable to that of idiomatic C++.

Elijjah also supports const correctness and immutable funtions, where an object is not allowed to be modified in any way.

### Ownership

Maybe the `borrow` keywword will be implemented one day.

### Types and polymorphism

Where not explicit, the types of variables (and values honestly) are deduced by the compiler.  If this proves insufficient over time , a proper type inferencer will  be adopted.

Both function and classes can be given [generic](https://en.wikipedia.org/wiki/Generic_programming "Generic programming") [parameters](https://en.wikipedia.org/wiki/Parameter_%28computer_programming%29 "Parameter (computer programming)"), and class `signature`s can be used to require a class to implement a certain interface without raxing the type system.  TGhe implementation of generics is similar to the typical implementation of C++ templates: a separate copy of the code is generated for each instantiation. This is called monomorphization and contrasts with the [type erasure](https://en.wikipedia.org/wiki/Type_erasure "Type erasure") scheme typically used in Java and Haskell. The benefit of monomorphization is optimized code for each specific use case; the drawback is increased compile time and size of the resulting binaries.

`struct`s are used to control memory layout. Structs cannot fully participate in OOP aand member function on structs must be resolvable statically.

There are no static members in Elijjah.  This functionality is implemented by `namespace`s, each of which is a singleton and can be counted on to exist only once in an entire program. (Note that multi-threading behavior is undefined here.)

### Main entry point 

The entry point for every program is a class called Main and a function called main, and must not be part of a namespace or class.  Other considerations exist for dlls and maybe applets or something.  You must get system level arguments by inheriting Arguments class.  In addition, the file should be in a directory by itself.  There are no other file restrictions.

### Extension methods

Similar to C# and Kotlin (and conceived independently), Elijjah allows a user to add methods to any class without the formalities of creating a derived class with new methods. Instead, Elijjah adds the concept of an [extension method](https://en.wikipedia.org/wiki/Extension_method "Extension method") which allows a function to be "glued" onto the public method list of any class without being formally placed inside of the class. In other words, an extension method is a helper method that has access to all the public interface of a class which it can use to create a new method interface to a target class and this method will appear exactly like a method of the class, appearing as part of code completion inspection of class methods. For example:

~~~~
 package MyStringExtensions

extend String { 
  def lastChar(): Char = get(Length - 1)
}
 
 >>> println("Elijjah".lastChar())
~~~~

This means a user can package a customization layer of a library into a namespace which is subsequently imported for use in other modules.

### Operator overloading

Operator overloading is accomplished in the same fashion as Python, by implementing a specially named function, such as `__add__`, `__lshift__`, `__divide__`, etc.

Note that constructors are declared with the `constructor` keyword (shortcut `ctor`), and destructors are declared with the `destructor` keyword (shortcut `dtor`).

### Higher-order functions

Elijjah provides support for [higher order functions](https://en.wikipedia.org/wiki/Higher_order_functions "Higher order functions") and [anonymous functions](https://en.wikipedia.org/wiki/Anonymous_functions "Anonymous functions") or lambdas.

~~~~
// the following function takes a lambda, f, and executes f passing it the string, "lambda"
// note that (s: String) -> Unit indicates a lambda with a String parameter and Unit return type
class Foo {
  executeLambda(f: function(s: String) -> Unit) {
    f("lambda")
  }
}
~~~~



Lambdas are declared using braces, `{|| }` . If a lambda takes parameters, they are declared within the `||` a la Smalltalk.




~~~~// the following statement defines a lambda that takes a single parameter and passes it to the println function
val l s= { |c : Maybe[Any]|  println(c.unwrap()) } }

probably should be:

val l s= { |c : Maybe[Any]|  match c {Some[d:Any] {println(d)} _ {} } }
// lambdas with no parameters may simply be defined using { }
val l2 = { || print("no parameters") }
~~~~



## Tools
*   Integration with common Java build tools is planned including [Apache Maven](https://en.wikipedia.org/wiki/Apache_Maven "Apache Maven"), [Apache Ant](https://en.wikipedia.org/wiki/Apache_Ant "Apache Ant"), and [Gradle](https://en.wikipedia.org/wiki/Gradle "Gradle").
Also support for Cmake and Bazel.  Integration with GObject and Python are planned features.


### Unimplemented things

  *  Kotlin/Python's spread (*) operator
  *  Kotlin Deconstructor methods
  *  Python multiple assignment ( const (x, y, z) coming soon)\
  *  String interpolation (uses Python method (%); ${scope} coming)
  *  Kotlin/Groovy safe navigation, elvis operator
  *  Kotlin overly complex hello world exapmle
  *  REPL

