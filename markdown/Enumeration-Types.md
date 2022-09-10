Next: [Defining Typedef Names](Defining-Typedef-Names.md), Previous:
[Arrays](Arrays.md), Up: [GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


## 17 Enumeration Types 


An *enumeration type* represents a limited set of integer values, each
with a name. It is effectively equivalent to a primitive integer type.

Suppose we have a list of possible emotional states to store in an
integer variable. We can give names to these alternative values with an
enumeration:

``` C
enum emotion_state { neutral, happy, sad, worried,
                     calm, nervous };
```

(Never mind that this is a simplistic way to classify emotional states;
it's just a code example.)

The names inside the enumeration are called *enumerators*. The
enumeration type defines them as constants, and their values are
consecutive integers; `neutral` is 0, `happy` is 1, `sad` is 2, and so
on. Alternatively, you can specify values for the enumerators explicitly
like this:

``` C
enum emotion_state { neutral = 2, happy = 5,
                     sad = 20, worried = 10,
                     calm = -5, nervous = -300 };
```

Each enumerator which does not specify a value gets value zero (if it is
at the beginning) or the next consecutive integer.

``` C
/* neutral is 0 by default,
   and worried is 21 by default.  */
enum emotion_state { neutral,
                      happy = 5, sad = 20, worried,
                      calm = -5, nervous = -300 };
```

If an enumerator is obsolete, you can specify that using it should cause
a warning, by including an attribute in the enumerator's declaration.
Here is how `happy` would look with this attribute:

``` C
happy __attribute__
      ((deprecated
        ("impossible under plutocratic rule")))
      = 5,
```

See [Attributes in Declarations](Attributes.md).

You can declare variables with the enumeration type:

``` C
enum emotion_state feelings_now;
```

In the C code itself, this is equivalent to declaring the variable
`int`. (If all the enumeration values are positive, it is equivalent to
`unsigned int`.) However, declaring it with the enumeration type has an
advantage in debugging, because GDB knows it should display the current
value of the variable using the corresponding name. If the variable's
type is `int`, GDB can only show the value as a number.

The identifier that follows `enum` is called a *type tag* since it
distinguishes different enumeration types. Type tags are in a separate
name space and belong to scopes like most other names in C. See [Type
Tags](Type-Tags.md), for explanation.

You can predeclare an `enum` type tag like a structure or union type
tag, like this:

``` C
enum foo;
```

The `enum` type is incomplete until you finish defining it.

You can optionally include a trailing comma at the end of a list of
enumeration values:

``` C
enum emotion_state { neutral, happy, sad, worried,
                     calm, nervous, };
```

This is useful in some macro definitions, since it enables you to
assemble the list of enumerators without knowing which one is last. The
extra comma does not change the meaning of the enumeration in any way.

------------------------------------------------------------------------

Next: [Defining Typedef Names](Defining-Typedef-Names.md), Previous:
[Arrays](Arrays.md), Up: [GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
