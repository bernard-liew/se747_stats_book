---
output:
  html_document: default
  pdf_document: default
---

# Data visualisation

## Download and load libraries {-}


```r
if (!require("pacman")) install.packages("pacman")
pacman::p_load(tidyverse, # All purpose wrangling for dataframes
               readr, # importing and writing data
               openxlsx, # writing excel documents
               purrr, # for piping %>%
               corrplot, # for correlation
               knitr,
               mosaic,
               yarrr,
               ez)
```



## Import data {-}

Let's load the 3 files from `data` folder into the workspace again.


```r
subjdat <-  read_delim (file = "data/SubjectData.txt", # file name
                        delim = "\t", # file separater
                        col_names = TRUE) # the first row of the data is a header row

scalfac <-  read_delim (file = "data/ScaleFact.txt", # file name
                        delim = "\t", # file separater
                        col_names = TRUE) # the first row of the data is a header row

strn <-  read.xlsx (xlsxFile = "data/STRENGTH.xlsx")
```

## Rename column names{-}


```r
# Method 1:
colnames (strn) <-  tolower(colnames (strn)) # captials to lower caps

# Method 2: Define new names
newnames <- c("atorq", "awork", "apow", "ktorq", "kwork", "kpow")
# [7:12] tells the system the column numbers you want to replace. In this instance it is columns 7 to 12
colnames (strn)[7:12] = newnames
```


## Introduction {-#intro-Graphics}


Graphics is a great strength of R. The `graphics` package is part of the 
standard distribution and contains many useful functions for creating a
variety of graphic displays. The base functionality has been expanded and made easier with `ggplot2`, part of the tidyverse of packages. In this chapter we will focus on examples using `ggplot2`. 

Graphics is a vast subject, and we can only scratch the surface here.
Winston Chang's [*R Graphics Cookbook, 2nd Edition*](http://shop.oreilly.com/product/0636920063704.do), is part of the O'Reilly Cookbook series
and walks through many useful recipes with a focus on `ggplot2`.
If you want to delve deeper, we recommend *R Graphics* by Paul Murrell
(Chapman & Hall, 2006). *R Graphics* discusses the paradigms behind R
graphics, explains how to use the graphics functions, and contains
numerous examples—including the code to re-create them. Some of the
examples are pretty amazing.

### The Illustrations {-}

The graphs in this chapter are mostly plain and unadorned. We did that
intentionally. When you call the `ggplot` function, as in:


```r
ggplot(strn, aes(ktorq, atorq)) +
  geom_point()
```

