Next: [The `#else` directive](else.md), Previous: [The `#if`
directive](if.md), Up: [Syntax of Preprocessing
Conditionals](Conditional-Syntax.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 26.6.2.3 The `defined` test 


The special operator `defined` is used in `#if` and `#elif` expressions
to test whether a certain name is defined as a macro. `defined name` and
`defined (name)` are both expressions whose value is 1 if
`name`{.variable} is defined as a macro at the current point in the
program, and 0 otherwise. Thus, `#if defined MACRO` is precisely
equivalent to `#ifdef MACRO`.

`defined` is useful when you wish to test more than one macro for
existence at once. For example,

``` C
#if defined (__arm__) || defined (__PPC__)
```

would succeed if either of the names `__arm__` or `__PPC__` is defined
as a macro---in other words, when compiling for ARM processors or
PowerPC processors.

Conditionals written like this:

``` C
#if defined BUFSIZE && BUFSIZE >= 1024
```

can generally be simplified to just `#if BUFSIZE >= 1024`, since if
`BUFSIZE` is not defined, it will be interpreted as having the value
zero.

In GCC, you can include `defined` as part of another macro definition,
like this:

``` C
#define MACRO_DEFINED(X) defined X

#if MACRO_DEFINED(BUFSIZE)
```

which would expand the `#if` expression to:

``` C
#if defined BUFSIZE
```

Generating `defined` in this way is a GNU C extension.
