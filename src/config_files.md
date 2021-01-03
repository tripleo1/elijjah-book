## Config Files

Config files allow a programmer to set variables that are processed by `.ez` files. 

They are the equivalent of `-D` directives to the C compiler and properties in maven.

Consider them a form of build profiles

### Format

```
values = ["use_ssl", "no_frob"]

[defines]
x = 1
y = 2
```

The format only supports the `values` array and `defines` dictionary/map. Everything else is ignored.


> I am not sure what to make of this. It seems the build system is getting complicated.
> It is also not currently implemented in the reference compiler.
