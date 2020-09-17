---
output:
  html_document: default
  pdf_document: default
---
# Input and Output

## Download and load libraries {-}


```r
if (!require("pacman")) install.packages("pacman")
pacman::p_load(tidyverse, # All purpose wrangling for dataframes
               readr, # importing and writing data
               openxlsx) # writing excel documents
```

## Dealing with “Cannot Open File” in Windows

You are running R on Windows, and you are using filenames such as
`C:\data\sample.txt`. R says it cannot open the file, but you know the
file does exist.

The backslashes in the filepath are causing trouble. You can solve this
problem in one of two ways:

-   Change the backslashes to forward slashes: `"C:/data/sample.txt"`.

-   Double the backslashes: `"C:\\data\\sample.txt"`.

When you open a file in R, you give the filename as a character string.
Problems arise when the name contains backslashes (`\`) because
backslashes have a special meaning inside strings. You’ll probably get
something like this:


```r
samp <- read.table("data\STRENGTH.txt")
```

```
## Error: '\S' is an unrecognized escape in character string starting ""data\S"
```
R escapes every character that follows a backslash and then removes the
backslashes. That leaves a meaningless filepath, such as
`C:Datasample-data.csv` in this example.

The simple solution is to use forward slashes instead of backslashes. R
leaves the forward slashes alone, and Windows treats them just like
backslashes. Problem solved:


```r
samp <- read_csv("data/STRENGTH.txt")
```

An alternative solution is to double the backslashes, since R replaces
two consecutive backslashes with a single backslash:


```r
samp <- read_csv("data\\STRENGTH.txt")
```


## Reading in ".txt" data

If you have a .txt file that you want to read into R, use the `read_delim()` function in the `readr` package.

| Argument| Description| 
|:------------|:-------------------------------------------------|
|`file`| The document's file path relative to the working directory unless specified otherwise. For example `file = "SubjectData.txt"` looks for the text file directly in the working directory, while `file = "data/SubjectData.txt"` will look for the file in an existing folder called `data` inside the working directory.<br>If the file is outside of your working directory, you can also specify a full file path (`file = "C:/Users/bl19622/Box/myBox/Documents/teaching/se747_ResearchMeth/sample_book/data/SubjectData.txt"`) |
|`col_names`|  A logical value indicating whether the data has a header row -- that is, whether the first row of the data represents the column names.|
|`delim`|  A string indicating how the columns are separated. For comma separated files, use `delim = ","`, for tab--delimited files, use `delim = "\t"` |


The three critical arguments to `read_delim()` are `file`, `delim`, and `col_names`. The `file` argument is a character value telling R where to find the file. If the file is in a folder in your working directory, just specify the path within your working directory (e.g.; `file = data/SubjectData.txt`. The `delim` argument tells R how the columns are separated in the file (again, for a comma--separated file, use `delim = ","`}, for a tab--delimited file, use `delim = "\t"`. The `col_names` argument is a logical value (TRUE or FALSE) telling R whether or not the first row in the data is the name of the data columns. 

Let's test this function out by reading in a text file titled `SubjectData.txt`. Since the text file is located in a folder called `data` in my working directory, I'll use the file path `file = "data/SubjectData.txt"` and since the file is tab--delimited, I'll use the argument `delim = "\t"`:


In your project folder, create another folder called `data`. Place all your data files in any formats (excels, text files, etc.) into the `data` folder. We will load the data into R using different packages and function depending on your file format. 


```r
subjdat <-  read_delim (file = "data/SubjectData.txt", # file name
                        delim = "\t", # file separater
                        col_names = TRUE) # the first row of the data is a header row

scalfac <-  read_delim (file = "data/ScaleFact.txt", # file name
                        delim = "\t", # file separater
                        col_names = TRUE) # the first row of the data is a header row
```

## writing to ".txt" data

For exporting data you created in R into a txt document.


```r
write_delim (scalfac,
            path = "data/ScaleFact_write.txt", # file name
            delim = "\t") # file separater)
```


## Reading in ".xlsx" Excel data

The `openxlsx` package makes reading in Excel files relatively easy. While there are lots of options in `openxlsx`, a typical pattern is to specify an Excel filename and a sheet name


```r
strn <-  read.xlsx (xlsxFile = "data/STRENGTH.xlsx")
```

## Writing a Data Frame to Excel

You want to write an R data frame to an Excel file. 

The `openxlsx` package makes writing to Excel files relatively easy. While there are lots of options in `openxlsx`, a typical pattern is to specify an Excel filename and a sheet name:


```r
write.xlsx(strn,
           sheetName = "strength",
           file = "data/STRENGTH_write.xlsx")
```



## Saving and loading into .RData files

The best way to store objects from R is with `.RData files`. `.RData` files are specific to R and can store as many objects as you'd like within a single file. Think about that. If you are conducting an analysis with 10 different dataframes and 5 hypothesis tests, you can save **all** of those objects in a single file called `ExperimentResults.RData`. 

### Saving a few items in workspace


To save selected objects into one `.RData` file, use the `save()` function. When you run the `save()` function with specific objects as arguments, (like `save(a, b, c, file = "myobjects.RData"`) all of those objects will be saved in a single file called `myobjects.RData`


\begin{figure}

{\centering \includegraphics[width=0.75\linewidth]{images/rdata_example} 

}

\caption{Saving multiple objects into a single .RData file.}(\#fig:rdata)
\end{figure}

Now we will save all three objects that we imported into R, in an a file called `study1.RData` in the data folder of my current working directory. To do this, you can run the following


```r
# Save three objects as a new .RData file
#   in the data folder of my current working directory

save(scalfac, 
     strn, 
     subjdat,
     file = "data/study1.RData")
```


\begin{figure}

{\centering \includegraphics[width=0.75\linewidth]{images/rdatavan} 

}

\caption{Our new study1.RData file is like a van filled with our objects.}(\#fig:rdatavan)
\end{figure}


Once you do this, you should see the `study1.RData` file in the data folder of your working directory. This file now contains all of your objects that you can easily access later using the `load()` function (we'll go over this in a second...).


### Saving entire workspace


If you have many objects that you want to save, then using `save` can be tedious as you'd have to type the name of every object. To save *all* the objects in your workspace as a .RData file, use the `save.image()` function. For example, to save my workspace in the `data` folder located in my working directory, I'd run the following:


```r
# Save my workspace to complete_image.RData in th,e
#  data folder of my working directory
save.image(file = "data/projectimage.RData")
```

### Reading in the saved workspace


To load an `.RData` file, that is, to import all of the objects contained in the `.RData` file into your current workspace, use the `load()` function.  For example, to load the three specific objects that I saved earlier (`study1.df`, `score.by.sex`, and `study1.htest`) in `study1.RData`, I'd run the following:


```r
# Load objects in study1.RData into my workspace
load(file = "data/study1.RData")
```

To load all of the objects in the workspace that I just saved to the data folder in my working directory in `projectimage.RData`, I'd run the following:


```r
# Load objects in projectimage.RData into my workspace
load(file = "data/projectimage.RData")
```

I hope you realize how awesome loading .RData files is. With R, you can store all of your objects, from dataframes to hypothesis tests, in a single `.RData` file. And then load them into any R session at any time using `load()`.

## Clearing the workspace

To remove objects from your workspace, use the `rm()` function. Why would you want to remove objects? At some points in your analyses, you may find that your workspace is filled up with one or more objects that you don't need -- either because they're slowing down your computer, or because they're just distracting. 

To remove specific objects, enter the objects as arguments to `rm()`. For example, to remove a huge dataframe called `scalfac`, I'd run the following;


```r
# Remove scalfac from workspace
rm(scalfac)
```


If you want to remove *all* of the objects in your working directory, enter the argument `list = ls()`


```r
# Remove ALL objects from workspace
rm(list = ls())
```

**Important!!!** Once you remove an object, you **cannot** get it back without running the code that originally generated the object! That is, you can't simply click 'Undo' to get an object back. Thankfully, if your R code is complete and well-documented, you should easily be able to either re-create a lost object (e.g.; the results of a regression analysis), or re-load it from an external file.


## Learning check {-}


1. Open up your `practice.Rmd`. Run the code chunks you created in sequential order.

2. Create a code chunk and open up the three files above into the R workspace. 

2. Copy and Paste the three files `SubjectData.txt`, `scaleFact.txt`, `STRENGTH.xlsx`, from this books `data` folder, into   your `se747/analysis/data` folder.

3. Open up your `practice.Rmd`. Run the code chunks you created in sequential order.

4. Create a code chunk and open up the three files above into the R workspace. Assign the data from `scaleFact.txt` to `scalfac`, `STRENGTH.xlsx` to `strn`, and `SubjectData.txt` to `subjdat`



