# Structures

- Similar to arrays: Groups elements into one logical entity.
- Named member vars stored together in memory (contiguously)
    - Members can be different types and are named instead of indexed.

### Syntax

Here is an example of a struct with a string and an int.
```
struct doggo {
    char* name;
    int age;
}; // <-- This semicolon needed btw

// Shorthand
typedef struct {
    char* name;
    unsigned long long age;
} catto;
```

Instantiation
```
struct doggo toby = {"toby", 37};
struct doggo mogus = {.name = "mogus"}; // Default initializes age to zero

catto marmoset = {"marmoset", 8181818928}; // Shorthand lets us omit the struct
```

Function parameter/return type
```
// Takes a doggo and returns the doggo
struct doggo getDog(struct doggo dog) { // Remember this is pass by value.
    return dog;
}

// Mutates a dog object
void ageDog(struct doggo *dog) {
    (*dog).age++; // Or dog->age++;
}
```

Array of Structures
```
catto cattos[2] = {marmoset, {"dog", 1}};
```

Structures Containing Structures
```
typedef struct {
    catto catto_boss;
    catto right_hand_man;
} catto_mafia;

catto_mafia italian_cattos = {{"tony", 88}, marmoset};
```