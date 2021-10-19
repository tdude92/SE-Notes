# Floating Point Numbers and Math Library

## Floating Point Numbers

- Float: 4 bytes, 7 dig precision, exponent +-38
- double: 8 bytes, 16 dig precision, +-308

### IEEE 754 Floating Point Standard
![](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d2/Float_example.svg/1180px-Float_example.svg.png)
Limited precision; cannot use == on two floats/doubles

### Errors
Notice that floats can only store rational numbers (not all reals).
- This is okay since rationals can approximate irrationals

**Absolute Error and Relative Error**

Let r be a real and p be an approximating rational
![](https://i.ytimg.com/vi/rtKYDvM68Oc/hqdefault.jpg)

### Floating Point Equality
```
double a = 1.0/3.0, b = 1.0/4.0, c = 7.0/12.0;
a + b == c; // FALSE????!??!?!?!?!?
```
- Due to imprecision, checking equality is risky.
- **Instead, check if abs(diff) < tolerance**

### Function Parameters

Pointers can point to a function!
```
double f1(double x) {
    return x;
}

double f2(double x) {
    return x*x;
}

double verbose_call(double (*f)(double), double x) {
    double out = f(x);
    printf("%f", out);
    return out;
}

verbose_call(f1, 10);
verbose_call(f2, 10);
```
