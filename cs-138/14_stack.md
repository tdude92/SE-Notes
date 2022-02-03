# Stack ADT

**Properties**
* Ordered
* LIFO on add/remove

**Operations**
* `push(Stack s, Element e_new)`
    * Adds e_new to the top
* `pop(Stack s)`
    * Pops top element off top
    * Usually returns top element 
* `peek(Stack s)`
    * Returns top element
* `isEmpty(Stack s)`
    * Returns if the stack is empty
* `initStack()`
    * Creates and returns an empty stack
* `destructor` (later on)

Sometimes `pop` and `peek` are combined, where `pop` just returns the top element (like in Python).

**More Mathematical Definitions**

```
initStack: none -> stack
    Pre: true
    Post: Return value is new empty stack

isEmpty: stack -> boolean
    Pre: true
    Post: Returns if the number of elements is zero

push: stack x element -> stack
    Pre: true
    Post: Returns new stack with element on top

pop: stack -> stack
    Pre: !isEmpty
    Post: Returns new stack with top removed

peek: stack -> element
    Pre: !isEmpty
    Post: Returns a copy of top element

nuke: stack -> stack
    Pre: true
    Post: Returns empty stack; old nodes deleted
```

### Typedefs

Say we have a stack ADT based on pointers to Node structs.

```
typedef Node* Stack
```