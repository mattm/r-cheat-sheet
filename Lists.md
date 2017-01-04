# Lists
Think of R lists like objects in JavaScript.

"A common use of lists is to combine multiple values into a single package that can be returned by a function. This is especially useful for statistical functions, which can have elaborate results." - *The Art of R Programming*

## Creating a list

```
> x <- list(a = 2, b = "matt")
```

This list has two components: `a` and `b`.

## Returning a value of a component
Three ways:

```
> x$a
[1] 2

> x[['a']]
[1] 2

> x[[1]]
[1] 2
```

You can use double brackets [[ ]] for referencing only a single component, with the result having the type of that component.

If you check the value of a component that doesn't exist, it returns `NULL`:

```
> x$madeup
NULL
```

## Returning one component as a list
If single brackets [ ] are used, the result is another list—a sublist of the original:

```
> x['a']
$a
[1] 2

> x[1]
$a
[1] 2
```

## Lists components don't have to be named
However, "it is generally considered clearer and less error-prone to use names instead of numeric indices."

```
> x <- list("a", 1, 2)
> x
[[1]]
[1] "a"

[[2]]
[1] 1

[[3]]
[1] 2
```

We can remove the names of a named list using `unname`:

```
> x <- list(a = 2, b = "matt")
x <- unname(x)
```

## Unlist
You can use `unlist` to return a vector of values:

If the list has tags it will returned name vectors:

```
> x <- list(a = 2, b = "matt")
> unlist(x)
> unlist(x)
     a      b 
   "2" "matt" 
> unlist(x)[['a']]
[1] "2"
```

"The return value of `unlist()` is a vector—in this case, a vector of character strings. Note that the element names in this vector come from the components in the original list."

If the list doesn't have tags:

```
> x <- list("a", 1, 2)
> unlist(x)
[1] "a" "1" "2"
```

If the component values have mixed types, R will choose the least common denominator:

```
> w <- list(a = 5,b = "xyz")
> wu <- unlist(w)
> class(wu)
[1] "character"
> wu
   a     b 
  "5" "xyz" 
```

## Adding to a list

```
> x <- list(a = 2, b = 3)
> x$c = 4
> x
$a
[1] 2

$b
[1] 3

$c
[1] 4
```

## Deleting a component
Set the component to `NULL`:

```
> x <- list(a = 2, b = 3)
> x$b = NULL
> x
$a
[1] 2
```

Note that this can change the indeces if you delete a component that isn't at the end of the list.

## Returning the component names

```
> names(x)
[1] "a" "b"
```

## Printing the contents of a list
Basic:

```
> x
$a
[1] 2

$b
[1] "matt"
```

Detailed:

```
> str(x)
List of 2
 $ a: num 2
 $ b: chr "matt"
```

## sapply

```
> x <- list(fruits = c("apple", "orange"), vegetables = c("greenbean"))
> sapply(x, length)
    fruits vegetables 
         2          1 
```

## lapply
"The lapply() function expects its first argument to be a list. Here it was a vector, but lapply() will coerce that vector to a list form. Also, lapply() expects its second argument to be a function. This could be the name of a function, as you saw before, or the actual code, as we have here."