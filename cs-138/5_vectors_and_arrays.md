## C-Style Arrays

C-style arrays are almost exactly the same as in C

```
int A[15];  // OK

const l = 10;
int A[l]    // OK
```

* Memory unsafe: No checks for writing past end of array.

## Vectors

Vectors are memory-safe wrappers for C-style arrays.

* Dynamically resizable

```
#include <vector>
using namespace std;

...
vector<int> A{};        // Vector of integers
A.size()                // Returns size
A[12]                   // Not memory safe
A.at(12)                // Checks bounds, safe
A.resize(30)            // Add 30 elements of space
A.push_back(123)             // Push the integer 123 to the end
```

**At any given moment:**
```
v.size() <= v.capacity()
v.back() == v.at(v.size() - 1)
```

## Stacks

**Two important operations**

```
push(e) : Push e onto the top
pop()   : Pop thing off the top
peek()  : Peek the top
```

Vectors can be used as a stack

```
vector<int> stack;

stack.push_back(12);
int e = stack.back();
stack.pop_back();
```

`push_back`: Doubles capacity if needed

`pop_back`: Generally does not decrease capacity

