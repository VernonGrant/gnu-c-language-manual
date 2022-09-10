Next: [Variable-Length Parameter
Lists](Variable-Number-of-Arguments.md), Up: [Advanced Function
Features](Advanced-Definitions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 22.7.1 Variable-Length Array Parameters 


An array parameter can have variable length: simply declare the array
type with a size that isn't constant. In a nested function, the length
can refer to a variable defined in a containing scope. In any function,
it can refer to a previous parameter, like this:

``` C
struct entry
tester (int len, char data[len][len])
{
  …
}
```

Alternatively, in function declarations (but not in function
definitions), you can use `[*]` to denote that the array parameter is of
a variable length, such that these two declarations mean the same thing:

``` C
struct entry
tester (int len, char data[len][len]);
```

``` C
struct entry
tester (int len, char data[*][*]);
```

The two forms of input are equivalent in GNU C, but emphasizing that the
array parameter is variable-length may be helpful to those studying the
code.

You can also omit the length parameter, and instead use some other
in-scope variable for the length in the function definition:

``` C
struct entry
tester (char data[*][*]);
…
int dataLength = 20;
…
struct entry
tester (char data[dataLength][dataLength])
{
  …
}
```


In GNU C, to pass the array first and the length afterward, you can use
a *parameter forward declaration*, like this:

``` C
struct entry
tester (int len; char data[len][len], int len)
{
  …
}
```

The '`int len`' before the semicolon is the parameter forward
declaration; it serves the purpose of making the name `len` known when
the declaration of `data` is parsed.

You can write any number of such parameter forward declarations in the
parameter list. They can be separated by commas or semicolons, but the
last one must end with a semicolon, which is followed by the "real"
parameter declarations. Each forward declaration must match a subsequent
"real" declaration in parameter name and data type.

Standard C does not support parameter forward declarations.

------------------------------------------------------------------------

Next: [Variable-Length Parameter
Lists](Variable-Number-of-Arguments.md), Up: [Advanced Function
Features](Advanced-Definitions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
