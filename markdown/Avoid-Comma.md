Previous: [Clean Use of the Comma Operator](Clean-Comma.md), Up:
[Comma Operator](Comma-Operator.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 8.5.3 When Not to Use the Comma Operator 

You can use a comma in any subexpression, but in most cases it only
makes the code confusing, and it is clearer to raise all but the last of
the comma-separated expressions to a higher level. Thus, instead of
this:

``` C
x = (y += 4, 8);
```

it is much clearer to write this:

``` C
y += 4, x = 8;
```

or this:

``` C
y += 4;
x = 8;
```

Use commas only in the cases where there is no clearer alternative
involving multiple statements.

By contrast, don't hesitate to use commas in the expansion in a macro
definition. The trade-offs of code clarity are different in that case,
because the *use* of the macro may improve overall clarity so much that
the ugliness of the macro's *definition* is a small price to pay. See
[Macros](Macros.md).
