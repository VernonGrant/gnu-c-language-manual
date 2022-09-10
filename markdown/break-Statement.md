Next: [`for` Statement](for-Statement.md), Previous: [`do-while`
Statement](do_002dwhile-Statement.md), Up: [Loop
Statements](Loop-Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 19.6.3 `break` Statement 


The `break` statement looks like '`break;`'. Its effect is to
exit immediately from the innermost loop construct or `switch` statement
(see [`switch` Statement](switch-Statement.md)).

For example, this loop advances `p` until the next null character or
newline.

``` C
while (*p)
  {
    /* End loop if we have reached a newline.  */
    if (*p == '\n')
      break;
    p++
  }
```

When there are nested loops, the `break` statement exits from the
innermost loop containing it.

``` C
struct list_if_tuples
{
  struct list_if_tuples next;
  int length;
  data *contents;
};

void
process_all_elements (struct list_if_tuples *list)
{
  while (list)
    {
      /* Process all the elements in this node’s vector,
         stopping when we reach one that is null.  */
      for (i = 0; i < list->length; i++
        {
          /* Null element terminates this node’s vector.  */
          if (list->contents[i] == NULL)
            /* Exit the for loop.  */
            break;
          /* Operate on the next element.  */
          process_element (list->contents[i]);
        }

      list = list->next;
    }
}
```

The only way in C to exit from an outer loop is with `goto` (see [`goto`
Statement and Labels](goto-Statement.md)).
