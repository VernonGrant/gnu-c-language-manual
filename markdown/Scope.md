Next: [Preprocessing](Preprocessing.md), Previous: [Type
Conversions](Type-Conversions.md), Up: [GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


## 25 Scope 


Each definition or declaration of an identifier is visible in certain
parts of the program, which is typically less than the whole of the
program. The parts where it is visible are called its *scope*.

Normally, declarations made at the top-level in the source -- that is,
not within any blocks and function definitions -- are visible for the
entire contents of the source file after that point. This is called
*file scope* (see [File-Scope
Variables](File_002dScope-Variables.md)).

Declarations made within blocks of code, including within function
definitions, are visible only within those blocks. This is called *block
scope*. Here is an example:

``` C
void
foo (void)
{
  int x = 42;
}
```

In this example, the variable `x` has block scope; it is visible only
within the `foo` function definition block. Thus, other blocks could
have their own variables, also named `x`, without any conflict between
those variables.

A variable declared inside a subblock has a scope limited to that
subblock,

``` C
void
foo (void)
{
  {
    int x = 42;
  }
  // x is out of scope here.
}
```

If a variable declared within a block has the same name as a variable
declared outside of that block, the definition within the block takes
precedence during its scope:

``` C
int x = 42;

void
foo (void)
{
  int x = 17;
  printf ("%d\n", x);
}
```

This prints 17, the value of the variable `x` declared in the function
body block, rather than the value of the variable `x` at file scope. We
say that the inner declaration of `x` *shadows* the outer declaration,
for the extent of the inner declaration's scope.

A declaration with block scope can be shadowed by another declaration
with the same name in a subblock.

``` C
void
foo (void)
{
  char *x = "foo";
  {
    int x = 42;
    …
    exit (x / 6);
  }
}
```

A function parameter's scope is the entire function body, but it can be
shadowed. For example:

``` C
int x = 42;

void
foo (int x)
{
  printf ("%d\n", x);
}
```

This prints the value of `x` the function parameter, rather than the
value of the file-scope variable `x`. However,

Labels (see [`goto` Statement and Labels](goto-Statement.md)) have
*function* scope: each label is visible for the whole of the containing
function body, both before and after the label declaration:

``` C
void
foo (void)
{
  …
  goto bar;
  …
  {  // Subblock does not affect labels.
    bar:
    …
  }
  goto bar;
}
```

Except for labels, a declared identifier is not visible to code before
its declaration. For example:

``` C
int x = 5;
int y = x + 10;
```

will work, but:

``` C
int x = y + 10;
int y = 5;
```

cannot refer to the variable `y` before its declaration.

This is part of the GNU C Intro and Reference Manual and covered by its
license.

------------------------------------------------------------------------

Next: [Preprocessing](Preprocessing.md), Previous: [Type
Conversions](Type-Conversions.md), Up: [GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
