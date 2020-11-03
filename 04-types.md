```
ル╹ヮ╹ルɔ margarine:~/work/elmtut
% elm repl
---- Elm 0.19.1 ----------------------------------------------------------------
Say :help for help and :exit to exit! More at <https://elm-lang.org/0.19.1/repl>
--------------------------------------------------------------------------------
```

```
> "hello"
"hello" : String
```

```
> not True
False : Bool
```

```
> round 3.141592
3 : Int
```

```
> [ "Alice", "Bob" ]
["Alice","Bob"] : List String
```

```
> [ 1.0, 8.6, 42.1 ]
[1,8.6,42.1] : List Float
```

```
> []
[] : List a
```

```
> String.length
<function> : String -> Int
```

```
> String.length "オハヨーハヨー"
7 : Int
```

```
> String.length [ 1, 2, 3 ]
-- TYPE MISMATCH ---------------------------------------------------------- REPL

The 1st argument to `length` is not what I expect:

3|   String.length [ 1, 2, 3 ]
                   ^^^^^^^^^^^
This argument is a list of type:

    List number

But `length` needs the 1st argument to be:

    String
```
