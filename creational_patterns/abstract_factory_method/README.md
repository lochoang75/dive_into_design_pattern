# Abstract factory
## Intent
- *Abstract Factory* is a creational design pattern that lets you produce families of related objects without specifying their concrete classes.
## Idea
- The first thing the Abstract Factory pattern suggests is to explicitly declare interfaces for each distinct product of the product family. Then you can make all variants of products follow those interfaces. 
- The next move is to delcare the `Abstract Factory`- an inteface with a list of creation methods for all products that are part of the product family. These method must return *abstract* product types represented by the interfaces we extracted previously and so on.
- For each variant of a product family, we create a separate factory class based on the `AbstractFactory` interface. A factory is a class that returns products of a particular kind.
- The client code has to work with both factories and products via their respective abstract interfaces. This let you can change the type of a factory that you pass to the client code, as well as the product variant that the client code receives, withou breaking the actual client code.
- There's one more thing left to clarify: if the client is only exposed to the abstract interfaces, what creates the actual factory objects? Usually, the application creates a concrete factory object at the initialization stage. Just before that, the app must select the factory type depeding on the configuration or the environment settings.
## Applicability
- Use the Abstract Factory when your code needs to work with various families of realted products, but you don't want it to depend on the concrete classes of those products-the might be unknown beforehand or you simply want to allow for future extensibility.
## How to implement ?
1. Map out a matrix of distinct types versus variants of these products.
2. Declare abstract product interfaces for all product types. Then make all concrete product classes implement these interfaces.
3. Declare the abstract factory interface with a set of creation methods for all abstract products.
4. Implement a set of concrete factory classes, one for each product variant.
5. Create factory initialization code somewhre in the app. It should instantiate one of the concrete factory classes, depending on the application configuration or the current environment. Pass this factory object to all classes that construct products.
6. Scan through the code and find all direct calls to product constructors. Replace them with calls to the appropriate creation method on the factory object.
## Pros and Cons
### Pros
- You can be sure that the product you're getting from a factory are compatible with each other.
- You avoid tight coupling between concrete products and client code.
- `Single Responsibility Principle`. You can extract the product creation code into one place, making the code easier to support.
- `Open/Close Principle`. You can introduce new variants of products without breaking existing client code.
### Cons
- The code may become more complicated than it should be, since a lot of new interfaces and classes are introduced along with the pattern.
