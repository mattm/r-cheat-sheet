## Creating shortcuts

We can add functions to the `.Rprofile` file in user root like so:

```
.define.fonts <- function () {
	quartzFonts( proxima.nova = c( "Proxima Nova Regular", "Proxima Nova Bold", "Proxima Nova Regular Italic", "Proxima Nova Bold Italic" ) )
	par( family = "proxima.nova" )
}

.First <- function() {}

.Last <- function() {}
```

These functions - which have to come before `.First` and `.Last` - will then be available after RStudio loads.
