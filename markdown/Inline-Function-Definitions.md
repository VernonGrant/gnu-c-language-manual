Previous: [Nested Functions](Nested-Functions.md), Up: [Advanced
Function Features](Advanced-Definitions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 22.7.4 Inline Function Definitions 


To declare a function inline, use the `inline` keyword in its
definition. Here's a simple function that takes a pointer-to-`int` and
increments the integer stored there---declared inline.

``` C
struct list
{
  struct list *first, *second;
};

inline struct list *
list_first (struct list *p)
{
  return p->first;
}

inline struct list *
list_second (struct list *p)
{
  return p->second;
}
```

optimized compilation can substitute the inline function's body for any
call to it. This is called *inlining* the function. It makes the code
that contains the call run faster, significantly so if the inline
function is small.

Here's a function that uses `list_second`:

``` C
int
pairlist_length (struct list *l)
{
  int length = 0;
  while (l)
    {
      length++;
      l = list_second (l);
    }
  return length;
}
```

Substituting the code of `list_second` into the definition of
`pairlist_length` results in this code, in effect:

``` C
int
pairlist_length (struct list *l)
{
  int length = 0;
  while (l)
    {
      length++;
      l = l->second;
    }
  return length;
}
```

Since the definition of `list_second` does not say `extern` or `static`,
that definition is used only for inlining. It doesn't generate code that
can be called at run time. If not all the calls to the function are
inlined, there must be a definition of the same function name in another
module for them to call.


Adding `static` to an inline function definition means the function
definition is limited to this compilation module. Also, it generates
run-time code if necessary for the sake of any calls that were not
inlined. If all calls are inlined then the function definition does not
generate run-time code, but you can force generation of run-time code
with the option `-fkeep-inline-functions`.


Specifying `extern` along with `inline` means the function is external
and generates run-time code to be called from other separately compiled
modules, as well as inlined. You can define the function as `inline`
without `extern` in other modules so as to inline calls to the same
function in those modules.

Why are some calls not inlined? First of all, inlining is an
optimization, so non-optimized compilation does not inline.

Some calls cannot be inlined for technical reasons. Also, certain usages
in a function definition can make it unsuitable for inline substitution.
Among these usages are: variadic functions, use of `alloca`, use of
computed goto (see [Labels as Values](Labels-as-Values.md)), and use
of nonlocal goto. The option `-Winline` requests a warning when
a function marked `inline` is unsuitable to be inlined. The warning
explains what obstacle makes it unsuitable.

Just because a call *can* be inlined does not mean it *should* be
inlined. The GNU C compiler weighs costs and benefits to decide whether
inlining a particular call is advantageous.

You can force inlining of all calls to a given function that can be
inlined, even in a non-optimized compilation. by specifying the
'`always_inline`' attribute for the function, like this:

``` C
/* Prototype.  */
inline void foo (const char) __attribute__((always_inline));
```

This is a GNU C extension. See [Attributes in
Declarations](Attributes.md).

A function call may be inlined even if not declared `inline` in special
cases where the compiler can determine this is correct and desirable.
For instance, when a static function is called only once, it will very
likely be inlined. With `-flto`, link-time optimization, any
function might be inlined. To absolutely prevent inlining of a specific
function, specify `__attribute__((__noinline__))` in the function's
definition.

------------------------------------------------------------------------

Previous: [Nested Functions](Nested-Functions.md), Up: [Advanced
Function Features](Advanced-Definitions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
