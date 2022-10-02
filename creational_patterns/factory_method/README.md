# FACTORY METHOD
## Itent
- *Factory Method* is a creational design pattern that provides an interface for creating objects in a superclass, but allows subclasses to alter the type of objects that will be created. 
## Idea
- The Factory Method pattern suggests that you replace direct object construction calls (using the `new` operator) with calls to a special factory method. Don’t worry: the objects are still created via the `new` operator, but it’s being called from within the factory method. Objects returned by a factory method are often referred to as products.
- There’s a slight limitation though: subclasses may return different types of products only if these products have a common base class or interface. Also, the factory method in the base class should have its return type declared as this interface.
## Applicability
- Use the Factory Method when you don't know before hand the exect types and dependencies of the objects your code should work with
- Use the Factory Method when you want to proide users of your library or framework with a way to extend its internal components
- Use the Factory Method when you want to save system resources by reusing existing objects instead of rebuilding them each time.
## How to implement ?
1. Make all products follow the same interface. This interface should declare methods that make sense in every product
2. Add an empty factory method inside the creator class. The return type of the method should match the common product interface.
3. In the creator's code find all references to product constructors. One by one, replace them with call to the factory method, while exxtracting the product creation code into the factory method.<br />
You might need to add a temporary parameter to the factory method to control the type of returned product. <br />
At this point, the code of the factory may look pretty ugly. It may have large `switch` statement that picks which product class to instantiate.
4. Now, create a set of creator subclasses for each type of product listed in the factory method. Override the factory method in the subclasses and extract the approriate bits of construction code from the base method.
5. If there are too many product types and it doesn't make sense to create subclasses for all of them, you can reuse the control parameter from the base class in subclasses.
6. If, after all of the extractions, the base factory method has become empty, you can make it abstract. If there's something left, you can make it a default behavior of the method.
## Pros and Cons
### Pros
- Can avoid tight coupling between the creator and the concrete products.
- Follow `Single Responsibility Principle`. You can move the product creation code into one place in the program, making the code easier to support.
- Follow `Open/Close Principle. You can introduce new types of products into the program without breaking existing client code.
### Cons
- The code may become more complicated since you need to introduce a lot of new subclasses to implement the pattern. The best case scenario is when you're introducing the pattern to an existing hierarchy of creator classes.

