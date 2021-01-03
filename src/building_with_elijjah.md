# Building with Elijjah

**Elijjah** includes a built-in build system for native code, and generates build files for the generated code.
This can be ant files, maven files, gradle files, Bazel files, CMake files, Meson files or normal Makefiles.
I'm sure I'm missing one or two.

The `__PACKAGE__` namespace is for generating Operating System packages.
The `__BUILD__` namespace is for generating Build System files.
And the `__PROJECT__` namespace is for describing the Project in ways the `.ez` file doesn't provide for.

It is expected that "plugin"-style support will be added at a later date to support all of this.

- [Ez Files](ez_files.md)
- [Config Files](config_files.md)
- [elget](el_get.md)
- [Package Management](package_management.md)


See [Special Namespaces](special_namespaces.md)

> Build generation is not implemented yet.
> This includes the special namespaces.