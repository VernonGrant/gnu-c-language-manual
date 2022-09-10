Previous: [Pragmas](Pragmas.md), Up: [Directing
Compilation](Directing-Compilation.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 30.2 Static Assertions 


You can add compiler-time tests for necessary conditions into your code
using `_Static_assert`. This can be useful, for example, to check that
the compilation target platform supports the type sizes that the code
expects. For example,

``` C
_Static_assert ((sizeof (long int) >= 8),
    "long int needs to be at least 8 bytes");
```

reports a compile-time error if compiled on a system with long integers
smaller than 8 bytes, with
'`long int needs to be at least 8 bytes`' as the error message.

Since calls `_Static_assert` are processed at compile time, the
expression must be computable at compile time and the error message must
be a literal string. The expression can refer to the sizes of variables,
but can't refer to their values. For example, the following static
assertion is invalid for two reasons:

``` C
char *error_message
  = "long int needs to be at least 8 bytes";
int size_of_long_int = sizeof (long int);

_Static_assert (size_of_long_int == 8, error_message);
```

The expression `size_of_long_int == 8` isn't computable at compile time,
and the error message isn't a literal string.

You can, though, use preprocessor definition values with
`_Static_assert`:

``` C
#define LONG_INT_ERROR_MESSAGE "long int needs to be \
at least 8 bytes"

_Static_assert ((sizeof (long int) == 8),
  LONG_INT_ERROR_MESSAGE);
```

Static assertions are permitted wherever a statement or declaration is
permitted, including at top level in the file, and also inside the
definition of a type.

``` C
union y
{
  int i;
  int *ptr;
  _Static_assert (sizeof (int *) == sizeof (int),
          "Pointer and int not same size");
};
```
