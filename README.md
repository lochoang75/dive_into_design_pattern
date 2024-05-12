Some worth noting:
+ Program to an interface, not an implementation. When programming when one class is dependent on others class, it should depend on the interface instead of the concrete class.
It bring more flexible and reusable for the whole system when we need to modify/extend the system.
+ Favor object composition over class inheritance. Class inheritance is different with interface implementations. Class inheritance is about using a baseclass and trying to reuse the same implementation from
base class to derived class. It (sometimes) can solve the `Do Not Repeat Yourself` in source code, but from the system design perspective, it may create the coupled class. Only one change from the base class can cause massive side
effect to other derived class. Object composition is different, when use the composition, we can change/ replace/ remove the object composition (in implement of one class) without cause side eject to the other class.
