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

```
> isNegative n = n < 0
<function> : number -> Bool
> isNegative 4
False : Bool
> isNegative 0
False : Bool
> isNegative -99
True : Bool
> isNegative ( -3 * -3 )
False : Bool
> isNegative $ -3 * -3
-- PARSE ERROR ------------------------------------------------------------- elm

Something went wrong while parsing repl_value_9's definition.

4| repl_value_9 =
5|   isNegative $ -3 * -3
                ^
I was expecting:

  - an argument, like `name` or `total`
  - an infix operator, like (+) or (==)
  - the rest of repl_value_9's definition. Maybe you forgot some code? Or maybe
    the body of `repl_value_9` needs to be indented?
```

```
> if True then 1 else 2
1 : number
> if True then + else -
-- PARSE ERROR ------------------------------------------------------------- elm

Something went wrong while parsing an `if` expression in repl_value_2's
definition.

4|   if True then + else -
                  ^
I was expecting to see an expression, like x or 42.
> (+)          
<function> : number -> number -> number
> if True then (+) else (-) 5 3
-- TYPE MISMATCH ----------------------------------------------------------- elm

The 2nd branch of this `if` does not match all the previous branches:

4|   if True then (+) else (-) 5 3
                           ^^^^^^^
The 2nd branch is:

    number

But all the previous branches result in:

    number -> number -> number

Hint: All branches in an `if` must produce the same type of values. This way, no
matter which branch we take, the result is always a consistent shape. Read
<https://elm-lang.org/0.19.0/union-types> to learn how to “mix” types.

Hint: Only Int and Float values work as numbers.
> (if True then (+) else (-)) 5 3
8 : number
> (if True then (+) else (-)) \
|   5 3
8 : number
```
