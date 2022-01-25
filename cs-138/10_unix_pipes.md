# UNIX Pipes

Unix philosophy: several tools that do one small function.
* Combine these tools with pipes and redirections

eg. How many words in first 20 lines of foo.txt
* `head -n file`: prints first n lines of file
* `wc`: counts words, lines, chars. `wc- wc` for words.

```
$ head -20 foo.txt | wc - w

or 

$ cat foo.txt | head -20 | wc -w
```