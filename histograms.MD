# Histograms

The generic function `hist` computes a histogram of the given data values.

## A simple example

```
x <- c( 10, 30, 5, 23, 24, 25, 42 )
hist( x, 
	breaks = seq( 0, 100, by = 5 ), 
	col = "lightgreen", 
	main = "A chart title",
	xlab = "X-Axis Title", 
	ylab = "Y-Axis Title" )
```

## Adding a vertical line at a specific value

```
true.cr <- 8
abline( v = true.cr, col = "darkblue", lwd = 5 )
```
