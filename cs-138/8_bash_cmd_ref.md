# Bash Command Reference

`which`: Prints path to a command.

```
$ which ls
/bin/ls
```

`echo`: Write arguments seperated by spaces and terminated by newline. Generally used in `.sh` scripts.

```
$ echo no place like HOME
no place like HOME

$ echo " no place like HOME"
 no place like HOME

$ echo no place like $HOME
no place like /user/trevor/home

$ echo 'no place like $HOME'
no place like $HOME
```

### Globbing

Generally, commands are executed with arguments.

```
command -arg1 arg2 -arg3
```

* Globbing lets us quickly grab multiple files that match a certain pattern.

Consider this sample directory
```
$ ls
q1.cpp q2.cc q3.c q4.cc q5.C readme.txt
```

`*` matches any sequence of 0 or more chars

`?` matches ONLY 1 char

```
$ echo q*
q1.cpp q2.cc q3.c q4.cc q5.C

$ echo q*.??
q2.cc q4.cc
```

* `{...}` matches any alternative in the set

```
echo *.{C, cc, c}
q2.cc q3.c q4.cc q5.C
```

* `[...]` matches 1 char in the set

```
$ echo q[12]*
q1.cpp q2.cc
```

* `[!...]` matches 1 char not in the set

```
$ echo q[!1]*
q2.cc q3.c q4.cc q5.C
```

* Can create ranges using hyphen
    * `[0-3]` == `[0123]`
    * `[a-zA-Z]` == lowercase or uppercase letter
    
    * Hyphen is escaped by putting it at the start or end of a set.
        * `[-?*]*` == Matches filenames starting with a `-`, `?`, `*`

* Note: `*` doesn't match dotfiles

### Quoting

* Globbing is disabled in single/double quotes
* Single quotes: *everything* up to next single quote is protected (including NL, double quotes, etc.)
* Double quotes: Protects everything except doublequote, backquote, and `$VAR`s