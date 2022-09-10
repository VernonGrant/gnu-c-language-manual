Next: [Function Calls](Function-Calls.md), Previous: [Function
Definitions](Function-Definitions.md), Up: [Functions](Functions.md)
 
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 22.2 Function Declarations 


To call a function, or use its name as a pointer, a *function
declaration* for the function name must be in effect at that point in
the code. The function's definition serves as a declaration of that
function for the rest of the containing scope, but to use the function
in code before the definition, or from another compilation module, a
separate function declaration must precede the use.

A function declaration looks like the start of a function definition. It
begins with the return value type (`void` if none) and the function
name, followed by argument declarations in parentheses (though these can
sometimes be omitted). But that's as far as the similarity goes: instead
of the function body, the declaration uses a semicolon.


A declaration that specifies argument types is called a *function
prototype*. You can include the argument names or omit them. The names,
if included in the declaration, have no effect, but they may serve as
documentation.

This form of prototype specifies fixed argument types:

``` C
rettype function (argtypes…);
```

This form says the function takes no arguments:

``` C
rettype function (void);
```

This form declares types for some arguments, and allows additional
arguments whose types are not specified:

``` C
rettype function (argtypes…, ...);
```

For a parameter that's an array of variable length, you can write its
declaration with '`*`' where the "length" of the array would
normally go; for example, these are all equivalent.

``` C
double maximum (int n, int m, double a[n][m]);
double maximum (int n, int m, double a[*][*]);
double maximum (int n, int m, double a[ ][*]);
double maximum (int n, int m, double a[ ][m]);
```

The old-fashioned form of declaration, which is not a prototype, says
nothing about the types of arguments or how many they should be:

``` C
rettype function ();
```

**Warning:** Arguments passed to a function declared without a prototype
are converted with the default argument promotions (see [Argument
Promotions](Argument-Promotions.md). Likewise for additional arguments
whose types are unspecified.

Function declarations are usually written at the top level in a source
file, but you can also put them inside code blocks. Then the function
name is visible for the rest of the containing scope. For example:

``` C
void
foo (char *file_name)
{
  void save_file (char *);
  save_file (file_name);
}
```

If another part of the code tries to call the function `save_file`, this
declaration won't be in effect there. So the function will get an
implicit declaration of the form `extern int save_file ();`. That
conflicts with the explicit declaration here, and the discrepancy
generates a warning.

The syntax of C traditionally allows omitting the data type in a
function declaration if it specifies a storage class or a qualifier.
Then the type defaults to `int`. For example:

``` C
static foo (double x);
```

defaults the return type to `int`. This is bad practice; if you see it,
fix it.

Calling a function that is undeclared has the effect of an creating
*implicit* declaration in the innermost containing scope, equivalent to
this:

``` C
extern int function ();
```

This declaration says that the function returns `int` but leaves its
argument types unspecified. If that does not accurately fit the
function, then the program **needs** an explicit declaration of the
function with argument types in order to call it correctly.

Implicit declarations are deprecated, and a function call that creates
one causes a warning.

------------------------------------------------------------------------

Next: [Function Calls](Function-Calls.md), Previous: [Function
Definitions](Function-Definitions.md), Up: [Functions](Functions.md)
 
[Contents](index.md#SEC_Contents "Table of contents")  
