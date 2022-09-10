Next: [UTF-8 String Constants](UTF_002d8-String-Constants.md),
Previous: [Character Constants](Character-Constants.md), Up:
[Constants](Constants.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 12.7 String Constants 


A *string constant* represents a series of characters. It starts with
'`"`' and ends with '`"`'; in between are the contents
of the string. Quoting special characters such as '`"`',
'`\`' and newline in the contents works in string constants as
in character constants. In a string constant, '`'`' does not
need to be quoted.

A string constant defines an array of characters which contains the
specified characters followed by the null character (code 0). Using the
string constant is equivalent to using the name of an array with those
contents. In simple cases, the length in bytes of the string constant is
one greater than the number of characters written in it.

As with any array in C, using the string constant in an expression
converts the array to a pointer (see [Pointers](Pointers.md)) to the
array's first element (see [Accessing Array
Elements](Accessing-Array-Elements.md)). This pointer will have type
`char *` because it points to an element of type `char`. `char *` is an
example of a type designator for a pointer type (see [Pointer-Type
Designators](Pointer-Type-Designators.md)). That type is used for
strings generally, not just the strings expressed as constants in a
program.

Thus, the string constant `"Foo!"` is almost equivalent to declaring an
array like this

``` C
char string_array_1[] = {'F', 'o', 'o', '!', '\0' };
```

and then using `string_array_1` in the program. There are two
differences, however:

-   The string constant doesn't define a name for the array.
-   The string constant is probably stored in a read-only area of
    memory.

Newlines are not allowed in the text of a string constant. The motive
for this prohibition is to catch the error of omitting the closing
'`"`'. To put a newline in a constant string, write it as
'`\n`' in the string constant.

A real null character in the source code inside a string constant causes
a warning. To put a null character in the middle of a string constant,
write '`\0`' or '`\000`'.

Consecutive string constants are effectively concatenated. Thus,

``` C
"Fo" "o!"   is equivalent to   "Foo!"
```

This is useful for writing a string containing multiple lines, like
this:

``` C
"This message is so long that it needs more than\n"
"a single line of text.  C does not allow a newline\n"
"to represent itself in a string constant, so we have to\n"
"write \\n to put it in the string.  For readability of\n"
"the source code, it is advisable to put line breaks in\n"
"the source where they occur in the contents of the\n"
"constant.\n"
```

The sequence of a backslash and a newline is ignored anywhere in a C
program, and that includes inside a string constant. Thus, you can write
multi-line string constants this way:

``` C
"This is another way to put newlines in a string constant\n\
and break the line after them in the source code."
```

However, concatenation is the recommended way to do this.

You can also write perverse string constants like this,

``` C
"Fo\
o!"
```

but don't do that---write it like this instead:

``` C
"Foo!"
```

Be careful to avoid passing a string constant to a function that
modifies the string it receives. The memory where the string constant is
stored may be read-only, which would cause a fatal `SIGSEGV` signal that
normally terminates the function (see [Signals](Signals.md). Even
worse, the memory may not be read-only. Then the function might modify
the string constant, thus spoiling the contents of other string
constants that are supposed to contain the same value and are unified by
the compiler.

------------------------------------------------------------------------

Next: [UTF-8 String Constants](UTF_002d8-String-Constants.md),
Previous: [Character Constants](Character-Constants.md), Up:
[Constants](Constants.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
