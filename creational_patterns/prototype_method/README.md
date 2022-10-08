# Prototype
## Intent
**Prototype** is a creational design pattern that lets you copy existing objects without making your code dependent on their classes
## Idea
- The prototype pattern delegates the cloning process to the actual objects that are being cloned. The pattern declares a common interface for all objects that support cloning. This interface lets you clone an object without coupling your code to the class of that object. Usually, such an interface contains just single `clone` method.
- The implementation of the `clone` method is very similar in all classes. The method creates an object of the current class and carries over all of the field values of the old object into the new one. You can even copy private fields because most programing languages let objects access private fields of other objects that belong to the same class.
- An object that supports cloning is called a *prototype*. When your objects have dozens of fields and hundreds of possible configurations, cloning them might serve as an alternatie to subclassing.
- Here's how it work: you create a set of objects, configured in various ways. When you need an object like the one you've configured, you just clone a prototype instead of constructing a new object from scratch.
## Applicability
- Use the Prototype pattern when your code shouldn't depend on the concrete classes of object that you need to copy
- Use the pattern when you want to reduce the number of subclasses that only differ in the way they initialize their perspective objects.
## How to implement ?
1. Create the prototype interface and declare the `clone` method in it. Or just add the method to all classes of an existing class hierarchy, if you have one.
2. A prototype class must define the alternative constructor that accepts an object of that class as an argument. The constructor must copy the values of all fields defined in the class from the passed object into the newly created instance. If you’re changing a subclass, you must call the parent constructor to let the superclass handle the cloning of its private fields.<br />
   If your programming language doesn’t support method overloading, you won’t be able to create a separate “prototype” constructor. Thus, copying the object’s data into the newly created clone will have to be performed within the `clone` method. Still, having this code in a regular constructor is safer because the resulting object is returned fully configured right after you call the `new` operator.
3. The cloning method usually consists of just one line: running a `new` operator with the prototypical version of the constructor. Note, that every class must explicitly override the cloning method and use its own class name along with the `new` operator. Otherwise, the cloning method may produce an object of a parent class.
4. Optionally, create a centralized prototype registry to store a catalog of frequently used prototypes.<br />
   You can implement the registry as a new factory class or put it in the base prototype class with a static method for fetching the prototype. This method should search for a prototype based on search criteria that the client code passes to the method. The criteria might either be a simple string tag or a complex set of search parameters. After the appropriate prototype is found, the registry should clone it and return the copy to the client. <br />
   Finally, replace the direct calls to the subclasses’ constructors with calls to the factory method of the prototype registry.
## Pros and Cons
### Pros
- You can clone objects without coupling to their concrete classes
- You can get rid of repeated initialization code in favor of cloning pre-build prototypes
- You can produce complex objects more conveniently
- You get an alternative to inheritance when dealing with configuration presets for complex objects
### Cons
- Cloning objects that have circular references might be very tricky  