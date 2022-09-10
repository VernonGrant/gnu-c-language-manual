Next: [Loop Statements](Loop-Statements.md), Previous:
[Blocks](Blocks.md), Up: [Statements](Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 19.5 `return` Statement 


The `return` statement makes the containing function return immediately.
It has two forms. This one specifies no value to return:

``` C
return;
```

That form is meant for functions whose return type is `void` (see [The
Void Type](The-Void-Type.md)). You can also use it in a function that
returns nonvoid data, but that's a bad idea, since it makes the function
return garbage.

The form that specifies a value looks like this:

``` C
return value;
```

which computes the expression `value` and makes the function
return that. If necessary, the value undergoes type conversion to the
function's declared return value type, which works like assigning the
value to a variable of that type.
