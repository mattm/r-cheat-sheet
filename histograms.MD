# Histograms
The generic function `hist` computes a histogram of the given data values.

## A simple example

```
x <- c( 10, 30, 5, 23, 24, 25, 42 )
hist( x,
	breaks = seq( 0, 100, by = 5 ),
	col = "lightgreen",
	main = "% of users who start NUX who saw the plans and pricing beforehand",
	xlab = "Number of Guesses",
	ylab = "Conversion Rate" )
```

## Adding a vertical line at a specific value

```
x.line <- 8
abline( v = x.line, col = "darkblue", lwd = 5 )
```