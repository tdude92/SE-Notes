# Arrays and Pointers

## Arrays

- Whenever a variable is created, memory is allocated on the stack.
- We can group a contiguous block of memory using arrays.

### Array Initializers
```
int a[5] = {1, 2, 3, 4, 5}
int a[] = {1, 2, 3, 4, 5}
int a[5] = {1, 2, 3} (Last 2 entries are zero)
int a[5] = {[2] = 2, [4] = 4}
```

```
// NOT VALID: Initialization fone at COMPILE TIME
int a[5];
a = {1, 2, 3, 4, 5};
```

### sizeof Operator
Computes number of bytes allocated for argument's data type.

Returns `size_t`, an unsigned integral type.

```
int a[4];
sizeof(a); // = (4 elements) * (4 bytes/element)
sizeof(a)/sizeof(a[0]) // = 4
```

### Arrays and Pointers
Pointers are types that store the memory address to another variable. They can be used to access and modify some other variable.
```
float f;
float *p; // Pointer to float type called a
a = &f; // & gives the mem addr of a var
printf("%f", *p); // * dereferences a pointer
```

Array variables are pointers to the first element (kinda).
```
int *a is ALMOST equivalent to int a[]
```
**POINTER DECAY**:
- Array types store the sizeof the entire array.
- Pointer types store the sizeof the pointer.
- *In function parameters, `int a[]` is an alias for `int *a`*.
    - sizeof information is not retained when passed to function.
    ```
    // These are the same
    int f(int *a);
    int f(int a[]);

    // To pass size information, use another argument
    int f(int a[], int n);
    ```

### Multidimensional Arrays
```
// 3 row, 4 col matrix
int mat[3][4] = {
    {1, 0, 0, 1},
    {0, 1, 0, 2},
    {0, 0, 1, 3}
}
```
- n-D arrays stored *row major* in memory
    ```
    addr    val
    ----    ---
    0       mat[0][0]
    1       mat[0][1]
    2       mat[0][2]
    3       mat[0][3]
    4       mat[1][0]
    .       .
    .       .
    .       .
    m*n-1   mat[m-1][n-1]
    ```
    - `int mat[][]` is equivalent to `int **mat`
        - n-D arrays are really just an array of pointers.