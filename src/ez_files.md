# Ez Files

To compile **Elijjah** source code, you need to create an .ez file.  The syntax is simple.

```
program program_name

lib
    library1: "library1"

generate
    lang: "c"

end
```

In the `lib` part, it is necessary to list all directories where **Elijjah** code resides, as this is where the compiler will look
for source.  Filenames in **Elijjah** have no meaning and there is no set directory structure.

As you can see, you name the program with a `program` directive, and there is a set of library files in the directory library1.
It also manually generates c code. It is not necessary to put this here, and sometimes even not recommended because of the 
desire to have cross-platform code.

Instead of a `program` directive, you can also put `shared` for shared (dynamic) libraries or `library` for static libraries.
Note that depending on your program dependencies, you may need to use a `shared` directive.  If `library` is specified by default, 
you cann override this in the specification section.

```
program program_name2

lib
    command: "."
    library1: ".."
    library_lgpl: ("library2", "0.3.4") [
        shared: true
    ]
    library_java: "library3" [
        only_gen: java
//        maven: ("x:y:z", "1.1.0")
    ]

generate
//    lang: "c"

end
```

Note here that `program_name2.elijah` is in the current directory, alongside it's `.ez` file, with common files it may share with
other programs in the parent directory. It loads `library2` by [elget](el_get.md) with a specific version that must always be specified.
This library is overridded as above to be linked dynamically as described above.  And finally, on Java outputs, it processes a
special directory `library3`.  The syntax to add maven dependencies is commented out above - in this case the `library3` will be ignored, 
and the directory wont be processed.  Finally `lang` is commented out in the `generate` section because of the cross-platform nature of the 
program here.  Processing with the Java native version of the compiler `eljc` will by default genereate a Java project and with the C-native
version `elcc` will produce a C project.  This can be overridden in both cases by using the `--gen` command-line oeprator.

> Talk about config files and ifdef
