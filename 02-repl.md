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

```
> fib n = \  
|   if n <= 1 \
|   then 1 \   
|   else fib (n - 1) + fib (n - 2)
<function> : number1 -> number
> fib 0
1 : number
> fib 1
1 : number
> fib 2
2 : number
> fib 3
3 : number
> fib 4
5 : number
> fib 5
8 : number
> fib 6
13 : number
> fib 10
89 : number
```

```
> fib_cps n c = \
|   if n <= 1 \    
|   then c 1 \     
|   else fib_cps (n - 1) \
|   \r1 -> fib_cps (n - 2) \
|   \r2 -> c (r1 + r2)
-- PARSE ERROR ------------------------------------------------------------- elm

Something went wrong while parsing an `if` expression in fib_cps's definition.

4|   if n <= 1 
5|   then c 1 
6|   else fib_cps (n - 1) 
7|   \r1 -> fib_cps (n - 2) 
     ^
I was expecting:

  - an argument, like `name` or `total`
  - an infix operator, like (+) or (==)
  - the end of that `if`. Maybe you forgot some code? Or maybe the body of
    `fib_cps` needs to be indented?
```

```
> fib_cps n c = \         
|   if n <= 1 \             
|   then c 1 \              
|   else fib_cps (n - 1) (\ 
|     \r1 -> fib_cps (n - 2) (\
|       \r2 -> c (r1 + r2) \   
|       ))
<function> : number1 -> (number -> a) -> a
> fib_cps 1 (\n -> n)
1 : number
> fib_cps 5 (\n -> n)
RangeError: Maximum call stack size exceeded> 
> fib_cps 2 (\n -> n)
RangeError: Maximum call stack size exceeded> 
```

at elm-lang.org/try:

```
import Html

fib n =
  if n < 2
  then 1
  else (fib (n-1)) + (fib (n-2))

fib_cps n c =
  if n < 2
  then c 1
  else
    fib_cps (n-1)
    (\r1 ->
      fib_cps (n-2)
      (\r2 -> c (r1 + r2)))
      
fact n =
  if n == 0
  then 1
  else n * fact (n-1)

fact_cps n c =
  if n == 0
  then c 1
  else
    fact_cps (n-1)
    (\r -> c (n * r))
    
fact_cps2 c n =
  if n == 0
  then c 1
  else
    fact_cps2
      (\r -> c (n * r))
      (n-1)

main =
  Html.text
  (String.fromInt (fib 10)) -- OK
  -- (fib_cps 10 String.fromInt) -- NG
  -- (String.fromInt (fact 10)) -- OK
  -- (fact_cps 10 String.fromInt) -- NG
  -- (fact_cps2 String.fromInt 10) -- NG
```

```
> names = [ "Alice", "Bob", "Victor" ]                                                           
["Alice","Bob","Victor"] : List String
> List.isEmpty names
False : Bool
> List.reverse names
["Victor","Bob","Alice"] : List String
> map
-- NAMING ERROR ------------------------------------------------------------ elm

I cannot find a `map` variable:

15|   map
      ^^^
These names seem close though:

    max
    min
    tan
    abs

Hint: Read <https://elm-lang.org/0.19.0/imports> to see how `import`
declarations work in Elm.
> List.map
<function> : (a -> b) -> List a -> List b
> List.map length names
-- NAMING ERROR ------------------------------------------------------------ elm

I cannot find a `length` variable:

15|   List.map length names
               ^^^^^^
These names seem close though:

    negate
    not
    List.length
    e

Hint: Read <https://elm-lang.org/0.19.0/imports> to see how `import`
declarations work in Elm.
> String.length
<function> : String -> Int
> List.map String.length names
[5,3,6] : List Int
> List.map String.fromInteger [ 100, 200, 300 ]
-- NAMING ERROR ------------------------------------------------------------ elm

I cannot find a `String.fromInteger` variable:

15|   List.map String.fromInteger [ 100, 200, 300 ]
               ^^^^^^^^^^^^^^^^^^
The `String` module does not expose a `fromInteger` variable. These names seem
close though:

    String.fromInt
    String.filter
    String.fromChar
    String.fromList

Hint: Read <https://elm-lang.org/0.19.0/imports> to see how `import`
declarations work in Elm.
> List.map String.fromInt [ 100, 200, 300 ]    
["100","200","300"] : List String
```

```
> List.zip
-- NAMING ERROR ------------------------------------------------------------ elm

I cannot find a `List.zip` variable:

15|   List.zip
      ^^^^^^^^
The `List` module does not expose a `zip` variable. These names seem close
though:

    List.map
    List.unzip
    List.all
    List.any

Hint: Read <https://elm-lang.org/0.19.0/imports> to see how `import`
declarations work in Elm.
> Tuple.zip
-- NAMING ERROR ------------------------------------------------------------ elm

I cannot find a `Tuple.zip` variable:

15|   Tuple.zip
      ^^^^^^^^^
The `Tuple` module does not expose a `zip` variable. These names seem close
though:

    Tuple.pair
    Tuple.first
    Maybe.map
    Sub.map

Hint: Read <https://elm-lang.org/0.19.0/imports> to see how `import`
declarations work in Elm.
> List.unzip
<function> : List ( a, b ) -> ( List a, List b )
> List.unzip [ ("abc", 100), ("def", 200), ("ghi", 300) ]
(["abc","def","ghi"],[100,200,300])
    : ( List String, List number )
```

```
> point = { x = 3, y = 4 }                                                                     
{ x = 3, y = 4 }
    : { x : number, y : number1 }
> point.x
3 : number
> point.y
4 : number
> point.x = 9
-- PARSE ERROR ------------------------------------------------------------- elm

I was not expecting this equals sign while parsing repl_value_23's definition.

15| repl_value_23 =
16|   point.x = 9
              ^
Maybe this is supposed to be a separate definition? If so, it is indented too
far. Spaces are not allowed before top-level definitions.
> .x point
3 : number
> under17 {age} = age < 17
<function> : { a | age : number } -> Bool
> under17 { age = 100, name = "Kin" }
False : Bool
> under17 { age = 17, name = "Laki" }
False : Bool
> under17 { age = 6, name = "Kuina" }
True : Bool
> under17 { age = 10, birthYear = 1978 }
True : Bool
> under17 { x = 3, y = 4 }
-- TYPE MISMATCH ----------------------------------------------------------- elm

The 1st argument to `under17` is not what I expect:

17|   under17 { x = 3, y = 4 }
              ^^^^^^^^^^^^^^^^
This argument is a record of type:

    { x : number, y : number1 }

But `under17` needs the 1st argument to be:

    { a | age : number }

Hint: Seems like a record field typo. Maybe age should be x?

Hint: Can more type annotations be added? Type annotations always help me give
more specific messages, and I think they could help a lot in this case!
```
