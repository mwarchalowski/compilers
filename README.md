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
