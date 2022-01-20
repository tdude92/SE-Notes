# File I/O

* From `<fstream>` library
    * We use `ifstream` and `ofstream` objects.
    * Create a stream object and use it just like `cin` or `cout`.
        * `myin.fail()` returns `true` if stream creation fails.
    
Usage:

```
#include <fstream>
using namespace std;

int main() {
    ifstream myin {"input.txt"};

    const string myin2 = "in2.txt";
    ifstream myin2 {myin2};

    int grade1, grade2;
    myin  >> grade1;
    myin2 >> grade2;

    // IMPORTANT: Close the files
    myin.close();
    myin2.close();

    return 0;
}
```

This is ok too:

```
ofstream os;
os.open("output_file.txt");
```

* Usually bad practice to reopen stream objects after closing them tho.

**istream \& ostream**: Base class of both if/ofstreams and cin/cout

```
void printAnswer(ofstream& os, string answer) {
    output << "The answer is " << answer << endl;
}

int main() {
    ofstream file {"foo.txt"};

    // All OK
    printAnswer(cout, 42);
    printAnswer(cerr, "Clean living");
    printAnswer(file, "Pancakes");

    file.close();
    return 0;
}
```


