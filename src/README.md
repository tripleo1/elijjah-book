# The Elijjah Book

> Done in the spirit of [The Rust Book](https://doc.rust-lang.org/stable/book/)

## Table of Contents

- [The Elijjah Book](#the-elijjah-book)
  - [Table of Contents](#table-of-contents)
  - [Background](#background)
  - [Install](#install)
  - [Other Software Required/Used](#other-software-requiredused)
  - [Usage](#usage)
  - [Progress](#progress)
  - [Documentation](#documentation)
  - [Contributing](#contributing)
  - [License](#license)
  - [Contact](#contact)

## Background


Elijjah is a high-level language suitable for replacement or supplementation of Java and C/C++. It is meant to integrate into current C and Java projects. 

It is intended to provide the power of C++, the expressibility of Python, and the utility of Java.  The code the reference compiler generates if C/C++ or Java is intended to complement each and every one of those in any combination.  It can reliably interact with Java libraries or C/C++ libraries like Swing/JavaFX, SWT, boost, or gtk and Qt.

[Read more](docs/language-overview.md)

## Install

Elijah is not ready for prime-time yet. But you can test it by running it from the checkout directory or install it to your home directory (actually this is not supported yet).

[See this document](https://gitlab.com/elijah-team/elijah-lang/-/wikis/Building-Elijjah-from-source)

## Other Software Required/Used

  * antlr (included)
  * javassist (not used yet, but included)
  * python (not yet)
  * java-compiler (java8, although I use 11)
  * JDeferred
  * Apache Commons Codec and CLI
  * XStream (although it is not being used now)
  * Google Guava

## Usage

Compile a system using an `.ez` file:

```
eljc test.ez
```

You will also be able to substitute `eljc` with `elcc` when I port the compiler to C.

## Progress

The current branch is [`pull-model`](https://gitlab.com/elijah-team/elijah-lang/-/tree/pull-model).
It is derived from [`genericA`](https://gitlab.com/elijah-team/elijah-lang/-/tree/genericA).
This will feed back into master/main 

The repo is currently buildable from maven.  You can also import into Eclipse and IDEA
and get up and running.  The tests need to run run from the root directory, which is 
done automatically in maven but not IDEA.

Much work is needed.

All of this is a work in progress and your support would be appreciated.

## Documentation

[wiki](https://gitlab.com/elijah-team/elijah-lang/-/wikis/home)

[GitBook: The Elijjah Book](https://oluoluolu-gh.gitbook.io/elijjah-book/)

[The Elijjah Book: mdbook](https://tripleo1.github.io/elijjah-book/) \(this one is better\)

[GitBook: Elijjah by Example](https://oluoluolu-gh.gitbook.io/elijjah-by-example/)

[Documentation on GitLab](https://elijah-team.gitlab.io/elijah-lang/) (look here first)

## Contributing

See [the contributing file](CONTRIBUTING.md)!

PRs accepted.

## License

**Elijjah** is free software intended for use on all systems, including GNU/Linux.

[LGPL 3](LICENSE)

## Contact

oluoluolu+elijah \(at\) gmail.com
[@tripleo_sw Twitter](https://twitter.com/tripleo_sw)

[google group](https://groups.google.com/forum/#!forum/elijjah)
