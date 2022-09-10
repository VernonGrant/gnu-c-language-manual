Next: [Macro Arguments](Macro-Arguments.md), Previous: [Object-like
Macros](Object_002dlike-Macros.md), Up: [Macros](Macros.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 26.5.2 Function-like Macros 


You can also define macros whose use looks like a function call. These
are called *function-like macros*. To define one, use the `#define`
directive with a pair of parentheses immediately after the macro name.
For example,

``` C
#define lang_init()  c_init()
lang_init()
     → c_init()
```

A function-like macro is expanded only when its name appears with a pair
of parentheses after it. If you write just the name, without
parentheses, it is left alone. This can be useful when you have a
function and a macro of the same name, and you wish to use the function
sometimes. Whitespace and line breaks before or between the parentheses
are ignored when the macro is called.

``` C
extern void foo(void);
#define foo() /* optimized inline version */
/* … */
  foo();
  funcptr = foo;
```

Here the call to `foo()` expands the macro, but the function pointer
`funcptr` gets the address of the real function `foo`. If the macro were
to be expanded there, it would cause a syntax error.

If you put spaces between the macro name and the parentheses in the
macro definition, that does not define a function-like macro, it defines
an object-like macro whose expansion happens to begin with a pair of
parentheses. Here is an example:

``` C
#define lang_init ()    c_init()
lang_init()
     → () c_init()()
```

The first two pairs of parentheses in this expansion come from the
macro. The third is the pair that was originally after the macro
invocation. Since `lang_init` is an object-like macro, it does not
consume those parentheses.

Any name can have at most one macro definition at a time. Thus, you
can't define the same name as an object-like macro and a function-like
macro at once.

------------------------------------------------------------------------

Next: [Macro Arguments](Macro-Arguments.md), Previous: [Object-like
Macros](Object_002dlike-Macros.md), Up: [Macros](Macros.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
