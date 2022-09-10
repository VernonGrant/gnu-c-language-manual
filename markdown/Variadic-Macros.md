Next: [Predefined Macros](Predefined-Macros.md), Previous:
[Concatenation](Concatenation.md), Up: [Macros](Macros.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 26.5.6 Variadic Macros 


A macro can be declared to accept a variable number of arguments much as
a function can. The syntax for defining the macro is similar to that of
a function. Here is an example:

``` C
#define eprintf(…) fprintf (stderr, __VA_ARGS__)
```

This kind of macro is called *variadic*. When the macro is invoked, all
the tokens in its argument list after the last named argument (this
macro has none), including any commas, become the *variable argument*.
This sequence of tokens replaces the identifier `__VA_ARGS__` in the
macro body wherever it appears. Thus, we have this expansion:

``` C
eprintf ("%s:%d: ", input_file, lineno)
     →  fprintf (stderr, "%s:%d: ", input_file, lineno)
```

The variable argument is completely macro-expanded before it is inserted
into the macro expansion, just like an ordinary argument. You may use
the `#` and `##` operators to stringify the variable argument or to
paste its leading or trailing token with another token. (But see below
for an important special case for `##`.)

**Warning:** don't use the identifier `__VA_ARGS__` for anything other
than this.

If your macro is complicated, you may want a more descriptive name for
the variable argument than `__VA_ARGS__`. You can write an argument name
immediately before the '`…`'; that name is used for the
variable argument.[^9^](#FOOT9) The `eprintf` macro above could
be written thus:

``` C
#define eprintf(args…) fprintf (stderr, args)
```

A variadic macro can have named arguments as well as variable arguments,
so `eprintf` can be defined like this, instead:

``` C
#define eprintf(format, …) \
  fprintf (stderr, format, __VA_ARGS__)
```

This formulation is more descriptive, but what if you want to specify a
format string that takes no arguments? In GNU C, you can omit the comma
before the variable arguments if they are empty, but that puts an extra
comma in the expansion:

``` C
eprintf ("success!\n")
     → fprintf(stderr, "success!\n", );
```

That's an error in the call to `fprintf`.

To get rid of that comma, the `##` token paste operator has a special
meaning when placed between a comma and a variable
argument.[^10^](#FOOT10) If you write

``` C
#define eprintf(format, …) \
  fprintf (stderr, format, ##__VA_ARGS__)
```

then use the macro `eprintf` with empty variable arguments, `##` deletes
the preceding comma.

``` C
eprintf ("success!\n")
     → fprintf(stderr, "success!\n");
```

This does *not* happen if you pass an empty argument, nor does it happen
if the token preceding `##` is anything other than a comma.

When the only macro parameter is a variable arguments parameter, and the
macro call has no argument at all, it is not obvious whether that means
an empty argument or a missing argument. Should the comma be kept, or
deleted? The C standard says to keep the comma, but the preexisting GNU
C extension deleted the comma. Nowadays, GNU C retains the comma when
implementing a specific C standard, and deletes it otherwise.

C99 mandates that the only place the identifier `__VA_ARGS__` can appear
is in the replacement list of a variadic macro. It may not be used as a
macro name, macro parameter name, or within a different type of macro.
It may also be forbidden in open text; the standard is ambiguous. We
recommend you avoid using that name except for its special purpose.

Variadic macros where you specify the parameter name is a GNU C feature
that has been supported for a long time. Standard C, as of C99, supports
only the form where the parameter is called `__VA_ARGS__`. For
portability to previous versions of GNU C you should use only named
variable argument parameters. On the other hand, for portability to
other C99 compilers, you should use only `__VA_ARGS__`.


------------------------------------------------------------------------

#### Footnotes 

##### [(9)](#DOCF9)

GNU C extension.

##### [(10)](#DOCF10)

GNU C extension.

------------------------------------------------------------------------

Next: [Predefined Macros](Predefined-Macros.md), Previous:
[Concatenation](Concatenation.md), Up: [Macros](Macros.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
