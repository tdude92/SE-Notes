# Interfaces (APIs) and Implementations

ADTs have an *explicit interface (API)* to seperate:
* High-level functionality: *clients*
* Low-level details: *implementors*

# Adapter Design Pattern

Redirecting function calls to adapt one ADT to another.
* For example, adapting a vector into a stack.

**Encapsulation (AKA Information Hiding)**:
* Seperate interface from implementation.
* *Hide implementation details.*
* Clients depend on interfaces which do not change as often.
    * But implementation can be updated lots without affecting the interface.