# Signletone
## Intent
**Singleton** is a creational design pattern that lets you ensure that a class has only one instance, while providing a global access point to this instance.
## Idea
- `Singleton` will solve two problems at the same time, but it violating the `Single Responsibility Principle`:
  + Ensure that a class has just a single instance, it's useful when we want to control access to some shared resource like database or file.
  + Provide a global access point to that instance. That really unsafe but singleton pattern lets you access some object from anywhere in the program. However, it also protets that instance from being overritten by other code.

- Basic steps:
1. Make the default constructor private, to prement other objects from using the `new` operator with the Singleton class
2. Create a static creation method that acts as a costructor. Under th hood, this method calls the private constructor to create an object and saves it in a static field. All following calls to this method return the cached object. <br />
3. If your code has access to the Singleton class, then it’s able to call the Singleton’s static method. So whenever that method is called, the same object is always returned.
## Applicability
- Use the Singleton pattern when a class in your program should have just a single instance available to all clients; for example, a single database object shared by different parts of the program.
- Use the Singleton pattern when you need stricter control over global variables.

## How to implement ?
1. Add a private static field to the class for storing the singleton instance
2. Declare a public static creation method for getting the singleton instance
3. Implement "lazy initialization" inside the static method. It should create a new object on its first call and put it into the static field. The method should always return that instance on all subseqeunt calls.
4. Make the constructor of the class private. The static method of the class will still be able to call the constructor, but not the other objects.
5. Go over the client code and replace all direct calls to the singleton's constructor with calls to its static creation method.
## Pros and Cons
### Pros
- You can be sure that a class has only a single instance.
- You gain a global access point to that instance.
- The singleton object is initialized only when it's requested for the first time.
### Cons
- Violates the Single Responsibility Principle. The pattern solves two problems at the time.
- The Singleton pattern can mask bad design, for instance, when the components of the program know too much about each other.
- The pattern requires special treatment in a multithreaded environment so that multiple threads won’t create a singleton object several times.
- It may be difficult to unit test the client code of the Singleton because many test frameworks rely on inheritance when producing mock objects. Since the constructor of the singleton class is private and overriding static methods is impossible in most languages, you will need to think of a creative way to mock the singleton. Or just don’t write the tests. Or don’t use the Singleton pattern.