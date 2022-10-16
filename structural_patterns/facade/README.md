# Facade
## Intent
- **Facade** is a structural design pattern that provides a simplified interface to library, a framework, or any other complex set of classes.
## Idea
- A **Facade** is a class that provides a simple interface to a complex subsytem which contains losts of moving parts.
- A facade might provide limited functionality in comparison to working with the subsystem directly. However, it includes only those features that clients really care about.
- Having a facade is handy when you need to integrate your app with a sophisticated library that has dozens of features, but you just need a tiny bit of its functionality.
## Apllicability
- Use the Facade pattern when you need to have a limited but straightforward interface to a complex subsystem.
- Use the Facade when you want to structure a subsystem into layers.
## How to implement
1. Check whether it’s possible to provide a simpler interface than what an existing subsystem already provides. You’re on the right track if this interface makes the client code independent from many of the subsystem’s classes.
2. Declare and implement this interface in a new facade class. The facade should redirect the calls from the client code to appropriate objects of the subsystem. The facade should be responsible for initializing the subsystem and managing its further life cycle unless the client code already does this.
3. To get the full benefit from the pattern, make all the client code communicate with the subsystem only via the facade. Now the client code is protected from any changes in the subsystem code. For example, when a subsystem gets upgraded to a new version, you will only need to modify the code in the facade.
4. If the facade becomes too big, consider extracting part of its behavior to a new, refined facade class.
## Pros and Cons
### Pros
- You can isolate your code from the complexity of a subsystem.
### Cons
- A facade can become **a god object** coupled to all classes of an app.