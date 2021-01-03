# Special Namespaces

**Elijjah** allows the use of special [namespaces](namespaces.md) to perform certain functions. This was always the original intent of namespaces, 
but features got added as the language grew.

## Native Code

The `__C__` namespace is for generating `extern "C"` constructs directly accessible from the C language.

## Building

The `__PACKAGE__` namespace is for generating Operating System packages.
The `__BUILD__` namespace is for generating Build System files.
And the `__PROJECT__` namespace is for describing the Project in ways the `.ez` file doesn't provide for.

## Other stuff

Put it here
