# Builder
## Intent
- *Builder* is a creational design pattern that lets you construct complex objects step by step. The pattern allows you to produce different types and representations of an object using the same construction code.
## Idea
- The builder pattern suggests that you extract the object construction code out of its own class and move it to separate objects called builder
- The pattern organizes object construction into a set of setps. To create an object, you execute a series of these steps on a builder object.
- You don't need to call all of the steps. You can call only those steps that are necessary for producing a particular configuration of an object.
- Some of the construction steps might be require different implementation when you need to build various representations of the product. In this case you can create serveral different builder classes that implement the same set of building steps, but in different manner. Then we can use these builder in the construction process to produce different kinds of objects.
- `Director` class defines the order in which to execute the building steps, while the builder provides the implementation for those steps.
- `Director` class is optional, it might be a good place to put various construction routines so you can reuse the across your program.
- `Director` class completely hides the details of product construction from the client code. The client only need to associate a builder with a director, launch the construction with the director and get the result from the builder.
## Applicability
- Use the Builder pattern to get rid of a "telescoping constructor".
- Use the Builder