# Installing a Package

```
install.packages("ggplot2")
```

You need to use quotes here.

# Including a package

```
library("ggplot2")
```

The quotes are optional so you can also do (which is the convention):

```
library(ggplot2)
```

# Checking R Version

```
> version
               _                           
platform       x86_64-apple-darwin13.4.0   
arch           x86_64                      
os             darwin13.4.0                
system         x86_64, darwin13.4.0        
status                                     
major          3                           
minor          1.3                         
year           2015                        
month          03                          
day            09                          
svn rev        67962                       
language       R                           
version.string R version 3.1.3 (2015-03-09)
nickname       Smooth Sidewalk
```

# Updating R

1. Download the latest version: https://cran.r-project.org/bin/macosx/
2. May need to update RStudio too: https://www.rstudio.com/products/rstudio/download3/
3. Restart RStudio
4. Check `version` to confirm.