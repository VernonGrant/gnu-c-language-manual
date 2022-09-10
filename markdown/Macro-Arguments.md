Next: [Stringification](Stringification.md), Previous: [Function-like
Macros](Function_002dlike-Macros.md), Up: [Macros](Macros.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 26.5.3 Macro Arguments 


Function-like macros can take *arguments*, just like true functions. To
define a macro that uses arguments, you insert *parameters* between the
pair of parentheses in the macro definition that make the macro
function-like. The parameters must be valid C identifiers, separated by
commas and optionally whitespace.

To invoke a macro that takes arguments, you write the name of the macro
followed by a list of *actual arguments* in parentheses, separated by
commas. The invocation of the macro need not be restricted to a single
logical line---it can cross as many lines in the source file as you
wish. The number of arguments you give must match the number of
parameters in the macro definition. When the macro is expanded, each use
of a parameter in its body is replaced by the tokens of the
corresponding argument. (The macro body is not required to use all of
the parameters.)

As an example, here is a macro that computes the minimum of two numeric
values, as it is defined in many C programs, and some uses.

``` C
#define min(X, Y)  ((X) < (Y) ? (X) : (Y))
  x = min(a, b);      → x = ((a) < (b) ? (a) : (b));
  y = min(1, 2);      → y = ((1) < (2) ? (1) : (2));
  z = min(a+28, *p);  → z = ((a+28) < (*p) ? (a+28) : (*p));
```

In this small example you can already see several of the dangers of
macro arguments. See [Macro Pitfalls](Macro-Pitfalls.md), for detailed
explanations.

Leading and trailing whitespace in each argument is dropped, and all
whitespace between the tokens of an argument is reduced to a single
space. Parentheses within each argument must balance; a comma within
such parentheses does not end the argument. However, there is no
requirement for square brackets or braces to balance, and they do not
prevent a comma from separating arguments. Thus,

``` C
macro (array[x = y, x + 1])
```

passes two arguments to `macro`: `array[x = y` and `x + 1]`. If you want
to supply `array[x = y, x + 1]` as an argument, you can write it as
`array[(x = y, x + 1)]`, which is equivalent C code. However, putting an
assignment inside an array subscript is to be avoided anyway.

All arguments to a macro are completely macro-expanded before they are
substituted into the macro body. After substitution, the complete text
is scanned again for macros to expand, including the arguments. This
rule may seem strange, but it is carefully designed so you need not
worry about whether any function call is actually a macro invocation.
You can run into trouble if you try to be too clever, though. See
[Argument Prescan](Argument-Prescan.md), for detailed discussion.

For example, `min (min (a, b), c)` is first expanded to

``` C
  min (((a) < (b) ? (a) : (b)), (c))
```

and then to

``` C
((((a) < (b) ? (a) : (b))) < (c)
 ? (((a) < (b) ? (a) : (b)))
 : (c))
```

(The line breaks shown here for clarity are not actually generated.)


You can leave macro arguments empty without error, but many macros will
then expand to invalid code. You cannot leave out arguments entirely; if
a macro takes two arguments, there must be exactly one comma at the top
level of its argument list. Here are some silly examples using `min`:

``` C
min(, b)        → ((   ) < (b) ? (   ) : (b))
min(a, )        → ((a  ) < ( ) ? (a  ) : ( ))
min(,)          → ((   ) < ( ) ? (   ) : ( ))
min((,),)       → (((,)) < ( ) ? ((,)) : ( ))

min()      error→ macro "min" requires 2 arguments, but only 1 given
min(,,)    error→ macro "min" passed 3 arguments, but takes just 2
```

Whitespace is not a preprocessing token, so if a macro `foo` takes one
argument, `foo ()` and `foo ( )` both supply it an empty argument.

Macro parameters appearing inside string literals are not replaced by
their corresponding actual arguments.

``` C
#define foo(x) x, "x"
foo(bar)        → bar, "x"
```

See the next subsection for how to insert macro arguments into a string
literal.

The token following the macro call and the last token of the macro
expansion do not become one token even if it looks like they could:

``` C
#define foo()  abc
foo()def        → abc def
```

------------------------------------------------------------------------

Next: [Stringification](Stringification.md), Previous: [Function-like
Macros](Function_002dlike-Macros.md), Up: [Macros](Macros.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
