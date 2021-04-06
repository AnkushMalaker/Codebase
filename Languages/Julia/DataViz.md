# Importing CSVs, Visualizing data, etc

Install CSV package by:

```
using Pkg
Pkg.add("CSV")
```

### importing

` iris = CSV.read("iris.csv")`  
This creates a DataFrames.DataFrame called iris.  
This results in headings like "Sepal.Length", which can conflict with the usage of `.` operator used in Julia to access properties.  
Thus, we can use the `normalizenames = true` parameter which will make the column names to be "Sepal_Length"

We can use `first(df, n)` to see dataframe structure and first n rows. [Like head(df, n)]  
Similarly, we have `last(df, n)`.

To see the statistics of the dataest, we can use
`describe(iris)`

We can extract columns from iris using `iris.Petal_Length`  
or  
`iris[<rows>, <columns>]`  
example:  
`iris[:,3]`  
This refers ALL ROWS and the 3rd column.

### Visualization

can be done using the package Plots

#### Create blank plot:

`plot()`

#### Add date to the plot:

`plot(x, y)`

#### Add more data to the plot using ! (mutation) operator:

`plot!(x, z)`  
or

```
p = plot(x,y)
plot!(p, x, z)
```

Title can be added using the title attribute in the plot() function.  
Label can be put by passing a string (in case of only one line) or an array of names to the label parameter in plot() function.  
X,Y labels can bechanged using xlabel and ylabel

Other plots:

- scatter()
- bar()
- histogram()

To show all charts in the same place, we can pass multiple plots into the plot() command and apss an arrangement like (2,2) to the layout attribute of plot() function.
