# Ez Files

To compile **Elijjah** source code, you need to create an.ez file.  The syntax is simple.

```
program program_name

lib
    library1: "library1"

generate
    lang: "c"

end
```

As you can see, you name the program with a program directive, and there is a set of library files in the directory library1.
It also manually generates c code. It is not necessary to put this here, and sometimes even not recommended because of the 
desire to have cross-plpatform code.
