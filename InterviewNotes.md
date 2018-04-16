# Interview Notes

## Learning
- Practice algorithm coding at https://www.codility.com/
- Describe how I currently use RESTful APIs
  - So far is looks like we use JAX-RS libs directly and Jersey. I don't fully get the relationship between the two. Jersey is a reference implementation of JAX-RS, yet we seem to use JAX-RS core lib classes on their own for things like annotations.
  - We have an application class which is the OSGi service implementation, the entry point for the OSGi service registry. This, in turn, loads a class which contains the rest endpoints.
- Java 8 Streaming, lambdas, method refs.


## Software Engineering

### SOLID Principles for OO
* Single Responsibility - A class has a single responsibility
* Open/closed - Open for extension/Closed for modification
* Liskov substitution - Design by contract. Every subclass/derived class should be substitutable for their base/parent class.
* Interface segregation - Many client specific interfaces are better than one specific interface.
* Dependency inversion - Depend on abstractions. Higher level modules should not depend on lower level modules. For example, depend on `DBConnectionInterface` rather than `MySQLConnectionImpl`.

### YAGNI
_You ain't gonna need it!_ Don't add functionality unless it's necessary.

### HATEOAS
_Hypermedia As The Engine Of Application State_  
> A REST client needs no prior knowledge about how to interact with an application or server beyond a generic understanding of hypermedia.

For example, a simple REST request containing a bank account number might return a list of links to all possible options for that account, withdraw, deposit, close, etc. If the account is overdrawn, only one option would be returned - deposit.

In my experience we've used this principle with Analytics reports where we tailor links for options on a report. For example we would only return a filter link for each distinct value in the result set. Therefore we would be returning options representative of the current state.
