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
- Use the Builder pattern when you want your code to be able to create different representations of some product.
- Use the Builder to construct Composite trees or other complex objects.
## How to implement ?
1. Make sure that you can clearly define the common construction steps for building all available product representation. Otherwise, you won't be able to procedd with implementing the pattern.
2. Declare these steps in the base builder interface
3. Create a concrete builder class for each of the product representations and implement their construction steps.
   Don't forget about implementing a method for fetching the result of the construction. The reason why this method can't be declared iside the builder interface is that various builders may construct products that don't hae a common interface. Therefore, you don't know what would be the return type for such a method. However, if you're dealing with products from a single hierachy, the fetching method can be safely added to the base interface.
4. Think about creating a director class. It may encapsulate various ways to construct a product using the same builder object.
5. The client code creates both the builder and the director objects. Before construction starts, the client must pass a builder object to the director. Usually, the client does this only one, via parameters of the director's class constructor. The director uses the builder object in all further construction. There's an alternative approach, where the builder is passed to a specific product cunstruction method of the director.
6. The construction result can be obtained directly from the director only if all products follow the same interface. Otherwise, the client should fetch the result from the builder.
## Pros and Cons
### Pros
- You can construct objects step-by-step, defer construction steps or run steps recursively.
- You can reuse the same construction code when building various representations of products.
- `Single Responsibility Principle`. You can isolate complex construction code from the business logic of the product.
### Cons
- The overall complexity of the code increases since the pattern requires creating multiple new classes.
