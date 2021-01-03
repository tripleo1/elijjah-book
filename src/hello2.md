# Hello, World! Part 2

Take the hello world file from [Part 1](hello.md), and create a `hello.ez` file in the same directory.

```
program hello_world

lib
    '.'

generate
    lang: "C"
end
```

Then call your compiler:

`eljc hello.ez`

The output will be somplace interesting. See [Compilations](compilations.md)
