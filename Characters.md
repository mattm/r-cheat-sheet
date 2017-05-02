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
```

## Find and replace
```
> gsub(" (Legacy)", "", "Standard (Legacy)", fixed = TRUE)
[1] "Standard"
```

The first argument - `pattern` is _character string containing a regular expression (or character string for fixed = TRUE) to be matched in the given character vector._