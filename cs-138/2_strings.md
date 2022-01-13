# Useful Libraries

### \<cassert\>

Same as C assertions

### \<string\> and String Processing

* Not null-terminated char arrays anymore.
    * More intuitive
    * Less error-prone
    ```
    #include <string>
    ...
        string s;

        // instead of
        char* s2;
    ```

* Operator overloads:
```
+                   String catenation
==, <=, <, etc.     Comparison based on standard lexical ordering
s.length()          Number of chars in s
s.at(i)             ith char (checked access)
s[i]                ith char (unchecked access)
s.c_str()           C-style char*
s.substr(i, n)      Substr of n chars starting at i
s.substr(i)         Substr from i to eos
s.find(str, pos)    Return first occurrence of chars at or after pos
s.rfind(str, pos)   Starts from the right
```

* Quotes matter! (Just like in C)
```
char c   = 'a'; // Single-quotes give char
string s = "a"; // Double-quotes give char*
```

```
string s1 = "g";
string s2 = "m";

cout << s2 + s1 << endl;                    // mg
cout << "mg" + "g" << endl;                 // **error
cout << (string)"m" + (string)"g" << endl;  //mg
cout << (string)"m" + 'g' << endl;          // 212 (=109+103)
```

\*\* C++ converts explicit strings to a char* which doesn't support the + overload

