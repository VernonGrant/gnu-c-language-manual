Next: [Allocating File-Scope Variables](Allocating-File_002dScope.md),
Previous: [Static Local Variables](Static-Local-Variables.md), Up:
[Variables](Variables.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 20.8 `extern` Declarations 


An `extern` declaration is used to refer to a global variable whose
principal declaration comes elsewhere---in the same module, or in
another compilation module. It looks like this:

``` C
extern basetype decorated-variable;
```

Its meaning is that, in the current scope, the variable name refers to
the file-scope variable of that name---which needs to be declared in a
non-`extern`, non-`static` way somewhere else.

For instance, if one compilation module has this global variable
declaration

``` C
int error_count = 0;
```

then other compilation modules can specify this

``` C
extern int error_count;
```

to allow reference to the same variable.

The usual place to write an `extern` declaration is at top level in a
source file, but you can write an `extern` declaration inside a block to
make a global or static file-scope variable accessible in that block.

Since an `extern` declaration does not allocate space for the variable,
it can omit the size of an array:

``` C
extern int array[];
```

You can use `array` normally in all contexts where it is converted
automatically to a pointer. However, to use it as the operand of
`sizeof` is an error, since the size is unknown.

It is valid to have multiple `extern` declarations for the same
variable, even in the same scope, if they give the same type. They do
not conflict---they agree. For an array, it is legitimate for some
`extern` declarations can specify the size while others omit it.
However, if two declarations give different sizes, that is an error.

Likewise, you can use `extern` declarations at file scope (see
[File-Scope Variables](File_002dScope-Variables.md)) followed by an
ordinary global (non-static) declaration of the same variable. They do
not conflict, because they say compatible things about the same meaning
of the variable.

------------------------------------------------------------------------

Next: [Allocating File-Scope Variables](Allocating-File_002dScope.md),
Previous: [Static Local Variables](Static-Local-Variables.md), Up:
[Variables](Variables.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
