# Pointers, Memory Allocation, Arrays, and Vectors

## Pointers

Pointers "point" to other pieces of data in memory.
- Allow the access and modification of pieces of data from other places.
    - eg. Modifying a variable in a function (remember we couldn't do this before bc functions make copies of the passed arguments).
- They "point" by storing the memory address of another piece of data.
    - C provides functionality to modify the pointed piece of data using its memory address (ie. pointer)

Pointer syntax:
```
int i = 6;
int *p; // POINTER to an integer type.
        // * = specifies pointer type.
        // int = specifies type of pointed data.

p = &i; // Set p to point to the address of variable i
        // & gets the address of a variable.

*p = 10 // i is now also 10
        // * is the dereference operator.
        //   It alows you to access and modify
        //   the data pointed to in memory.

int *q = p; // Set pointer q to point to the same location as p
*q = 16;    // i is now 16
```
- Type specifier needed in pointer declaration to let the compiler know how many bytes the pointed data is.

## Sections of Memory

In CS 137, we only cover

1. **Code**: Stores machine code (machine readable), done during compilation.
2. **Read-Only Data**: Stores global constants.
3. **Global Data**: Stores global variables available throughout the entire execution of the program.
4. **Heap**: Used to dynamically allocate memory.
5. **Stack**: Used to store local variables and return addresses (to manage function calls).
    - Each function call creates a *stack frame*
        - Stack frames contain argument values, local variables, and the return address of a function call.
    - Stack grows towards lower memory addresses

## Pointer Arithmetic

Mostly used for accessing array elements.
- Recall: Arrays are a contiguous block of memory stored as pointers to their first element.
    - Elements are accessed by moving this pointer down the block of memory.
    - *Pointer arithmetic used to shift the address pointers point to.*

- Can add integers to pointers
    - Increments the memory address the pointer points to by a multiple of the `sizeof` the pointed type.
- Cannot add two pointers.
- Pointers of the same type can be subtracted from each other.
- Pointers can be compared using the comparison operators
    ```
    // POINTER EXAMPLE
    int a[8] = {2, 3, 4, 5, 6, 7, 8, 9};
    int *p, *q, i;
    p = &(a[2]);    // p points to a[2]
    q = p + 3;      // q points to a[5]
                    // Memory address in p gets incremented by sizeof(int)*3 (Moves three elements)
    p += 4;         // p points to a[6]
    q = q - 2;      // q points to a[3]
    i = q - p;      // i = 3 - 6 = -3
    i = p - q;      // i = 6 - 3 = 3

    p < q;          // false since p points to a greater index than q.

    // Increment/Decrement Operator + Dereference
    // ++/-- takes precedence over *P

    *p++;   // ++ then * (equiv. *(p++))
    (*p)++; // * then ++
    *++p;   // ++ then *
    ++*p;   // * then ++ (equiv. ++(*p))
    ```

## Dynamically Allocated Memory

Memory that is stored on the Heap.
- Useful for:
    - Resize array when they are full.
    - Store global data accessible to the entire program.
        - Accessed using pointers to locations in the heap.

Heap memory is a "pool" of memory available to the program.
- Memory dynamically allocated at runtime and deallocated (returned to OS for reuse) when no longer needed.
- **MUST DEALLOCATE DYNAMICALLY ALLOCATED ARRAYS**
    - Or else you leak memory and you will run out of memory.

### **STACK VS. HEAP**
**Stack**
- Scratch space for thread execution.
- Each thread gets a stack.
- Newer elements stacked on top of older ones (memory is ordered).
- Faster since allocation/deallocation is easy.

**Heap**
- Memory set aside for dynamic allocation.
- Typically only one heap for the entire application.
- Entries can be unordered and chaotic.
- Usually slower since a lookup table is needed to access elements (more bookkeeping).

### **Syntax**

We use `malloc` and `free` from `<stdlib.h>`.

```
void* malloc(size_t size);
```
- Allocates `size` bytes but doesn't initialize.
- Returns `void` pointer so that it can store any type of data.
    - Compiler learns the pointed type after the malloc'd data is assigned to a variable with a pointer type.
- Returns `NULL` for insufficient mem or `size==0`

```
void free(void *p)
```
- Frees a memory block that p is pointing at that was allocated by the user.
- Failure to free allocated memory is a memory leak.
- No need to pass size of memory: `malloc` stores some hidden size data that is read by `free`.

```
void* calloc(size_t nmemb, size_t size)
```
- Clear allocate.
- Allocates `nmemb` elements of `size` bytes each initialized to zero.

```
void* realloc(void *p, size_t size)
```
- Resizes a previously allocated block to a `size` bytes.
- May create a new block if insufficient space around the block.

### NULL Pointer

A NULL pointer is a pointer that points to nothing.

Syntax:
```
int *p = NULL; // Preferred; Most clear.
int *p = 0;
int *p = (int *) 0;
int *p = (void *) 0;
```

- `(void *)` automatically casts to the correct type. More on this later (int the course).

`NULL` is defined in most of C's standard library.

### Dynamic Memory Example

```
int *q = malloc(100 * sizeof(int)); // Allocate enough space for 100 integers.
assert(q); // Ensures q is not NULL

// Initialize values in array
for (int i = 0; i < 100; ++i) {
    q[i] = i;
}

free(q); // Avoids memory leak.
```
