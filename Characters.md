# Characters

```
> x <- "matt"
```

## Length
Remember that `x` is actually a single element vector so doing `length(x)` will return `1`. Use `nchar` instead:

```
> nchar(x)
[1] 4
```

## Substring

```
> substr(x, 1, 2)
[1] "ma"
``````