# C++ Lite Bootcamp

```
#include <iostream>     // Access to C++ IO streams: cin, cout, cerr
#include <string>       // C++ string class wrapper for C strings
using namespace std;

const string kidDrink = "juice"; // const: cannot change variable value
string adultDrink = "coffee";

int main(int argc, char* argv[]) {
    int age = 100;
    while (age > 0) {
        cout << "How old are you? ";    // Print input prompt (equivalent to printf)
        cin >> age;                     // Read input         (equivalent to scanf)
        cout << "Would you like some ";
        if (age < 18) {
            cout << kidDrink << "?" << endl; // endl is a newline
                                             // Can print variables directly (no %d, %s weirdness)
        } else {
            cout << adultDrink << "?" << endl;
        }

        if (age == 56) {
            adultDrink = "beer"; // Change global variable (RISKY BUSINESS)
        }
    }
}
```

### Booleans

C++ has a special bool type built-in

```
bool isTrue = true;
const bool isFalse = false;
if (isTrue) {
    // code
}
```

* Arithmetic (including `char`) and pointer values can have true/false meaning...
    * Zero (`nullptr`) == `false`
    * Nonzero (non-`nullptr`) == `true`

### Signedness

Adding `unsigned` in front of an integral type specifier makes the variable an unsigned type.
* i.e. the variable can only hold positive values but the upper limit is doubled.
    * Because the extra sign bit is freed up for use.