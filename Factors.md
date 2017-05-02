# Factors
## Creating a factor
```
factor(x = character(), levels, labels = levels,
       exclude = NA, ordered = is.ordered(x), nmax = NA)
```

* x: a vector of data, usually taking a small number of distinct values.`
* levels: an optional vector of the values (as character strings) that x might have taken. The default is the unique set of values taken by as.character(x), sorted into increasing order of x.

Example:

```
factor(c("Lunch","Dinner"), levels=c("Lunch","Dinner"))
```

