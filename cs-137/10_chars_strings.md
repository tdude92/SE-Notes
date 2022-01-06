# Characters and Strings

In C, strings are arrays of characters terminated with the `\0` character (NULL).

```
// Equivalent statements
char s[] = "Hello";
char t[] = {'H', 'e', 'l', 'l', 'o', '\0'};
```

* String Literal: Sequence of characters enclosed in double-quotes stored in a char pointer.

    ```
    char* string_literal = "Hello"
    ```

    * String literals are **immutable**.

        ```
        string_literal[2] = 'n'; // Undefined behaviour
        ```

    * Space seperated literals are concatenated.
    
        ```
        char* s = "Hello" " World!"; // "Hello World!"
        ```

* Character arrays: String literals can be used to initialize **mutable** arrays.

    ```
    char sarr[] = "Hello!";
    sarr[2] = 'n'; // OK

    // sarr is {'H', 'e', 'n', 'l', 'o', '\0'}
    ```

    * As long as a char array or string literal is null-terminated, it can be treated as a string.

* Note that sizeof() length is maintained in char[] but not char*

## const and #define

* `const`: Compiler errors if a const variable is modified.

    ```
    const int x = 1;
    x = 2; // ILLEGAL!
    ```
    * Const pointers vs Pointers to const

        ```
        const int *ptr; // Pointer to const type
        int *const ptr; // Pointer itself is const
        ```

* `#define`: Replaces all occurrences of one sequence of characters with another. Scoping rules do not apply since this is a preprocessor directive, not a variable.

    ```
    #include <stdio.h>
    #define BIG printf("BIG ");
    #define DIC printf("Division of Integer Combinations\n");

    int main(void) {
        BIG DIC
    }

    // This is a legal program
    // Prints "BIG Division of Integer Combinations\n"
    ```

## <string.h>

Provides string manipulation utilities.

**Functions**

```
size_t strlen(const char* s);

char* strcpy(char* s0, const char* s1);

char* strncpy(char* s0, const char* s1, size_t n);

char* strcat(char* s0, const char* s1);

int strcmp(const char* s0, const char* s1);
```

**String Reading**
* `scanf()`: Terminates on ANY whitespace.
* `gets()`: Terminates only on newline.