Previous: [The `#else` directive](else.md), Up: [Syntax of
Preprocessing Conditionals](Conditional-Syntax.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 26.6.2.5 The `#elif` directive 


One common case of nested conditionals is used to check for more than
two possible alternatives. For example, you might have

``` C
#if X == 1
/* … */
#else /* X != 1 */
#if X == 2
/* … */
#else /* X != 2 */
/* … */
#endif /* X != 2 */
#endif /* X != 1 */
```

Another conditional directive, `#elif`, allows this to be abbreviated as
follows:

``` C
#if X == 1
/* … */
#elif X == 2
/* … */
#else /* X != 2 and X != 1*/
/* … */
#endif /* X != 2 and X != 1*/
```

`#elif` stands for "else if". Like `#else`, it goes in the middle of a
conditional group and subdivides it; it does not require a matching
`#endif` of its own. Like `#if`, the `#elif` directive includes an
expression to be tested. The text following the `#elif` is processed
only if the original `#if`-condition failed and the `#elif` condition
succeeds.

More than one `#elif` can go in the same conditional group. Then the
text after each `#elif` is processed only if the `#elif` condition
succeeds after the original `#if` and all previous `#elif` directives
within it have failed.

`#else` is allowed after any number of `#elif` directives, but `#elif`
may not follow `#else`.
