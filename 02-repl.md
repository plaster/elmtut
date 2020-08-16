```
% elm repl
elm: getCurrentDirectory:getWorkingDirectory: does not exist (Current working directory no longer exists)
% cd
% cd work/elmtut
% elm repl
---- Elm 0.19.0 ----------------------------------------------------------------
Read <https://elm-lang.org/0.19.0/repl> to learn more: exit, help, imports, etc.
--------------------------------------------------------------------------------
```

```
> 1
1 : number
> 1+1
2 : number
> "Hello, World"
"Hello, World" : String
```

```
> ;
-- PARSE ERROR ------------------------------------------------------------- elm

Something went wrong while parsing repl_value_4's definition.

3| repl_value_4 =
4|   ;
     ^
I was expecting to see an expression, like x or 42.
```
