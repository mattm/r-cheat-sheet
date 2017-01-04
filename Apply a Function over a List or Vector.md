# Apply a Function over a List or Vector

## lapply
"List apply" returns a list:

```
> rounder <- function( y ) {
	round( y )
}

> lapply( c( 1.4, 2.5 ), rounder )
[[1]]
[1] 1

[[2]]
[1] 2
```

## sapply
"Simple apply" applies a function to a vector or list:

```
> rounder <- function( y ) {
	round( y )
}
> sapply( c( 1.2, 2.5 ), rounder )
[1] 1 2
```

Note that `sapply` is equivalent to `unlist( lapply( ..., ... ) )`.