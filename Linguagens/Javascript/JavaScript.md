JavaScript is a script language which evolved to be a full featured language. Even if, as any "old" language, it has its counter parts, it's also a pretty good language. It's a interpreted or just-in-time compiled programming language with first-class functions. Besides, it's a prototype-based, multi-paradigm  and single-threaded. It supports P.O.O, imperative and declarative.

JavaScript's standards are defined by the ECMAScript language specification and ECMAScript Internationalization API specification.
#### First-Class Function
It means that functions are treated like any other variable. It's possible to inform functions as parameters, it can be returned by another function and can be assigned as as value to a variable.
#### Prototype-Based
It means that we do not need to define classes in order to create an object. We can simply create an empty object or an object that already exists and add properties and methods to this object.
## Pure Function
A pure function is a function that does not change any value that existed before its call. In this case, imagine that we have a function that perform math operations and take two parameters as input. Now, you perform your calculations and return the value. But, before realizing the calculations, it changed the value in the memory (it's not pure). It would be pure if the parameters had not changed.
Other thing is: given the same input, you would obtain the same result.

> You should take this approach in consideration when programming functionally.
## Node Js
Node Js is a runtime environment that powers javascript outside the browser. It was created by Ryan Dahl in 2009 and in 2010 the version 0.1.14 was launched It was adopted by Microsoft, Yahoo! and LinkedIn. The OpenJS Foundation was created to maintain and evolve node js. In 2015, the node js adopted ecma script standards.  
### How it works? 
Node Js relys on the JavaScript engine to execute the javascript code. Node js uses the V8, that is used by the Google Chrome to execute javascript. Then, the creator created the libuv, which is the layer written in C++ that executes the event loop and interacts with the operational system.