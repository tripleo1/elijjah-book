# Compilations

The **Elijjah** compiler uses what is called a compilation to analyze, generate and finalize code into a program or library.

Each compilation has a unique id that makes for a [reproducible build](https://en.wikipedia.org/wiki/Reproducible_builds).

Basically, the output will be in `COMP/$id/...`. Sorry, the indeterminacy is determined by the underlying build system.

> The id doesn't really make it reproducible, but this support is close to trivial to include in the compiler
> in the future.