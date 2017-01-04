# Aggregate

> Splits the data into subsets, computes summary statistics for each, and returns the result in a convenient form.  
Two forms:

```
aggregate(x, by, FUN, ..., simplify = TRUE)
```

* `x`: is the data frame.
* `by`: *a list of grouping elements, each as long as the variables in the data frame x. The elements are coerced to factors before use.*
* `FUN`: *a function to compute the summary statistics which can be applied to all data subsets.*

```
## S3 method for class 'formula'
aggregate(formula, data, FUN, ..., subset, na.action = na.omit)
```

* `formula`: *a formula, such as y ~ x or cbind(y1, y2) ~ x1 + x2, where the y variables are numeric data to be split into groups according to the grouping x variables (usually factors).*
* `data`: *a data frame (or list) from which the variables in formula should be taken.*
* `FUN`: same as above

> ~ in aggregate() separates, to the left side, what is being "aggregated", and to the right side, what is being used to "aggregate" the items. ([Source](http://stackoverflow.com/questions/14078591/what-is-the-meaning-of-in-aggregate)).  

> f = price ~ carat  

> We start by creating the formula f using the strange looking tilde operator. That tells the R interpreter that we're defining a symbolic formula, rather than an expression to be evaluated immediately. So, our definition of formula f says, "price is a function of carat". ([Source](http://stackoverflow.com/questions/14078591/what-is-the-meaning-of-in-aggregate)).  

## Examples

### How many of each value?

```
> values <- data.frame(value = c("a", "a", "a", "a", "a", "b", "b", "b", "c", "c", "c", "c"))
> values
   value
1      a
2      a
3      a
4      a
5      a
6      b
7      b
8      b
9      c
10     c
11     c
12     c
> aggregate(values, list(unique.values = values$value), length)
  unique.values value
1             a     5
2             b     3
3             c     4
```

([Source](https://www.r-bloggers.com/aggregate-a-powerful-tool-for-data-frame-in-r/))

For each data subset in `values$value`, we apply the `length` function to compute the summary statistic.

### One column as a function of another column

```
> usage = data.frame(user_id = c(1, 1, 1, 1, 2, 3, 3), timestamp = c(1451606518, 1451606519, 1451607549, 1451608511, 1451608555, 1451608773, 1451679101))
> usage
  user_id  timestamp
1       1 1451606518
2       1 1451606519
3       1 1451607549
4       1 1451608511
5       2 1451608555
6       3 1451608773
7       3 1451679101
> aggregate(timestamp ~ user_id, usage, length)
  user_id timestamp
1       1         4
2       2         1
3       3         2

# We could also do it like this:
> aggregate(usage["timestamp"], usage["user_id"], length)
  user_id timestamp
1       1         4
2       2         1
3       3         2
```
Note that `NA` values are automatically removed:

```
> d <- data.frame(list(kids = c("Jack", "Jill"), ages = c(12, NA)))
> d
  kids ages
1 Jack   12
2 Jill   NA
> aggregate(ages ~ kids, d, length)
  kids ages
1 Jack    1
```
