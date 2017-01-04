# NA vs NULL

> In statistical data sets, we often encounter missing data, which we represent in R with the value NA. NULL, on the other hand, represents that the value in question simply doesn’t exist, rather than being existent but unknown. - The Art of R Programming  
Like undefined vs null in JavaScript.

## Using NULL to build a vector

```
> z <- NULL
> for ( i in 1:10 ) {
    if ( i %% 2 == 0 ) {
        z <- c( z, i )
    }
}
> z
[1] 2 4 6 8 10
``````