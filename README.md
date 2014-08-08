# Widukind for Julia

This package gives the possibility of downloading Widukind data into Julia.

# Installation

From the Julia command line:
```
Pkg.clone("https://github.com/Widukind/Widukind.jl.git")
```

This will install the package in Julia's packages directory.

Then, in every session where you want to use the package, issue the following:
```
using Widukind
```

# Retrieving a series as a `TimeArray` object

If you know the id of a series, you can get it as a `TimeArray` object (from
the `TimeSeries` package), with the `get_series` method.

For example:
```
get_series("eurostat", "5369a7fe9f8f083631ab1b2a")
```

# Retrieving a series as a `DataFrame` object

Alternatively, you can retrieve it as a `DataFrame` (from the `DataFrames`
package). Note that missing values will be correctly reported as `NA` in that
case (instead of `NaN` in the `TimeArray` case).

For example:
```
get_series("eurostat", "5369a7fe9f8f083631ab1b2a", DataFrame)
```

# Lower lever interface

For each accessible method of the web API there is a Julia counterpart. It
returns the JSON object as a Julia `Array`.

The methods are:
- retrieving all categories: `list_categories(db)`
- retrieving a specific category: `get_category(db, category_id)`
- retrieving all series of a category: `list_series(db, category_id)`
- retrieving a specific series: `get_series(db, series_id, Array)`
