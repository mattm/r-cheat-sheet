# Dates and Times

## Converting a character string to a time

```
> as.POSIXct("1985-05-08 14:00:00", "UTC")
[1] "1985-05-08 14:00:00 UTC"
```

## Converting a Unix timestamp to a time
Using `as.Date`:

```
> as.Date(1453725582 / 86400, origin = "1970-01-01")
[1] "2016-01-25"
```

Using `as.POSIXct`:

```
> as.POSIXct(1479740483, "UTC", origin = "1970-01-01")
[1] "2016-11-21 15:01:23 UTC"
```

## Formatting a date
When the date is the  `character` class:

```
> as.Date("2016-01-29 15:23:26", format="%Y-%m-%d")
[1] "2016-01-29"
```

When the date is the `Date` class or `POSIXlt`:

```
> format(as.Date(1453725582 / 86400, origin = "1970-01-01"), "%Y")
[1] "2016"
```


## Determining how much time is between two dates
Use `difftime` - note that the *older* time is the second argument:

```
> start <- as.POSIXct("1985-05-08 14:00:00", "UTC")
> difftime(Sys.time(), start)
Time difference of 11521.04 days
```

Or as an integer:

```
> as.integer(difftime(Sys.time(), start))
[1] 11521
```

`difftime` defaults to `days`, but you can specify other units too:

```
> as.integer(difftime(Sys.time(), start, units = c("hours")))
[1] 276505
```