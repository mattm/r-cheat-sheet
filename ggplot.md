# ggplot
Resources:

* [Introduction to R Graphics with ggplot2](http://tutorials.iq.harvard.edu/R/Rgraphics/Rgraphics.html)

The basic idea: independently specify plot building blocks and combine them to create just about any kind of graphical display you want. Building blocks of a graph include:

* data
* aesthetic mapping
* geometric object
* statistical transformations
* scales
* coordinate system
* position adjustments
* faceting

In ggplot land aesthetic means "something you can see". Each type of geom accepts only a subset of all aesthetics–refer to the geom help pages to see what mappings each geom accepts. Aesthetic mappings are set with the `aes()` function.

Note that *variables* are mapped to aesthetics with the `aes()` function, while *fixed aesthetics* are set outside the `aes()` call.

Geometric objects are the actual marks we put on a plot. Examples include:

* points (`geom_point`, for scatter plots, dot plots, etc)
* lines (`geom_line`, for time series, trend lines, etc)
* boxplot (`geom_boxplot`, for, well, boxplots!)
* `geom_line` for a smoothed out line (with gray area showing range)

Each geom accepts a particualar set of *mappings*.

Each geom has a default **statistic**, but these can be changed. For example, `geom_histogram()` is `stat`:

```
> args(geom_histogram)
function (mapping = NULL, data = NULL, stat = "bin", 
  position = "stack", ..., binwidth = NULL, 
  bins = NULL, na.rm = FALSE, show.legend = NA,
  inherit.aes = TRUE)
```

You can see the argets for the `bin` stat like this:

```
> args(stat_bin)
function (mapping = NULL, data = NULL, geom = "bar", position = "stack", 
    ..., binwidth = NULL, bins = NULL, center = NULL, boundary = NULL, 
    closed = c("right", "left"), pad = FALSE, na.rm = FALSE, 
    show.legend = NA, inherit.aes = TRUE) 
```

Arguments to `stat_` functions can be passed through `geom_` functions. For example, `bin` has a `binwidth` argument so we can pass it through to the `geom_`:

```
geom_histogram(binwidth = 4000)
```

## The `ggplot` function

```
ggplot(
  data = NULL, 
  mapping = aes(), ...,
  environment = parent.frame())
```

* Default dataset to use for plot.
* Default list of aesthetic mappings to use for plot. If not specified, must be suppled in each layer added to the plot.

Typically:

```
ggplot(df, aes(x, y, <other aesthetics>))
```

## Examples:

```
> housing <- read.csv("data/landdata-states.csv")
> states <- subset(housing, State %in% c("MA", "TX"))
> g <- ggplot(states, aes(x = Date, y = Home.Value, color = State))
> g <- g + geom_point()
```

Could have also done this without specifying `x` and `y`:

```
> g <- ggplot(states, aes(Date, Home.Value, color = State))
```

Instead of `geom_point()`, we could have used another geometric object like `geom_line()`.

### Simple line chart

```
df <- data.frame(x = seq(1:4),y = c(4.2, 10, 29.5))
> ggplot(data = df, aes(x = x, y = y, group = 1)) + geom_line() + geom_point()
```

### Stacked bar chart

```
g <- ggplot(data, aes(x = expiry_month, y = quantity, fill = auto_renew))
g <- g + geom_bar(stat = "identity")
```

## Customizing the chart

### Adding a title

```
ggtitle("Sign Ups by Date and Vertical")
```

### Setting the X and Y axis labels

```
labs(x = "Date", y = "Vertical")
```

### Adding a margin around the chart

```
theme(plot.margin = unit(c(1, 1, 1, 1), "cm"))
```

### Formatting the y axis values

```
library(scales)
scale_y_continuous(labels = comma)
```

