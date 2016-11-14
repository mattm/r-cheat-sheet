# Histograms

The generic function `hist` computes a histogram of the given data values.

## A simple example

```
x <- c( 10, 30, 5, 23, 24, 25, 42 )
hist( x, 
	breaks = seq( 0, 100, by = 5 ), 
	col = "lightgreen", 
	main = "The % of who saw plans and pricing who then started the NUX",
	xlab = "Conversion Rate", 
	ylab = "Number of Guesses" )
```

## Adding a vertical line at a specific value

```
true.cr <- 8
abline( v = true.cr, col = "darkblue", lwd = 5 )
```
