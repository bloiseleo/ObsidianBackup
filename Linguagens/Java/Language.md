The Java Programming Language was born aiming to write once and run everywhere. The main goal is to write an application and have it working on whatever device your friends have.
## How it Works
### Source Code
At first, you'll need to write your code. It'll be most of the times in Java, but you can write Scala, Kotlin and any other language supported by the Java Virtual Machine.
### Bytecode
When your code goes through the compiler, it will checks for errors and won't let you compile the code until you fix it. When it compiles, it'll create a document called `bytecode`, which contains your code ready to be executed. This code is platform independent, so, any place that is able to run java, it'll be able to run the program.
### Java Virtual Machine
The Java Virtual Machine is a software that is capable to run java software. When it'll execute your software, it looks for a `main` method inside the class you informed through the CLI command. Every application must contain a single `main` method in one class.
When you want to compile and execute a single file of java program, you should execute:  `javac FileName.java`. It'll generate a `FileName.class` file. This file `.class` is written in bytecode, so It can be executed by the JVM. Now, if you want to execute this software, you must execute it like this: `java FileName`.
## Variables
In java, we have primitive values and complex values. When you're creating them, you can declare it or you can initialize it. But, you have two ways of doing it:
- Complete: `Type varName = value;`
- Succint: `var varName = value;`
There are the following primitive data types:
- byte -> 8-bit signed two's complement integer. Its minimum value is -128 and the maximum is 127.
- short -> 16-bit signed two's complement integer. Its minimum value is -32.768 and the maximum is 32.767.
- int -> 32-bit signed two's complement integer. Its minimum value is -2^31 and the maximum is 2^31
- long -> 64-bit signed two's complement integer. Its minium value is -2^61 and the maximum is 2^63
- float -> single precision floating point.
- double -> double precision floating point.
- boolean -> true or false
- char -> 16-bit Unicode character.
Their default values are "zerable".
