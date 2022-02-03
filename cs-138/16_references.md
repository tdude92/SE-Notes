# References

### Parameter Types

**Pass-by-value**: Copy values of object when passing as argument to a function.
* C and Java only allow this sort of passing.
* Bad when arguments are large and needs to all copied.

**Pass-by-pointer**: Finicky and error-prone.

**Pass-by-reference**:
* Parameter not copied to call-stack
* References are like a pointer but not as error-prone.
    * Essentially the same as giving an alias to a piece of data.

```
void addOne(int& x) {
    x++;
}

x = 1;
addOne(x);
// x is now 2
```

### const& Reference

```
void printVector(const vector<string>& v);
void printString(const string& s);

// Functionally the same as a pass-by-value.
// But now, can pass literals instead of only variables.
```