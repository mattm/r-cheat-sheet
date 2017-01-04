# Modes

> R variable types are called modes. Recall from Chapter 1 that all elements in a vector must have the same mode, which can be integer, numeric (floating-point number), character (string), logical (Boolean), complex, and so on. If you need your program code to check the mode of a variable x, you can query it by the call `typeof(x)` - The Art of R Programming  
sss

```
> x <- 4

> typeof( x )
[1] "double"

> mode(x)
[1] "numeric"

> class(x)
[1] "numeric"
```

> The `class()` is used to define/identify what "type" an object is from the point of view of object-oriented programming in R. `typeof()` gives the "type" of object from R's point of view, whilst `mode()` gives the "type" of object from the point of view of Becker, Chambers & Wilks (1988). [StackOverflow](http://stats.stackexchange.com/questions/3212/mode-class-and-type-of-r-objects)  
[Examples from StackOverflow](http://stackoverflow.com/a/37469255/156835):

```
> x <- 1
> c(class(x), mode(x), storage.mode(x), typeof(x))
[1] "numeric" "numeric" "double"  "double" 

> x <- letters
> c(class(x), mode(x), storage.mode(x), typeof(x))
[1] "character" "character" "character" "character"

> x <- TRUE 
> c(class(x), mode(x), storage.mode(x), typeof(x))
[1] "logical" "logical" "logical" "logical"

> x <- cars
> c(class(x), mode(x), storage.mode(x), typeof(x))
[1] "data.frame" "list"       "list"       "list"      

> x <- cars[1]
> c(class(x), mode(x), storage.mode(x), typeof(x))
[1] "data.frame" "list"       "list"       "list"      

> x <- cars[[1]]
> c(class(x), mode(x), storage.mode(x), typeof(x))
[1] "numeric" "numeric" "double"  "double" 

> x <- matrix(cars)
> c(class(x), mode(x), storage.mode(x), typeof(x))
[1] "matrix" "list"   "list"   "list"  
``````