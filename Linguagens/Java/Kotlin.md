## Annotations
This is a way of attaching metadata to code and change its behavior in the runtime.  To create one, you should create a class with the `annotation` modifier in the class:
```
annotation class AnnotationName
```
Now, you should setup a bunch of stuff in order to get this annotation working properly:
- `@Target`: It specifies the possible kinds of elements which can be annotated with the annotation (such as classes, functions, properties and expressions).
- `@Retention`: It specifies whether the annotation is stored in the compiled class files and whether it's visible through reflection at runtime (by default, both are true).
- `@Repeatable` it allows using the same annotation on a single element multiple times.
- `@MustBeDocumented` it specifies that the annotation is part of the public API and should be included in the class or method signature shown in the generated API documentation.