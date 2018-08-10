# Kotlin

## Getting started

### Hello World

```kotlin
package my.program

fun main(args: Array<String>) {
    println("Hello, world!")
}
```

### Hello World using Companion Object

```kotlin
package my.program

class App{
    companion object{
        @JvmStatic fun main(args: Array<String>) {
            println("Hello, world!")
        }
    }
}
```

A slight version that instantiates the class to use the function

```kotlin
package my.program

class App{
    companion object{
        @JvmStatic fun main(args: Array<String>) {
            App().run()
        }
    }

    fun run(){
        println("Hello, world!")
    }
}
```

### Hello World using an Object Declaration

```kotlin
package my.program

object App{
    @JvmStatic fun main(args: Array<String>) {
        println("Hello, world!")
    }
}
```

### Main method using varargs

```kotlin
package my.program

fun main(vararg args: String) {
    println("Hello, World!")
}
```

### Compile and Run Kotlin

_kotlinc_: to compile kotlin file </br>
_kotlin_: to run the kotlin file after compile

## Basics of Kotlin

### Basic examples

The Unit return type declaration is optional for functions.

```kotlin
fun printHello(name: String): Unit {
    if(name != null)
        println("Hello ${name}")
}

fun printHello(name: String) {
    ...
}
```

Single-Expression functions: When a function return a single expression, the curly braces can be ommited and the body is specified after "="

```kotlin
fun double(x: Int): Int = x * 2
```

Explicity declaring the return type is optional when this can be inferred by the compiler

```kotlin
fun double(x: Int) = x * 2
```

String interpolation

```java
int num = 10;
String s = "i =" + i;
```

```kotlin
val num = 10
val s = "i = $num"
```

In Kotlin, the type system distinguishes between references that can hold null and those that can not. For example:

```kotlin
var a: String = "abc"
a = null // compilcation error
```

To allow nulls, whe can declare a variable as nullable string, written *String?*:

```kotlin
var a: String? = "abc"
a = null // compilcation ok
```

In Kotlin, "==" is used to check for equality of value. By convention, an expression like *"a == b"* is translated to

    a?.equals(b) ?: (b === null)

## Strings

### String equality

The "==" operator is used to check the strutural equality.

```kotlin
val str1 = "Hello, World!"
val str2 = "Hello, " + " World!"
println(str1 == str2) // print true
```

For referential equality is checked with "===" operator

```kotlin
val str1 = """
|Hello, World!
""".trimMargin()

val str2 = """
#Hello, World!
""".trimMargin("#")

val str3 = str1

println(str1 == str2) // Prints true
println(str1 === str2) // Prints false
println(str1 === str3) // Prints true
```