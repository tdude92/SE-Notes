# More on Tail Recursion and Map and Reduce

## Tail Recursion

Recall:
- Recursive fib(n) creates a giant @ss expression out of recursive calls.
    ```
    --> return fib(n - 1) + fib(n - 2)
    ```
    - U will run out of memory and die of alzheimers.

**Tail Recursive (Accumulative) Solution**: It is possible to improve the space efficiency of recursion (Without switching to iteration).
- A function is tail recursive if the recursive call is the last thing executed by the function.
- Essentially a translation of iteration into recursion.
- Saves on space
    - No expensive expression at the end of recursion

```
// FIBONACCI
int fib_tr(int prev, int cur, int n) {
    // Tail-recursive helper
    if (n == 0) return cur;
    return fib_tr(cur, prev + cur, n - 1);
    // NO GIANT EXPRESSION! Computed values are "accumulated" into prev and cur.
}

int fib(int n) {
    if (n == 0) return 0;
    return fib_tr(0, 1, n - 1);
}
```

## Higher-Order Functions

**Definition**: Functions that operate on functions.

We generalize types using the `void*` type.

### Map

Applies a unary function to each element in the array

```
void map(void* src, size_t n, size_t src_bytes,
         void* dest, size_t dest_bytes,
         void* (*f)(void*));

// Example implementation

{
    if (n == 0) return;
    void* ret = f(src);
    memcpy(dest, ret, dest_bytes);
    free(ret);
    map(src + src_bytes, --n, src_bytes, dest + dest_bytes, dest_bytes, f);
}
```

- `f` can take any type and return any type

```
// Possible f
void* float_to_int(void* f) {
    float d = *(float*)f;
    int* i = malloc(sizeof(int));
    *i = (int)d;
    return i;
}

void* multiply_by_2(void* f) {
    float d = *(float*)f;
    float* i = malloc(sizeof(float));
    *i = 2*d;
    return i;
}
```

### Reduce

Applies a binary function over an array to produce a final answer.

```
src = [a0, a1, ..., an]
dest = f(a0, f(a1, f(a2, ... (f(an, BASE_CASE)))))
```

```
// This is tail-recursive!
void reduce(void* src, size_t n, size_t src_bytes, void* dest, void (*f)(void*, void*)) {
    if (n == 1) {
        f(src, dest);
        return;
    }
    reduce(src + src_bytes, n - 1, src_bytes, dest, f);
    f(src, dest);
}

// Product of all entries in array
void mult(void* lhs, void* rhs) {
    *(int*)rhs = *(int*)lhs * *(int*)rhs
}
```

### Note
Compiler may raise the error `Unknown size for type 'void'.`

Just replace recursive call
```
src + src_bytes
with
(char*)src + src_bytess
```