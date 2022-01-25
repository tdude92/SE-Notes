# I/O with iostream and argc & argv

### argc & argv

Allows us to access command line arguments.

```
$ ./myprog -flurble blat

(in myprog.cc)
int main(int argc, char* argv[]) {
    // argc = 3
    // argv = {"./myprog", "-flurble", "blat"}
}
```
* `argc`: Number of cmd-line arguments
* `argv`: Arguments given as an array of char*

### Simple I/O

* `iostream` gives three useful streams
    1. `cin`: stdin
    2. `cout`: stdout
    3. `cerr`: stderr

* `>>` and `<<` operators have been overloaded for sending data to streams.

```
#include <iostream>
using namespace std;

int main() {
    cout << "Hello world~" << endl;

    int age;
    string name;
    cout << "Input your name and age" << endl;
    cin >> name >> age;

    if (age >= 18 && name == "Matthews") {
        cout << "heyyy" << endl;
    } else if (name == "Trevor") {
        cerr << endl;
        exit(1);
    } else {
        cout << "hey" << endl;
    }

    return 0;
}
```

**Input whitespace**

Note:
```
string foo, bar;
cin >> foo >> bar;

// Grabs next two tokens in input stream
// Skips all intermediate whitespace (space, tab, newline, etc.)
```

```
string foo;
getline(cin, foo);
// Gets input with whitespace intact
```

### iomanip

Output formatting tools

```
#include <iomanip>

for () {
    cout << left << setw(20) ... etc. 
}
```
### Variable-length Input and EOF

How to read variable amounts of inputs:
* C++ raises an `EOF` flag in `cin`

```
To check EOF (these acc work for any istream):
cin.eof() is true
cin.fail() is better in case there is a failure when reading the input stream.

// IMPORTANT
// Check eof/fail after the read
//                before the input is used.
while (true) {
    double next;
    cin >> next;
    if (cin.fail()) {
        break;
    }
    sum += next;
    count++;
}

// Note that cin.fail() will also be triggered if non-double garbage is inputted.

// Another method
while (cin >> next) {
    // cin >> next returns the cin object
    // which returns !cin.fail() when coerced into a bool.
}

// Distinguishing between eof and failure
while (true) {
    int i;
    if (!(cin >> i)) {
        if (cin.eof()) {
            break; // EOF! We're done here.
        }
        // Bad data, continue.
    }
}
```

* There is an implicit progress marker for each input stream
    * Assume `line` is a string variable.

    * `getline(cin, line)` means:
        * Read each character including whitespace
        * On the first newline:
            * Move the marker past the newline (but don't read it)
        * If marker at end of stream, set EOF flag to be true.
    
    * `cin >> flurble` means:
        * Move marker past all whitespace chars
        * Read each non-ws char into flurble
            * Stops just before the first following ws
        * If you reach the end of input, EOF flag raised
            * This is why EOF is not set to true until after the first failed read.
        
        ```
        // Complicated border case
        int n;
        string line;

        cin >> n;

        // stuff

        cin >> line;

        // Input "123input" will be split into 123 and input bc C++ is clever.
        // HOWEVER, if we read string first and inputted "input123", it won't split.
        ```

## I/O Redirection

```
./main

./main < in.txt

./main < in.txt > out.txt
// Input from in.txt
// Output to out.txt
```

* `>` single arrow truncates file
* `>>` double arrow appends to file