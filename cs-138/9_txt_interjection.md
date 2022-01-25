# Text File Representations

**ASCII**: American Standard Code for Information Interchange
* 7 bits per char
* 8th bit for parity checking

**EBCDIC**: IBM encoding for mainframes
* 8 bits per char

### ASCII
* 7 bits ==> 128 chars
* ASCII defines sorting order

* Ranges
    * 0 - 32: Non-printing control chars
        * 0: Null
        * 9: Tab
        * 10: Line Feed         (LF)
        * 13: Carriage Return   (CR)
        * 32: Space
    * 48 - 57: 0 to 9
    * 65 - 90: A to Z
    * 97 - 122: a to z

* Encoding newlines
    * Mac (pre-OSX):    CR      (\r)
    * Windows:          CRLF    (\r\n)
    * UNIX:             LF      (\n)

* Last line ends with newline in UNIX but not Windows.
