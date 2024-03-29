# Adapter
## Intent
- Adapter is a structural design pattern that allows objects with incompatible interfaces to collaborate.
## Idea
- *Adapter* is a special object that converts the interface of one object so that another object can understand it.
- An adapter wraps one of the objects to hide the complexity of conversion happening behind the scences. The wrapped object isn't even aware of the adapter.
- Adapters can not only convert data into various formats but can also help objects with different interfaces collaborate. Here's how it works:
1. The adapter gets an interface, compatible with one of the existing objects.
2. Using this interface, the existing object can safely call the adapter's methods.
3. Upon receiving a call, the adapter passes the request to the second object, but in a formal and order that the second object expects.
Sometimes it's possible to create a two-way adapter that can convert the calls in both directions.
## Applicability
- Use the Adapter class when you want to use some existing class, but its interface isn’t compatible with the rest of your code.
- Use the pattern when you want to reuse several existing subclasses that lack some common functionality that can’t be added to the superclass.
## How to implement
1. Make sure that you have at least two classes with incompatible interfaces:
    - A useful *service* class, which you can't change(often 3rd-party, legacy or with lots of existing dependencies).
    - One or serveral *client* classes that would benefit from using the service class.
2. Declare the client interface and describe how clients communicate with the service.
3. Create the adapter class and make it follow the client interface. Leave all the method empty for now.
4. Add a field to adapter class to store a reference to the service object. The common practice is to initialize this field via the constructor, but sometimes it's more convenient to pass it to the adapter when calling its methods.
5. One by one, implement all method of the client interface int the adapter class. The adapter should delegate most of the real work to the service object, handling only the interface or data format conversion.
6. Clients should use the adapter via the client interface. This will let you exchange or extend the adapters without affecting the client code.
## Pros and Cons
### Pros
- *Single Responsibility Principle*. You can separate the interface or data conversion code from the primary business logic of the program.
- *Open/Closed Principle*. You can introduce new types of adapters into the program without breaking the existing client code, as long as they work with the adapters through the client interface.
### Cons
- The overall complexity of the code increases because you need to introduce a set of new interfaces and classes. Sometimes it’s simpler just to change the service class so that it matches the rest of your code.