![(\#fig:simpleplot)Simple plot](07-visualization_files/figure-latex/simpleplot-1.pdf) 

you get a plain, graphical representation of *x* and *y* as shown in Figure \@ref(fig:simpleplot).
You could adorn the graph with colors, a title, labels, a legend, text, and so forth, but
then the call to `ggplot` becomes more and more crowded, obscuring the
basic intention. 


```r
ggplot(strn, aes(ktorq, atorq)) +
  geom_point() +
  labs(
    title = "Simple Plot Example",
    subtitle = "with a subtitle",
    x = "x-values",
    y = "y-values"
  ) +
  theme(panel.background = element_rect(fill = "white", colour = "grey50"))
```

![(\#fig:complicatedplot)Slightly more complicated plot](07-visualization_files/figure-latex/complicatedplot-1.pdf) 
The resulting plot is shown in Figure \@ref(fig:complicatedplot). We want to keep the recipes clean, so we emphasize the basic plot and then show later how to add adornments.

### Notes on ggplot2 basics {-}

While the package is called `ggplot2`, the primary plotting function in the package is called `ggplot`. It is important to understand the basic pieces of a `ggplot2` graph. In the preceding examples, you can see that we pass data into `ggplot`, then define how the graph is created by stacking together small phrases that describe some aspect of the plot. This stacking together of phrases is part of the "grammar of graphics" ethos (that's where the `gg` comes from).
To learn more, you can read ["A Layered Grammar of Graphics"](http://vita.had.co.nz/papers/layered-grammar.pdf) written by `ggplot2` author Hadley Wickham.
The "grammar of graphics" concept originated with Leland Wilkinson, who articulated the idea of building graphics up from a set of primitives (i.e., verbs and nouns). With `ggplot`, the underlying data need not be fundamentally reshaped for each type of graphical representation. In general, the data stays the same and the user then changes syntax slightly to illustrate the data differently. This is significantly more consistent than base graphics, which often require reshaping the data in order to change the way it is visualized. 

As we talk about `ggplot` graphics, it's worth defining the components of a `ggplot` graph:

`geometric object functions`

:   These are geometric objects that describe the type of graph being created. These start with `geom_` and examples include `geom_line`, `geom_boxplot`, and `geom_point,` along with dozens more. 

`aesthetics`

:   The aesthetics, or aesthetic mappings, communicate to `ggplot` which fields in the source data get mapped to which visual elements in the graphic. This is the `aes` line in a `ggplot` call.

`stats`

:   Stats are statistical transformations that are done before displaying the data. Not all graphs will have stats, but a few common stats are `stat_ecdf` (the empirical cumulative distribution function) and `stat_identity`, which tells `ggplot` to pass the data without doing any stats at all.

`facet functions`

:   Facets are subplots where each small plot represents a subgroup of the data. The faceting functions include `facet_wrap` and `facet_grid`.

`themes`

:   Themes are the visual elements of the plot that are not tied to data. These might include titles, margins, table of contents locations, or font choices. 

`layer`

:   A layer is a combination of data, aesthetics, a geometric object, a stat, and other options to produce a visual layer in the `ggplot` graphic. 

### "Long" Versus "Wide" Data with ggplot {-}

One of the first sources of confusion for new `ggplot` users is that they are inclined to reshape their data to be "wide" before plotting it. "Wide" here means every variable they are plotting is its own column in the underlying data frame. This is an approach that many users develop while using Excel and then bring with them to R. `ggplot` works most easily with "long" data where additional variables are added as rows in the data frame rather than columns. The great side effect of adding more measurements as rows is that any properly constructed `ggplot` graphs will automatically update to reflect the new data without changing the `ggplot` code. If each additional variable were added as a column, then the plotting code would have to be changed to introduce additional variables. This idea of "long" versus "wide" data will become more obvious in the examples in the rest of this chapter. 


## Creating a Scatter Plot 

We can plot the data by calling `ggplot`, passing in the data frame, and invoking a geometric point function:


```r
ggplot(strn, aes(ktorq, atorq)) +
  geom_point()
```

In this example, the data frame is called `strn` and the *x* and *y* data are in fields named `ktorq` and `atorq`, which we pass to the aesthetic in the call `aes(x, y)`.


A scatter plot is a common first attack on a new dataset. It’s a quick
way to see the relationship, if any, between *x* and *y*. 

Plotting with `ggplot` requires telling `ggplot` what data frame to use, then what type of graph to create, and which aesthetic mapping (`aes`) to use. The `aes` in this case defines which field from `df` goes into which axis on the plot. Then the command `geom_point` communicates that you want a point graph, as opposed to a line or other type of graphic. 

## Cleaveland dotplots

One of the most important types of scatterplot is a cleaveland dotplot. It plots individual data points of a variable for every single row of your data. Useful for outlier detection, different spread of data a covariate.



```r
# Save the figure into an object called f1
ggplot(data = strn) + 
  geom_point(aes(y = seq(1,nrow(strn),1), x = atorq)) +
  ylab ("row number") + # Label you like
  xlab ("ankle torque") # Label you like
```

![(\#fig:unnamed-chunk-5)Ankle torque by group and time](07-visualization_files/figure-latex/unnamed-chunk-5-1.pdf) 

## Adding a Title and Labels 

You want to add a title to your plot or add labels for the axes.


With `ggplot` we add a `labs` element that controls the labels for the title and axes. 

When calling `labs` in `ggplot`, specify:

`title`

:   The desired title text

`x`

:   x-axis label

`y`

:   y-axis label


```r
ggplot(strn, aes(ktorq, atorq)) +
  geom_point() +
  labs(title = "The Title",
       x = "knee torque",
       y = "ankle torque")
```

A title and better labels will make a graph more interesting and easier to interpret. 


## Adding (or Removing) a Grid 

You want to change the background grid to your graphic.

With `ggplot` background grids come as a default, as you have seen in other recipes. However, we can alter the background grid using the `theme` function or by applying a prepackaged theme to our graph. 
We can use `theme` to alter the background panel of our graphic:


```r
ggplot(strn, aes(ktorq, atorq)) +
  geom_point() +
  theme(panel.background = element_rect(fill = "white", colour = "grey50"))
```

![(\#fig:whitebackground)White background](07-visualization_files/figure-latex/whitebackground-1.pdf) 

`ggplot` fills in the background with a grey grid by default. So you may find yourself wanting to remove that grid completely or change it to something else. Let's create a `ggplot` graphic and then incrementally change the background style.

We can add or change aspects of our graphic by creating a `ggplot` object, then calling the object and using the `+` to add to it. The background shading in a `ggplot` graphic is actually three different graph elements:

`panel.grid.major`:

   These are white by default and heavy.
   
`panel.grid.minor`:

   These are white by default and light.
   
`panel.background`:



## Applying a Theme to a ggplot Figure



You want your plot to use a preset collection of colors, styles, and formatting. 


`ggplot` supports *themes*, which are collections of settings for your figures. To use one of the themes, just add the desired theme function to your `ggplot` with a `+`:


```r
ggplot(strn, aes(ktorq, atorq)) +
  geom_point() +
  theme_bw()
```

The `ggplot2` package contains the following themes Figure \@ref(fig:ggthemes):

```
theme_bw()
theme_dark() 
theme_classic()
theme_gray()
theme_linedraw()
theme_light()
theme_minimal()
theme_test()
theme_void()
```

\begin{figure}

{\centering \includegraphics[width=0.5\linewidth]{images/visualization-themes} 

}

\caption{Default themes in ggplot.}(\#fig:ggthemes)
\end{figure}

## Creating a Scatter Plot of Multiple Groups

You have data in a data frame with multiple observations per record: *x*, *y*, and a
factor *f* that indicates the group. You want to create a scatter
plot of *x* and *y* that distinguishes among the groups.

With `ggplot` we control the mapping of shapes to the factor `group` by passing `shape = group` to the `aes`. 


```r
ggplot(strn, aes(ktorq, atorq, shape = group)) +
  geom_point()
```


Plotting multiple groups in one scatter plot creates an uninformative
mess unless we distinguish one group from another. We make this distinction in `ggplot` by setting the `shape` parameter of the `aes` function. 

We can add `shape = group` and `color = group` to our `aes` call, to get each species with a different shape and color, shown in Figure \@ref(fig:strnshape).


```r
ggplot(strn, aes(ktorq, atorq, shape = group, color =group)) +
  geom_point()
```

![(\#fig:strnshape)strength: shape and color](07-visualization_files/figure-latex/strnshape-1.pdf) 

`ggplot` conveniently sets up a legend for you as well, which is handy. 


## Adding (or Removing) a Legend


You want your plot to include a *legend*, the little box that decodes
the graphic for the viewer.

In most cases `ggplot` will add the legends automatically, as you can see in the previous recipe. If you do not have explicit grouping in the `aes`, then `ggplot` will not show a legend by default. If we want to force `ggplot` to show a legend, we can set the shape or line type of our graph to a constant. `ggplot` will then show a legend with one group. We then use `guides` to guide `ggplot` in how to label the legend.

This can be illustrated with our `strn` scatter plot:


```r
ggplot(strn, aes(ktorq, atorq, color =group)) +
  geom_point() +
  guides(color =guide_legend(title="My Legend Title")) 
```

![(\#fig:needslegend)Legend added](07-visualization_files/figure-latex/needslegend-1.pdf) 
Figure \@ref(fig:needslegend) illustrates the result of setting the shape to a string value and then relabeling the legend using `guides`.

More commonly, you may want to turn legends off, which you can do by setting the `legend.position = "none"` in the `theme`. We can use the `strn` plot from the prior recipe and add the `theme` call as shown in Figure \@ref(fig:shapelegend):


```r
ggplot(strn, aes(ktorq, atorq, color =group)) +
  geom_point() +
  theme(legend.position = "none")
```

![(\#fig:shapelegend)Legend removed](07-visualization_files/figure-latex/shapelegend-1.pdf) 


Adding legends to `ggplot` when there is no grouping is an exercise in "tricking" `ggplot` into showing the legend by passing a string to a grouping parameter in `aes`. While this will not change the grouping (as there is only one group), it will result in a legend being shown with a name. 

Then we can use `guides` to alter the legend title. It's worth noting that we are not changing anything about the data, just exploiting settings in order to coerce `ggplot` into showing a legend when it typically would not. 

One of the huge benefits of `ggplot` is its very good defaults. Getting positions and correspondence between labels and their point types is done automatically, but can be overridden if needed. To remove a legend totally, we set `theme` parameters with `theme(legend.position = "none")`. In addition to `"none"` you can set the `legend.position` to be `"left"`, `"right"`, `"bottom"`, `"top"`, or a two-element numeric vector. Use a two-element numeric vector in order to pass `ggplot` specific coordinates of where you want the legend. If you're using the coordinate positions, the values passed are between 0 and 1 for the *x* and *y* position, respectively. 

Figure \@ref(fig:shapelegend-moved) shows an example of a legend positioned at the bottom, created with this adjustment to the `legend.position`:


```r
ggplot(strn, aes(ktorq, atorq, color =group)) +
  geom_point() + 
  theme(legend.position = "bottom")
```

![(\#fig:shapelegend-moved)Legend on the bottom](07-visualization_files/figure-latex/shapelegend-moved-1.pdf) 
Or we could use the two-element numeric vector to put the legend in a specific location, as in Figure \@ref(fig:shapelegend-moved2). The example puts the center of the legend at 80% to the right and 20% up from the bottom. 


```r
ggplot(strn, aes(ktorq, atorq, color =group)) +
  geom_point() + 
  theme(legend.position = c(.8, .2))
```

![(\#fig:shapelegend-moved2)Legend at a point](07-visualization_files/figure-latex/shapelegend-moved2-1.pdf) 

In many aspects beyond legends, `ggplot` uses sane defaults but offers the flexibility to override them and tweak the details. You can find more details on `ggplot` options related to legends in the help for `theme` by typing `**?theme**` or looking in the `ggplot` [online reference material](http://ggplot2.tidyverse.org/reference/theme.html).



## Creating One Scatter Plot for Each Group 

Your dataset contains (at least) two numeric variables and a factor or character field defining a group. You want to create several scatter plots for the numeric variables, with one
scatter plot for each level of the factor or character field.


We produce this kind of plot, called a _conditioning plot_, in `ggplot` by adding `facet_wrap` to our plot.
In this example we use the data frame `strn`, which contains three columns: *x*, *y*, and *f*, with *f* being a factor (or a character string). 


```r
ggplot(strn, aes(ktorq, atorq)) +
  geom_point() +
  facet_wrap( ~ group)
```

## Creating a Bar Chart 

You want to create a bar chart.

A common situation is to have a column of data that represents a group and then another column that represents a measure about that group. This format is "long" data because the data runs vertically instead of having a column for each group. 

Using the `geom_bar` function in `ggplot`, we can plot the heights as bars. If the data is already aggregated, we add `stat = "identity"` so that `ggplot` knows it needs to do no aggregation on the groups of values before plotting. 

The first thing to do when trying to generate nice plots is to create a dataframe of the values you want to plot. In this case, since I want to plot the mean group by time values of `ktorq`, and include one standard deviation error bars, I need to generate these values.

In `ggplot` we can use the `fill` parameter in `aes` to tell `ggplot` what field to base the colors on. If we pass a numeric field to `ggplot`, we will get a continuous gradient of colors; and if we pass a factor or character field to `fill`, we will get contrasting colors for each group. 


```r
# generate a summarized dataframe 
df.plot = strn %>%
  group_by(group, time) %>%
  summarize (Mean = mean (ktorq, na.rm = T), # change ktorq to other variables you desire
             Sd = sd (ktorq, na.rm = T)) %>%
  ungroup()

# Combined plot
ggplot(data = df.plot) + 
geom_bar (aes(y = Mean, x = group, fill = time), stat = "identity", color="black", position=position_dodge()) +
ylab ("Knee torque") +
xlab ("Group")
```

![(\#fig:ktorqbar)Knee torque by group](07-visualization_files/figure-latex/ktorqbar-1.pdf) 


Figure \@ref(fig:ktorqbar) shows the resulting bar chart. 

This example uses `stat = "identity"`, which assumes that the heights of your bars are conveniently stored as a value in one field with only one record per column. 


## Adding standard deviation error bars to a Bar Chart 

You want to augment a bar chart with standard deviation.



```r
ggplot(data = df.plot) + 
geom_bar (aes(y = Mean, x = group, fill = time), stat = "identity", color="black", position=position_dodge()) +
geom_errorbar(aes(ymin=Mean -Sd, ymax=Mean +Sd, x = group, colour = time), 
              width=.2,
               position=position_dodge(0.9)) +
ylab ("Knee torque") +
xlab ("Group")
```

![(\#fig:ktorqbarerrors)Knee torque by group with error bars as 1SD](07-visualization_files/figure-latex/ktorqbarerrors-1.pdf) 

## Custom coloring a Bar Chart

You want to manually customize the color or shade the bars of a bar chart.

We can customize the colour using the `scale_fill_manual` and/or the `scale_colour_manual` commands. When you include `fill` in `aes`, customize the colour using `scale_fill_manual`, and if you include `colour` in `aes`, customize using `scale_colour_manual`. You can change colours by keying in the actual names of different colours after the `value` command. The order of colours matches the order of levels in the factor.[This is a link of the myriad colours and their names available in ggplot] (http://sape.inf.usi.ch/quick-reference/ggplot2/colour)


```r
ggplot(data = df.plot) + 
geom_bar (aes(y = Mean, x = group, fill = time), stat = "identity", color="black", position=position_dodge()) +
geom_errorbar(aes(ymin=Mean -Sd, ymax=Mean +Sd, x = group, colour = time), 
              width=.2,
               position=position_dodge(0.9)) +
scale_fill_manual(values = c("blue", "red")) +
scale_colour_manual(values = c("blue", "red")) +
ylab ("Knee torque") +
xlab ("Group")
```

![(\#fig:customcol)Knee torque by group with error bars as 1SD](07-visualization_files/figure-latex/customcol-1.pdf) 

## Histogram 

Useful for outlier detection, different spread of data a covariate

Knee torque by group and time

The `geom_histogram` function must decide how many cells (bins) to create for
binning the data. In this example, the default algorithm chose 30
bins. If we wanted fewer bins, we would include the `bins` parameter to tell `geom_histogram` how many bins we want:


```r
ggplot(data = strn) +
geom_histogram(aes(x = ktorq, fill = group), binwidth = 10) + # try binwidth of 0.1, 1, 10, 100
facet_wrap(  ~ time, scales = "fixed") +
ylab ("Frequency") +
xlab ("knee torque")
```

![(\#fig:kneehist)Histogram of knee torque](07-visualization_files/figure-latex/kneehist-1.pdf) 

## Creating a Boxplot 

You want to create a boxplot of your data.


Use `geom_boxplot` from `ggplot` to add a boxplot geom to a `ggplot` graphic. Using the `strn` data frame from the prior recipe, we can create a boxplot of the values in the `y` column. The resulting graph is shown in Figure \@ref(fig:boxplot).Provides interquartile range (25th, 75th percentile), median, outliers. Useful for detecing outliers, and spread of data per covariate.



```r
ggplot(data = strn) +
  geom_boxplot(aes(y = ktorq, x = group, fill = time)) +
  scale_fill_manual(values = c("blue", "red")) +
  ylab ("Knee torque") +
  xlab ("Group")
```

![(\#fig:boxplot)Boxplot of knee torque by group and time](07-visualization_files/figure-latex/boxplot-1.pdf) 


A boxplot provides a quick and easy visual summary of a dataset.

-   The thick line in the middle is the median.

-   The box surrounding the median identifies the first and third
    quartiles; the bottom of the box is Q1, and the top is Q3.

-   The “whiskers” above and below the box show the range of the data,
    excluding outliers.

-   The circles identify outliers. By default, an outlier is defined as
    any value that is farther than 1.5×IQR away from the box. (IQR is
    the *interquartile range*, or Q3–Q1.) In this example, there are
    a few outliers on the high side. 


## Writing Your Plot to a File {#recipe-id188}

You want to save your graphics in a file, such as a PNG, JPEG, or
PostScript file.

With `ggplot` figures we can use `ggsave` to save a displayed image to a file. `ggsave` will make some default assumptions about size and file type for you, allowing you to specify only a filename:


```r
fig <- ggplot(data = strn) +
  geom_boxplot(aes(y = ktorq, x = group, fill = time)) +
  scale_fill_manual(values = c("blue", "red")) +
  ylab ("Knee torque") +
  xlab ("Group")

ggsave(filename = "export/fig.jpg", # folder/filename
       plot = fig, # the figure you want to export
       units = "in", 
       width = 5, 
       height = 4) 
```

The file type is derived from the extension you use in the filename you pass to `ggsave`. You can control details of size, file type, and scale by passing parameters to `ggsave`. See `?ggsave` for specific details.


In RStudio, a shortcut is to click on `Export` in the Plots window and then click on "Save as Image," "Save as PDF," or "Copy to Clipboard." The save options will prompt you for a file type
and a filename before writing the file. The "Copy to Clipboard" option can be handy if you are manually copying and pasting your graphics into a presentation or word processor. 

Remember that the file will be written to your current working directory
(unless you use an absolute filepath), so be certain you know which
directory is your working directory before calling `savePlot`.

In a noninteractive script using `ggplot`, you can pass plot objects directly to `ggsave` so they need not be displayed before saving. In the prior recipe we created a plot object called `g1`. We can save it to a file like this:

Note that the units for `height` and `width` in `ggsave` are specified with the `units` parameter. In this case we used `in` for inches, but `ggsave` also supports `mm` and `cm` for the more metricly inclined. 


## Learning check {-}

1. Open up your `practice.Rmd`. Run the code chunks you created in sequential order.

2. Generate a cleaveland dotplot of `aexttorq`. 

3. Create a barplot with mean and error bars as standard deviation of `kexttorq` per `group` per `time`, and assign this figure to an object name `fig`.





