Next: [`return` Statement](return-Statement.md), Previous: [`if-else`
Statement](if_002delse-Statement.md), Up:
[Statements](Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 19.4 Blocks 


A *block* is a construct that contains multiple statements of any kind.
It begins with '`{`' and ends with '`}`', and has a
series of statements and declarations in between. Another name for
blocks is *compound statements*.

Is a block a statement? Yes and no. It doesn't *look* like a normal
statement---it does not end with a semicolon. But you can *use* it like
a statement; anywhere that a statement is required or allowed, you can
write a block and consider that block a statement.

So far it seems that a block is a kind of statement with an unusual
syntax. But that is not entirely true: a function body is also a block,
and that block is definitely not a statement. The text after a function
header is not treated as a statement; only a function body is allowed
there, and nothing else would be meaningful there.

In a formal grammar we would have to choose---either a block is a kind
of statement or it is not. But this manual is meant for humans, not for
parser generators. The clearest answer for humans is, "a block is a
statement, in some ways."


A block that isn't a function body is called an *internal block* or a
*nested block*. You can put a nested block directly inside another
block, but more often the nested block is inside some complex statement,
such as a `for` statement or an `if` statement.

There are two uses for nested blocks in C:

-   To specify the scope for local declarations. For instance, a local
    variable's scope is the rest of the innermost containing block.
-   To write a series of statements where, syntactically, one statement
    is called for. For instance, the `execute-if-true` of an
    `if` statement is one statement. To put multiple statements there,
    they have to be wrapped in a block, like this:
    
    ``` C
    if (x < 0)
      {
        printf ("x was negative\n");
        x = -x;
      }
    ```
    

This example (repeated from above) shows a nested block which serves
both purposes: it includes two statements (plus a declaration) in the
body of a `while` statement, and it provides the scope for the
declaration of `q`.

``` C
void
free_intlist (struct intlistlink *p)
{
  while (p)
    {
      struct intlistlink *q = p;
      p = p->next;
      free (q);
    }
}
```

------------------------------------------------------------------------

Next: [`return` Statement](return-Statement.md), Previous: [`if-else`
Statement](if_002delse-Statement.md), Up:
[Statements](Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
