# Bridge
## Intent
**Bridge** is a structural design pattern that lets you split a large class or set of closely related classes into two separate hierachies-abstraction and implementation-which can be developed indeplendtly of each other.
## Idea
- The inheritance issue when try to extend the classes into two independent dimensions cause the class grow exponentially.
- The Brigde pattern attempts to solve this problem by switching from inheritance to the object composition.
- You will extract one of the dimentions into a separate class hierachy, so that the original classes will reference an object of the new hierachy, instead of having all of its tate and behaviors within one class
## Application
- Use the Bridge pattern when you want to devide and organize a monolithic class that has several variants of some functionality (for example, if the class can work with various database servers).
- Use the pattern when you need to extend a class in several orthogonal (independent) dimensions.
- Use the Bridge if you need to be able to switch implementation at runtime.
## How to implement ?
1. Identify the orthogonal dimensions in your classes. These independent concepts could be: abstraction/platform, domain/infrastructure, front-end/back-end, or interface/implementation.