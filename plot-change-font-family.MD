# Changing the Plot's Font Family

## Specifying the font details

```
quartzFonts( proxima.nova = c( "Proxima Nova Regular", "Proxima Nova Bold", "Proxima Nova Regular Italic", "Proxima Nova Bold Italic" ) )
```

The argument is "a character vector containing the four PostScript font names for plain, bold, italic, and bolditalic versions of a font family."

The names are from Font Book:

![Font Book](/images/fontbook.png)

## Setting the plot's font family to the new font

```
par( family = "proxima.nova" )
```

## Creating a shortcut

We can add these to the `.Rprofile` file in user root like so:

```
.define.fonts <- function () {
	quartzFonts( proxima.nova = c( "Proxima Nova Regular", "Proxima Nova Bold", "Proxima Nova Regular Italic", "Proxima Nova Bold Italic" ) )
	par( family = "proxima.nova" )
}

.First <- function() {}

.Last <- function() {}
```

Then we can type `.define.fonts()` after RStudio loads to set the plot font to Proxima Nova.

Note that you unfortunately can't add the function call to `.First` because RStudio will complain about `quartzFonts` not being a function:

```
Error in .First() : could not find function "quartzFonts"
```
