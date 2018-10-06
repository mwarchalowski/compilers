## LL(1) Recursive-Descent Parser

![syntax tree](/assets/llrdc1.png)

```c
/** To parse a statement, call stat(); */
void stat() { returnstat(); }
void returnstat() { match("return" ); expr(); match(";" ); }
void expr() { match("x" ); match("+" ); match("1" ); }
```

![syntax tree](/assets/llrdc2.png)
```c
void stat() {
if ( «lookahead token is return» ) returnstat();
else if ( «lookahead token is identifier» ) assign();
else if ( «lookahead token is if » ) ifstat();
else «parse error»
}
```

#### Key Points

* Top-down parser because it starts at the
top of the parse tree and works its way down to the token leaf nodes.
* Descent refers to its top-down nature, and recursive refers
to the fact that its functions potentially call themselves. For example, the stat substructure
for the assignment statement appears within (under) the stat for
the if statement.
* The formal designation for a top-down parser that uses
a single lookahead token is LL(1).
* The first L means “read the input from left to right.”
* The second L means “descend into parse tree children from left to right.”
* For complicated languages, we can use more lookahead yielding. LL(k) Recursive-Descent Parser
