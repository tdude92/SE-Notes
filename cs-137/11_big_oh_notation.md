# Big-O Notation

Now we consider the time efficiency of our algorithms.

**Definition** *Big-O Notation*:

```
Let f: R --> R
Define O(f(x)) to be the set of real functions such that for all g(x) in this set, there exists a real C > 0 and X such that |g(x)| <= C|f(x)| for all x >= X.
```

In English: O(f(x)) is the set of all functions that grow aasymptotically equal or faster than f(x).
- We usually write g(x) = O(f(x)) instead of g(x) ϵ O(f(x))
- Generally, CS uses N rather than R.

**Useful Theorems**
```
For positive real functions f and g,

(1) If lim x->inf f/g < inf, then f = O(g)
(2) If lim x->inf f/g = inf, then g = O(f)
```

**Propositions**

1. For all x >= 1, x ϵ N,
    ```
    Let f(x) be any polynomial of degree n
    f(x) = O(x^n)
    ```

2. For a, b >0
    ```
    log_a(x) = O(log_b(x))
    ```

3. Let g0 ϵ O(f0) and g1 ϵ O(f1)
    ```
    (1) g0 + g1 ϵ O(|f0| + |f1|)

    (2) g0g1 ϵ O(f0f1)

    (3) O(|f0| + |f1|) = O(max{|f0|, |f1|})
    ```

4. Transitivity
    ```
    h = O(g) and g = O(f) ==> h = O(f)
    ```

**Growth Rates of Functions**

Notation <<: f << g <==> f = O(g)

```
Let c, ϵ be constants

1 << log(n) << n^ϵ << c^n << n! << n^n
```

Generally, we want Big-O notation to be as tight as possible.
- Even though n^2 + 1 = O((n!)^n^n^n), it's more accurate to write n^2 + 1 = O(n^2)