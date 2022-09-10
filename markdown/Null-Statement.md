Next: [`goto` Statement and Labels](goto-Statement.md), Previous:
[Case Ranges](Case-Ranges.md), Up: [Statements](Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 19.11 Null Statement 


A *null statement* is just a semicolon. It does nothing.

A null statement is a placeholder for use where a statement is
grammatically required, but there is nothing to be done. For instance,
sometimes all the work of a `for`-loop is done in the `for`-header
itself, leaving no work for the body. Here is an example that searches
for the first newline in `array`:

``` C
for (p = array; *p != '\n'; p++)
  ;
```
