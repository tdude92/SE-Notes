# Abstract Data Types

Mathematical structure that has well-defined and recognizable behaviour.
* Contains data and operations
* Each operation has:
    * **Signature**
    * **Pre-Condition**:
    * **Post-Condition**

### Pre- and Post-conditions

Statements that involve the parameters, return value, and maybe global program state.

**Pre-condition**

* Is there anything we need to *assume* about params/state.
* Want it to be as logically broad as possible.

**Post-condition**

* Relationship between inputs params/state and output params/state.
* Want it to be as logically narrow as possible.

### ADT Examples

Pretty much every language has an stdlib with implementations of these ADTs.

* **Vector/Sequence**
    * Ordered
    * Random access
    * Usually allows add/delete at the end
* **Stack**
    * Ordered
    * LIFO policy on add/delete
    * No random access to arbitrary elements
        * Only O(1) access to top of stack
* **Queue**
    * Ordered
    * FIFO policy on add/delete
    * No random access to arbitrary elements
        * Only O(1) access to front of queue

* **Set**
    * Unordered
    * Contains a given element only once
    * **Subtypes**
        * **Multi-set**
            * Allows duplicates
        * **Dictionary/Map**
            * Contains key-value pairs (k, v)
            * (a, b) and (a, c) in Map M ==> b == c
                * Multi-map allows duplicates
            * Can do lookup based on the key
                * M[a] returns b <==> (a, b) in M

### (Aside) Ordered Maps in C++

* In math, we think of maps and sets as unordered.
* Original C++ implementations had sorted maps and sets
* More efficient implementations:
    * `unordered_map`
    * `unordered_set`

### Meaning of Abstract (in ADT)

* Implementation may vary, but the *abstract* concept is the same.
* Programming languages let you define an *interface* around ADTs and other structures.
    * Interfaces enforce limited access of data through provided methods.

### Data (in ADTs)

* Most ADTs are containers.
    * Organize data in different ways to make different types of access more efficient.

### Style of ADTs

* **Functional**
    * We use this style before learning about OOP.
    * Inefficient due to parameter copying.
    * General format:
        ```
        newADT operationName(oldADT, otherParams);
        ```

Later on...
* Reference parameters ADTs
* OOP ADTs