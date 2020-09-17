--- 
title: "A Minimal Cookbook for your Basic Statistics Needs in R"
author: "Bernard Liew"
date: "2020-09-08"
output: bookdown::gitbook
documentclass: book
link-citations: yes
mainfont: Arial
monofont: Courier New
monofontoptions: Scale=0.7
bibliography: [book.bib]
site: bookdown::bookdown_site
biblio-style: apalike
---

# Preface {#intro}

The purpose of this book is to help you do stats **EASILY** but not fast at first.


**What this book is**

This books is intended to be a cookbook based approach. It has problems and it has solutions. You will find a similar document ".Rmd" in the supplied folder. Double click it and pressing run will execute everything you see in the PDF. 


**What this book is not**

This book does not cover any one topic in extensive detail. If you are interested in conducting analyses or creating plots not covered in the book, I'm sure you'll find the answer with a quick Google search!

## Why is R so great?

1. R is 100\% free and as a result, has a huge support community. Unlike SPSS, Matlab, Excel and JMP, R is, and always will be completely free. This doesn't just help your wallet - it means that a huge community of R programmers will constantly develop an distribute new R functionality and packages at a speed that leaves all those other packages in the dust! Unlike Fight Club, the first rule of R is "Do talk about R!" The size of the R programming community is staggering. If you ever have a question about how to implement something in R, a quick Poogle\footnote{I am in the process of creating Poogle - Google for Pirates. Kickstarter page coming soon...} search will lead you to your answer virtually every single time.

2. R is the present, and future of statistical programming. To illustrate this, look at the following three figures. These are Google trend searches for three terms: R Programming, Matlab, and SPSS. Try and guess which one is which.

\begin{figure}

{\centering \includegraphics[width=12.76in]{images/googletrends} 

}

\caption{Google trends for different statistical package}(\#fig:googletrend)
\end{figure}

3. R is incredibly versatile. You can use R to do everything from calculating simple summary statistics, to performing complex simulations to creating gorgeous plots. If you can imagine an analytical task, you can almost certainly implement it in R.

4. Using RStudio, a program to help you write R code, You can easily and seamlessly combine R code, analyses, plots, and written text into elegant documents all in one place using Sweave (R and Latex) or RMarkdown. In fact, I translated this entire book (the text, formatting, plots, code...yes, everything) in RStudio using Sweave. With RStudio and Sweave, instead of trying to manage two or three programs, say Excel, Word and (sigh) SPSS, where you find yourself spending half your time copying, pasting and formatting data, images and test, you can do everything in one place so nothing gets misread, mistyped, or forgotten.

5. Analyses conducted in R are transparent, easily shareable, and reproducible. If you ask an SPSS user how they conducted a specific analyses, they will either A) Not remember,  B) Try (nervously) to construct an analysis procedure on the spot that makes sense - which may or may not correspond to what they actually did months or years ago, or C) Ask you what you are doing in their house. I used to primarily use SPSS, so I speak from experience on this. If you ask an R user (who uses good programming techniques!) how they conducted an analysis, they should always be able to show you the exact code they used. Of course, this doesn't mean that they used the appropriate analysis or interpreted it correctly, but with all the original code, any problems should be completely transparent!


## Why R is like a relationship... {#rrelationship}

Yes, R is very much like a relationship. Like relationships, there are two major truths to R programming:

\begin{figure}

\includegraphics[width=8.75in]{images/rrelationship} \hfill{}

\caption{R will become both your best friend and your worst nightmare. The bad times will make the good times oh so much sweeter.}(\#fig:relationship)
\end{figure}

1. There is nothing more *frustrating* than when your code does *not* work

2. There is nothing more *satisfying* than when your code *does* work!


Anything worth doing, from losing weight to getting a degree, takes time. Learning R is no different. Especially if this is your first experience programming, you are going to experience a *lot* of headaches when you get started. You will run into error after error and pound your fists against the table screaming: "WHY ISN'T MY CODE WORKING?!?!? There must be something wrong with this stupid software!!!" You will spend hours trying to find a bug in your code, only to find that - frustratingly enough, you had had an extra space or missed a comma somewhere. You'll then wonder why you ever decided to learn R when (::sigh::) SPSS was so "nice and easy."


\begin{figure}

{\centering \includegraphics[width=5.99in]{images/gosling} 

}

\caption{When you first meet R, it will look so fugly that you'll wonder if this is all some kind of sick joke. But trust me, once you learn how to talk to it, and clean it up a bit, all your friends will be crazy jealous.}(\#fig:gosling)
\end{figure}

**Fun Fact!** SPSS stands for "Shitty Piece of Shitty Shit". True story.

This is perfectly normal! Don't get discouraged and DON'T GO BACK TO SPSS! That would be quitting on exercise altogether because you had a tough workout.

Trust me, as you gain more programming experience, you'll experience fewer and fewer bugs (though they'll never go away completely). Once you get over the initial barriers, you'll find yourself conducting analyses much, much faster than you ever did before.


## R resources


### R Cheatsheets

\begin{figure}

{\centering \includegraphics[width=0.75\linewidth]{images/rreferencess} 

}

\caption{The R reference card written by Tom Short is absolutely indispensable!}(\#fig:rreferencecard)
\end{figure}

Over the course of this book, you will be learning *lots* of new functions. Wouldn't it be nice if someone created a Cheatsheet / Dictionary of many common R functions? Yes it would, and thankfully several friendly R programmers have done just that. Below is a table of some of them that I recommend. I highly encourage you to print these out and start highlighting functions as you learn them!

| CheatSheet| Author| Link|
|:------------------------|:-----------|:-----------------------|
|     R Basics| Tom Short |    [https://cran.r-project.org/doc/contrib/Short-refcard.pdf](https://cran.r-project.org/doc/contrib/Short-refcard.pdf)|
|    Advanced R |   Arianne Colton and Sean Chen | [hhttps://www.rstudio.com/wp-content/uploads/2016/02/advancedR.pdf](https://www.rstudio.com/wp-content/uploads/2016/02/advancedR.pdf)|
| Base R | [Mhairi McNeill](http://mhairihmcneill.com/) |http://github.com/rstudio/cheatsheets/raw/master/base-r.pdf|
| Strings | [RStudio](https://www.rstudio.com) | https://github.com/rstudio/cheatsheets/raw/master/strings.pdf|
| Data import| [RStudio](https://www.rstudio.com) | https://github.com/rstudio/cheatsheets/raw/master/data-import.pdf|
|Data transformation| [RStudio](https://www.rstudio.com) | https://github.com/rstudio/cheatsheets/raw/master/data-import.pdf |
|RStudio application| [RStudio](https://www.rstudio.com) | https://github.com/rstudio/cheatsheets/raw/master/rstudio-ide.pdf|
| Plotting with ggplot2 | [RStudio](https://www.rstudio.com) |https://github.com/rstudio/cheatsheets/raw/master/data-visualization-2.1.pdf|
| RMarkdown| [RStudio](https://www.rstudio.com) |https://www.rstudio.com/wp-content/uploads/2015/03/rmarkdown-reference.pdf|


### Getting R help and inspiration online

Here are some great resources for R help and inspiration:

| Site| Description|
|:----------------------------|:-----------------------------------|
|     [www.google.com](http://www.google.com)| Seriously, Google is any programmer's best friend. More likely than not you will be directed to [www.stackoverflow.com](www.stackoverflow.com) or [www.stackexchange.com](www.stackexchange.com)|
|     [www.r-bloggers.com](http://www.r-bloggers.com)| R bloggers is my go-to place to discover the latest and greatest with R.|
|     [blog.revolutionanalytics.com](http://blog.revolutionanalytics.com)| Revolution analytics always has great R related material.|



### Other R books

There are many, many excellent (non-pirate) books on R, some of which are available online for free. Here are some that I highly recommend:

| Book| Description|
|:----------------------------|:-----------------------------------|
|     [R for Data Science by Garrett Grolemund and Hadley Wickham](http://r4ds.had.co.nz/)| The best book to learn the latest tools for elegantly doing data science.|
|     [R Graphics Cookbook by Winston Chang](http://www.cookbook-r.com/Graphs/)| is indispensible for creating graphics.|
|     [R Cookbook by James (JD) Long and Paul Teetor](https://rc2e.com/index.html)|is a useful bag of tips and tricks to get started with R .|
|     [Discovering Statistics with R by Field, Miles and Field](https://www.amazon.com/Discovering-Statistics-Using-Andy-Field/dp/1446200469/ref=sr_1_2?ie=UTF8&qid=1487759316&sr=8-2&keywords=statistics+with+r)| A classic text focusing on the theory and practice of statistical analysis with R|


<!--chapter:end:index.Rmd-->

---
output:
  html_document: default
  pdf_document: default
---
# Getting Started {#started}

## Installing Base-R and RStudio

To use R, we'll need to download two software packages: **Base-R**, and **RStudio**. Base-R is the basic software which contains the R programming language. RStudio is software that makes R programming easier. In everyday parlance, R is the engine and RStudio is the car's frame. Just like you can transfer an engine to different car frames, you can use R using other platforms. But I will use RStudio. Of course, they are totally free and open source.

### Check for version updates

R and RStudio have been around for several years -- however, they are *constantly* being updated with new features and bug-fixes. At the time that I am writing this sentence (10:00, Friday, 6 Sep 2019), the latest version of Base-R is 3.6.1 which was released on 5 Jul 2019, and the latest version of RStudio is 1.2.1335 released on 8 Apr 2019.

\begin{figure}

{\centering \includegraphics[width=0.4\linewidth]{images/rlogo} 

}

\caption{R logo}(\#fig:rlogo)
\end{figure}

To install Base-R, click on one of the following links and follow the instructions.

| Operating System| Link|
|:------|:----|
|     Windows|    [http://cran.r-project.org/bin/windows/base/](http://cran.r-project.org/bin/windows/base/)|
|     Mac|    [http://cran.r-project.org/bin/macosx/](http://cran.r-project.org/bin/macosx/)|


Once you've installed base-R on your computer, try opening it. When you do you should see a screen like the one in Figure \@ref(fig:rscreenshot) (this is the Windows version). As you can see, base R is very much bare-bones software. It's kind of the equivalent of a simple text editor that comes with your computer.

\begin{figure}

{\centering \includegraphics[width=0.75\linewidth]{images/RScreenshot} 

}

\caption{Here is how the base R application looks. While you can use the base R application alone, most people I know use RStudio -- software that helps you to write and use R code more efficiently!}(\#fig:rscreenshot)
\end{figure}


\begin{figure}

{\centering \includegraphics[width=0.4\linewidth]{images/RStudio} 

}

\caption{RStudio logo}(\#fig:rstudiologo)
\end{figure}

While you can do pretty much everything you want within base-R, you'll find that most people these days do their R programming in an application called RStudio. RStudio is a graphical user interface (GUI)-like interface for R that makes programming in R a bit easier. In fact, once you've installed RStudio, you'll likely never need to open the base R application again. To download and install RStudio (around 40mb), go to[http://www.rstudio.com/products/rstudio/download/](http://www.rstudio.com/products/rstudio/download/)| and follow the instructions.


Let's go ahead and boot up RStudio and see how she looks!

## The four RStudio Windows

When you open RStudio, you'll see the following four windows (also called panes) shown in in Figure \@ref(fig:rstudiowindows). However, your windows might be in a different order that those in Figure \@ref(fig:rstudiowindows). If you'd like, you can change the order of the windows under RStudio preferences. You can also change their shape by either clicking the minimize or maximize buttons on the top right of each panel, or by clicking and dragging the middle of the borders of the windows.


\begin{figure}

{\centering \includegraphics[width=1\linewidth]{images/RStudio_Screenshot_Labels} 

}

\caption{The four panes of RStudio.}(\#fig:rstudiowindows)
\end{figure}

Now, let's see what each window does in detail.

### Source - Your notepad for code

\begin{figure}

{\centering \includegraphics[width=1\linewidth]{images/piratesanalysisss} 

}

\caption{The Source contains all of your individual R scripts. The code won't be evaluated until you send it to the Console.}(\#fig:sourcewindow)
\end{figure}

The source pane is where you create and edit "R Scripts" - your collections of code. Don't worry, R scripts are just text files with the ".R" extension. When you open RStudio, it will automatically start a new Untitled script. Before you start typing in an untitled R script, you should always save the file under a new file name (like, "StatsAnal.R"). That way, if something on your computer crashes while you're working, R will have your code waiting for you when you re-open RStudio.

You'll notice that when you're typing code in a script in the Source panel, R won't actually evaluate the code as you type. To have R actually evaluate your code, you need to first 'send' the code to the Console (we'll talk about this in the next section).

There are many ways to send your code from the Source to the console. The slowest way is to copy and paste. A faster way is to highlight the code you wish to evaluate and clicking on the "Run" button on the top right of the Source. Alternatively, you can use the hot-key "Command + Return" on Mac, or "Control + Enter" on PC to send all highlighted code to the console.


### Console: R's Heart

\begin{figure}
\includegraphics[width=0.75\linewidth]{images/consoless} \caption{The console the calculation heart of R. All of your code will (eventually) go through here.}(\#fig:consolewindow)
\end{figure}


The console is the heart of R. Here is where R actually evaluates code. At the beginning of the console you'll see the character \texttt{>}. This is a prompt that tells you that R is ready for new code. You can type code directly into the console after the \texttt{>} prompt and get an immediate response. For example, if you type 1+1 into the console and press enter, you'll see that R immediately gives an output of 2.


```r
1+1
```

```
## [1] 2
```


Try calculating 1+1 by typing the code directly into the console - then press Enter. You should see the result [1] 2. Don't worry about the [1] for now, we'll get to that later. For now, we're happy if we just see the 2. Then, type the same code into the Source, and then send the code to the Console by highlighting the code and clicking the ``Run" button on the top right hand corner of the Source window. Alternatively, you can use the hot-key "Command + Return" on Mac or "Control + Enter" on Windows.

**Tip**: Try to write most of your code in a document in the Source. Only type directly into the Console to de-bug or do quick analyses.

So as you can see, you can execute code either by running it from the Source or by typing it directly into the Console. However, 99\% most of the time, you should be using the Source rather than the Console. The reason for this is straightforward: If you type code into the console, it won't be saved (though you can look back on your command History). And if you make a mistake in typing code into the console, you'd have to re-type everything all over again. Instead, it's better to write all your code in the Source. When you are ready to execute some code, you can then send "Run" it to the console.


### Environment / History


\begin{figure}
\includegraphics[width=0.75\linewidth]{images/environmentss} \caption{The environment panel shows you all the objects you have defined in your current workspace. You'll learn more about workspaces in Chapter 7.}(\#fig:environwindow)
\end{figure}

The Environment tab of this panel shows you the names of all the data objects (like vectors, matrices, and dataframes) that you've defined in your current R session. You can also see information like the number of observations and rows in data objects. The tab also has a few clickable actions like ``Import Dataset" which will open a graphical user interface (GUI) for important data into R. However, I almost never look at this menu.

The History tab of this panel simply shows you a history of all the code you've previously evaluated in the Console. To be honest, I never look at this. In fact, I didn't realize it was even there until I started writing this tutorial.

As you get more comfortable with R, you might find the Environment / History panel useful. But for now you can just ignore it. If you want to declutter your screen, you can even just minimize the window by clicking the minimize button on the top right of the panel.


### Files / Plots / Packages / Help

The Files / Plots / Packages / Help panel shows you lots of helpful information. Let's go through each tab in detail:

1. Files - The files panel gives you access to the file directory on your hard drive. One nice feature of the "Files" panel is that you can use it to set your working directory - once you navigate to a folder you want to read and save files to, click "More" and then "Set As Working Directory." We'll talk about working directories in more detail soon.

2. Plots - The Plots panel (no big surprise), shows all your plots. There are buttons for opening the plot in a separate window and exporting the plot as a pdf or jpeg (though you can also do this with code using the `pdf()` or `jpeg()` functions.)

Let's see how plots are displayed in the Plots panel. Run the code on the right to display a histogram of the weights of chickens stored in the `ChickWeight` dataset. When you do, you should see a plot similar to the one in Figure \@ref(fig:plotpanel) show up in the Plots panel.


```r
hist(x = ChickWeight$weight,
     main = "Chicken Weights",
     xlab = "Weight",
     col = "skyblue",
     border = "white")
```


\begin{figure}
\includegraphics[width=0.75\linewidth]{images/plotpanelss} \caption{The plot panel contains all of your plots, like this histogram of the distribution of chicken weights.}(\#fig:plotpanel)
\end{figure}



3. Packages - Shows a list of all the R packages installed on your harddrive and indicates whether or not they are currently loaded. Packages that are loaded in the current session are checked while those that are installed but not yet loaded are unchecked. We'll discuss packages in more detail in the next section.

4. Help - Help menu for R functions. You can either type the name of a function in the search window, or use the code \texttt{?function.name} to search for a function with the name \texttt{function.name}



```r
?hist   # How does the histogram function work?
?t.test # What about a t-test?
```


## Reading and writing Code

### Code Chunks

In this book, R code is (almost) always presented in a separate gray box like this one:


```r
# A code chunk

# Define a vector a as the integers from 1 to 5
a <- 1:5

# Print a
a
```

```
## [1] 1 2 3 4 5
```

```r
# What is the mean of a?
mean(a)
```

```
## [1] 3
```

This is called a *code chunk*. You should always be able to copy and paste code chunks directly into R. If you copy a chunk and it does not work for you, it is most likely because the code refers to a package, function, or object that I defined in a previous chunk. If so, read back and look for a previous chunk that contains the missing definition.

### Comments with \#

Lines that begin with \# are comments. If you evaluate any code that starts with \#, R will just ignore that line. In this book, comments will be either be literal comments that I write directly to explain code, or they will be *output* generated automatically from R. For example, in the code chunk below, you see lines starting with \#\#. These are the output from the previous line(s) of code. When you run the code yourself, you should see the same output in your *console*.


```r
# This is a comment I wrote

1 + 2
```

```
## [1] 3
```

```r
# The line above (## [1] 3) is the output from the previous code that has been 'commented out'
```


### Element numbers in output [1] 

The output you see will often start with one or more number(s) in brackets such as [1]. This is just a visual way of telling you where the numbers occur in the output. For example, in the code below, I will print a long vector containing the multiples of 2 from 0 to 100:


```r
seq(from = 0, to = 100, by = 2)
```

```
##  [1]   0   2   4   6   8  10  12  14  16  18  20  22  24  26  28  30  32  34  36
## [20]  38  40  42  44  46  48  50  52  54  56  58  60  62  64  66  68  70  72  74
## [39]  76  78  80  82  84  86  88  90  92  94  96  98 100
```

As you can see, the first line of the output starts with \#\# [1], and the next two lines start with [18] and [35]. This is just telling you that 0 is the [1]st element, 34 is the [18]th element, and 68 is the [35]th element. Sometimes this information will be helpful, but most of the time you can just ignore it.

## Debugging

When you are programming, you will always, and I do mean always, make errors (also called bugs) in your code. You might misspell a function, include an extra comma, or some days...R just won't want to work with you  (again, see section [Why R is like a Relationship](#rrelationship)).

Debugging will always be a challenge. However, over time you'll learn which bugs are the most common and get faster and faster at finding and correcting them. 

Here are the most common bugs you'll run into as you start your R journey.


### R is not ready (>)

Another very common problem occurs when R does not seem to be responding to your code. That is, you might run some code like `mean(x)` expecting some output, but instead, nothing happens. This can be very frustrating because, rather than getting an error, just nothing happens at all. The most common reason for this is because R isn't *ready* for new code, instead, it is *waiting* for you to finish code you started earlier, but never properly finished. 

Think about it this way, R can be in one of two states: it is either **Ready** (>) for new code, or it is **Waiting** (+) for you to finish old code. To see which state R is in, all you have to do is look at the symbol on the console. The `>` symbol means that R is Ready for new code -- this is usually what you want to see. The `+` symbol means that R is Waiting for you to (properly) finish code you started before. If you see the `+` symbol, then no matter how much new code you write, R won't actually evaluate it until you finish the code you started before.

Thankfully there is an easy solution to this problem (See Figure \@ref(fig:rstate)): Just hit the escape key on your keyboard. This will cancel R's waiting state and make it Ready!


\begin{figure}

{\centering \includegraphics[width=0.5\linewidth]{images/escapesolution} 

}

\caption{To turn R from a Waiting (+) state to a Ready (>) state, just hit Escape.}(\#fig:rstate)
\end{figure}


### Misspelled object or function

If you spell an object or function incorrectly, you'll receive an error like `Error: could not find function` or `Error: object 'x' not found`.

In the code below, I'll try to take the mean of a vector `data`, but I will misspell the function `mean()`


```r
data <- c(1, 4, 3, 2, 1)

# Misspelled function: should be mean(x), not meeen(x)
meeen(data)
```
<div class="error">Error: could not find function "meeen"</div>

Now, I'll misspell the object `data` as `dta`:


```r
# Misspelled object: should be data, not dta
mean(dta)
```

<div class="error">Error: object 'dta' not found</div>

R is case-sensitive, so if you don't use the correct capitalization you'll receive an error. In the code below, I'll use `Mean()` instead of the correct version `mean()`


```r
# Capitalization is wrong: should be mean(), not Mean()
Mean(data)
```
<div class="error">Error: could not find function "Mean"</div>

Here is the correct version where both the object `data` and function `mean()` are correctly spelled:





```r
# Correct: both the object and function are correctly spelled
mean(data)
```

```
## [1] 2.2
```


### Punctuation problems

Another common error is having bad coding "punctuation". By that, I mean having an extra space, missing a comma, or using a comma (,) instead of a period (.). In the code below, I'll try to create a vector using periods instead of commas:


```r
# Wrong: Using periods (.) instead of commas (,)
mean(c(1. 4. 2))
```
<div class="error">Error: unexpected numeric constant in "mean(c(1. 4."</div>

Because I used periods instead of commas, I get the above error. Here is the correct version


```r
# Correct
mean(c(1, 4, 2))
```

```
## [1] 2.333333
```

If you include an extra space in the middle of the name of an object or function, you'll receive an error. In the code below, I'll accidentally write `Chick Weight` instead of `ChickWeight`:


```r
# Wrong: Extra space in the ChickWeight object name
head(Chick Weight)
```

<div class="error">Error: unexpected symbol in "head(Chick Weight"</div>

Because I had an extra space in the object name, I get the above error. Here is the correction:


```r
# Correct:
head(ChickWeight)
```

## Learning check {-}


1. Download R software and RStudio software

2. Open up RStudio software and type the following code below into the **console**. What does it give you?

```r
1+10
```

3. Look at the code below. What will R return after the third line? Make a prediction, then test the code yourself.



```r
a <- 10
a + 10
a
```

<!--chapter:end:01-gettingstarted.Rmd-->

---
output:
  pdf_document: default
  html_document: default
---
# The Basics {#basics}

## Download and load libraries

Libraries are like your iphone apps. The iphone comes with some basic functionality, e.g. weather. If you wanted more, you have to download. Subsequent chapters are going to start with this code chunk. This is only needed if you are running one chapter independent from others. Notice how I am using the package called `pacman`. This is a package manager, which loads any package you typed into it, and if it is not available, download it automatically from CRAN and load it.


```r
if (!require("pacman")) install.packages("pacman")
pacman::p_load(tidyverse, # All purpose wrangling for dataframes
               readr, # importing and writing data
               readxl,# read and write excel documents
               purrr, # for piping %>%
               corrplot, # for correlation
               knitr,
               yarrr)
```

If you're like most people, you think of R as a statistics program. However, while R is definitely the coolest, most badass, pirate-y way to conduct statistics -- it's not really a program. Rather, it's a programming *language* that was written by and for statisticians. 


In this chapter, we'll go over the basics of the R language and the RStudio programming environment.


## The command-line (Console)


\begin{figure}

{\centering \includegraphics[width=0.5\linewidth]{images/woodcalc} 

}

\caption{Yep. R is really just a fancy calculator. This R programming device was found on a shipwreck on the Bodensee in Germany. I stole it from a museum and made a pretty sweet plot with it. But I don't want to show it to you.}(\#fig:unnamed-chunk-2)
\end{figure}


R code, on its own, is just text. You can write R code in a new script within R or RStudio, or in any text editor. Hell, you can write R code on Twitter if you want. However, just writing the code won't do the whole job -- in order for your code to be executed (aka, interpreted) you need to send it to R's *command-line interpreter*. In RStudio, the command-line interpreter is called the Console.


\begin{figure}

{\centering \includegraphics[width=0.75\linewidth]{images/commandline} 

}

\caption{You can always type code directly into the command line to get an immediate response.}(\#fig:unnamed-chunk-3)
\end{figure}


In R, the command-line interpreter starts with the `>` symbol. This is called the **prompt**. Why is it called the prompt? Well, it's "prompting" you to feed it with some R code. The fastest way to have R evaluate code is to type your R code directly into the command-line interpreter. For example, if you type `1+1` into the interpreter and hit enter you'll see the following



```r
1+1
```

```
## [1] 2
```

As you can see, R returned the (thankfully correct) value of 2. You'll notice that the console also returns the text [1]. This is just telling you you the index of the value next to it. Don't worry about this for now, it will make more sense later. As you can see, R can, thankfully, do basic calculations. In fact, at its heart, R is technically just a fancy calculator. But that's like saying Michael Jordan is *just* a fancy ball bouncer or Donald Trump is *just* an orange with a dead fox on his head. It (and they), are much more than that.

## Writing R scripts in an editor

There are certainly many cases where it makes sense to type code directly into the console. For example, to open a help menu for a new function with the ? command, to take a quick look at a dataset with the `head()` function, or to do simple calculations like `1+1`, you should type directly into the console. However, the problem with writing all your code in the console is that nothing that you write will be saved. So if you make an error, or want to make a change to some earlier code, you have to type it all over again. Not very efficient. For this (and many more reasons), you'll should write any important code that you want to save as an R script. An R script is just a bunch of R code in a single file. You can write an R script in any text editor, but you should save it with the `.R` suffix to make it clear that it contains R code.} in an editor. 


In RStudio, you'll write your R code in the...wait for it...*Source* window. To start writing a new R script in RStudio, click File -- New File -- R Script.


When you open a new script, you'll see a blank page waiting for you to write as much R code as you'd like. In Figure \@ref(fig:editor), I have a new script called `examplescript` with a few random calculations.


\begin{figure}

{\centering \includegraphics[width=0.75\linewidth]{images/sourcess} 

}

\caption{Here's how a new script looks in the editor window on RStudio. The code you type won't be executed until you send it to the console.}(\#fig:editor)
\end{figure}

You can have several R scripts open in the source window in separate tabs (like I have above).

### Send code from a source to the console

\begin{figure}

{\centering \includegraphics[width=0.75\linewidth]{images/runningcode} 

}

\caption{To evaluate code from the source, highlight it and run it.}(\#fig:runcode)
\end{figure}

When you type code into an R script, you'll notice that, unlike typing code into the Console, nothing happens. In order for R to interpret the code, you need to send it from the Editor to the Console. There are a few ways to do this, here are the three most common ways:

1. Copy (using Crtl+C) the code from the Editor (or anywhere that has valid R code), and paste it into the Console (using Crtl+V).

2. Highlight the code you want to run (with your mouse or by holding Shift), then use the Alt+Enter shortcut.

3. Place the cursor on a single line you want to run, then use the Alt+Enter shortcut to run just that line.

99\% of the time, I use method 2, where I highlight the code I want, then use the Command--Return shortcut . However, method 3 is great for trouble-shooting code line-by-line.

## Writing R scripts using notebooks

To start writing a new R notebook in RStudio, in the `+` image under File, click on it and you should see an image below. 

\begin{figure}

{\centering \includegraphics[width=0.75\linewidth]{images/new_notebook} 

}

\caption{How to create a new notebook.}(\#fig:newnotebook)
\end{figure}

Click on `R Notebook` and you should see a blank notebook. What you see in the image below is a new notebook. A notebook is a special type of script that allows you to view the results below the code. As you can see, there are instructions that tells you how to function in a notebook.

\begin{figure}

{\centering \includegraphics[width=0.75\linewidth]{images/notebook_in_source} 

}

\caption{What a notebook looks like.}(\#fig:notebookview)
\end{figure}

The notebook is a very systematic way of analysing your data, because you can add comments before the code chunk (reminding you of what you did), keep the codes you painfully typed out, and see the results below. You can add more code chunks by pressing the `Insert` button and selecting the `R` option. **I recommend this way of working.**

\begin{figure}

{\centering \includegraphics[width=0.75\linewidth]{images/notebook_instruc} 

}

\caption{How to work in a notebook }(\#fig:notebookinstruc)
\end{figure}



## A brief style guide: Commenting and spacing

Like all programming languages, R isn't just meant to be read by a computer, it's also meant to be read by other humans -- or very well-trained dolphins. For this reason, it's important that your code looks nice and is understandable to other people and your future self. To keep things brief, I won't provide a complete style guide -- instead I'll focus on the two most critical aspects of good style: commenting and spacing.



\begin{figure}

{\centering \includegraphics[width=0.5\linewidth]{images/futureself} 

}

\caption{As Stan discovered in season six of South Park, your future self is a lazy, possibly intoxicated moron. So do your future self a favor and make your code look nice. Also maybe go for a run once in a while.}(\#fig:futureself)
\end{figure}


### Commenting code with the \# (pound) sign

Comments are completely ignored by R and are just there for whomever is reading the code. You can use comments to explain what a certain line of code is doing, or just to visually separate meaningful chunks of code from each other. Comments in R are designated by a \# (pound) sign. Whenever R encounters a \# sign, it will ignore **all** the code after the \# sign on that line. Additionally, in most coding editors (like RStudio) the editor will display comments in a separate color than standard R code to remind you that it's a comment:

Here is an example of a short script that is nicely commented. Try to make your scripts look like this!


```r
# Author: Pirate Jack
# Title: My nicely commented R Script
# Date: None today :(

# Step 1: Load the yarrr package
library(yarrr)

# Step 2: See the column names in the movies dataset
names(movies)

# Step 3: Calculations

# What percent of movies are sequels?
mean(movies$sequel, na.rm = T)

# How much did Pirate's of the Caribbean: On Stranger Tides make?
movies$revenue.all[movies$name == 'Pirates of the Caribbean: On Stranger Tides']
```



I cannot stress enough how important it is to comment your code! Trust me, even if you don't plan on sharing your code with anyone else, keep in mind that your future self will be reading it in the future. 


### Spacing

Howwouldyouliketoreadabookiftherewerenospacesbetweenwords?
I'mguessingyouwouldn't.
Soeverytimeyouwritecodewithoutproperspacing,rememberthissentence.

Commenting isn't the only way to make your code legible. It's important to make appropriate use of spaces and line breaks. For example, I include spaces between arithmetic operators (like =, + and -) and after commas (which we'll get to later). For example, look at the following code:

\begin{figure}

{\centering \includegraphics[width=0.5\linewidth]{images/pileofshit} 

}

\caption{Don't make your code look like what a sick Triceratops with diarrhea left behind for Jeff Goldblum.}(\#fig:pileofshit)
\end{figure}


```r
# Shitty looking code
a<-(100+3)-2
mean(c(a/100,642564624.34))
t.test(formula=revenue.all~sequel,data=movies)
plot(x=movies$budget,y=movies$dvd.usa,main="myplot")
```

That code looks like shit. Don't write code like that. It makes my eyes hurt. Now, let's use some liberal amounts of commenting and spacing to make it look less shitty.


```r
# Some meaningless calculations. Not important

a <- (100 + 3) - 2
mean(c(a / 100, 642564624.34))

# t.test comparing revenue of sequels v non-sequels

t.test(formula = revenue.all ~ sequel,
       data = movies)

# A scatterplot of budget and dvd revenue. 
#  Hard to see a relationship

plot(x = movies$budget,
     y = movies$dvd.usa,
     main = "myplot")
```


See how much better that second chunk of code looks? Not only do the comments tell us the purpose behind the code, but there are spaces and line-breaks separating distinct elements.

## Objects and functions

To understand how R works, you need to know that R revolves around two things: objects and functions. Almost everything in R is either an object or a function. In the following code chunk, I'll define a simple object called `tattoos` using a function `c()`:


```r
# 1: Create a vector object called tattoos
tattoos <- c(4, 67, 23, 4, 10, 35)

# 2: Apply the mean() function to the tattoos object
mean(tattoos)
```

```
## [1] 23.83333
```

What is an object? An object is a thing -- like a number, a dataset, a summary statistic like a mean or standard deviation, or a statistical test. Objects come in many different shapes and sizes in R. There are simple objects like \textit{scalars} which represent single numbers, **vectors** (like our `tattoos` object above) which represent several numbers, more complex objects like **dataframes** which represent tables of data, and even more complex objects like **hypothesis tests** or **regression** which contain all sorts of statistical information.

Different types of objects have different *attributes*. For example, a vector of data has a length attribute (i.e.; how many numbers are in the vector), while a hypothesis test has many attributes such as a test-statistic and a p-value. Don't worry if this is a bit confusing now -- it will all become clearer when you meet these new objects in person in later chapters. For now, just know that objects in R are things, and different objects have different attributes.
 
What is a function? A function is a *procedure* that typically takes one or more objects as arguments (aka, inputs), does something with those objects, then returns a new object. For example, the `mean()` function we used above takes a vector object, like `tattoos`, of numeric data as an argument, calculates the arithmetic mean of those data, then returns a single number (a scalar) as a result.A great thing about R is that you can easily create your own functions that do whatever you want -- but we'll get to that much later in the book. Thankfully, R has hundreds (thousands?) of built-in functions that perform most of the basic analysis tasks you can think of.

99\% of the time you are using R, you will do the following: 1) Define objects. 2) Apply functions to those objects. 3) Repeat!. Seriously, that's about it. However, as you'll soon learn, the hard part is knowing how to define objects they way you want them, and knowing which function(s) will accomplish the task you want for your objects.

### Numbers versus characters

For the most part, objects in R come in one of two flavors: **numeric** and **character**. It is very important to keep these two separate as certain functions, like `mean()`, and `max()` will only work for numeric objects, while functions like `grep()` and `strtrim()` only work for character objects.

A numeric object is just a number like `1`, `10` or `3.14`. You don't have to do anything special to create a numeric object, just type it like you were using a calculator.


```r
# These are all numeric objects
1
10
3.14
```

A **character** object is a name like `"Madisen"`, `"Brian"`, or `"University of Konstanz"`. To specify a character object, you need to include quotation marks `""` around the text.


```r
# These are all character objects
"Madisen"
"Brian"
"10"
```

If you try to perform a function or operation meant for a numeric object on a character object (and vice-versa), R will yell at you. For example, here's what happens when I try to take the mean of the two character objects `"1"` and `"10"`:


```r
# This will return an error because the arguments are not numeric!
mean(c("1", "10"))
```
<div class="error">Warning message: argument is not numeric or logical, returning NA</div>

If I make sure that the arguments are numeric (by not including the quotation marks), I won't receive the error:


```r
# This is ok!
mean(c(1, 10))
```

```
## [1] 5.5
```


### Creating new objects with <-

By now you know that you can use R to do simple calculations. But to really take advantage of R, you need to know how to create and manipulate objects. All of the data, analyses, and even plots, you use and create are, or can be, saved as objects in R. For example the `movies` dataset which we've used before is an object stored in the `yarrr` package. This object was defined in the `yarrr` package with the name `movies`. When you loaded the `yarrr` package with the `library('yarrr')` command, you told R to give you access to the `movies` object. Once the object was loaded, we could use it to calculate descriptive statistics, hypothesis tests, and to create plots.

To create new objects in R, you need to do *object assignment*. Object assignment is our way of storing information, such as a number or a statistical test, into something we can easily refer to later. This is a pretty big deal. Object assignment allows us to store data objects under relevant names which we can then use to slice and dice specific data objects anytime we'd like to.

To do an assignment, we use the almighty `<-` operator called *assign* To assign something to a new object (or to change an existing object), use the notation `object <- ...`}, where `object` is the new (or updated) object, and `...` is whatever you want to store in `object`. Let's start by creating a very simple object called `a` and assigning the value of 100 to it:

Good object names strike a balance between being easy to type (i.e.; short names) and interpret. If you have several datasets, it's probably not a good idea to name them `a`, `b`, `c` because you'll forget which is which. However, using long names like `March2015Group1OnlyFemales` will give you carpal tunnel syndrome.



```r
# Create a new object called a with a value of 100
a <- 100
```


Once you run this code, you'll notice that R doesn't tell you anything. However, as long as you didn't type something wrong, R should now have a new object called `a` which contains the number 100. If you want to see the value, you need to call the object by just executing its name. This will print the value of the object to the console:


```r
# Print the object a
a
```

```
## [1] 100
```

Now, R will print the value of `a` (in this case 100) to the console. If you try to evaluate an object that is not yet defined, R will return an error. For example, let's try to print the object `b` which we haven't yet defined:


```r
b
```
<div class="error">Error: object 'b' not found</div>


As you can see, R yelled at us because the object `b` hasn't been defined yet.

Once you've defined an object, you can combine it with other objects using basic arithmetic. Let's create objects `a` and `b` and play around with them.


```r
a <- 1
b <- 100

# What is a + b?
a + b
```

```
## [1] 101
```

```r
# Assign a + b to a new object (c)
c <- a + b

# What is c?
c
```

```
## [1] 101
```



#### To change an object, you must assign it again!

Normally I try to avoid excessive emphasis, but because this next sentence is so important, I have to just go for it. Here it goes...

**To change an object, you \textit{must} assign it again!**

No matter what you do with an object, if you don't assign it again, it won't change. For example, let's say you have an object `z` with a value of 0. You'd like to add 1 to `z` in order to make it 1. To do this, you might want to just enter `z + 1` -- but that won't do the job. Here's what happens if you **don't** assign it again:


```r
z <- 0
z + 1
```

```
## [1] 1
```

Ok! Now let's see the value of `z`


```r
z
```

```
## [1] 0
```

Damn! As you can see, the value of z is still 0! What went wrong? Oh yeah...

**To change an object, you *must* assign it again!**


The problem is that when we wrote `z + 1` on the second line, R thought we just wanted it to calculate and print the value of `z + 1`, without storing the result as a new `z` object. If we want to actually update the value of `z`, we need to reassign the result back to `z` as follows:


```r
z <- 0
z <- z + 1  # Now I'm REALLY changing z
z
```

```
## [1] 1
```


Phew, z is now 1. Because we used assignment, z has been updated. About freaking time.


### How to name objects

You can create object names using any combination of letters and a few special characters (like `.` and `_`). Here are some valid object names


```r
# Valid object names
group.mean <- 10.21
my.age <- 32
FavoritePirate <- "Jack Sparrow"
sum.1.to.5 <- 1 + 2 + 3 + 4 + 5
```


All the object names above are perfectly valid. Now, let's look at some examples of *invalid* object names. These object names are all invalid because they either contain spaces, start with numbers, or have invalid characters:


```r
# Invalid object names!
famale ages <- 50 # spaces
5experiment <- 50 # starts with a number
a! <- 50 # has an invalid character
```


If you try running the code above in R, you will receive a warning message starting with <div class="error">Error: unexpected symbol</div>. Anytime you see this warning in R, it almost always means that you have a naming error of some kind.

#### R is case-sensitive!

\begin{figure}

{\centering \includegraphics[width=0.5\linewidth]{images/datetext} 

}

\caption{Like a text message, you should probably watch your use of capitalization in R.}(\#fig:datetext)
\end{figure}


Like English, R is case-sensitive -- it R treats capital letters differently from lower-case letters. For example, the four following objects `Plunder`, `plunder` and `PLUNDER` are totally different objects in R:


```r
# These are all different objects
Plunder <- 1
plunder <- 100
PLUNDER <- 5
```

I try to avoid using too many capital letters in object names because they require me to hold the shift key. This may sound silly, but you'd be surprised how much easier it is to type `mydata` than `MyData` 100 times.



###Example: Pirates of The Caribbean

Let's do a more practical example -- we'll define an object called `blackpearl.usd` which has the global revenue of Pirates of the Caribbean: Curse of the Black Pearl in U.S. dollars. A quick Google search showed me that the revenue was \$634,954,103. I'll create the new object using assignment:


```r
blackpearl.usd <- 634954103
```



Now, my fellow European pirates might want to know how much this is in Euros. Let's create a new object called `{blackpearl.eur` which converts our original value to Euros by multiplying the original amount by 0.88 (assuming 1 USD = 0.88 EUR)


```r
blackpearl.eur <- blackpearl.usd * 0.88
blackpearl.eur
```

```
## [1] 558759611
```


It looks like the movie made 558,759,611 in Euros. Not bad. Now, let's see how much more Pirates of the Caribbean 2: Dead Man's Chest made compared to "Curse of the Black Pearl." Another Google search uncovered that Dead Man's Chest made \$1,066,215,812 (that wasn't a mistype, the freaking movie made over a billion dollars). 


```r
deadman.usd <- 1066215812
```

Now, I'll divide `deadman.usd` by `blackpearl.usd`:


```r
deadman.usd / blackpearl.usd
```

```
## [1] 1.679201
```


It looks like "Dead Man's Chest" made 168\% as much as "Curse of the Black Pearl" - not bad for two movies based off of a ride from Disneyland.


<!--chapter:end:02-basics.Rmd-->

---
output:
  html_document: default
  pdf_document: default
---
# Navigating the Software {#NavigatingTheSoftware}

## Introduction {-}


Both R and RStudio are big chunks of software, first and foremost. You will inevitably
spend time doing what one does with any big piece of software:
configuring it, customizing it, updating it, and fitting it into your
computing environment. This chapter will help you perform those tasks.
There is nothing here about numerics, statistics, or graphics. This is
all about dealing with R and RStudio as software.

## Download and load libraries {-}


```r
if (!require("pacman")) install.packages("pacman")
pacman::p_load(tidyverse, # All purpose wrangling for dataframes
               readr, # importing and writing data
               readxl,# read and write excel documents
               purrr, # for piping %>%
               corrplot, # for correlation
               knitr,
               yarrr)
```


\begin{figure}

{\centering \includegraphics[width=0.75\linewidth]{images/workspace} 

}

\caption{Your workspace -- all the objects, functions, and delicious glue you've defined in your current session.}(\#fig:workspace)
\end{figure}


Remember way back in Chapter 2 when I said everything in R is an object? Well, that's still true. In this chapter, we'll cover the basics of R object management. We'll cover how to load new objects like external datasets into R, how to manage the objects that you already have, and how to export objects from R into external files that you can share with other people or store for your own future use.






## Getting and Setting the Working Directory

Your computer is a maze of folders, files. Outside of R, when you want to open a specific file, you probably open up an explorer window that allows you to visually search through the folders on your computer. Or, maybe you select recent files, or type the name of the file in a search box to let your computer do the searching for you. While this system usually works for non-programming tasks, it is a no-go for R. Why? Well, the main problem is that all of these methods require you to *visually* scan your folders and move your mouse to select folders and files that match what you are looking for. When you are programming in R, you need to specify *all* steps in your analyses in a way that can be easily replicated by others and your future self. This means you can't just say: "Find this one file I emailed to myself a week ago" or "Look for a file that looks something like `experimentAversion3.txt`." Instead, need to be able to write R code that tells R *exactly* where to find critical files -- either on your computer or on the web.

To make this job easier, R uses **working directories**. 

You want to change your working directory, or you just want to know what
it is.


RStudio

:   Navigate to a directory in the Files pane. Then from the Files pane, select More → Set As Working Directory, as shown in Figure \@ref(fig:workingdir).

\begin{figure}
\includegraphics[width=13.53in]{images/rstudio.files} \caption{RStudio: Set As Working Directory}(\#fig:workingdir)
\end{figure}

Console

:   Use `getwd` to report the working directory, and use `setwd` to
    change it:


```r
getwd()
```

```
## [1] "C:/Users/liew_/Box/myBox/Documents/teaching/SE747_PgResMeth/se747_stats_book"
```

Saving the working directory path into an object called `currwd`

```r
currwd <- getwd()
```


```r
# setting it manually with copy + paste
setwd("C:/Users/bl19622/Box/myBox/Documents/teaching/SE747_PgResMeth/sample_book")

#  setting it using the object we created
setwd (currwd)
```

Your working directory is important because it is the default location
for all file input and output—including reading and writing data files,
opening and saving script files, and saving your workspace image. When
you open a file and do not specify an absolute path, R will assume that
the file is in your working directory.

If you're using RStudio projects, your default working directory will be the home directory of the project. 

## Creating a new Rstudio project

You want to create a new RStudio project to keep all your files related to a specific project. 
Click File → New Project as in Figure \@ref(fig:filenew-drop). ** I ALWAYS use this approach, please use it too**

\begin{figure}
\includegraphics[width=7.25in]{images/rstudio.file.newproject} \caption{Selecting New Project}(\#fig:filenew-drop)
\end{figure}

This will open the New Project dialog box and allow you to choose which type of project you would like to create, as shown in Figure \@ref(fig:filenewmenu).

\begin{figure}
\includegraphics[width=14.92in]{images/rstudio.newproject.dialog} \caption{New Project dialog}(\#fig:filenewmenu)
\end{figure}

Projects are a powerful concept that's specific to RStudio. They help you by doing the following:

-  Setting your working directory to the project directory.
-  Preserving window state in RStudio so when you return to a project your windows are all as you left them. This includes opening any files you had open when you last saved your project. 
-  Preserving RStudio project settings.

To hold your project settings, RStudio creates a project file with an *.Rproj* extension in the project directory. If you open the project file in RStudio, it works like a shortcut for opening the project. In addition, RStudio creates a hidden directory named *.Rproj.user* to house temporary files related to your project. 

Any time you're working on something nontrivial in R we recommend creating an RStudio project. Projects help you stay organized and make your project workflow easier. 


## Viewing Your Command History

You want to see your recent sequence of commands.

Depending on what you are trying to accomplish, you can use a few different methods to access your prior command history. If you are in the RStudio console pane, you can press the up arrow to interactively scroll through past commands. 

If you want to see a listing of past commands, you can either execute the `history`
function or access the History pane in RStudio to view your most recent input:


```r
history()
```

In RStudio typing `history()` into the console simply activates the History pane in RStudio (Figure \@ref(fig:history)). You could also make that pane visible by clicking on it with your cursor. 

\begin{figure}
\includegraphics[width=9.78in]{images/history} \caption{RStudio History pane}(\#fig:history)
\end{figure}


The `history` function displays your most recent commands. In RStudio the `history` command will activate the History pane. If you were running R outside of RStudio, `history` shows the most recent 25 lines, but you can request more like so:


```r
history(100)          # Show 100 most recent lines of history
history(Inf)          # Show entire saved history
```
From within RStudio, the History tab shows an exhaustive list of past commands in chronological order, with the most recent at the bottom of the list. You can highlight past commands with your cursor, then click on "To Console" or "To Source" to copy past commands into the console or source editor, respectively. This can be terribly handy when you've done interactive data analysis and then decide you want to save some past steps to a source file for later use. 

From the console you can see your history by simply pressing the up arrow to scroll backward through your input, which causes your previous typing to reappear, one line at a time.

If you’ve exited from R or RStudio, you can still see your command history. R
saves the history in a file called *.Rhistory* in the working directory. Open the file with a text editor and then scroll to the
bottom; you will see your most recent typing.


## Installing Packages 

When you download and install R for the first time, you are installing the Base R software. Base R will contain most of the functions you'll use on a daily basis like `mean()` and `hist()`. However, only functions written by the original authors of the R language will appear here. If you want to access data and code written by other people, you'll need to install it as a *package*. An R package is simply a bunch of data, from functions, to help menus, to vignettes (examples), stored in one neat package.


\begin{figure}

{\centering \includegraphics[width=0.5\linewidth]{images/packagebulb} 

}

\caption{An R package is like a lightbulb. First you need to order it with install.packages(). Then, every time you want to use it, you need to turn it on with library()}(\#fig:package)
\end{figure}


A package is like a light bulb. In order to use it, you first need to order it to your house (i.e.; your computer) by *installing* it. Once you've installed a package, you never need to install it again. However, every time you want to actually use the package, you need to turn it on  by *loading* it. Here's how to do it.


### Installing a new package

Installing a package simply means downloading the package code onto your personal computer. There are two main ways to install new packages. The first, and most common, method is to download them from the Comprehensive R Archive Network (CRAN). CRAN is the central repository for R packages. To install a new R package from CRAN, you can simply run the code `install.packages("name")`, where "name" is the name of the package. For example, to download the `yarrr` package, which contains several data sets and functions we will use in this book, you should run the following:


\begin{figure}

{\centering \includegraphics[width=0.5\linewidth]{images/cran} 

}

\caption{CRAN (Comprehensive R Archive Network) is the main source of R packages}(\#fig:cran)
\end{figure}





```r
# Install the yarrr package from CRAN
#   You only need to install a package once!
install.packages("yarrr")
```


When you run `install.packages("name")` R will download the package from CRAN. If everything works, you should see some information about where the package is being downloaded from, in addition to a progress bar.

\begin{figure}

{\centering \includegraphics[width=0.75\linewidth]{images/installingpackages} 

}

\caption{When you install a new package, you'll see some random text like this you the download progress. You don't need to memorize this.}(\#fig:installingpackages)
\end{figure}


Like ordering a light bulb, once you've installed a package on your computer you never need to install it again (unless you want to try to install a new version of the package). However, every time you want to use it, you need to turn it on by loading it.


### Loading a package

Once you've installed a package, it's on your computer. However, just because it's on your computer doesn't mean R is ready to use it. If you want to use something, like a function or dataset, from a package you *always* need to *load* the package in your R session first. Just like a light bulb, you need to turn it on to use it!

To load a package, you use the `library()` function. For example, now that we've installed the `yarrr` package, we can load it with `library("yarrr")`:


```r
# Load the yarrr package so I can use it!
#   You have to load a package in every new R session!
library("yarrr")
```


Now that you've loaded the `yarrr` package, you can use any of its functions! One of the coolest functions in this package is called `pirateplot()`. Rather than telling you what a pirateplot is, let's just make one. Run the following code chunk to make your own pirateplot. Don't worry about the specifics of the code below, you'll learn more about how all this works later. For now, just run the code and marvel at your pirateplot.


```r
# Make a pirateplot using the pirateplot() function
#  from the yarrr package!

pirateplot(formula = weight ~ Time, 
           data = ChickWeight,
           pal = "xmen")
```

![](03-navigatingworkspace_files/figure-latex/unnamed-chunk-9-1.pdf)<!-- --> 

There is one way in R to temporarily load a package without using the `library()` function. To do this, you can simply use the notation `package::function` notation. This notation simply tells R to load the package just for this one chunk of code. For example, I could use the `pirateplot` function from `yarrr` package as follows:


```r
# Use the pirateplot() function without loading the yarrr package first
yarrr::pirateplot(formula = weight ~ Diet,
                  data = ChickWeight)
```

![](03-navigatingworkspace_files/figure-latex/unnamed-chunk-10-1.pdf)<!-- --> 


Again, you can think about the `package::function` method as a way to temporarily loading a package for a single line of code. One benefit of using the `package::function` notation is that it's immediately clear to anyone reading the code which package contains the function. However, a drawback is that if you are using a function from a package often, it forces you to constantly retype the package name. You can use whichever method makes sense for you.

## Learning check {-}


1. Create a folder called `se747` on your computer desktop.

2. Create a new project in the folder `se747`, click File -- New Project -- New Directory -- New Project -- Browse, sear for `se747` folder -- under Directory name, type `analysis`.

3. Create a new R script, click File -- New File -- R Script.

4. Save the new R script, click File -- Save As. Use the file name `new_script`. It will have the extension `.R`

5. Enter the code below into your new script, and save it. 


```r
a <- 10
a + 10
a
```

6. Close RStudio, reopen RStudio. In the Files tab on the bottom right, you should see the script you created `new_script.R`. Click on it to open and you should see the code you typed.

5. Create a new R notebook, click File -- New File -- R Notebook.

6. Save the new R notebook, click File -- Save As. Use the file name `practice`. It will have the extension `.Rmd`

7. Clear all the default comments after the headers and before the code chunk. Insert the code chunk below in the notebook and type a few comments before the code to remind you what you executed.


```r
if (!require("pacman")) install.packages("pacman")
pacman::p_load(tidyverse, # All purpose wrangling for dataframes
               readr, # importing and writing data
               openxlsx) # writing excel documents
```


8. Remember to save the notebook.





<!--chapter:end:03-navigatingworkspace.Rmd-->

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




<!--chapter:end:04-input_output.Rmd-->

---
output:
  html_document: default
  pdf_document: default
---

# (PART) Data manipulation via tidyverse {-} 

# Data manipulation

## Download and load libraries {-}


```r
if (!require("pacman")) install.packages("pacman")
pacman::p_load(tidyverse, # All purpose wrangling for dataframes
               readr, # importing and writing data
               openxlsx, # writing excel documents
               purrr, # for piping %>%
               corrplot, # for correlation
               knitr,
               yarrr)
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

## Data overview {-}

Design: This is a randomized controlled trial of two groups undergoing two strength training programs. Each subject was tested before and after training for their ankle and knee extensor strength variables.

Number of Subjects:32
Number of Groups: 2
Number of sides: 2
Number of repetitions: variable between 2 to 4

## Peeking at the Data

Let's take a look at the first 6 (by default) rows of data:


```r
head(subjdat) #look at the top rows
```

```
## # A tibble: 6 x 17
##    SUBJ GROUP   AGE    WT    HT   BMI `RunExp ` RunFreq6wks RunFreq12mths
##   <dbl> <chr> <dbl> <dbl> <dbl> <dbl>     <dbl>       <dbl>         <dbl>
## 1     1 G        29  82.3  182   24.8        10           3             3
## 2     2 G        34  42.3  161   16.3         5           2             2
## 3     3 T        36  90.5  166   32.8         3           5             3
## 4     4 G        42  82.8  183   24.7        10           1             1
## 5     5 T        28  66.3  169   23.2         5           5             4
## 6     6 T        34  72.8  172.  24.5        16           6             6
## # ... with 8 more variables: RunDistWkly6wks <dbl>, RunDistWkly12mths <dbl>,
## #   LoadRunExp <chr>, RunLoad <dbl>, HxLoad <chr>, WtTrainFreq6wks <dbl>,
## #   WtTrainFreq12mths <dbl>, WtTrainStatus <chr>
```

```r
tail (subjdat) #look at the bottom rows
```

```
## # A tibble: 6 x 17
##    SUBJ GROUP   AGE    WT    HT   BMI `RunExp ` RunFreq6wks RunFreq12mths
##   <dbl> <chr> <dbl> <dbl> <dbl> <dbl>     <dbl>       <dbl>         <dbl>
## 1    27 T        20  57.5  168.  20.4        10           4             3
## 2    28 T        26  62.8  157.  25.6         2           1             3
## 3    29 T        18  83.4  183.  24.8         3           3             4
## 4    30 G        29  83.9  178.  26.4        15           4             2
## 5    31 G        32  67.9  177   21.7         5           1             2
## 6    32 G        19  47.7  167   17.1        10           3             1
## # ... with 8 more variables: RunDistWkly6wks <dbl>, RunDistWkly12mths <dbl>,
## #   LoadRunExp <chr>, RunLoad <dbl>, HxLoad <chr>, WtTrainFreq6wks <dbl>,
## #   WtTrainFreq12mths <dbl>, WtTrainStatus <chr>
```

## Checking the number of rows and columns we have in our strength data

I like to do this first, as it is the most basic check - does the number columns and rows conform to the number of variables you entered and the number of observations measured.


```r
dimn <- dim(strn)

# Print the number 
cat ("The number of rows is:",  dimn[1], "\n")
```

```
## The number of rows is: 992
```

```r
cat ("The number of cols is:",  dimn[2], "\n")
```

```
## The number of cols is: 12
```

## Tidy data

You can represent the same underlying data in multiple ways. The example below shows the same data organised in four different ways. This dataset is **not the data you loaded**, but rather came with the `tidyverse package`. Each dataset shows the same values of four variables *country*, *year*, *population*, and *cases*, but each dataset organises the values in a different way.


```r
table1
```

```
## # A tibble: 6 x 4
##   country      year  cases population
##   <chr>       <int>  <int>      <int>
## 1 Afghanistan  1999    745   19987071
## 2 Afghanistan  2000   2666   20595360
## 3 Brazil       1999  37737  172006362
## 4 Brazil       2000  80488  174504898
## 5 China        1999 212258 1272915272
## 6 China        2000 213766 1280428583
```

```r
table2
```

```
## # A tibble: 12 x 4
##    country      year type            count
##    <chr>       <int> <chr>           <int>
##  1 Afghanistan  1999 cases             745
##  2 Afghanistan  1999 population   19987071
##  3 Afghanistan  2000 cases            2666
##  4 Afghanistan  2000 population   20595360
##  5 Brazil       1999 cases           37737
##  6 Brazil       1999 population  172006362
##  7 Brazil       2000 cases           80488
##  8 Brazil       2000 population  174504898
##  9 China        1999 cases          212258
## 10 China        1999 population 1272915272
## 11 China        2000 cases          213766
## 12 China        2000 population 1280428583
```

```r
table3
```

```
## # A tibble: 6 x 3
##   country      year rate             
## * <chr>       <int> <chr>            
## 1 Afghanistan  1999 745/19987071     
## 2 Afghanistan  2000 2666/20595360    
## 3 Brazil       1999 37737/172006362  
## 4 Brazil       2000 80488/174504898  
## 5 China        1999 212258/1272915272
## 6 China        2000 213766/1280428583
```

```r
# Spread across two tables
table4a  # cases
```

```
## # A tibble: 3 x 3
##   country     `1999` `2000`
## * <chr>        <int>  <int>
## 1 Afghanistan    745   2666
## 2 Brazil       37737  80488
## 3 China       212258 213766
```

```r
table4b  # population
```

```
## # A tibble: 3 x 3
##   country         `1999`     `2000`
## * <chr>            <int>      <int>
## 1 Afghanistan   19987071   20595360
## 2 Brazil       172006362  174504898
## 3 China       1272915272 1280428583
```

These are all representations of the same underlying data, but they are not equally easy to use. One dataset, the tidy dataset, will be much easier to work with. 

There are three interrelated rules which make a dataset tidy:

1.  Each variable must have its own column.
1.  Each observation must have its own row.
1.  Each value must have its own cell.

Figure \@ref(fig:tidy-structure) shows the rules visually.

\begin{figure}
\includegraphics[width=1\linewidth]{images/tidy-1} \caption{Following three rules makes a dataset tidy: variables are in columns, observations are in rows, and values are in cells.}(\#fig:tidy-structure)
\end{figure}

These three rules are interrelated because it's impossible to only satisfy two of the three. 

In this example, only `table1` is tidy. It's the only representation where each column is a variable.

Why ensure that your data is tidy? There are two main advantages:

1.  There's a general advantage to picking one consistent way of storing
    data. If you have a consistent data structure, it's easier to learn the
    tools that work with it because they have an underlying uniformity.
    
1.  There's a specific advantage to placing variables in columns because
    it allows R's vectorised nature to shine. As you learned in
    [mutate](#mutate-funs) and [summary functions](#summary-funs), most 
    built-in R functions work with vectors of values. That makes transforming 
    tidy data feel particularly natural.
    

Let's have a look at our data `strn` which is in a tidy format. **the "right" way**


```r
head(strn) #look at the top rows
```

```
##   SUBJ GROUP TIME SIDE SET REP AEXTTORQ AEXTWORK AEXTPOW KEXTTORQ KEXTWORK
## 1    1     G  PRE    R   1   1       70       34      58      111      107
## 2    1     G  PRE    R   1   2       72       36      70      137      113
## 3    1     G  PRE    R   1   3       73       37      67      160      130
## 4    1     G  PRE    R   1   4       73       35      69      137      115
## 5    1     G  PRE    R   2   1       72       36      65      160      140
## 6    1     G  PRE    R   2   2       72       32      51      163      139
##   KEXTPOW
## 1      92
## 2     139
## 3     136
## 4     121
## 5     164
## 6     165
```

## Spreading and gathering

The principles of tidy data seem so obvious that you might wonder if you'll ever encounter a dataset that isn't tidy. Unfortunately, however, most data that you will encounter will be untidy. There are two main reasons:

1.  Most people aren't familiar with the principles of tidy data, and it's hard
    to derive them yourself unless you spend a _lot_ of time working with data.
    
2.  Data is often organised to facilitate some use other than analysis. For 
    example, data is often organised to make entry as easy as possible.
    
This means for most real analyses, you'll need to do some tidying. The first step is always to figure out what the variables and observations are. Sometimes this is easy; other times you'll need to consult with the people who originally generated the data. 
The second step is to resolve one of two common problems:

1. One variable might be spread across multiple columns.

2. One observation might be scattered across multiple rows.

Typically a dataset will only suffer from one of these problems; it'll only suffer from both if you're really unlucky! To fix these problems, you'll need the two most important functions in tidyr: `gather()` and `spread()`.

### Spreading {-}

Let's make it wide. This is how you probably entered your data.


```r
wide <- strn %>% # original data
  unite ("time_side_set_rep", # give the new variable a name
         TIME, SIDE, SET, REP, # merged different columns of data into one
         sep = "_") %>% # choose a separator. I like "_"
  select (SUBJ, GROUP, time_side_set_rep, AEXTTORQ) %>% # choose columns which I want and discard the rest
  spread (key = time_side_set_rep, value = AEXTTORQ) # spread it

head (wide)
```

```
##   SUBJ GROUP POST_L_1_1 POST_L_1_2 POST_L_1_3 POST_L_1_4 POST_L_2_1 POST_L_2_2
## 1    1     G         73         79         78         76         79         81
## 2    2     G         60         56         58         61         57         60
## 3    3     T         72         75         76         68         74         64
## 4    4     G         90         95         94         89        104        100
## 5    5     T        100         93         91         98        101        106
## 6    6     T        109        115        113        102        109        117
##   POST_L_2_3 POST_L_2_4 POST_R_1_1 POST_R_1_2 POST_R_1_3 POST_R_1_4 POST_R_2_1
## 1         78         79         74         76         77         80         86
## 2         64         64         60         66         64         68         58
## 3         84         74         94         92         93         94         88
## 4        105        111         93         92         92         92        108
## 5        104        104         92         94         92         89         93
## 6        118        118        108        111        105        120        127
##   POST_R_2_2 POST_R_2_3 POST_R_2_4 PRE_L_1_1 PRE_L_1_2 PRE_L_1_3 PRE_L_1_4
## 1         88         89         85        66        59        66        63
## 2         62         62         62        41        44        42        41
## 3         87         86         88        55        45        54        58
## 4        107        104        106        58        60        57        58
## 5         87         92         85        62        64        57        57
## 6        120        120        121        84        88        80        78
##   PRE_L_2_1 PRE_L_2_2 PRE_L_2_3 PRE_L_2_4 PRE_R_1_1 PRE_R_1_2 PRE_R_1_3
## 1        64        72        66        67    70.000    72.000   73.0000
## 2        42        41        40        33    52.000    54.000   60.0000
## 3        54        56        53        52    57.000    64.000   65.0000
## 4        58        59        61        65    58.000    50.000   65.0000
## 5        70        68        69        71    68.132    65.249   67.9594
## 6        85        79        82        86    76.000   100.000   89.0000
##   PRE_R_1_4 PRE_R_2_1 PRE_R_2_2 PRE_R_2_3 PRE_R_2_4
## 1   73.0000   72.0000   72.0000    67.000   72.0000
## 2   56.0000   47.0000   47.0000    50.000   54.0000
## 3   62.0000   76.0000   75.0000    86.000   82.0000
## 4   71.0000   75.0000   65.0000    71.000   75.0000
## 5   63.5177   60.1266   58.8245    63.419   58.0649
## 6   90.0000   88.0000   80.0000    86.000   88.0000
```

### Gathering {-}

If your data is wide originally, make sure you have a very consistent labelling system. Then you can convert between formats easily.


Let's make it tall again. Converting messy data to tidy data. Why is it important to have a consistent naming terminology? It is a bad idea to use mathematical operators (e.g. "*", "-", "\") when naming, bad idea to have spaces when naming, and long names (e.g."ankle_kinematics_sagittal_plane").


```r
tall  <-  wide %>%
  gather (-c(1:2), # I want to gather all columns except the first two columns
          key = time_side_set_rep, # column name which contains the variable names
          value = AEXTTORQ) %>% # column name containing the values
  separate (time_side_set_rep, # split a long word in one column
            into = c("TIME", "SIDE", "SET", "REP"), sep = "_") # give it column names

head (tall)# see how I recreate the original data?
```

```
##   SUBJ GROUP TIME SIDE SET REP AEXTTORQ
## 1    1     G POST    L   1   1       73
## 2    2     G POST    L   1   1       60
## 3    3     T POST    L   1   1       72
## 4    4     G POST    L   1   1       90
## 5    5     T POST    L   1   1      100
## 6    6     T POST    L   1   1      109
```

## Renaming variables and values

### Rename variable names {-}

I dislike excessively using capitals. It is alot of effort.


```r
# Upper to lower caps
colnames (strn) <-  tolower(colnames (strn)) # captials to lower caps

# Manually create new names
strn <- strn %>%
  rename (atorq = aexttorq, # new name = old name
          awork = aextwork,
          apow = aextpow,
          ktorq = kexttorq,
          kwork = kextwork,
          kpow = kextpow)

head (strn)
```

```
##   subj group time side set rep atorq awork apow ktorq kwork kpow
## 1    1     G  PRE    R   1   1    70    34   58   111   107   92
## 2    1     G  PRE    R   1   2    72    36   70   137   113  139
## 3    1     G  PRE    R   1   3    73    37   67   160   130  136
## 4    1     G  PRE    R   1   4    73    35   69   137   115  121
## 5    1     G  PRE    R   2   1    72    36   65   160   140  164
## 6    1     G  PRE    R   2   2    72    32   51   163   139  165
```

### Rename values in variable names {-}

Let's us rename the values within the variable called GROUP. Instead of G, call it general; instead of T, call it target


```r
strn <- strn %>%
  mutate (group = recode (group, # the variable name
                          "G" = "general", # old label = new label
                          "T" = "target")) # old label = new label

head (strn)
```

```
##   subj   group time side set rep atorq awork apow ktorq kwork kpow
## 1    1 general  PRE    R   1   1    70    34   58   111   107   92
## 2    1 general  PRE    R   1   2    72    36   70   137   113  139
## 3    1 general  PRE    R   1   3    73    37   67   160   130  136
## 4    1 general  PRE    R   1   4    73    35   69   137   115  121
## 5    1 general  PRE    R   2   1    72    36   65   160   140  164
## 6    1 general  PRE    R   2   2    72    32   51   163   139  165
```


### Creating factors {-}

Since R can handle factor variables (see `?factor`), we can recode the levels to be more intuitive. Why do you need to convert categorical variables to factors? For now, let's accept it, for every statistical thing you do with categorical variables must be factors.

Make group, time, side, a factor


```r
strn <-  strn %>%
  mutate (group = factor (group, levels = c("general", "target")), # levels = c(first, second)
          time = factor (time, levels = c("PRE", "POST")),
          side = factor (side, levels = c("L", "R")))

head (strn)
```

```
##   subj   group time side set rep atorq awork apow ktorq kwork kpow
## 1    1 general  PRE    R   1   1    70    34   58   111   107   92
## 2    1 general  PRE    R   1   2    72    36   70   137   113  139
## 3    1 general  PRE    R   1   3    73    37   67   160   130  136
## 4    1 general  PRE    R   1   4    73    35   69   137   115  121
## 5    1 general  PRE    R   2   1    72    36   65   160   140  164
## 6    1 general  PRE    R   2   2    72    32   51   163   139  165
```

## Making a new variable

I want to:

1. add ankle torque and knee torque to create a new variable called total torque
2. subtract their torques to create a variable called dtorq


```r
strn <-  strn %>%
  mutate (ttorq = atorq + ktorq, # this will add a new variable called ttorq
          dtorq = atorq - ktorq) # this will add a new variable called dtorq
head (strn)
```

```
##   subj   group time side set rep atorq awork apow ktorq kwork kpow ttorq dtorq
## 1    1 general  PRE    R   1   1    70    34   58   111   107   92   181   -41
## 2    1 general  PRE    R   1   2    72    36   70   137   113  139   209   -65
## 3    1 general  PRE    R   1   3    73    37   67   160   130  136   233   -87
## 4    1 general  PRE    R   1   4    73    35   69   137   115  121   210   -64
## 5    1 general  PRE    R   2   1    72    36   65   160   140  164   232   -88
## 6    1 general  PRE    R   2   2    72    32   51   163   139  165   235   -91
```


You are only interested in the change scores of each subject's average strength


```r
strn_change <-  strn %>% # original data
  group_by(subj, group, time) %>% # calculate an outcome per group
  summarize (atorq = mean (atorq)) %>% # in this case you want to calculate average
  spread (key = time, value = atorq) %>% # spread it
  mutate (atorq_diff = POST-PRE)  %>% # find the difference
  ungroup ()
```

```
## `summarise()` regrouping output by 'subj', 'group' (override with `.groups` argument)
```

```r
head (strn)
```

```
##   subj   group time side set rep atorq awork apow ktorq kwork kpow ttorq dtorq
## 1    1 general  PRE    R   1   1    70    34   58   111   107   92   181   -41
## 2    1 general  PRE    R   1   2    72    36   70   137   113  139   209   -65
## 3    1 general  PRE    R   1   3    73    37   67   160   130  136   233   -87
## 4    1 general  PRE    R   1   4    73    35   69   137   115  121   210   -64
## 5    1 general  PRE    R   2   1    72    36   65   160   140  164   232   -88
## 6    1 general  PRE    R   2   2    72    32   51   163   139  165   235   -91
```

## Transforming a variable

The subject's mass is stored in another file called `subjdat`. we need to merge two documents making sure each row is joined correctly.


```r
# convert names to lower cases
colnames (subjdat)  <-  tolower (colnames (subjdat))

# create another object, keeping only two variables of 
subj_mass <-  select (subjdat, # original dataframe
                      subj, wt) # two variables

# 
strn_scal <-  subj_mass %>%
  inner_join(strn, by = "subj") %>% # combine two dataframes, ensuring each rows are combined exactly
  mutate (ttorq_s = ttorq/wt, # divide total torque by weight
          dtorq_s = dtorq/wt) # divide difference torque by weight

head (strn_scal)
```

```
## # A tibble: 6 x 17
##    subj    wt group  time  side    set   rep atorq awork  apow ktorq kwork  kpow
##   <dbl> <dbl> <fct>  <fct> <fct> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl>
## 1     1  82.3 gener~ PRE   R         1     1    70    34    58   111   107    92
## 2     1  82.3 gener~ PRE   R         1     2    72    36    70   137   113   139
## 3     1  82.3 gener~ PRE   R         1     3    73    37    67   160   130   136
## 4     1  82.3 gener~ PRE   R         1     4    73    35    69   137   115   121
## 5     1  82.3 gener~ PRE   R         2     1    72    36    65   160   140   164
## 6     1  82.3 gener~ PRE   R         2     2    72    32    51   163   139   165
## # ... with 4 more variables: ttorq <dbl>, dtorq <dbl>, ttorq_s <dbl>,
## #   dtorq_s <dbl>
```


## Filtering 

Filtering is removing rows you do not want and keeping rows you want based on some condition(s).

### Keep rows based on category you wish to keep

You are only interested in keeping pre strength variables


```r
strn_pre <-  strn %>%
      filter (time == "PRE")

head (strn_pre)
```

```
##   subj   group time side set rep atorq awork apow ktorq kwork kpow ttorq dtorq
## 1    1 general  PRE    R   1   1    70    34   58   111   107   92   181   -41
## 2    1 general  PRE    R   1   2    72    36   70   137   113  139   209   -65
## 3    1 general  PRE    R   1   3    73    37   67   160   130  136   233   -87
## 4    1 general  PRE    R   1   4    73    35   69   137   115  121   210   -64
## 5    1 general  PRE    R   2   1    72    36   65   160   140  164   232   -88
## 6    1 general  PRE    R   2   2    72    32   51   163   139  165   235   -91
```

### Include rows based on a numerical range

Keep ankle torque values less than 100 in magnitude and knee torque more than 150


```r
strn_filt <-  strn %>%
      filter (atorq < 100 & ktorq > 150)

head (strn_filt)
```

```
##   subj   group time side set rep atorq awork apow ktorq kwork kpow ttorq dtorq
## 1    1 general  PRE    R   1   3    73    37   67   160   130  136   233   -87
## 2    1 general  PRE    R   2   1    72    36   65   160   140  164   232   -88
## 3    1 general  PRE    R   2   2    72    32   51   163   139  165   235   -91
## 4    1 general  PRE    R   2   3    67    34   63   157   133  155   224   -90
## 5    1 general  PRE    R   2   4    72    36   66   165   145  158   237   -93
## 6    1 general  PRE    L   2   1    64    33   63   170   168  165   234  -106
```

### Exclude rows variables based on a numerical range

Exclude ankle torque values less than 100 


```r
# notice the !. It is equivalent to saying "not". Not less than 100 in this instance

strn_filt <-  strn %>%
      filter (!atorq < 100) 

head (strn_filt)
```

```
##   subj   group time side set rep atorq awork apow ktorq kwork kpow ttorq dtorq
## 1    4 general POST    R   2   1   108    50   76   182   194  177   290   -74
## 2    4 general POST    R   2   2   107    49   79   179   182  185   286   -72
## 3    4 general POST    R   2   3   104    44   74   169   180  175   273   -65
## 4    4 general POST    R   2   4   106    49   86   176   185  173   282   -70
## 5    4 general POST    L   2   1   104    50   95   138   166  141   242   -34
## 6    4 general POST    L   2   2   100    48   98   141   158  145   241   -41
```

## Selecting

Selecting removing columns you do not want and keeping columns you want

You are only interested in keeping columns `subj`, `group` in dataframe `strn` 


```r
strn.subset <-  strn %>%
      select (subj, group)

head (strn.subset)
```

```
##   subj   group
## 1    1 general
## 2    1 general
## 3    1 general
## 4    1 general
## 5    1 general
## 6    1 general
```


## Check for missing NA values 

### Check if there is any missing


```r
na_count <-  sum (is.na (strn))

cat ("The number of missing values =", na_count)
```

```
## The number of missing values = 0
```

For the sick of practice, let me create a dataset with NA in each. You do not have to know this. 


```r
strn.miss <- strn

strn.miss[,c(7:14)] <-  map_df(strn.miss [,c(7:14)],
                               function(x) {x[sample(c(TRUE, NA), 
                                                     prob = c(0.9, 0.1), 
                                                     size = length(x),
                                                     replace = TRUE)]})

strn.miss [100,c(7:14)] = NA

na_count = sum (is.na (strn.miss))

cat ("The number of missing values is now =", na_count)
```

```
## The number of missing values is now = 854
```

### Find the number of missing values per column


```r
na_count <-  strn.miss %>%
  select(everything()) %>%  # replace to your needs
  summarise_all(funs(sum(is.na(.))))
```

```
## Warning: `funs()` is deprecated as of dplyr 0.8.0.
## Please use a list of either functions or lambdas: 
## 
##   # Simple named list: 
##   list(mean = mean, median = median)
## 
##   # Auto named with `tibble::lst()`: 
##   tibble::lst(mean, median)
## 
##   # Using lambdas
##   list(~ mean(., trim = .2), ~ median(., na.rm = TRUE))
## This warning is displayed once every 8 hours.
## Call `lifecycle::last_warnings()` to see where this warning was generated.
```

```r
kable (na_count, caption = "Number of missing per col") 
```

\begin{table}

\caption{(\#tab:unnamed-chunk-18)Number of missing per col}
\centering
\begin{tabular}[t]{r|r|r|r|r|r|r|r|r|r|r|r|r|r}
\hline
subj & group & time & side & set & rep & atorq & awork & apow & ktorq & kwork & kpow & ttorq & dtorq\\
\hline
0 & 0 & 0 & 0 & 0 & 0 & 103 & 108 & 92 & 102 & 125 & 100 & 111 & 113\\
\hline
\end{tabular}
\end{table}

### Keep rows with 100% no NA across any columns


```r
strn_compl <-  strn.miss %>%
  na.omit ()
```

### Keep rows with 100% no NA across the columns you want 


```r
col2filt = c("atorq", "ktorq") # add as many variables you want

strn_compl <-  strn.miss %>%
  filter_at(vars(col2filt), all_vars(complete.cases(.)))
```

```
## Note: Using an external vector in selections is ambiguous.
## i Use `all_of(col2filt)` instead of `col2filt` to silence this message.
## i See <https://tidyselect.r-lib.org/reference/faq-external-vector.html>.
## This message is displayed once per session.
```

```r
head (strn_compl)
```

```
##   subj   group time side set rep atorq awork apow ktorq kwork kpow ttorq dtorq
## 1    1 general  PRE    R   1   1    70    34   58   111    NA   NA   181   -41
## 2    1 general  PRE    R   1   3    73    NA   67   160   130  136   233   -87
## 3    1 general  PRE    R   1   4    73    35   69   137   115  121   210   -64
## 4    1 general  PRE    R   2   1    72    NA   65   160   140  164   232   -88
## 5    1 general  PRE    R   2   2    72    NA   51   163   139  165   235   -91
## 6    1 general  PRE    R   2   3    67    34   63   157   133  155   224   -90
```

### Keep rows **with** NA across columns you want. 

Keeping NA is useful if you want to inspect if the missing-ness is due to data entry errors, etc...


```r
col2filt = c("atorq", "ktorq") # add as many variables you want

strn_miss <-  strn.miss %>%
  filter_at(vars(col2filt), all_vars(!complete.cases(.))) 

head (strn_miss)
```

```
##   subj   group time side set rep atorq awork apow ktorq kwork kpow ttorq dtorq
## 1    1 general POST    L   2   3    NA    41   NA    NA   164   NA   224   -68
## 2    4 general  PRE    R   1   4    NA    NA   NA    NA    NA   NA    NA    NA
## 3    7 general  PRE    R   2   4    NA    36   75    NA   120  129   201    NA
## 4   17 general POST    L   2   1    NA    36   71    NA    91   86   162   -18
## 5   26 general POST    L   2   1    NA    44   91    NA   126  134    NA   -45
## 6   27  target POST    L   2   1    NA    40   76    NA    NA  153   208   -50
```

## Learning check {-}


1. Open up your `practice.Rmd`. Run the code chunks you created in sequential order.

2. Create a code chunk and open up the three files above into the R workspace. Subsequently, any task should automatically be associated with creating a new code chunk. If unsure, have more chunks.

3. Make all column header names to lowercases. 

4. Remove `aexttorq` values that are below 75, and assign this new data to an object called `strn.sub`. How many rows are left in the new dataframe.


<!--chapter:end:05-data_manipulation.Rmd-->

---
output:
  html_document: default
  pdf_document: default
---


# General statistics

## Download and load libraries {-}


```r
if (!require("pacman")) install.packages("pacman")
pacman::p_load(tidyverse, # All purpose wrangling for dataframes
               readr, # importing and writing data
               openxlsx, # writing excel documents
               purrr, # for piping %>%
               corrplot, # for correlation
               knitr,
               yarrr)
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


## Summarizing your data

The Solution exhibits the summary of a vector. The `1st Qu.` and `3rd Qu.` are the first and third quartile, respectively. Having both the median and mean is useful because you can
quickly detect skew. 


```r
# Quick way
summary (strn)
```

```
##       subj          group               time               side          
##  Min.   : 1.00   Length:992         Length:992         Length:992        
##  1st Qu.: 8.00   Class :character   Class :character   Class :character  
##  Median :17.00   Mode  :character   Mode  :character   Mode  :character  
##  Mean   :16.61                                                           
##  3rd Qu.:25.00                                                           
##  Max.   :32.00                                                           
##       set           rep           atorq            awork            apow       
##  Min.   :1.0   Min.   :1.00   Min.   : 33.00   Min.   :17.00   Min.   : 18.00  
##  1st Qu.:1.0   1st Qu.:1.75   1st Qu.: 67.00   1st Qu.:32.00   1st Qu.: 60.51  
##  Median :1.5   Median :2.50   Median : 82.00   Median :39.00   Median : 74.50  
##  Mean   :1.5   Mean   :2.50   Mean   : 83.94   Mean   :40.03   Mean   : 76.01  
##  3rd Qu.:2.0   3rd Qu.:3.25   3rd Qu.: 99.00   3rd Qu.:47.00   3rd Qu.: 90.00  
##  Max.   :2.0   Max.   :4.00   Max.   :145.00   Max.   :72.00   Max.   :151.00  
##      ktorq           kwork            kpow      
##  Min.   : 75.0   Min.   : 78.0   Min.   : 24.0  
##  1st Qu.:120.8   1st Qu.:124.0   1st Qu.:106.0  
##  Median :146.0   Median :145.0   Median :134.0  
##  Mean   :150.2   Mean   :151.8   Mean   :135.8  
##  3rd Qu.:175.0   3rd Qu.:172.0   3rd Qu.:165.0  
##  Max.   :322.0   Max.   :324.0   Max.   :328.0
```

```r
# Tidy way

strn %>%
  summarize (Mean = mean (atorq, na.rm = T),
             Median = median (atorq, na.rm = T),
             Max = max (atorq, na.rm = T),
             Min = min (atorq, na.rm = T),
             Sd = sd (atorq, na.rm = T),
             Iqr = IQR (atorq, na.rm = T),
             quant25 = quantile (atorq, probs = 0.25, na.rm = T),
             quant75 = quantile (atorq, probs = 0.75, na.rm = T))
```

```
##       Mean Median Max Min       Sd Iqr quant25 quant75
## 1 83.94082     82 145  33 22.23734  32      67      99
```

## Finding the correlation between variables 

Applicable only to numeric variables, e.g. between height and weight


```r
M <- cor(strn[, c(7:12)]) # if you are interested in correlation between columns 7 to 9, change it to [7:9]
corrplot(M, method="circle")
```

![](06-general_statistics_files/figure-latex/unnamed-chunk-5-1.pdf)<!-- --> 

```r
M
```

```
##           atorq     awork      apow     ktorq     kwork      kpow
## atorq 1.0000000 0.9774470 0.8962872 0.6178820 0.5823672 0.3975232
## awork 0.9774470 1.0000000 0.8920214 0.5954282 0.5573902 0.3642013
## apow  0.8962872 0.8920214 1.0000000 0.5554066 0.5152769 0.3254336
## ktorq 0.6178820 0.5954282 0.5554066 1.0000000 0.9524378 0.7824349
## kwork 0.5823672 0.5573902 0.5152769 0.9524378 1.0000000 0.8075578
## kpow  0.3975232 0.3642013 0.3254336 0.7824349 0.8075578 1.0000000
```

## Summarizing your data at a group level

If you have two or more groups per variable, and multiple variables, and you want a summary at each combination of factors.


```r
# grouped summaries
strn %>%
  group_by(group, time) %>%
  summarize (Mean = mean (atorq, na.rm = T),
             Median = median (atorq, na.rm = T),
             Max = max (atorq, na.rm = T),
             Min = min (atorq, na.rm = T),
             Sd = sd (atorq, na.rm = T),
             Iqr = IQR (atorq, na.rm = T),
             quant25 = quantile (atorq, probs = 0.25, na.rm = T),
             quant75 = quantile (atorq, probs = 0.75, na.rm = T))
```

```
## `summarise()` regrouping output by 'group' (override with `.groups` argument)
```

```
## # A tibble: 4 x 10
## # Groups:   group [2]
##   group time   Mean Median   Max   Min    Sd   Iqr quant25 quant75
##   <chr> <chr> <dbl>  <dbl> <dbl> <dbl> <dbl> <dbl>   <dbl>   <dbl>
## 1 G     POST   95.4   95     145    56  19.8  26.2    80      106.
## 2 G     PRE    72.7   70.5   122    33  17.0  21      61       82 
## 3 T     POST   92.8   91.5   140    45  23.1  32.5    77.8    110.
## 4 T     PRE    74.9   76     124    33  18.7  26.2    60.8     87
```

## Testing the Mean of a Sample (t Test)

You have a sample from a population. Given this sample, you want to know
if the mean of the population could reasonably be a particular value *m*.

Apply the `t.test` function to the sample *x* with the argument `mu = m`:


```r
m <- 50

t.test(x = strn$atorq, # data$variable_name
       mu = m)
```

The output includes a *p*-value. Conventionally, if *p* &lt; 0.05 then
the population mean is unlikely to be *m*, whereas *p* &gt; 0.05 provides
no such evidence.

If your sample size *n* is small, then the underlying population must be
normally distributed in order to derive meaningful results from the *t*
test. A good rule of thumb is that “small” means *n* &lt; 30.


The *t* test is a workhorse of statistics, and this is one of its basic
uses: making inferences about a population mean from a sample. The
following example simulates sampling from a normal population with mean
*μ* = 100. It uses the *t* test to ask if the population mean could be
95, and `t.test` reports a *p*-value of 0.005:


```r
x <- rnorm(75, mean = 100, sd = 15)
t.test(x, mu = 95)
```

```
## 
## 	One Sample t-test
## 
## data:  x
## t = 2.9576, df = 74, p-value = 0.004159
## alternative hypothesis: true mean is not equal to 95
## 95 percent confidence interval:
##   96.86608 104.57155
## sample estimates:
## mean of x 
##  100.7188
```

The *p*-value is small and so it’s unlikely (based on the sample data)
that 95 could be the mean of the population.

Informally, we could interpret the low *p*-value as follows. If the
population mean were really 95, then the probability of observing our
test statistic (*t* = 2.8898 or something more extreme) would be only
0.005. That is very improbable, yet that is the value we observed.
Hence we conclude that the null hypothesis is wrong; therefore, the
sample data does not support the claim that the population mean is 95.

In sharp contrast, testing for a mean of 100 gives a *p*-value of
0.9:


```r
t.test(x, mu = 100)
```

```
## 
## 	One Sample t-test
## 
## data:  x
## t = 0.37176, df = 74, p-value = 0.7111
## alternative hypothesis: true mean is not equal to 100
## 95 percent confidence interval:
##   96.86608 104.57155
## sample estimates:
## mean of x 
##  100.7188
```

The large *p*-value indicates that the sample is consistent with
assuming a population mean *μ* of 100. In statistical terms, the data
does not provide evidence against the true mean being 100.

A common case is testing for a mean of zero. If you omit the `mu`
argument, it defaults to zero.


## Comparing the Means of Two Samples 

You have one sample each from two populations. You want to know if the
two populations could have the same mean.

Perform a *t* test by calling the `t.test` function:


```r
# Fictitious data
x <- rnorm(100, mean = 0, sd = 1)
y <- rnorm(100, mean = 0, sd = 2)

t.test(x, y)
```

By default, `t.test` assumes that your data are not paired. If the
observations are paired (i.e., if each *x~i~* is paired with one
*y~i~*), then specify `paired=TRUE`:


```r
t.test(x, y, paired = TRUE)
```

In either case, `t.test` will compute a *p*-value. Conventionally, if
*p* &lt; 0.05 then the means are likely different, whereas *p* &gt; 0.05
provides no such evidence:

-   If either sample size is small, then the populations must be
    normally distributed. Here, “small” means fewer than 20 data points.

-   If the two populations have the same variance, specify
    `var.equal=TRUE` to obtain a less conservative test.


We often use the *t* test to get a quick sense of the difference between
two population means. It requires that the samples be large enough (i.e., both
samples have 20 or more observations) or that the underlying populations
be normally distributed. We don’t take the “normally distributed” part
too literally. Being bell-shaped and reasonably symmetrical should be good enough.

A key distinction here is whether or not your data contains paired
observations, since the results may differ in the two cases. Suppose we
want to know if coffee in the morning improves scores on SATs. We
could run the experiment two ways:

*  Randomly select one group of people. Give them the SAT twice,
    once with morning coffee and once without morning coffee. For each
    person, we will have two SAT scores. These are paired observations.

*  Randomly select two groups of people. One group has a cup of morning
    coffee and takes the SAT. The other group just takes the test.
    We have a score for each person, but the scores are not paired in
    any way.

Statistically, these experiments are quite different. In experiment 1,
there are two observations for each person (caffeinated and decaf) and
they are not statistically independent. In experiment 2, the data are
independent.

If you have paired observations (experiment 1) and erroneously analyze
them as unpaired observations (experiment 2), then you could get this
result with a *p*-value of 0.3:


```r
load("data/sat.rdata")
t.test(x, y)
```

```
## 
## 	Welch Two Sample t-test
## 
## data:  x and y
## t = -0.95364, df = 197.97, p-value = 0.3414
## alternative hypothesis: true difference in means is not equal to 0
## 95 percent confidence interval:
##  -46.42359  16.15942
## sample estimates:
## mean of x mean of y 
##  1053.733  1068.865
```

The large *p*-value forces you to conclude there is no difference
between the groups. Contrast that result with the one that follows from
analyzing the same data but correctly identifying it as paired:


```r
t.test(x, y, paired = TRUE)
```

```
## 
## 	Paired t-test
## 
## data:  x and y
## t = -18.08, df = 99, p-value < 2.2e-16
## alternative hypothesis: true difference in means is not equal to 0
## 95 percent confidence interval:
##  -16.79278 -13.47139
## sample estimates:
## mean of the differences 
##               -15.13208
```

The *p*-value plummets to 2e-16, and we reach the exactly opposite
conclusion.


## Comparing the means of Two Samples Nonparametrically 

If the populations are not normally distributed (bell-shaped) and either
sample is small, consider using the Wilcoxon–Mann–Whitney test.

You have samples from two populations. You don’t know the distribution
of the populations, but you know they have similar means. You want to
know: Is one population's mean different from the other?

You can use a nonparametric test, the Wilcoxon–Mann–Whitney test, which
is implemented by the `wilcox.test` function. For paired observations
(every *x*~*i*~ is paired with *y*~*i*~), set `paired=TRUE`:


```
## 
## 	Wilcoxon signed rank test
## 
## data:  x and y
## V = 169, p-value = 0.1981
## alternative hypothesis: true location shift is not equal to 0
```

For unpaired observations, let `paired` default to `FALSE`:




```r
wilcox.test(x, y, FALSE)
```

The test output includes a *p*-value. Conventionally, a *p*-value of
less than 0.05 indicates that the second population is different with respect to the first population, whereas a *p*-value exceeding 0.05 provides no such evidence.

When we stop making assumptions regarding the distributions of
populations, we enter the world of nonparametric statistics. The
Wilcoxon–Mann–Whitney test is nonparametric and so can be applied to
more datasets than the *t* test, which requires that the data be
normally distributed (for small samples). This test’s only assumption is
that the two populations have the same shape.

In this recipe, we are asking: Is the second population shifted left or
right with respect to the first? This is similar to asking whether the
average of the second population is smaller or larger than the first.
However, the Wilcoxon–Mann–Whitney test answers a different question: it
tells us whether the central locations of the two populations are
significantly different or, equivalently, whether their relative
frequencies are different.

## Learning check {-}

1. Open up your `practice.Rmd`. Run the code chunks you created in sequential order.

2. Quickly generate a simple summary of the `strn` data using the `summary ()` function. 

3. Calculate the mean and standard deviation values of `aexttorq` per `group` per `time`, and assign this values to an object name `summ`.

<!--chapter:end:06-general_statistics.Rmd-->

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






<!--chapter:end:07-visualization.Rmd-->

# (PART) Statistical Inference via infer {-} 

# Sampling {#sampling}

Chapter \@ref(sampling), \@ref(confidence-intervals), \@ref(hypothesis-testing), are taken from the online book below, which I highly recommend:

| Book| Description|
|:----------------------------|:-----------------------------------|
|     [ModernDive. Statistical Inference via Data Science by Chester Ismay and Albert Kim] (https://moderndive.com/)|

In this chapter, we kick off this book on statistical inference by learning about *sampling*. The concepts behind sampling form the basis of confidence intervals and hypothesis testing, which we'll cover in Chapters \@ref(confidence-intervals) and \@ref(hypothesis-testing). We will see that the tools that you learned in the data science portion of this book, in particular data visualization and data wrangling, will also play an important role in the development of your understanding.  As mentioned before, the concepts throughout this text all build into a culmination allowing you to "tell the story with data." 


### Needed packages {-}


```r
if (!require("pacman")) install.packages("pacman")
pacman::p_load(tidyverse, # All purpose wrangling for dataframes
               readr, # importing and writing data
               openxlsx, # writing excel documents
               purrr, # for piping %>%
               corrplot, # for correlation
               knitr,
               moderndive,
               kableExtra,
               cowplot)
```


## Sampling bowl activity {#sampling-activity}

Let's start with a hands-on activity.

### What proportion of this bowl's balls are red?

Take a look at the bowl in Figure \@ref(fig:sampling-exercise-1). It has a certain number of red and a certain number of white balls all of equal size. Furthermore, it appears the bowl has been mixed beforehand, as there does not seem to be any coherent pattern to the spatial distribution of the red and white balls. 

Let's now ask ourselves, what proportion of this bowl's balls are red?

\begin{figure}
\includegraphics[width=0.8\linewidth]{images/sampling/balls/sampling_bowl_1} \caption{A bowl with red and white balls.}(\#fig:sampling-exercise-1)
\end{figure}

One way to answer this question would be to perform an exhaustive count: remove each ball individually, count the number of red balls and the number of white balls, and divide the number of red balls by the total number of balls. However, this would be a long and tedious process. 

### Using the shovel once 

Instead of performing an exhaustive count, let's insert a shovel into the bowl as seen in Figure \@ref(fig:sampling-exercise-2). Using the shovel let's remove 5 $\times$ 10 = 50 balls, as seen in Figure \@ref(fig:sampling-exercise-3).

\begin{figure}
\includegraphics[width=0.8\linewidth]{images/sampling/balls/sampling_bowl_2} \caption{Inserting a shovel into the bowl.}(\#fig:sampling-exercise-2)
\end{figure}


\begin{figure}
\includegraphics[width=0.8\linewidth]{images/sampling/balls/sampling_bowl_3_cropped} \caption{Fifty balls from the bowl.}(\#fig:sampling-exercise-3)
\end{figure}

Observe that 17 of the balls are red and thus 0.34 = 34% of the shovel's balls are red. We can view the proportion of balls that are red in this shovel as a guess of the proportion of balls that are red in the entire bowl. While not as exact as doing an exhaustive count of all the balls in the bowl, our guess of 34% took much less time and energy to make. 

However, say, we started this activity over from the beginning. In other words, we replace the 50 balls back into the bowl and start over. Would we remove exactly 17 red balls again? In other words, would our guess at the proportion of the bowl's balls that are red be exactly 34% again? Maybe? 

What if we repeated this activity several times? Would we obtain exactly 17 red balls each time? In other words, would our guess at the proportion of the bowl's balls that are red be exactly 34% every time? Surely not. Let's repeat this exercise several times with the help of 33 groups of friends to understand how the value differs with repetition.

### Using the shovel 33 times {#student-shovels}

Each of our 33 groups of friends will do the following: 

- Use the shovel to remove 50 balls each. 
- Count the number of red balls and thus compute the proportion of the 50 balls that are red.
- Return the balls into the bowl.
- Mix the contents of the bowl a little to not let a previous group's results influence the next group's. 

\begin{figure}
\includegraphics[width=0.3\linewidth]{images/sampling/balls/tactile_2_a} \includegraphics[width=0.3\linewidth]{images/sampling/balls/tactile_2_b} \includegraphics[width=0.3\linewidth]{images/sampling/balls/tactile_2_c} \caption{Repeating sampling activity 33 times.}(\#fig:sampling-exercise-3b)
\end{figure}

Before returning the balls into the bowl, each of our 33 groups of friends are going to mark their proportion of the 50 balls that were red in a hand-drawn histogram as seen in Figure \@ref(fig:sampling-exercise-4).

\begin{figure}
\includegraphics[width=0.8\linewidth]{images/sampling/balls/tactile_3_a} \caption{Constructing a histogram of proportions.}(\#fig:sampling-exercise-4)
\end{figure}

Histograms allow us to visualize the *distribution* \index{distribution} of a numerical variable. In particular, where the center of the values falls and how the values vary. A partially completed histogram of the first 10 out of 33 groups of friends' results can be seen in Figure \@ref(fig:sampling-exercise-5).

\begin{figure}
\includegraphics[width=0.8\linewidth]{images/sampling/balls/tactile_3_c} \caption{Hand-drawn histogram of first 10 out of 33 proportions.}(\#fig:sampling-exercise-5)
\end{figure}

Observe the following in the histogram in Figure \@ref(fig:sampling-exercise-5):

* At the low end, one group removed 50 balls from the bowl with proportion between 0.20 and 0.25.
* At the high end, another group removed 50 balls from the bowl with proportion between 0.45 and 0.5 red.
* However the most frequently occurring proportions were between 0.30 and 0.35 red, right in the middle of the distribution.
* The shape of this distribution is somewhat bell-shaped. 

Let's construct this same hand-drawn histogram in R using your data visualization skills that you honed. We saved our 33 groups of friends' results in a data frame `tactile_prop_red` included in the `moderndive` package. Run the following to display the first 10 of 33 rows:


```r
tactile_prop_red
```

```
## # A tibble: 33 x 4
##    group            replicate red_balls prop_red
##    <chr>                <int>     <int>    <dbl>
##  1 Ilyas, Yohan             1        21     0.42
##  2 Morgan, Terrance         2        17     0.34
##  3 Martin, Thomas           3        21     0.42
##  4 Clark, Frank             4        21     0.42
##  5 Riddhi, Karina           5        18     0.36
##  6 Andrew, Tyler            6        19     0.38
##  7 Julia                    7        19     0.38
##  8 Rachel, Lauren           8        11     0.22
##  9 Daniel, Caroline         9        15     0.3 
## 10 Josh, Maeve             10        17     0.34
## # ... with 23 more rows
```

Observe for each `group` that we have their names, the number of `red_balls` they obtained, and the corresponding proportion out of 50 balls that were red named `prop_red`. We also have a variable `replicate` enumerating each of the 33 groups; we chose this name because each row can be viewed as one instance of a replicated (in other words repeated) activity: using the shovel to remove 50 balls and computing the proportion of those balls that are red. 

Let's visualize the distribution of these 33 proportions using a `geom_histogram()` with `binwidth = 0.05` in Figure \@ref(fig:samplingdistribution-tactile). This is a computerized and complete version of the partially completed hand-drawn histogram you saw in Figure \@ref(fig:sampling-exercise-5). 


```r
ggplot(tactile_prop_red, aes(x = prop_red)) +
  geom_histogram(binwidth = 0.05, boundary = 0.4, color = "white") +
  labs(x = "Proportion of 50 balls that were red", 
       title = "Distribution of 33 proportions red") 
```
![(\#fig:samplingdistribution-tactile)Distribution of 33 proportions based on 33 samples of size 50.](08-sampling_files/figure-latex/samplingdistribution-tactile-1.pdf) 

### What did we just do?

What we just demonstrated in this activity is the statistical concept of \index{sampling} *sampling*. We would like to know the proportion of the bowl's balls that are red. However, because the bowl has a very large number of balls, performing an exhaustive count of the red and white balls would be very time-consuming. We therefore extracted a *sample* of 50 balls using the shovel to make an *estimate*. Using this sample of 50 balls, we estimated the proportion of the *bowl's* balls that are red to be 34%.

Moreover, because we mixed the balls before each use of the shovel, the samples were randomly drawn. Because each sample was drawn at random, the samples were different from each other. Because the samples were different from each other, we obtained the different proportions red observed in Figure \@ref(fig:samplingdistribution-tactile). This is known as the concept of *sampling variation*. \index{sampling!variation}

The purpose of this sampling activity was to develop an understanding of two key concepts relating to sampling: 

1. Understanding the effect of sampling variation.
1. Understanding the effect of sample size on sampling variation. 

In Section \@ref(sampling-simulation), we'll mimic the hands-on sampling activity we just performed on a computer. This will allow us not only to repeat the sampling exercise much more than 33 times, but it will also allow us to use shovels with different numbers of slots than just 50. 

Afterwards, we'll present you with definitions, terminology, and notation related to sampling in Section \@ref(sampling-framework). As in many disciplines, such necessary background knowledge may seem very inaccessible and even confusing at first. However, as with many difficult topics, if you truly understand the underlying concepts and practice, practice, practice, you'll be able to master them.

To tie the contents of this chapter to the real-word, we'll present an example of one of the most recognizable uses of sampling: polls. In Section \@ref(sampling-case-study) we'll look at a particular case study: a 2013 poll on then U.S. President Obama's popularity among young Americans, conducted by the Harvard Kennedy School's Institute of Politics.

To close this chapter we'll generalize the previous "sampling from a bowl" exercise to other sampling scenarios, present an important theoretical result known as the *Central Limit Theorem*, and present a few mathematical formulas related to sampling.


## Virtual sampling {#sampling-simulation}

In the previous Section \@ref(sampling-activity), we performed a *tactile* sampling activity by hand. In other words, we used a physical bowl of balls and a physical shovel. We performed this sampling activity by hand first so that we develop a firm understanding of the root ideas behind sampling. In this section, we'll mimic this tactile sampling activity with a *virtual* sampling activity using a computer. In other words, we'll use a virtual analog to the bowl of balls and a virtual analog to the shovel. 


### Using the virtual shovel once

Let's start by performing the virtual analog of the tactile sampling exercise we performed in Section \@ref(sampling-activity). We first need a virtual analog of the bowl seen in Figure \@ref(fig:sampling-exercise-1). To this end, we included a data frame `bowl` in the `moderndive` package. The rows of `bowl` correspond exactly with the contents of the actual bowl. 


```r
bowl
```

```
## # A tibble: 2,400 x 2
##    ball_ID color
##      <int> <chr>
##  1       1 white
##  2       2 white
##  3       3 white
##  4       4 red  
##  5       5 white
##  6       6 white
##  7       7 red  
##  8       8 white
##  9       9 red  
## 10      10 white
## # ... with 2,390 more rows
```

Observe that `bowl` has 2400 rows, telling us that the bowl contains 2400 equally-sized balls. The first variable `ball_ID` is used as an *identification variable*; none of the balls in the actual bowl are marked with numbers. The second variable `color` indicates whether a particular virtual ball is red or white. View the contents of the bowl in RStudio's data viewer and scroll through the contents to convince yourself that `bowl` is indeed a virtual analog of the actual bowl in Figure \@ref(fig:sampling-exercise-1).

Now that we have a virtual analog of our bowl, we now need a virtual analog to the shovel seen in Figure \@ref(fig:sampling-exercise-2) to generate virtual samples of 50 balls. We're going to use the `rep_sample_n()` function included in the `moderndive` package. This function allows us to take `rep`eated, or `rep`licated, `samples` of size `n`. 


```r
virtual_shovel <- bowl %>% 
  rep_sample_n(size = 50)
virtual_shovel
```

```
## # A tibble: 50 x 3
## # Groups:   replicate [1]
##    replicate ball_ID color
##        <int>   <int> <chr>
##  1         1    1416 red  
##  2         1    1895 white
##  3         1    1414 white
##  4         1    1666 red  
##  5         1     285 red  
##  6         1    2079 red  
##  7         1    2370 white
##  8         1    1105 white
##  9         1     110 white
## 10         1     731 white
## # ... with 40 more rows
```

Observe that `virtual_shovel` has 50 rows corresponding to our virtual sample of size 50. The `ball_ID` variable identifies which of the 2400 balls from `bowl` are included in our sample of 50 balls while `color` denotes its color. However what does the `replicate` variable indicate? In `virtual_shovel`'s case, `replicate` is equal to 1 for all 50 rows. This is telling us that these 50 rows correspond to the first repeated/replicated use of the shovel, in our case our first sample. We'll see in what follows when we "virtually" take 33 samples, `replicate` will take values between 1 and 33. 

Let's compute the proportion of balls in our virtual sample that are red. First, for each of our 50 sampled balls, let's identify if it is red or not using a test for equality using `==`. Let's create a new Boolean variable `is_red` using the `mutate()` function:


```r
virtual_shovel %>% 
  mutate(is_red = (color == "red"))
```

```
## # A tibble: 50 x 4
## # Groups:   replicate [1]
##    replicate ball_ID color is_red
##        <int>   <int> <chr> <lgl> 
##  1         1    1416 red   TRUE  
##  2         1    1895 white FALSE 
##  3         1    1414 white FALSE 
##  4         1    1666 red   TRUE  
##  5         1     285 red   TRUE  
##  6         1    2079 red   TRUE  
##  7         1    2370 white FALSE 
##  8         1    1105 white FALSE 
##  9         1     110 white FALSE 
## 10         1     731 white FALSE 
## # ... with 40 more rows
```

Observe that for every row where `color == "red"`, the Boolean `TRUE` is returned and for every row where `color` is not equal to `"red"`, the Boolean `FALSE` is returned.

Second, let's compute the number of balls out of 50 that are red using the `summarize()` function. Recall  that `summarize()` takes a data frame with many rows and returns a data frame with a single row containing summary statistics, like the `mean()` or `median()`. In this case, we use the `sum()`:


```r
virtual_shovel %>% 
  mutate(is_red = (color == "red")) %>% 
  summarize(num_red = sum(is_red))
```

```
## `summarise()` ungrouping output (override with `.groups` argument)
```

```
## # A tibble: 1 x 2
##   replicate num_red
##       <int>   <int>
## 1         1      22
```

```
## `summarise()` ungrouping output (override with `.groups` argument)
```

Why does this work? Because R treats `TRUE` like the number `1` and `FALSE` like the number `0`. So summing the number of `TRUE`'s and `FALSE`'s is equivalent to summing `1`'s and `0`'s. In the end, this operation counts the number of balls where `color` is `red`. In our case, 22 of the 50 balls were red. However, you might've gotten a different number red because of the randomness of the virtual sampling.

Third and lastly, let's compute the proportion of the 50 sampled balls that are red by dividing `num_red` by 50:


```r
prop_red <- virtual_shovel %>% 
  mutate(is_red = color == "red") %>% 
  summarize(num_red = sum(is_red)) %>% 
  mutate(prop_red = num_red / 50) %>%
  select (prop_red)
```

```
## `summarise()` ungrouping output (override with `.groups` argument)
```

In other words, 44% of this virtual sample's balls were red. Let's make this code a little more compact and succinct by combining the first `mutate()` and the `summarize()` as follows:


```r
virtual_shovel %>% 
  summarize(num_red = sum(color == "red")) %>% 
  mutate(prop_red = num_red / 50)
```

```
## `summarise()` ungrouping output (override with `.groups` argument)
```

```
## # A tibble: 1 x 3
##   replicate num_red prop_red
##       <int>   <int>    <dbl>
## 1         1      22     0.44
```

Great! 44% of `virtual_shovel`'s 50 balls were red! So based on this particular sample of 50 balls, our guess at the proportion of the `bowl`'s balls that are red is 44%. But remember from our earlier tactile sampling activity that if we repeat this sampling, we will not necessarily obtain the same value of 44% again. There will likely be some variation. In fact, our 33 groups of friends computed 33 such proportions whose distribution we visualized in Figure \@ref(fig:sampling-exercise-5). We saw that these estimates *varied*. Let's now perform the virtual analog of having 33 groups of students use the sampling shovel!

### Using the virtual shovel 33 times

Recall that in our tactile sampling exercise in Section \@ref(sampling-activity) we had 33 groups of students each use the shovel, yielding 33 samples of size 50 balls. We then used these 33 samples to compute 33 proportions. In other words we repeated/replicated using the shovel 33 times. We can perform this repeated/replicated sampling virtually by once again using our virtual shovel function `rep_sample_n()`, but by adding the `reps = 33` argument. This is telling R that we want to repeat the sampling 33 times. 

We'll save these results in a data frame called `virtual_samples`. While we provide a preview of the first 10 rows of `virtual_samples` in what follows, we highly suggest you scroll through its contents using RStudio's spreadsheet viewer by running `View(virtual_samples)`. 


```r
virtual_samples <- bowl %>% 
  rep_sample_n(size = 50, reps = 33)
virtual_samples
```

```
## # A tibble: 1,650 x 3
## # Groups:   replicate [33]
##    replicate ball_ID color
##        <int>   <int> <chr>
##  1         1      37 white
##  2         1    2395 red  
##  3         1     476 red  
##  4         1    1732 white
##  5         1     995 white
##  6         1     375 white
##  7         1     208 red  
##  8         1    1985 white
##  9         1       9 red  
## 10         1    1533 red  
## # ... with 1,640 more rows
```

Observe in the spreadsheet viewer that the first 50 rows of `replicate` are equal to `1` while the next 50 rows of `replicate` are equal to `2`. This is telling us that the first 50 rows correspond to the first sample of 50 balls while the next 50 rows correspond to the second sample of 50 balls. This pattern continues for all `reps = 33` replicates and thus `virtual_samples` has 33 $\times$ 50 = 1650 rows. 

Let's now take `virtual_samples` and compute the resulting 33 proportions red. We'll use the same `dplyr` verbs as before, but this time with an additional `group_by()` of the `replicate` variable. We display a preview of the first 10 out of 33 rows:


```r
virtual_prop_red <- virtual_samples %>% 
  group_by(replicate) %>% 
  summarize(red = sum(color == "red")) %>% 
  mutate(prop_red = red / 50)
```

```
## `summarise()` ungrouping output (override with `.groups` argument)
```

```r
virtual_prop_red
```

```
## # A tibble: 33 x 3
##    replicate   red prop_red
##        <int> <int>    <dbl>
##  1         1    22     0.44
##  2         2    19     0.38
##  3         3    17     0.34
##  4         4    17     0.34
##  5         5    15     0.3 
##  6         6    21     0.42
##  7         7    20     0.4 
##  8         8    22     0.44
##  9         9    22     0.44
## 10        10    18     0.36
## # ... with 23 more rows
```

As with our 33 groups of friends' tactile samples, there is variation in the resulting 33 virtual proportions red. Let's visualize this variation in a histogram in Figure \@ref(fig:samplingdistribution-virtual). Note that we add `binwidth = 0.05` and `boundary = 0.4` arguments as well. Setting `boundary = 0.4` indicates that we want a binning scheme such that one of the bins' boundary is at 0.4. Since the `binwidth = 0.05` is also set, this will create bins with boundaries at 0.30, 0.35, 0.45, 0.5, etc as well.


```r
ggplot(virtual_prop_red, aes(x = prop_red)) +
  geom_histogram(binwidth = 0.05, boundary = 0.4, color = "white") +
  labs(x = "Proportion of 50 balls that were red", 
       title = "Distribution of 33 proportions red") 
```
![(\#fig:samplingdistribution-virtual)Distribution of 33 proportions based on 33 samples of size 50.](08-sampling_files/figure-latex/samplingdistribution-virtual-1.pdf) 

Observe that we occasionally obtained proportions red that are less than 30%. On the other hand, we occasionally  obtained proportions that are greater than 45%. However, the most frequently occurring proportions were between 35% and 40% (for 11 out of 33 samples). Why do we have these differences in proportions red? Because of *sampling variation*. 

Let's now compare our virtual results with our tactile results from the previous section in Figure \@ref(fig:tactile-vs-virtual). Observe that both histograms are somewhat similar in their center and variation, although not identical. These slight differences are again due to random sampling variation. Furthermore, observe that both distributions are somewhat bell-shaped.

![(\#fig:tactile-vs-virtual)Comparing 33 virtual and 33 tactile proportions red.](08-sampling_files/figure-latex/tactile-vs-virtual-1.pdf) 


### Using the virtual shovel 1000 times {#shovel-1000-times}

Now say we want to study the effects of sampling variation not for 33 samples, but rather for a very large number of samples, say 1000. We have two choices at this point. We could have our groups of friends manually take 1000 samples of 50 balls and compute the corresponding 1000 proportions. However, this would be a very tedious and time-consuming task. This is where computers excel: automating long and repetitive tasks while performing them very quickly. Thus at this point we will abandon tactile sampling in favor of only virtual sampling. Let's once again use the `rep_sample_n()` function with sample `size` set to be 50 once again, but this time with the number of replicates `reps = 1000`. Be sure to scroll through the contents of `virtual_samples` in RStudio's viewer. 


```r
virtual_samples <- bowl %>% 
  rep_sample_n(size = 50, reps = 1000)
virtual_samples
```

```
## # A tibble: 50,000 x 3
## # Groups:   replicate [1,000]
##    replicate ball_ID color
##        <int>   <int> <chr>
##  1         1     583 white
##  2         1     260 white
##  3         1    1947 red  
##  4         1      19 white
##  5         1     393 white
##  6         1     282 white
##  7         1     438 white
##  8         1     622 red  
##  9         1     751 red  
## 10         1     354 red  
## # ... with 49,990 more rows
```

Observe that now `virtual_samples` has 1000 $\times$ 50 = 50,000 rows, instead of the 33 $\times$ 50 = 1650 rows from earlier. Using the same data wrangling code as earlier, let's take the data frame `virtual_samples` with 1000 $\times$ 50 = 50,000 and compute the resulting 1000 proportions red. 


```r
virtual_prop_red <- virtual_samples %>% 
  group_by(replicate) %>% 
  summarize(red = sum(color == "red")) %>% 
  mutate(prop_red = red / 50)
```

```
## `summarise()` ungrouping output (override with `.groups` argument)
```

```r
virtual_prop_red
```

```
## # A tibble: 1,000 x 3
##    replicate   red prop_red
##        <int> <int>    <dbl>
##  1         1    14     0.28
##  2         2    21     0.42
##  3         3    20     0.4 
##  4         4    13     0.26
##  5         5    18     0.36
##  6         6    15     0.3 
##  7         7    17     0.34
##  8         8    14     0.28
##  9         9    18     0.36
## 10        10    13     0.26
## # ... with 990 more rows
```

Observe that we now have 1000 replicates of `prop_red`, the proportion of 50 balls that are red. Using the same code as earlier, let's now visualize the distribution of these 1000 replicates of `prop_red` in a histogram in Figure \@ref(fig:samplingdistribution-virtual-1000).


```r
ggplot(virtual_prop_red, aes(x = prop_red)) +
  geom_histogram(binwidth = 0.05, boundary = 0.4, color = "white") +
  labs(x = "Proportion of 50 balls that were red", 
       title = "Distribution of 1000 proportions red") 
```

```
## `summarise()` ungrouping output (override with `.groups` argument)
```

![(\#fig:samplingdistribution-virtual-1000)Distribution of 1000 proportions based on 33 samples of size 50.](08-sampling_files/figure-latex/samplingdistribution-virtual-1000-1.pdf) 

Once again, the most frequently occurring proportions red occur between 35% and 40%. Every now and then, we obtain proportions as low as between 20% and 25%, and others as high as between 55% and 60%. These are rare, however. Furthermore, observe that we now have a much more symmetric and smoother bell-shaped distribution. This distribution is, in fact, a Normal distribution. 


### Using different shovels {#different-shovels}

Now say instead of just one shovel, you have three choices of shovels to extract a sample of balls with: shovels of size 25, 50, and 100.

\begin{figure}

{\centering \includegraphics[width=1\linewidth]{images/sampling/balls/three_shovels} 

}

\caption{Three shovels to extract three different sample sizes.}(\#fig:three-shovels)
\end{figure}

If your goal is still to estimate the proportion of the bowl's balls that are red, which shovel would you choose? In our experience, most people would choose the largest shovel with 100 slots because it would yield the "best" guess of the proportion of the bowl's balls that are red. Let's define some criteria for "best" in this subsection.

Using our newly developed tools for virtual sampling, let's unpack the effect of having different sample sizes! In other words, let's use `rep_sample_n()` with `size = 25`, `size = 50`, and `size = 100`, while keeping the number of repeated/replicated samples at 1000:

1. Virtually use the appropriate shovel to generate 1000 samples with `size` balls.
1. Compute the resulting 1000 replicates of the proportion of the shovel's balls that are red.
1. Visualize the distribution of these 1000 proportions red using a histogram.

Run each of the following code segments individually and then compare the three resulting histograms.


```r
# Segment 1: sample size = 25 ------------------------------
# 1.a) Virtually use shovel 1000 times
virtual_samples_25 <- bowl %>% 
  rep_sample_n(size = 25, reps = 1000)

# 1.b) Compute resulting 1000 replicates of proportion red
virtual_prop_red_25 <- virtual_samples_25 %>% 
  group_by(replicate) %>% 
  summarize(red = sum(color == "red")) %>% 
  mutate(prop_red = red / 25)

# 1.c) Plot distribution via a histogram
ggplot(virtual_prop_red_25, aes(x = prop_red)) +
  geom_histogram(binwidth = 0.05, boundary = 0.4, color = "white") +
  labs(x = "Proportion of 25 balls that were red", title = "25") 


# Segment 2: sample size = 50 ------------------------------
# 2.a) Virtually use shovel 1000 times
virtual_samples_50 <- bowl %>% 
  rep_sample_n(size = 50, reps = 1000)

# 2.b) Compute resulting 1000 replicates of proportion red
virtual_prop_red_50 <- virtual_samples_50 %>% 
  group_by(replicate) %>% 
  summarize(red = sum(color == "red")) %>% 
  mutate(prop_red = red / 50)

# 2.c) Plot distribution via a histogram
ggplot(virtual_prop_red_50, aes(x = prop_red)) +
  geom_histogram(binwidth = 0.05, boundary = 0.4, color = "white") +
  labs(x = "Proportion of 50 balls that were red", title = "50")  


# Segment 3: sample size = 100 ------------------------------
# 3.a) Virtually using shovel with 100 slots 1000 times
virtual_samples_100 <- bowl %>% 
  rep_sample_n(size = 100, reps = 1000)

# 3.b) Compute resulting 1000 replicates of proportion red
virtual_prop_red_100 <- virtual_samples_100 %>% 
  group_by(replicate) %>% 
  summarize(red = sum(color == "red")) %>% 
  mutate(prop_red = red / 100)

# 3.c) Plot distribution via a histogram
ggplot(virtual_prop_red_100, aes(x = prop_red)) +
  geom_histogram(binwidth = 0.05, boundary = 0.4, color = "white") +
  labs(x = "Proportion of 100 balls that were red", title = "100") 
```

For easy comparison, we present the three resulting histograms in a single row with matching x and y axes in Figure \@ref(fig:comparing-sampling-distributions).


```
## `summarise()` ungrouping output (override with `.groups` argument)
## `summarise()` ungrouping output (override with `.groups` argument)
## `summarise()` ungrouping output (override with `.groups` argument)
```

![(\#fig:comparing-sampling-distributions)Comparing the distributions of proportion red for different sample sizes.](08-sampling_files/figure-latex/comparing-sampling-distributions-1.pdf) 

Observe that as the sample size increases, the variation of the 1000 replicates of the proportion of red decreases. In other words, as the sample size increases, there are fewer differences due to sampling variation and the distribution centers more tightly around the same value. Eyeballing Figure \@ref(fig:comparing-sampling-distributions), all three histograms appear to center around roughly 40%.

We can be numerically explicit about the amount of variation in our 3 sets of 1000 values of `prop_red` using the *standard deviation* \index{standard deviation}. A standard deviation is a summary statistic that measures the amount of variation within a numerical variable. For all three sample sizes, let's compute the standard deviation of the 1000 proportions red by running the following data wrangling code that uses the `sd()` summary function.


```r
# n = 25
virtual_prop_red_25 %>% 
  summarize(sd = sd(prop_red))

# n = 50
virtual_prop_red_50 %>% 
  summarize(sd = sd(prop_red))

# n = 100
virtual_prop_red_100 %>% 
  summarize(sd = sd(prop_red))
```

Let's compare these three measures of variation of the distributions in Table \@ref(tab:comparing-n).


```
## `summarise()` ungrouping output (override with `.groups` argument)
```

\begin{table}[!h]

\caption{(\#tab:comparing-n)Comparing standard deviations of proportions red for 3 different shovels.}
\centering
\fontsize{10}{12}\selectfont
\begin{tabular}[t]{rr}
\toprule
Number of slots in shovel & Standard deviation of proportions red\\
\midrule
25 & 0.099\\
50 & 0.071\\
100 & 0.048\\
\bottomrule
\end{tabular}
\end{table}

As we observed in Figure \@ref(fig:comparing-sampling-distributions), as the sample size increases, the variation decreases. In other words, there is less variation in the 1000 values of the proportion red. So as the sample size increases, our guesses at the true proportion of the bowl's balls that are red get more precise. 


## Sampling framework {#sampling-framework}

In both our tactile and our virtual sampling activities, we used sampling for the purpose of estimation. We extracted samples in order to *estimate* the proportion of the bowl's balls that are red. We used sampling as a less time consuming approach than to perform an exhaustive count of all the balls. Our virtual sampling activity built up to the results shown in Figure \@ref(fig:comparing-sampling-distributions) and Table \@ref(tab:comparing-n): comparing 1000 proportions red based on samples of size 25, 50, and 100. This was our first attempt at understanding two key concepts relating to sampling for estimation:

1. The effect of *sampling variation* on our estimates.
1. The effect of sample size on *sampling variation*.

Let's now introduce some terminology and notation as well as statistical definitions related to sampling. Given the number of new words you'll need to learn, you will likely have to read this section a few times. Keep in mind, however, that all of the concepts underlying these terminology, notation, and definitions tie directly to the concepts underlying our tactile and virtual sampling activities. It will simply take time and practice to master them. 


### Terminology & notation {#terminology-and-notation}

Here is a list of terminology and mathematical notation relating to sampling.

First, A **(study) population** is a collection of individuals or observations about which we are interested in. We mathematically denote the population's size using upper case $N$.  In our sampling activities, the (study) population is the collection of $N$ = 2400 identically sized red and white balls contained in the bowl.

Second, a **population parameter** is a numerical summary quantity about the population that is unknown, but you wish you knew. For example, when this quantity is a mean, the population parameter of interest is the *population mean*. This is mathematically denoted with the Greek letter $\mu$ pronounced "mu" (We'll see a sampling activity involving means in the upcoming Section \@ref(resampling-tactile)). In our earlier sampling from the bowl activity however, since we were interested in the proportion of the bowl's balls that were red, the population parameter is the *population proportion* . This is mathematically denoted with the letter $p$. 

Third, a **census** is an exhaustive enumeration or counting of all $N$ individuals or observations in the population in order to compute the population parameter's value *exactly*. In our sampling activity, this would correspond to counting the number of balls out of $N$ = 2400 that are red and computing the *population proportion* $p$ that are red *exactly*. When the number $N$ of individuals or observations in our population is large as was the case with our bowl, a census can be very expensive in terms of time, energy, and money. 

Fourth, **sampling** is the act of collecting a sample from the population when we don't have the means to perform a census. We mathematically denote the sample's size using lower case $n$, as opposed to upper case $N$ which denotes the population's size. Typically the sample size $n$ is much smaller than the population size $N$.  Thus sampling is a much cheaper alternative than performing a census. In our sampling activities, we used shovels with 25, 50, and 100 slots to extract a sample of size $n$ = 25, $n$ = 50, and $n$ = 100. 

Fifth, A **point estimate (AKA sample statistic)** is a summary statistic computed from a sample that *estimates* an unknown population parameter. In our sampling activities, recall that the unknown population parameter was the population proportion and that this is mathematically denoted with $p$. Our point estimate is the *sample proportion*: the proportion of the shovel's balls that are red. In other words, it is our guess of the proportion of the bowl's balls balls that are red. We mathematically denote the sample proportion using $\widehat{p}$. The "hat" on top of the $p$ indicates that it is an estimate of the unknown population proportion $p$. 

Sixth, the idea of **representative sampling**. A sample is said to be a *representative sample* if it roughly *looks like* the population. In other words, are the sample's characteristics a good representation of the population's characteristics? In our sampling activity, are the samples of $n$ balls extracted using our shovels representative of the bowl's $N$ = 2400 balls?

Seventh, the idea of **generalizability**. We say a sample is generalizable if any results based on the sample can generalize to the population. In other words, does the value of the point estimate *generalize* to the population? In our sampling activity, can we generalize the sample proportion from our shovels to the entire bowl? Using our mathematical notation, this is akin to asking if $\widehat{p}$ a "good guess" of $p$?

Eighth, we say **biased sampling** occurs if certain individuals or observations in a population have a higher chance of being included in a sample than others. We say a sampling procedure is *unbiased* if every observation in a population had an equal chance of being sampled. In our sampling activities, since each equally sized balls had an equal chance of being sampled in our shovels, our samples were unbiased.

Ninth and lastly, the idea of **random sampling**. We say a sampling procedure is *random* if we sample randomly from the population in an unbiased fashion. In our sampling activities, this would correspond to sufficiently mixing the bowl before each use of the shovel. 

Phew, that's a lot of new terminology and notation to learn! Let's put them all together to describe the paradigm of sampling.

**In general**: 

* If the sampling of a sample of size $n$ is done at **random**, then
* the sample is **unbiased** and **representative** of the population of size $N$, thus
* any result based on the sample can **generalize** to the population, thus
* the point estimate is a **"good guess"** of the unknown population parameter, thus
* instead of performing a census, we can **infer** about the population using sampling.

**Specific to our sampling activity:**: 

* If we extract a sample of $n=50$ balls at **random**, in other words, we mix e equally-sized balls before using the shovel, then
* the contents of the shovel are an **unbiased representation** of the contents of the bowl's 2400 balls, thus
* any result based on the shovel's balls can **generalize** to the bowl, thus
* the sample proportion $\widehat{p}$ of the $n=50$ balls in the shovel that are red is a **"good guess"** of the population proportion $p$ of the $N$=2400 balls that are red, thus
* instead of manually going over all 2400 balls in the bowl, we can **infer** about the bowl using the shovel. 

Note that last word we wrote in bold: **infer**. The act of "inferring" means to deduce or conclude (information) from evidence and reasoning. In our sampling activities, we wanted to infer about the proportion of the bowl's balls that are red. *Statistical inference* is the "theory, methods, and practice of forming judgments about the parameters of a population and the reliability of statistical relationships, typically on the basis of random sampling" (Wikipedia). In other words, statistical inference is the act of inference via sampling. In the upcoming Chapter \@ref(confidence-intervals) on confidence intervals, we'll introduce the `infer` package, which makes statistical inference "tidy" and transparent. It is why this third portion of the book is called "Statistical inference via infer".

### Statistical definitions {#sampling-definitions}

Now for some important statistical definitions related to sampling. As a refresher of our 1000 repeated/replicated virtual samples of size $n$ = 25, $n$ = 50, and $n$ = 100 in Section \@ref(sampling-simulation), let's display Figure \@ref(fig:comparing-sampling-distributions) again.  

![(\#fig:comparing-sampling-distributions-1b)Previously seen three sampling distributions of the sample proportion $\widehat{p}$.](08-sampling_files/figure-latex/comparing-sampling-distributions-1b-1.pdf) 

These types of distributions have a special name: **sampling distributions**; \index{sampling distributions} their visualization displays the effect of sampling variation on the distribution of any point estimate, in this case, the sample proportion $\widehat{p}$. Using these sampling distributions, for a given sample size $n$, we can make statements about what values we can typically expect. 

For example, observe the centers of all three sampling distributions: they are all roughly centered around 0.4 = 40%. Furthermore, observe that while we are somewhat likely to observe sample proportions red of 0.2 = 20% when using the shovel with 25 slots, we will almost never observe a proportion of 20% when using the shovel with 100 slots. Observe also the effect of sample size on the sampling variation. As the sample size $n$ increases from 25 to 50 to 100, \index{sampling distribution!relationship to sample size} the variation of the sampling distribution decreases and thus the values cluster more and more tightly around the same center of around 40%. We quantified this variation using the standard deviation of our sample proportions in Table \@ref(tab:comparing-n), which we display again:


```
## `summarise()` ungrouping output (override with `.groups` argument)
```

\begin{table}[!h]

\caption{(\#tab:comparing-n-repeat)Previously seen comparing standard deviations of proportions red for 3 different shovels.}
\centering
\fontsize{10}{12}\selectfont
\begin{tabular}[t]{rr}
\toprule
Number of slots in shovel & Standard deviation of proportions red\\
\midrule
25 & 0.099\\
50 & 0.071\\
100 & 0.048\\
\bottomrule
\end{tabular}
\end{table}

So as the sample size increases, the standard deviation decreases. This type of standard deviation has another special name: \index{standard error} **standard error**. Standard errors quantify the effect of sampling variation induced on our estimates. In other words, they quantify how much we can expect different proportions of a shovel's balls that are red *to vary* from one sample to another sample to another sample, and so on. 

Unfortunately, these names confuse many people new to statistical inference. For example, it's common for people new to statistical inference to call the "sampling distribution" the "sample distribution." Another additional source of confusion is the name "standard deviation" and "standard error." Remember that a standard error is merely a *kind* of standard deviation: the standard deviation of any point estimate from sampling. In other words, all standard errors are standard deviations, but not all standard deviations are necessarily a standard error. 

To help reinforce these concepts, let's re-display Figure \@ref(fig:comparing-sampling-distributions) but using our new terminology, notation, and definitions relating to sampling in Figure \@ref(fig:comparing-sampling-distributions-2). 

![(\#fig:comparing-sampling-distributions-2)Three sampling distributions of the sample proportion $\widehat{p}$.](08-sampling_files/figure-latex/comparing-sampling-distributions-2-1.pdf) 

Furthermore, let's re-display Table \@ref(tab:comparing-n) but using our new terminology, notation, and definitions relating to sampling in Table \@ref(tab:comparing-n-2).


```
## `summarise()` ungrouping output (override with `.groups` argument)
```

\begin{table}[!h]

\caption{(\#tab:comparing-n-2)Three standard errors of the sample proportion based on n = 25, 50, 100.}
\centering
\fontsize{10}{12}\selectfont
\begin{tabular}[t]{lr}
\toprule
Sample size (n) & Standard error of \$\textbackslash{}widehat\{p\}\$\\
\midrule
n = 25 & 0.099\\
n = 50 & 0.071\\
n = 100 & 0.048\\
\bottomrule
\end{tabular}
\end{table}

Remember the key message of this last table: that as the sample size $n$ goes up, the "typical" error of your point estimate will go down (as quantified by the *standard error*).

### The moral of the story {#moral-of-the-story}

Let's recap this section so far. We've seen that if a sample is generated at random, then the resulting point estimate is a "good guess" of the true unknown population parameter. In our sampling activities, since we made sure to mix the balls first before extracting a sample with the shovel, the resulting sample proportion $\widehat{p}$ of the shovel's balls that were red was a "good guess" of the population proportion $p$ of the bowl's balls that were red. 

However, what do we mean by our point estimate being a "good guess"? Sometimes we'll get an estimate that is less than the true value of the population parameter, while at other times we'll get an estimate that is greater. This is due to sampling variation. However, despite this sampling variation, our estimates will "on average" be correct and thus will be centered at the true value. This is because our sampling was done at random and thus in an unbiased fashion. 

In our sampling activities, sometimes our sample proportion $\widehat{p}$ was less than the true population proportion $p$, while at other times it was greater. This was due to the sampling variability. However, despite this sampling variation, our sample proportions $\widehat{p}$ were "on average" correct and thus were centered at the true value of the population proportion $p$. This is because we mixed our bowl before taking samples and thus the sampling was done at random and thus in an unbiased fashion. This is also known as having an *accurate* estimate\index{accuracy}.

What was the value of the population proportion $p$ of the $N$ = 2400 balls in the actual bowl that were red? There were 900 red balls, for a proportion red of 900/2400 = 0.375 = 37.5%! How do we know this? Did the authors do an exhaustive count of all the balls? No! They were listed in the contents of the box that the bowl came in! Hence we were able to make the contents of the virtual `bowl` match the tactile bowl:


```r
bowl %>% 
  summarize(sum_red = sum(color == "red"), 
            sum_not_red = sum(color != "red"))
```

```
## # A tibble: 1 x 2
##   sum_red sum_not_red
##     <int>       <int>
## 1     900        1500
```

Let's re-display our sampling distributions from Figures \@ref(fig:comparing-sampling-distributions) and \@ref(fig:comparing-sampling-distributions-2), but now with a vertical red line marking the true population proportion $p$ of balls that are red = 37.5% in Figure \@ref(fig:comparing-sampling-distributions-3). We see that while there is a certain amount of error in the sample proportions $\widehat{p}$ for all three sampling distributions, on average the $\widehat{p}$ are centered at the true population proportion red $p$.

![(\#fig:comparing-sampling-distributions-3)Three sampling distributions with population proportion $p$ marked in red.](08-sampling_files/figure-latex/comparing-sampling-distributions-3-1.pdf) 

We also saw in this section that as your sample size $n$ increases, your point estimates will vary less and less and be more and more concentrated around the true population parameter. This variation is quantified by the decreasing *standard error*. In other words, the typical error of your point estimates will decrease. In our sampling exercise, as the sample size increased, the variation of our sample proportions $\widehat{p}$ decreased. You can observe this behavior in Figure \@ref(fig:comparing-sampling-distributions-3).  This is also known as having a *precise* estimate\index{precision}. 

So random and unbiased sampling ensures our point estimates are *accurate*, while on the other hand having a large sample size ensures our point estimates are *precise*. While the terms "accuracy" and "precision" may sound like they mean the same thing, there is a subtle difference. Accuracy describes how "on target" our estimates are, whereas precision describes how "consistent" our estimates are. Figure \@ref(fig:accuracy-vs-precision) illustrates the difference.

\begin{figure}
\includegraphics[width=0.5\linewidth]{images/accuracy_vs_precision} \caption{Comparing accuracy and precision.}(\#fig:accuracy-vs-precision)
\end{figure}

As this point, you might be asking yourself: "If we already knew the true proportion of the bowl's balls that are red was 37.5%, then why did do any sampling?" You might also be asking: "Why did we take 1000 repeated samples of size n = 25, 50, and 100? Shouldn't we be taking only *one* sample that's as large as possible?" If you did ask yourself these questions, your suspicion is merited! 

The sampling activity involving the bowl is merely an *idealized version* of how sampling is done in real-life. We performed this exercise only to study and understand:

1. The effect of sampling variation.
1. The effect of sample size on sampling variation.

This not how sampling is done in real-life. In a real-life scenario, we won't know what the true value of the population parameter is. Furthermore we wouldn't take 1000 repeated/replicated samples, but rather a single sample that's as large as we can afford. In the next section, let's now study a real-life example of sampling: polls.


## Case study: Polls {#sampling-case-study}

Let's now switch gears to a more realistic sampling scenario than our bowl activity: a poll. In practice, pollsters do not take 1000 repeated samples as we did in our previous sampling activities, but rather take only a *single sample* that's as large as possible.

On December 4, 2013, National Public Radio in the US reported on a poll of President Obama's approval rating among young Americans aged 18-29 in an article ["Poll: Support For Obama Among Young Americans Eroding"](https://www.npr.org/sections/itsallpolitics/2013/12/04/248793753/poll-support-for-obama-among-young-americans-eroding). The poll was conducted by the Harvard University Institute of Politics. A quote from the article:

> After voting for him in large numbers in 2008 and 2012, young Americans are souring on President Obama.
> 
> According to a new Harvard University Institute of Politics poll, just 41 percent of millennials — adults ages 18-29 — approve of Obama's job performance, his lowest-ever standing among the group and an 11-point drop from April.

Let's tie elements of the real-life poll in this new article with our "tactile" and "virtual" bowl activity from Sections \@ref(sampling-activity) and \@ref(sampling-simulation) using the terminology, notations, and definitions we learned in Section \@ref(sampling-framework). You see that our sampling activity with the bowl is an idealized version of what pollsters are trying to do in real-life. 

First, who is the **(Study) Population** of $N$ individuals or observations of interest? \index{sampling!population}

* Bowl: $N$ = 2400 identically-sized red and white balls
* Obama poll: $N$ = ? young Americans aged 18-29

Second, what is the **population parameter**? \index{sampling!population parameter}

* Bowl: The population proportion $p$ of *all* the balls in the bowl that are red.
* Obama poll: The population proportion $p$ of *all* young Americans who approve of Obama's job performance.

Third, what would a **census** look like? \index{sampling!census}

* Bowl: Manually going over all $N$ = 2400 balls and exactly computing the population proportion $p$ of the balls that are red.
* Obama poll: Locating all $N$ young Americans and asking them all if they approve of Obama's job performance. In the case, we don't even know what the population size $N$ is!

Fourth, how do you perform **sampling** to obtain a sample of size $n$? \index{sampling}

* Bowl: Using a shovel with $n$ slots. 
* Obama poll: One method is to get a list of phone numbers of all young Americans and pick out $n$ phone numbers. In this poll's case, the sample size of this poll was $n$ = 2089 young Americans.

Fifth, what is your **point estimate (AKA sample statistic)** of the unknown population parameter?

* Bowl: The sample proportion $\widehat{p}$ of the balls in the shovel that were red. 
* Obama poll: The sample proportion $\widehat{p}$ of young Americans in the sample that approve of Obama's job performance. In this poll's case, $\widehat{p}$ = 0.41 = 41%, the quoted percentage in the second paragraph of the article. \index{point estimate} \index{sample statistic}

Sixth, is the sampling procedure **representative**? \index{sampling!representative}

* Bowl: Are the contents of the shovel representative of the contents of the bowl? Because we mixed the bowl before sampling, we can feel confident that they are. 
* Obama poll: Is the sample of $n$ = 2089 young Americans representative of *all* young Americans aged 18-29? This depends on whether the sampling was random.

Seventh, are the samples **generalizable** to the greater population? \index{generalizability}

* Bowl: Is the sample proportion $\widehat{p}$ of the shovel's balls that are red a "good guess" of the population proportion $p$ of the bowl's balls that are red? Given that the sample was representative, the answer is yes.
* Obama poll: Is the sample proportion $\widehat{p}$ = 0.41 of the sample of young Americans who support Obama a "good guess" of the population proportion $p$ of all young Americans who support Obama? In other words, can we confidently say that roughly 41% of *all* young Americans approve of Obama? Again, this depends on whether the sampling was random.

Eighth, is the sampling procedure **unbiased**? In other words, do all observations have an equal chance of being included in the sample? \index{bias}

* Bowl: Since each ball was equally sized and we mixed the bowl before using the shovel, each ball had an equal chance of being included in a sample and hence the sampling was unbiased. 
* Obama poll: Did all young Americans have an equal chance at being represented in this poll? Again, this depends on whether the sampling was random.

Ninth and lastly, was the sampling done at **random**? \index{sampling!random}

* Bowl: As long as you mixed the bowl sufficiently before sampling, your samples would be random.
* Obama poll: Was the sample conducted at random? We can't answer this question without knowing about the *sampling methodology*\index{sampling methodology} used by the Harvard University Institute of Politics. We'll discuss this more at the end of this section.

In other words, the Harvard University Institute of Politics poll can be thought of as *an instance* of using the shovel to sample balls from the bowl. Furthermore, if another polling company conducted a similar poll of young Americans at roughly the same time, they would likely get a different estimate than 41%. This is due to *sampling variation*.

Let's now revisit the sampling paradigm from Section \@ref(terminology-and-notation):

**In general**: 

* If the sampling of a sample of size $n$ is done at **random**, then
* the sample is **unbiased** and **representative** of the population of size $N$, thus
* any result based on the sample can **generalize** to the population, thus
* the point estimate is a **"good guess"** of the unknown population parameter, thus
* instead of performing a census, we can **infer** about the population using sampling.

**Specific to the bowl:**: 

* If we extract a sample of $n=50$ balls at **random**, in other words, we mix e equally-sized balls before using the shovel, then
* the contents of the shovel are an **unbiased representation** of the contents of the bowl's 2400 balls, thus
* any result based on the shovel's balls can **generalize** to the bowl, thus
* the sample proportion $\widehat{p}$ of the $n=50$ balls in the shovel that are red is a **"good guess"** of the population proportion $p$ of the $N$=2400 balls that are red, thus
* instead of manually going over all 2400 balls in the bowl, we can **infer** about the bowl using the shovel. 

**Specific to the Obama poll:**: 

* If we had a way of contacting a **randomly** chosen sample of 2089 young Americans and poll their approval of President Obama, then
* these 2089 young Americans would be an **unbiased** and **representative** sample of *all* young Americans, thus 
* any results based on this sample of 2089 young Americans can **generalize** to the entire population of *all* young Americans, thus
* the reported sample approval rating of 41% of these 2089 young Americans is a **good guess** of the true approval rating among all young Americans, thus
* instead of performing an expensive census of all young Americans, we can **infer** about all young Americans using polling.

So as you can see, it was critical for the Harvard University Institute of Politics sample to be truly random in order to infer about *all* young Americans' opinions about Obama. Was their sample truly random? It's hard to answer such questions without knowing about the *sampling methodology* used\index{sampling methodology}. For example, if this poll was conducted using only mobile phone numbers, people without mobile phones would be left out and therefore not represented in the sample. What about if the Harvard University Institute of Politics conducted this poll on an internet news site? Then people who don't read this internet news site would be left out. Ensuring that our samples were random was easy to do in our sampling bowl exercises, however in a real-life situation like the Obama poll, this is much harder to do.

## Conclusion {#sampling-conclusion}

<!--
TODO:

### Random sampling vs random assignment {#sampling-conclusion-sampling-vs-assignment}

As big point of confusion is the difference between random sampling and random assignment.
-->


### Sampling scenarios {#sampling-conclusion-table}

In this chapter, we performed both tactile and virtual sampling exercises to infer about an unknown proportion. We also presented a case study of sampling in real-life: polls. In both cases, we used the sample proportion $\widehat{p}$ to estimate the population proportion $p$. However, we are not just limited to scenarios related to proportions. In other words, we can use sampling to estimate other population parameters using other point estimates as well. We present 5 more such scenarios in Table \@ref(tab:table-ch8). 

\begin{table}[!h]

\caption{(\#tab:table-ch8)\label{tab:summarytable-ch8}Scenarios of sampling for inference}
\centering
\fontsize{10}{12}\selectfont
\begin{tabular}[t]{>{\raggedleft\arraybackslash}p{0.5in}>{\raggedright\arraybackslash}p{0.7in}>{\raggedright\arraybackslash}p{1in}>{\raggedright\arraybackslash}p{1.1in}>{\raggedright\arraybackslash}p{1in}}
\toprule
Scenario & Population parameter & Notation & Point estimate & Notation.\\
\midrule
1 & Population proportion & $p$ & Sample proportion & $\widehat{p}$\\
2 & Population mean & $\mu$ & Sample mean & $\overline{x}$ or $\widehat{\mu}$\\
3 & Difference in population proportions & $p_1 - p_2$ & Difference in sample proportions & $\widehat{p}_1 - \widehat{p}_2$\\
4 & Difference in population means & $\mu_1 - \mu_2$ & Difference in sample means & $\overline{x}_1 - \overline{x}_2$\\
5 & Population regression slope & $\beta_1$ & Fitted regression slope & $b_1$ or $\widehat{\beta}_1$\\
\addlinespace
6 & Population regression intercept & $\beta_0$ & Fitted regression intercept & $b_0$ or $\widehat{\beta}_0$\\
\bottomrule
\end{tabular}
\end{table}

In the rest of this book, we'll cover all the remaining scenarios as follows:

* In Chapter \@ref(confidence-intervals), we'll cover examples of statistical inference for
    + Scenario 2: The mean age $\mu$ of all pennies in circulation in the US.
    + Scenario 3: The difference $p_1 - p_2$ in the proportion of people who yawn *when seeing someone else yawn first* minus the proportion of people who yawn *without seeing someone else yawn first*. This is an example of *two-sample* inference\index{two-sample inference}.
* In Chapter \@ref(hypothesis-testing), we'll cover an example of statistical inference for
    + Scenario 4: The difference $\mu_1 - \mu_2$ in mean IMDb ratings for action and romance movies. This is another example of *two-sample* inference.
* We will not be covering Scenario 5 and 6.

<!--chapter:end:08-sampling.Rmd-->

# Bootstrapping & Confidence Intervals {#confidence-intervals}
    
In Chapter \@ref(sampling), we studied sampling. We started with a "tactile" exercise where we wanted to know the proportion of balls in the sampling bowl in Figure \@ref(fig:sampling-exercise-1) that are red. While we could have performed an exhaustive count, this would have been a tedious process. So instead we used a shovel to extract a sample of 50 balls and used the resulting proportion that were red as an *estimate*. Furthermore, we made sure to mix the bowl's contents before every use of the shovel. Because of the randomness induced by the mixing, different uses of the shovel yielded different proportions red and hence different estimates of the proportion of the bowl's balls that are red. 

We then mimicked this "tactile" sampling exercise with an equivalent "virtual" sampling exercise performed on the computer. Using our computers' random number generator, we very quickly mimicked the above sampling procedure a large number of times. In Section \@ref(different-shovels), we quickly repeated this sampling procedure 1000 times, using three different "virtual" shovels with 25, 50, and 100 slots. We visualized these three sets of 1000 estimates in Figure \@ref(fig:comparing-sampling-distributions-3) and saw that as the sample size increased, the variation in the estimates decreased.

What we did was construct *sampling distributions*. The motivation for taking 1000 repeated samples and visualizing the resulting estimates was to study how these estimates varied from one sample to another; in other words we wanted to study the effect of *sampling variation*. We quantified the variation of these estimates using their standard deviation, which has a special name: the *standard error*. In particular, we saw that as the sample size increased from 25 to 50 to 100, the standard error decreased and thus the sampling distributions narrowed. In other words, larger sample sizes lead to more *precise* estimates that varied less around the center. 

We then tied these sampling exercises to terminology and mathematical notation related to sampling in Section \@ref(terminology-and-notation). Our *study population* was the large bowl with $N$ = 2400 balls, while the *population parameter*, the unknown quantity of interest, here was the population proportion $p$ of the bowl's balls that are red. Since performing a *census* would be very expensive in terms of time and energy, we instead extracted a *sample* of size $n$ = 50. The *point estimate*, also known as a *sample statistic*, used to estimate $p$ was the sample proportion $\widehat{p}$ of these 50 sampled balls that were red. Furthermore, since the sample was obtained at *random*, it can be considered as *unbiased* and *representative* of the population. Thus any results based on the sample could be *generalized* to the population. Thus, the proportion of the shovel's balls that were red was a "good guess" of the proportion of the bowl's balls that are red. In other words, we used the sample to *infer* about the population.

However, as described in Section \@ref(sampling-simulation), both the tactile and virtual sampling exercises are not what one would do in real life; this was merely an activity used to study the effects of sampling variation. In a real life situation, we would not take 1000 samples of size $n$, but rather take a *single* representative sample that's as large as possible. Additionally, we knew what the true proportion of the bowl's balls that were red was 37.5%. In a real life situation, we will not know what this value is. Because if we did, then why would we take a sample to estimate it? 

An example of a realistic sampling situation would be a poll, like the [Obama poll](https://www.npr.org/sections/itsallpolitics/2013/12/04/248793753/poll-support-for-obama-among-young-americans-eroding) you saw in Section \@ref(sampling-case-study). Pollsters did not know the true proportion of *all* young Americans who supported President Obama, and thus they took a single sample of size $n$ = 2089 young Americans to estimate this value.

So how does one quantify the effects of sampling variation when you only have a *single sample* to work with? You cannot directly study the effects of sampling variation when you only have one sample. One common method to study this is *bootstrapping resampling*, which will be the focus of the earlier sections of this chapter. 

Furthermore, what if we would like not only a single estimate of the unknown population parameter, but also a *range of highly plausible* values? Going back to the Obama poll article, it stated that the pollsters' estimate of the proportion of all young Americans who supported President Obama was 41%. But in addition it stated that the poll's "margin of error was plus or minus 2.1 percentage points." In other words, this "plausible range" was [41% - 2.1%, 41% + 2.1%] = [37.9%, 43.1%]. This range of plausible values is what's known as a *confidence interval*, which will be the focus of the later sections of this chapter. 


### Needed packages {-}


```r
if (!require("pacman")) install.packages("pacman")
pacman::p_load(tidyverse, # All purpose wrangling for dataframes
               readr, # importing and writing data
               readxl,# read and write excel documents
               purrr, # for piping %>%
               corrplot, # for correlation
               knitr,
               moderndive,
               kableExtra,
               cowplot,
               infer)
```


## Pennies activity {#resampling-tactile}

As we did in Chapter \@ref(sampling), we'll begin with a hands-on tactile activity.

### What is the average year on US pennies in 2019?

Try to imagine all the pennies being used in the United States in 2019. That's a lot of pennies! Now say we're interested in the average year of minting of *all* these pennies. One way to compute this value would be to gather up all pennies being used in the US, record the year, and compute the average. However, this would be near impossible! So instead, let's collect a *sample* of 50 pennies collected from a local bank in downtown Northampton, Massachusetts, USA as seen in Figure \@ref(fig:resampling-exercise-a).

\begin{figure}
\includegraphics[width=0.4\linewidth]{images/sampling/pennies/bank} \includegraphics[width=0.4\linewidth]{images/sampling/pennies/roll} \caption{Collecting a sample of 50 US pennies from a local bank.}(\#fig:resampling-exercise-a)
\end{figure}

An image of these 50 pennies can be seen in Figure \@ref(fig:resampling-exercise-c). For each the 50 pennies starting in the top left, progressing row-by-row, and ending in the bottom right, we assigned an "ID" identification variable and marked the year of minting.

\begin{figure}
\includegraphics[width=1\linewidth]{images/sampling/pennies/deliverable/3} \caption{50 US pennies labelled.}(\#fig:resampling-exercise-c)
\end{figure}

The `moderndive` \index{moderndive!pennies\_sample} package contains this data on our 50 sampled pennies in the `pennies_sample` data frame:


```r
pennies_sample
```

```
## # A tibble: 50 x 2
##       ID  year
##    <int> <dbl>
##  1     1  2002
##  2     2  1986
##  3     3  2017
##  4     4  1988
##  5     5  2008
##  6     6  1983
##  7     7  2008
##  8     8  1996
##  9     9  2004
## 10    10  2000
## # ... with 40 more rows
```

The `pennies_sample` data frame has 50 rows corresponding to each penny with two variables. The first variable `ID` corresponds to the ID labels in Figure \@ref(fig:resampling-exercise-c) whereas the second variable `year` corresponds to the year of minting saved as an integer, in other words a whole number.

Based on these 50 sampled pennies, what can we say about *all* US pennies in 2019? Let's study some properties of our sample by performing an exploratory data analysis. Let's first visualize the distribution of the year of these 50 pennies using our data visualization tools. Since `year` is a numerical variable, we use a histogram in Figure \@ref(fig:pennies-sample-histogram) to visualize its distribution.


```r
ggplot(pennies_sample, aes(x = year)) +
  geom_histogram(binwidth = 10, color = "white")
```

![(\#fig:pennies-sample-histogram)Distribution of year on 50 US pennies.](09-confidence-intervals_files/figure-latex/pennies-sample-histogram-1.pdf) 

Observe a slightly left-skewed \index{skew} distribution, since most pennies fall in between 1980 and 2010 with only a few pennies older than 1970. What is the average year for the 50 sampled pennies? Eyeballing the histogram it appears to be around 1990. Let's now compute this value exactly using our data wrangling tools.


```r
pennies_sample %>% 
  summarize(mean_year = mean(year))
```

```
## # A tibble: 1 x 1
##   mean_year
##       <dbl>
## 1     1995.
```


Thus, if we're willing to assume that `pennies_sample` is a representative sample from *all* US pennies, a "good guess" of the average year of minting of all US pennies would be 1995.44. In other words, around 1995. This should all start sounding similar to what we did previously in Chapter \@ref(sampling)!

In Chapter \@ref(sampling), our *study population* was the bowl of $N$ = 2400 balls. Our *population parameter* was the *population proportion* of these balls that were red, denoted mathematically by $p$. In order to estimate $p$, we extracted a sample of 50 balls using the shovel. We then computed the relevant *point estimate*: the *sample proportion* of these 50 balls that were red, denoted mathematically by $\widehat{p}$.

Here our population is $N$ = whatever the number of pennies are being used in the US, a value which we don't know and probably never will. The population parameter of interest is now the *population mean* year of all these pennies, a value denoted mathematically by the Greek letter $\mu$ (pronounced "mu"). In order to estimate $\mu$, we went to the bank and obtained a sample of 50 pennies and computed the relevant point estimate: the *sample mean* year of these 50 pennies, denoted mathematically by $\overline{x}$ (pronounced "x-bar"). An alternative and more intuitive notation for the sample mean is $\widehat{\mu}$. However this is unfortunately not as commonly used, so in this book we'll stick with convention and always denote the sample mean as $\overline{x}$.

We summarize the correspondence between the sampling bowl exercise in Chapter \@ref(sampling) and our pennies exercise in Table \@ref(tab:table-ch8-b), which are the first two rows of the previously seen Table \@ref(tab:table-ch8) of the various sampling scenarios we'll cover in this text.

\begin{table}[!h]

\caption{(\#tab:table-ch8-b)Scenarios of sampling for inference}
\centering
\fontsize{10}{12}\selectfont
\begin{tabular}[t]{>{\raggedleft\arraybackslash}p{0.5in}>{\raggedright\arraybackslash}p{0.7in}>{\raggedright\arraybackslash}p{1in}>{\raggedright\arraybackslash}p{1.1in}>{\raggedright\arraybackslash}p{1in}}
\toprule
Scenario & Population parameter & Notation & Point estimate & Notation.\\
\midrule
1 & Population proportion & $p$ & Sample proportion & $\widehat{p}$\\
2 & Population mean & $\mu$ & Sample mean & $\overline{x}$ or $\widehat{\mu}$\\
\bottomrule
\end{tabular}
\end{table}

Going back to our 50 sampled pennies in Figure \@ref(fig:resampling-exercise-c), the point estimate of interest is the sample mean $\overline{x}$ of 1995.44. This quantity is an *estimate* of the population mean year of *all* US pennies $\mu$.

Recall that we also saw in Chapter \@ref(sampling) that such estimates are prone to *sampling variation*. For example, in this particular sample in Figure \@ref(fig:resampling-exercise-c), we observed three pennies with the year of 1999. If we sampled another 50 pennies, would we observe exactly three pennies with the year of 1999 again? More than likely not. We might observe none, or one, or two, or maybe even all 50! The same can be said for the other 26 unique years that are represented in our sample of 50 pennies.

To study the effects of *sampling variation* in Chapter \@ref(sampling) we took many samples, something we could easily do with our shovel. In our case with pennies however, how would we obtain another sample? By going to the bank and getting another roll of 50 pennies. Say we're feeling lazy however and don't want to go back to the bank. How can we study the effects of sampling variation using our *single sample*. We will do so using a technique known as "bootstrap resampling with replacement," which we now illustrate.

### Resampling once

**Step 1**: Let's print out identically-sized slips of paper representing our 50 pennies as seen in Figure \@ref(fig:tactile-resampling-1).

\begin{figure}
\includegraphics[width=0.5\linewidth]{images/sampling/pennies/tactile_simulation/1_paper_slips} \caption{Step 1: 50 slips of paper representing 50 US pennies.}(\#fig:tactile-resampling-1)
\end{figure}

**Step 2**: Put the 50 slips of paper into a hat or tuque as seen in Figure \@ref(fig:tactile-resampling-2).

\begin{figure}
\includegraphics[width=0.5\linewidth]{images/sampling/pennies/tactile_simulation/2_insert_in_hat} \caption{Step 2: Putting 50 slips of paper in a hat.}(\#fig:tactile-resampling-2)
\end{figure}

**Step 3**: Mix the hat's contents and draw one slip of paper at random as seen in Figure \@ref(fig:tactile-resampling-3). Record the year.

\begin{figure}
\includegraphics[width=0.5\linewidth]{images/sampling/pennies/tactile_simulation/3_draw_at_random} \caption{Step 3: Drawing one slip of paper at random.}(\#fig:tactile-resampling-3)
\end{figure}

**Step 4**: Put the slip of paper back in the hat! In other words, replace it as seen in Figure \@ref(fig:tactile-resampling-4). 

\begin{figure}
\includegraphics[width=0.5\linewidth]{images/sampling/pennies/tactile_simulation/4_put_it_back} \caption{Step 4: Replacing slip of paper.}(\#fig:tactile-resampling-4)
\end{figure}

**Step 5**: Repeat Steps 3 and 4 49 more times, resulting in 50 recorded years.

What we just performed was a *resampling* \index{resampling} of the original sample of 50 pennies. We are not sampling 50 pennies from the population of all US pennies as we did in our trip to the bank. Instead, we are mimicking this act by resampling 50 pennies from our original sample of 50 pennies. 

Now ask yourselves, why did we replace our resampled slip of paper back into the hat in Step 4? Because if we left the slip of paper out of the hat each time we performed Step 4, we would end up with the same 50 original pennies! In other words, replacing the slips of paper induces *sampling variation*.

Being more precise with our terminology, we just performed a *resampling with replacement* from the original sample of 50 pennies. Had we left the slip of paper out of the hat each time we performed Step 4, this would be *resampling without replacement*.

Let's study our 50 resampled pennies via an exploratory data analysis. First, let's load the data into R by manually creating a data frame `pennies_resample` of our 50 resampled values. We'll do this using the `tibble()` command from the `dplyr` package. Note that the 50 values you resample will almost certainly not be the same as ours given the inherent randomness.


```r
pennies_resample <- tibble(
  year = c(1976, 1962, 1976, 1983, 2017, 2015, 2015, 1962, 2016, 1976, 
           2006, 1997, 1988, 2015, 2015, 1988, 2016, 1978, 1979, 1997, 
           1974, 2013, 1978, 2015, 2008, 1982, 1986, 1979, 1981, 2004, 
           2000, 1995, 1999, 2006, 1979, 2015, 1979, 1998, 1981, 2015, 
           2000, 1999, 1988, 2017, 1992, 1997, 1990, 1988, 2006, 2000)
)
```

The 50 values of `year` in `pennies_resample` represent a resample of size 50 from the original sample of 50 pennies. We display the 50 resampled pennies in Figure \@ref(fig:resampling-exercise-d).

\begin{figure}
\includegraphics[width=1\linewidth]{images/sampling/pennies/deliverable/4} \caption{50 resampled US pennies labelled.}(\#fig:resampling-exercise-d)
\end{figure}

Let's compare the distribution of the numerical variable `year` of our 50 resampled pennies with the distribution of the numerical variable `year` of our original sample of 50 pennies in Figure \@ref(fig:origandresample).


```r
ggplot(pennies_resample, aes(x = year)) +
  geom_histogram(binwidth = 10, color = "white") +
  labs(title = "Resample of 50 pennies")
ggplot(pennies_sample, aes(x = year)) +
  geom_histogram(binwidth = 10, color = "white") +
  labs(title = "Original sample of 50 pennies")
```

(ref:compare-plots) Comparing `year` in the resampled `pennies_resample` with the original sample `pennies_sample`.


```
## Warning: Removed 2 rows containing missing values (geom_bar).

## Warning: Removed 2 rows containing missing values (geom_bar).
```

![(\#fig:origandresample)(ref:compare-plots)](09-confidence-intervals_files/figure-latex/origandresample-1.pdf) 

Observe in Figure \@ref(fig:origandresample) that while the general shapes of both distributions of `year` is roughly similar, they are not identical. 

Recall from the previous section that the sample mean of the original sample of 50 pennies from the bank was 1995.44. What about for our resample? Any guesses? Let's have `dplyr` help us out as before:


```r
pennies_resample %>% 
  summarize(mean_year = mean(year))
```

```
## # A tibble: 1 x 1
##   mean_year
##       <dbl>
## 1     1995.
```


We obtained a different mean year of 1994.74. This variation is induced by resampling *with replacement* we performed earlier.

What if we repeated this resampling exercise many times? Would we obtain the same mean `year` each time? In other words, would our guess at the mean year of all pennies in the US in 2019 be exactly 1994.74 every time? Just as we did in Chapter \@ref(sampling), let's perform this resampling activity with the help of 35 of our friends.


### Resampling 35 times {#student-resamples}

Each of our 35 friends will repeat the same 5 steps:

1. Start with 50 identically-sized slips of paper representing the 50 pennies. 
1. Put the 50 small pieces of paper into a hat or beanie cap.
1. Mix the hat's contents and draw one slip of paper at random. Record the year in a spreadsheet.
1. Replace the slip of paper back in the hat! 
1. Repeat Steps 3 and 4 49 more times, resulting in 50 recorded years.

Since we had 35 of our friends perform this task, we ended up with 35 $\times$ 50 = 1750 values. We recorded these values in a [shared spreadsheet](https://docs.google.com/spreadsheets/d/1y3kOsU_wDrDd5eiJbEtLeHT9L5SvpZb_TrzwFBsouk0/) with 50 rows (plus a header row) and 35 columns. We display a snapshot of the first 10 rows and 5 columns of this shared spreadsheet in Figure \@ref(fig:tactile-resampling-5).


\begin{figure}
\includegraphics[width=0.7\linewidth]{images/sampling/pennies/tactile_simulation/5_shared_spreadsheet} \caption{Snapshot of shared spreadsheet of resampled pennies.}(\#fig:tactile-resampling-5)
\end{figure}

For your convenience, we've taken these 35 $\times$ 50 = 1750 values and saved them in `pennies_resamples`, a "tidy" data frame included in the `moderndive` package. We saw what it means for a data frame to be "tidy".


```r
pennies_resamples
```

```
## # A tibble: 1,750 x 3
## # Groups:   name [35]
##    replicate name     year
##        <int> <chr>   <dbl>
##  1         1 Arianna  1988
##  2         1 Arianna  2002
##  3         1 Arianna  2015
##  4         1 Arianna  1998
##  5         1 Arianna  1979
##  6         1 Arianna  1971
##  7         1 Arianna  1971
##  8         1 Arianna  2015
##  9         1 Arianna  1988
## 10         1 Arianna  1979
## # ... with 1,740 more rows
```

What did each of our 35 friends obtain as the mean year? Once again, `dplyr` to the rescue! After grouping the rows by `name`, we summarize each group of 50 rows by their mean `year`:


```r
resampled_means <- pennies_resamples %>% 
  group_by(name) %>% 
  summarize(mean_year = mean(year))
```

```
## `summarise()` ungrouping output (override with `.groups` argument)
```

```r
resampled_means
```

```
## # A tibble: 35 x 2
##    name      mean_year
##    <chr>         <dbl>
##  1 Arianna       1992.
##  2 Artemis       1996.
##  3 Bea           1996.
##  4 Camryn        1997.
##  5 Cassandra     1991.
##  6 Cindy         1995.
##  7 Claire        1996.
##  8 Dahlia        1998.
##  9 Dan           1994.
## 10 Eindra        1994.
## # ... with 25 more rows
```

Observe that `resampled_means` has 35 rows corresponding to the 35 means based on the 35 resamples. Furthermore, observe the variation in the 35 values in the variable `mean_year`. Let's visualize this variation using a histogram in Figure \@ref(fig:tactile-resampling-6). Recall that adding the argument `boundary = 1990` to the `geom_histogram()` sets the binning structure so that one of the bin boundaries is 1990 exactly. 


```r
ggplot(resampled_means, aes(x = mean_year)) +
  geom_histogram(binwidth = 1, color = "white", boundary = 1990) +
  labs(x = "Sampled mean year")
```

![(\#fig:tactile-resampling-6)Distribution of 35 sample means from 35 resamples.](09-confidence-intervals_files/figure-latex/tactile-resampling-6-1.pdf) 

Observe in Figure \@ref(fig:tactile-resampling-6) that the distribution looks roughly normal and that we rarely observe sample mean years less than in 1992 or greater than 2000. Also observe how the distribution is roughly centered at 1995, which is the sample mean of 1995.44 of the *original sample* of 50 pennies from the bank.


### What did we just do?

What we just demonstrated in this activity is the statistical procedure known as *bootstrap resampling with replacement* \index{bootstrap}. We used *resampling* to mimic the sampling variation we studied in Chapter \@ref(sampling) on sampling. However in this case, we did so using only a *single* sample from the population.

In fact, the histogram of sample means from 35 resamples in Figure \@ref(fig:tactile-resampling-6) is called the *bootstrap distribution* \index{bootstrap!distribution}. It is an *approximation* to the *sampling distribution* of the sample mean, in the sense that both distributions will have a similar shape and similar spread. In fact in the upcoming Section \@ref(ci-conclusion), we'll show you that this is the case.  

Using this bootstrap distribution, we can study the effect of sampling variation on our estimates. In particular, we'll study the typical "error" of our estimates, known as the *standard error* \index{standard error}. 

In Section \@ref(resampling-simulation) we'll mimic our tactile resampling activity virtually on the computer, allowing us to quickly perform the resampling many more than 35 times. In Section \@ref(ci-build-up) we'll define the statistical concept of a *confidence interval*, which builds off bootstrap distributions.

In Section \@ref(bootstrap-process), construct confidence intervals using the `dplyr` package, as well as a new package: the `infer` package for "tidy" and transparent statistical inference. We've already used one of the `infer` package's functions, `rep_sample_n()`, but there's a lot more. We'll introduce the "tidy" statistical inference framework that was the motivation for the `infer` package pipeline that will be the driving package throughout the rest of this book.


## Computer simulation of resampling {#resampling-simulation}

Let's now mimic our tactile resampling activity virtually by using our computer.

### Virtually resampling once

First, let's perform the virtual analog of resampling once. Recall that the `pennies_sample` data frame included in the `moderndive` package contains the years of our original sample of 50 pennies from the bank. Furthermore, recall in Chapter \@ref(sampling) on sampling that we used the `rep_sample_n()` function as a virtual shovel to sample balls from our virtual bowl of 2400 balls as follows: 


```r
virtual_shovel <- bowl %>% 
  rep_sample_n(size = 50)
```

Let's modify this code to perform the resampling with replacement of the 50 slips of paper representing our original sample 50 pennies:


```r
virtual_resample <- pennies_sample %>% 
  rep_sample_n(size = 50, replace = TRUE)
```

Observe how we explicitly set the `replace` argument to `TRUE` in order to tell `rep_sample_n()` that we would like to sample pennies \index{sampling!with replacement} *with* replacement. Had we not set `replace = TRUE`, the function would've assumed the default value of `FALSE` and hence done resampling *without* replacement. Additionally, since we didn't specify the number of replicates via the `reps` argument, the function assumes the default of one replicate `reps = 1`. Lastly, observe also that the `size` argument is set to match the original sample size of 50 pennies. 

Let's look at only the first 10 out of 50 rows of `virtual_resample`:


```r
virtual_resample
```

```
## # A tibble: 50 x 3
## # Groups:   replicate [1]
##    replicate    ID  year
##        <int> <int> <dbl>
##  1         1    12  1995
##  2         1    19  1983
##  3         1    10  2000
##  4         1     1  2002
##  5         1    24  2017
##  6         1    28  2006
##  7         1    27  1993
##  8         1    50  2017
##  9         1    46  2017
## 10         1    38  1999
## # ... with 40 more rows
```

The `replicate` variable only takes on the value of 1 corresponding to us only having `reps = 1`, the `ID` variable indicates which of the 50 pennies from `pennies_sample` was resampled, and `year` denotes the year of minting. 

Let's now compute the mean `year` in our virtual resample of size 50 using data wrangling functions included in the `dplyr` package:


```r
virtual_resample %>% 
  summarize(resample_mean = mean(year))
```

```
## `summarise()` ungrouping output (override with `.groups` argument)
```

```
## # A tibble: 1 x 2
##   replicate resample_mean
##       <int>         <dbl>
## 1         1         1997.
```

As we saw when we did our tactile resampling exercise, the resulting mean year is different than the mean year of our 50 originally sampled pennies of 1995.44.

### Virtually resampling 35 times {#bootstrap-35-replicates}

Let's now perform the virtual analog of our 35 friends' resampling. Using these results, we'll be able to study the variability in the sample means from 35 resamples of size 50. Let's first add a `reps = 35` argument to `rep_sample_n()` \index{infer!rep\_sample\_n()} to indicate we would like 35 replicates. Thus, we want to repeat the resampling with the replacement of 50 pennies 35 times.


```r
virtual_resamples <- pennies_sample %>% 
  rep_sample_n(size = 50, replace = TRUE, reps = 35)
virtual_resamples
```

```
## # A tibble: 1,750 x 3
## # Groups:   replicate [35]
##    replicate    ID  year
##        <int> <int> <dbl>
##  1         1    13  2015
##  2         1    24  2017
##  3         1    11  1994
##  4         1    10  2000
##  5         1     8  1996
##  6         1    41  1992
##  7         1    22  1976
##  8         1    45  1997
##  9         1    48  1988
## 10         1    15  1974
## # ... with 1,740 more rows
```

The resulting `virtual_resamples` data frame has 35 $\times$ 50 = 1750 rows corresponding to 35 resamples of 50 pennies. Let's now compute the resulting 35 sample means using the same `dplyr` code as we did in the previous section, but this time adding a `group_by(replicate)`:


```r
virtual_resampled_means <- virtual_resamples %>% 
  group_by(replicate) %>% 
  summarize(mean_year = mean(year))
```

```
## `summarise()` ungrouping output (override with `.groups` argument)
```

```r
virtual_resampled_means
```

```
## # A tibble: 35 x 2
##    replicate mean_year
##        <int>     <dbl>
##  1         1     1996.
##  2         2     1996.
##  3         3     1995 
##  4         4     1995.
##  5         5     1997.
##  6         6     1993.
##  7         7     1997.
##  8         8     1996.
##  9         9     1995.
## 10        10     1995.
## # ... with 25 more rows
```

Observe that `virtual_resampled_means` has 35 rows, corresponding to the 35 resampled means. Furthermore, observe that the values of `mean_year` vary. Let's visualize this variation using a histogram in Figure \@ref(fig:tactile-resampling-7).


```r
ggplot(virtual_resampled_means, aes(x = mean_year)) +
  geom_histogram(binwidth = 1, color = "white", boundary = 1990) +
  labs(x = "Resample mean year")
```

![(\#fig:tactile-resampling-7)Distribution of 35 sample means from 35 resamples.](09-confidence-intervals_files/figure-latex/tactile-resampling-7-1.pdf) 

Let's compare our virtually constructed bootstrap distribution with the one our 35 friends constructed via our tactile resampling exercise in Figure \@ref(fig:orig-and-resample-means). Observe how they are somewhat similar, but not identical.

![(\#fig:orig-and-resample-means)Comparing distributions of means from resamples.](09-confidence-intervals_files/figure-latex/orig-and-resample-means-1.pdf) 

Recall that in the "resampling with replacement" scenario we are illustrating here both of these histograms have a special name: the *bootstrap distribution of the sample mean*. Furthermore, they are an approximation to the *sampling distribution* of the sample mean, a concept you saw in Chapter \@ref(sampling) on sampling. These distributions allow us to study the effect of sampling variation on our estimates of the true population mean, in this case the true mean year for *all* US pennies. However, unlike in Chapter \@ref(sampling) where took multiple samples (something one would never do in practice), bootstrap distributions are constructed by taking multiple resamples from a *single* sample. In this case the 50 original pennies from the bank. 


### Virtually resampling 1000 times {#bootstrap-1000-replicates}

Remember that one of the goals of resampling with replacement is to construct the bootstrap distribution, which is an approximation of the sampling distribution. However, the bootstrap distribution in Figure \@ref(fig:tactile-resampling-7) is based only on 35 resamples and hence looks a little coarse. Let's increase the number of resamples to 1000, so that we can hopefully better see the shape and the variability between different resamples. 


```r
# Repeat resampling 1000 times
virtual_resamples <- pennies_sample %>% 
  rep_sample_n(size = 50, replace = TRUE, reps = 1000)

# Compute 1000 sample means
virtual_resampled_means <- virtual_resamples %>% 
  group_by(replicate) %>% 
  summarize(mean_year = mean(year))
```

```
## `summarise()` ungrouping output (override with `.groups` argument)
```

However, in the interest of brevity, going forward let's combine these two operations into a single chain of `%>%` pipe operators:


```r
virtual_resampled_means <- pennies_sample %>% 
  rep_sample_n(size = 50, replace = TRUE, reps = 1000) %>% 
  group_by(replicate) %>% 
  summarize(mean_year = mean(year))
```

```
## `summarise()` ungrouping output (override with `.groups` argument)
```

```r
virtual_resampled_means
```

```
## # A tibble: 1,000 x 2
##    replicate mean_year
##        <int>     <dbl>
##  1         1     1997.
##  2         2     1992.
##  3         3     1995.
##  4         4     1995.
##  5         5     1996.
##  6         6     1994.
##  7         7     1997.
##  8         8     1997.
##  9         9     1998.
## 10        10     1996.
## # ... with 990 more rows
```

In Figure \@ref(fig:one-thousand-sample-means) let's visualize the bootstrap distribution of these 1000 means based 1000 virtual resamples:


```r
ggplot(virtual_resampled_means, aes(x = mean_year)) +
  geom_histogram(binwidth = 1, color = "white", boundary = 1990) +
  labs(x = "sample mean")
```

![(\#fig:one-thousand-sample-means)Bootstrap resampling distribution based on 1000 resamples.](09-confidence-intervals_files/figure-latex/one-thousand-sample-means-1.pdf) 

Note here that the bell shape is starting to become much more apparent. We now have a general sense for the range of values that the sample mean may take on. But where is this histogram centered? Let's compute the mean of the 1000 resample means:


```r
virtual_resampled_means %>% 
  summarize(mean_of_means = mean(mean_year))
```

```
## # A tibble: 1 x 1
##   mean_of_means
##           <dbl>
## 1         1995.
```


The mean of these 1000 means is 1995.45, which is quite close to the mean of our original sample of 50 pennies of 1995.44. This is the case since each of the 1000 resamples are based on the original sample of 50 pennies.

Congratulations! You've just constructed your first bootstrap distribution! In the next section, you'll see how to use this bootstrap distribution to construct *confidence intervals*.

## Understanding confidence intervals {#ci-build-up}

Let's start this section with an analogy involving fishing. Say you are trying to catch a fish. On the one hand, you could use a spear, while on the other you could use a net. Using the net will probably allow you to catch more fish! 

Now think back to our pennies exercise where you are trying to estimate the true population mean year $\mu$ of *all* US pennies. \index{confidence interval!analogy to fishing} Think of the value of $\mu$ as a fish.

On the one hand, we could use the appropriate *point estimate/sample statistic* to estimate $\mu$, which we saw in Table \@ref(tab:table-ch8-b) is the sample mean $\overline{x}$. Based on our sample of 50 pennies from the bank, the sample mean was 1995.44. Think of using this value as "fishing with a spear."

What would "fishing with a net" correspond to? Look at the bootstrap distribution in Figure \@ref(fig:one-thousand-sample-means) once more. Between which two years would you say that "most" sample means lie?  While this question is somewhat subjective, saying that most sample means lie between 1992 and 2000 would not be unreasonable. Think of this interval as the "net."

What we've just illustrated is the concept of a *confidence interval*, which we'll abbreviate with "CI" throughout this book. As opposed to a point estimate/sample statistic that estimates the value of an unknown population parameter with a single value, a *confidence interval* \index{confidence interval} gives what can be interpreted as a range of plausible values. Going back to our analogy, point estimates/sample statistics can be thought of as spears, whereas confidence intervals can be thought of as nets. 


\begin{figure}

{\centering \includegraphics[width=1\linewidth]{images/shutterstock/point_estimate_vs_conf_int} 

}

\caption{Analogy of difference between point estimates and confidence intervals.}(\#fig:point-estimate-vs-conf-int)
\end{figure}

Our proposed interval of 1992 to 2000 was constructed by eye and was thus somewhat subjective. We now introduce two methods for constructing such intervals in a more exact fashion: the *percentile method* and the *standard error method*.

Both methods for confidence interval construction share some commonalities. First, they are both constructed from a bootstrap distribution, as you constructed in Subsection \@ref(bootstrap-1000-replicates) and visualized in Figure \@ref(fig:one-thousand-sample-means).

Second, they both require you to specify the \index{confidence level} *confidence level*. Commonly used confidence levels include 90%, 95%, and 99%.  All other things being equal, higher confidence levels correspond to wider confidence intervals and lower confidence levels correspond to narrower confidence intervals. In this book, we'll be mostly using 95% and hence constructing "95% confidence intervals for $\mu$."


### Percentile method {#percentile-method}



One method to construct a confidence interval is to use the middle 95% of values of the bootstrap distribution. We can do this by computing the 2.5^th^ and 97.5^th^ percentiles, which are  and  respectively. This is known as the *percentile method* for constructing confidence intervals. 

For now, let's focus only on the concepts behind a percentile method constructed confidence interval; we'll show you the code to compute these values in the next section.

Let's mark these percentiles on the bootstrap distribution with vertical lines in Figure \@ref(fig:percentile-method). About 95% of the values in the `mean_year` variable in `virtual_resampled_means` fall between the  and  endpoints, with 2.5% to the left of the left-most line and 2.5% to the right of the right-most line. 

![(\#fig:percentile-method)Percentile method 95 percent confidence interval. Interval marked by vertical lines.](09-confidence-intervals_files/figure-latex/percentile-method-1.pdf) 


### Standard error method {#se-method}



We know that if a numerical variable follows a normal distribution, or in other words the histogram of this variable is bell-shaped, then roughly 95% of values fall between $\pm$ 1.96 standard deviations of the mean. Given that our bootstrap distribution based on 1000 resamples with replacement in Figure \@ref(fig:one-thousand-sample-means) is normally shaped, let's use this fact about normal distributions to construct a confidence interval in a different way.

First, recall the bootstrap distribution has a mean equal to 1995.45. This value almost coincides exactly with the value of the sample mean $\overline{x}$ of our original 50 pennies of 1995.44. Second, let's compute the standard deviation of the bootstrap distribution using the values of `mean_year` in the `virtual_resampled_means` data frame:


```r
virtual_resampled_means %>% 
  summarize(SE = sd(mean_year))
```

```
## # A tibble: 1 x 1
##      SE
##   <dbl>
## 1  2.16
```

What is this value? Recall that the bootstrap distribution is an approximation to the sampling distribution. Recall also that the standard deviation of a sampling distribution has a special name: the *standard error*. Putting these two facts together, we can say that 2.15695 is an approximation of the standard error of $\overline{x}$.  

Thus, using our 95% rule of thumb about normal distributions, we can use the following formula to determine the lower and upper endpoints of a 95% confidence interval for $\mu$:

$$
\begin{aligned}
\overline{x} \pm 1.96 \cdot SE &= (\overline{x} - 1.96 \cdot SE, \overline{x} + 1.96 \cdot SE)\\
&= (1995.44 - 1.96 \cdot 2.16, 1995.44 + 1.96 \cdot 2.16)\\
&= (1991.15, 1999.73)
\end{aligned}
$$

Let's now add the SE method confidence interval with dashed lines in Figure \@ref(fig:percentile-and-se-method).

![(\#fig:percentile-and-se-method)Comparing two 95 percent confidence interval methods.](09-confidence-intervals_files/figure-latex/percentile-and-se-method-1.pdf) 

We see that both methods produce nearly identical 95% confidence intervals for $\mu$ with the percentile method yielding $(1991.4, 1999.66)$ while the standard error method being $(1991.21, 1999.67)$. However, recall that we can only use the standard error rule when the bootstrap distribution is roughly normally-shaped. 

Now that we've introduced the concept of confidence intervals and laid out the intuition behind two methods for constructing them, let's explore the code that allows us to construct them. 


## Constructing confidence intervals {#bootstrap-process}

Recall that the process of resampling with a replacement we performed by hand in Section \@ref(resampling-tactile) and virtually in Section \@ref(resampling-simulation) is known as \index{bootstrap!colloquial definition} *bootstrapping*. The term bootstrapping originates in the expression of "pulling oneself up by their bootstraps," meaning to ["succeed only by one's own efforts or abilities."](https://en.wiktionary.org/wiki/pull_oneself_up_by_one%27s_bootstraps) From a statistical perspective, it alludes to succeeding in being able to study the effects of sampling variation on estimates from the "effort" of a single sample. Or more precisely, \index{bootstrap!statistical reference} constructing an approximation to the sampling distribution using only one sample.

To perform this resampling with replacement virtually in Section \@ref(resampling-simulation), we used the `rep_sample_n()` function, making sure that the size of the resamples matched the original sample size of 50. In this section, we'll build off these ideas to construct confidence intervals using a new package: the `infer` package for "tidy" and transparent statistical inference. 

### Original workflow

Recall that in Section \@ref(resampling-simulation), we virtually performed bootstrap resampling with replacement to construct bootstrap distributions. Such distributions are approximations to the sampling distributions we saw in Chapter \@ref(sampling), but are constructed using only a single sample. Let's revisit the original workflow using the `%>%` pipe operator:

First, we used the `rep_sample_n()` function to resample `size = 50` pennies with replacement from the original sample of 50 pennies in `pennies_sample` by setting `replace = TRUE`. Furthermore, we repeated this resampling 1000 times by setting `reps = 1000`:


```r
pennies_sample %>% 
  rep_sample_n(size = 50, replace = TRUE, reps = 1000)
```

Second, since for each of our 1000 resamples of size 50, we wanted to compute a separate sample mean, we used the `dplyr` verb `group_by()` to group observations/rows together by the `replicate` variable...


```r
pennies_sample %>% 
  rep_sample_n(size = 50, replace = TRUE, reps = 1000) %>% 
  group_by(replicate) 
```

... followed by using `summarize()` to compute the sample `mean()` year for each `replicate` group:


```r
pennies_sample %>% 
  rep_sample_n(size = 50, replace = TRUE, reps = 1000) %>% 
  group_by(replicate) %>% 
  summarize(mean_year = mean(year))
```


For this simple case, we can get by with using the `rep_sample_n()` function and a couple of `dplyr` verbs to construct the bootstrap distribution. However, using only `dplyr` verbs only provides us with a limited set of tools. For more complicated situations, we'll need a little more firepower. Let's repeat this using the `infer` package.

### infer package workflow {#infer-workflow}

The `infer` package is an R package for statistical inference. It makes efficient use of the `%>%` pipe operator to spell out the sequence of steps necessary to perform statistical inference in a "tidy" and transparent fashion.\index{operators!pipe} Furthermore, just as the `dplyr` package provides functions with intuitive verb-like names to perform data wrangling, the `infer` package provides functions intuitive verb-like names to perform statistical inference.

Let's go back to our pennies. Previously, we computed the value of the sample mean $\overline{x}$ using the `dplyr` function `summarize()`:


```r
pennies_sample %>% 
  summarize(stat = mean(year))
```

We'll see that we can also do this using `infer` functions `specify()` and `calculate()`: \index{infer!observed statistic shortcut}


```r
pennies_sample %>% 
  specify(response = year) %>% 
  calculate(stat = "mean")
```

You might be asking yourself: "Isn't the `infer` code longer? Why would I use that code?" While not immediately apparent, you'll see that there are three chief benefits to the `infer` workflow as opposed to the `dplyr` workflow.

First, the `infer` verb names better align with the overall resampling framework you need to understand to construct confidence intervals and to conduct hypothesis tests (in Chapter \@ref(hypothesis-testing)). We'll see flowchart diagrams of this framework in the upcoming Figures \@ref(fig:infer-workflow-ci) and \@ref(fig:htdowney).

Second, you can jump back and forth seamlessly between confidence intervals and hypothesis testing with minimal changes to your code. This will become apparent in Subsection \@ref(comparing-infer-workflows) when we'll compare the `infer` code for both these inferential methods.

Third, the `infer` workflow is much simpler for conducting inference when you have *more than one variable*. We'll see two such situations. We'll first see situations of *two-sample* inference\index{two-sample inference} where the sample data is collected from two groups.

Let's now illustrate the sequence of verbs necessary to construct a confidence interval for $\mu$, the population mean year of minting of all pennies in the US.

#### 1. `specify` variables {-}

\begin{figure}

{\centering \includegraphics[width=0.2\linewidth]{images/flowcharts/infer/specify} 

}

\caption{Diagram of specify() variables.}(\#fig:infer-specify)
\end{figure}

The `specify()` \index{infer!specify()} function is used to choose which variables in a data frame will be the focus of our statistical inference. We do this by specifying the `response` argument. For example, in our `pennies_sample` data frame of the 50 pennies sampled from the bank, the variable of interest is `year`:


```r
pennies_sample %>% 
  specify(response = year)
```

```
## Response: year (numeric)
## # A tibble: 50 x 1
##     year
##    <dbl>
##  1  2002
##  2  1986
##  3  2017
##  4  1988
##  5  2008
##  6  1983
##  7  2008
##  8  1996
##  9  2004
## 10  2000
## # ... with 40 more rows
```

Notice how the data itself doesn't change, but the `Response: year (numeric)` *meta-data* does\index{meta-data}. This is similar to how the `group_by()` verb from `dplyr` doesn't change the data, but only adds "grouping" meta-data.

We can also specify which variables will be the focus of our statistical inference using a `formula = y ~ x`. The response variable `y` is separated from the explanatory variable `x` by a `~` "tilde." The following use of `specify()` with the `formula` argument yields the same result seen previously:


```r
pennies_sample %>% 
  specify(formula = year ~ NULL)
```

Since in the case of pennies we only have a response variable and no explanatory variable of interest, we set the `x` on the right-hand side of the `~` to be `NULL`. 


#### 2. `generate` replicates {-}

\begin{figure}

{\centering \includegraphics[width=0.5\linewidth]{images/flowcharts/infer/generate} 

}

\caption{Diagram of generate() replicates.}(\#fig:infer-generate)
\end{figure}

After we `specify()` the variables of interest, we pipe the results into the `generate()` function to generate replicates. In other words, repeat the resampling process a large number of times. Recall in Sections \@ref(bootstrap-35-replicates) and \@ref(bootstrap-1000-replicates) we did this 35 and 1000 times.

The `generate()` \index{infer!generate()} function's first argument is `reps`, which sets the number of replicates we would like to generate. Since we want to resample the 50 pennies in `pennies_sample` with replacement 1000 times, we set `reps = 1000`. The second argument `type` determines the type of computer simulation we'd like to perform. We set this to `type = "bootstrap"` indicating that we want to perform bootstrap resampling. You'll see different options for `type` in Chapter \@ref(hypothesis-testing). 


```r
pennies_sample %>% 
  specify(response = year) %>% 
  generate(reps = 1000, type = "bootstrap")
```


```
## Response: year (numeric)
## # A tibble: 50,000 x 2
## # Groups:   replicate [1,000]
##    replicate  year
##        <int> <dbl>
##  1         1  1978
##  2         1  1997
##  3         1  2004
##  4         1  1983
##  5         1  2004
##  6         1  1988
##  7         1  1999
##  8         1  2017
##  9         1  2015
## 10         1  2018
## # ... with 49,990 more rows
```

Observe that the resulting data frame has 50,000 rows. This is because we performed resampling of 50 pennies with replacement 1000 times and 50,000 = 50 $\times$ 1000. The variable `replicate` indicates which resample each row belongs to. So it has the value `1` 50 times, the value `2` 50 times, all the way through to the value `1000` 50 times. 

The default value of the `type` argument is `"bootstrap"`, so if the last line was written as `generate(reps = 1000)`, we'd obtain the same results. 

**Comparing with original workflow**: Note that the steps up of the infer workflow so far produce the same results as the original workflow using the `rep_sample_n()` function we saw earlier. In other words, the following two code chunks produce similar results:


```r
# infer workflow:                   # Original workflow:
pennies_sample %>%                  pennies_sample %>% 
  specify(response = year) %>%        rep_sample_n(size = 50, replace = TRUE, 
  generate(reps = 1000)                            reps = 1000)              
```


#### 3. `calculate` summary statistics {-}

\begin{figure}

{\centering \includegraphics[width=0.7\linewidth]{images/flowcharts/infer/calculate} 

}

\caption{Diagram of calculate() summary statistics.}(\#fig:infer-calculate)
\end{figure}

After we `generate()` many replicates of bootstrap resampling with replacement, we next want to summarize each of 1000 resamples of size 50 to a single statistic value. As seen in the diagram, the `calculate()` \index{infer!calculate()} function does this.

In our case, we want to calculate the mean `year` for each bootstrap resample of size 50. To do so, we set the `stat` argument to `"mean"`. You can also set the `stat` argument to a variety of other common summary statistics, like `"median"`, `"sum"`, `"sd"` (standard deviation), and `"prop"` (proportion). To see a list of all possible summary statistics you can use, type `?calculate` to read the help file. We'll use these `stat` functions throughout this book.

Let's save the result in a data frame called `bootstrap_distribution` and explore it's contents:


```r
bootstrap_distribution <- pennies_sample %>% 
  specify(response = year) %>% 
  generate(reps = 1000) %>% 
  calculate(stat = "mean")
bootstrap_distribution
```


```
## # A tibble: 1,000 x 2
##    replicate  stat
##        <int> <dbl>
##  1         1 1997.
##  2         2 1993.
##  3         3 1997.
##  4         4 1996.
##  5         5 1997.
##  6         6 1991.
##  7         7 1995.
##  8         8 1997.
##  9         9 1992.
## 10        10 1997.
## # ... with 990 more rows
```

Observe that the resulting data frame has 1000 rows and 2 columns corresponding to the 1000 `replicate` values and the mean year for each bootstrap resample saved in the variable `stat`. 

**Comparing with original workflow**: You may have recognized at this point that the `calculate()` step in the `infer` workflow produces the same output as the `group_by() %>% summarize()` steps in the original workflow: 


```r
# infer workflow:                   # Original workflow:
pennies_sample %>%                  pennies_sample %>% 
  specify(response = year) %>%        rep_sample_n(size = 50, replace = TRUE, 
  generate(reps = 1000) %>%                        reps = 1000) %>%              
  calculate(stat = "mean")            group_by(replicate) %>% 
                                      summarize(mean_year = mean(year))
```


#### 4. `visualize` the results {-}

\begin{figure}

{\centering \includegraphics[width=1\linewidth]{images/flowcharts/infer/visualize} 

}

\caption{Diagram of visualize() results.}(\#fig:infer-visualize)
\end{figure}

The `visualize()` \index{infer!visualize()} verb provides a quick way to visualize the bootstrap distribution as a histogram of the numerical `stat` variable's values.  


```r
visualize(bootstrap_distribution)
```

![(\#fig:boostrap-distribution-infer)Bootstrap distribution.](09-confidence-intervals_files/figure-latex/boostrap-distribution-infer-1.pdf) 

**Comparing with original workflow**: In fact, `visualize()` is a *wrapper function* for the `ggplot()` function that uses a `geom_histogram()` layer. 


```r
# infer workflow:                    # Original workflow:
visualize(bootstrap_distribution)    ggplot(bootstrap_distribution, 
                                            aes(x = stat)) +
                                       geom_histogram()
```

The `visualize()` function can take many other arguments which we'll see momentarily to customize the plot further. It also works with helper functions to do the shading of the histogram values corresponding to the confidence interval values.

Let's recap the steps of the `infer` workflow for constructing a bootstrap distribution and then visualizing it.

\begin{figure}

{\centering \includegraphics[width=1\linewidth]{images/flowcharts/infer/ci_diagram} 

}

\caption{infer package workflow for confidence intervals.}(\#fig:infer-workflow-ci)
\end{figure}

Recall how we introduced two different methods for constructing 95% confidence intervals for an unknown population parameter in Section \@ref(ci-build-up): the *percentile method* and the *standard error method*. Let's now check out the `infer` package code that explicitly constructs these. There are also some additional neat functions to visualize the resulting confidence intervals built-in!


### Percentile method with infer {#percentile-method-infer}

Recall the percentile method for constructing 95% confidence intervals we introduced in Section \@ref(percentile-method). This method sets the lower endpoint of the confidence interval at the 2.5^th^ percentile of the bootstrap distribution and similarly sets the upper endpoint at the 97.5^th^ percentile. The resulting interval captures the middle 95% of the values of the sample mean in the bootstrap distribution.

We can compute the 95% confidence interval by piping the `bootstrap_distribution` data frame we created into the `get_confidence_interval()` \index{infer!get\_confidence\_interval()} function from the `infer` package, with the confidence `level` set to 0.95 and the confidence interval `type` to be percentile. Let's save the results in `percentile_ci`.


```r
percentile_ci <- bootstrap_distribution %>% 
  get_confidence_interval(level = 0.95, type = "percentile")
percentile_ci
```

```
## # A tibble: 1 x 2
##   lower_ci upper_ci
##      <dbl>    <dbl>
## 1    1991.    2000.
```

Alternatively, we can visualize the interval (1991.34, 1999.54) by piping the `bootstrap_distribution` data frame into the `visualize()` function and adding a `shade_confidence_interval()` \index{infer!shade\_confidence\_interval()} layer. We set the `endpoints` argument to be `percentile_ci`.


```r
visualize(bootstrap_distribution) + 
  shade_confidence_interval(endpoints = percentile_ci)
```

![(\#fig:percentile-ci-viz)Percentile method 95 percent confidence interval shaded corresponding to potential values.](09-confidence-intervals_files/figure-latex/percentile-ci-viz-1.pdf) 

Observe in Figure \@ref(fig:percentile-ci-viz) that 95% of the sample means stored in the `stat` variable in `bootstrap_distribution` fall between the two endpoints marked with the darker lines, with 2.5% of the sample means to the left of the shaded area and 2.5% of the sample means to the right. You also have the option to change the colors of the shading using the `color` and `fill` arguments. 

You can also use the shorter named function `shade_ci()` and the results will be the same. This is for folks that don't want to type out all of `confidence_interval` and prefer to type out `ci` instead. Try out the following code!


```r
visualize(bootstrap_distribution) + 
  shade_ci(endpoints = percentile_ci, color = "hotpink", fill = "khaki")
```


### Standard error method with infer {#infer-se}

Recall the standard error method for constructing 95% confidence intervals we introduced in Section \@ref(se-method). For any distribution that is normally shaped, roughly 95% of the values lie within two standard deviations of the mean. In the case of the bootstrap distribution, the standard deviation has a special name: the standard error. 

So in our case, 95% of values of the bootstrap distribution will lie within $\pm$ 1.96 standard errors of $\overline{x}$. Thus, a 95% confidence interval is $\overline{x} \pm 1.96 \cdot SE$ = $(\overline{x} - 1.96 \cdot SE,$ $\overline{x} + 1.96 \cdot SE)$.

Computation of the 95% confidence interval can once again be done by piping the `bootstrap_distribution` data frame we created into the `get_confidence_interval()` function. However, this time we set the first `type` argument to be `"se"`. Second, we must specify the `point_estimate` argument in order to set the center of the confidence interval. We set this to be the sample mean of the original sample of 50 pennies of 1995.44.


```r
standard_error_ci <- bootstrap_distribution %>% 
  get_confidence_interval(type = "se", point_estimate = 1995.44)
```

```
## Using `level = 0.95` to compute confidence interval.
```

```r
standard_error_ci
```

```
## # A tibble: 1 x 2
##   lower_ci upper_ci
##      <dbl>    <dbl>
## 1    1991.    2000.
```

If we would like to visualize the interval (1991.32, 1999.56), we can once again pipe the `bootstrap_distribution` data frame into the `visualize()` function and add a `shade_confidence_interval()` layer to our plot. We set the `endpoints` argument to be `standard_error_ci`. The resulting standard-error method based 95% confidence interval for $\mu$ can be seen in Figure \@ref(fig:se-ci-viz).


```r
visualize(bootstrap_distribution) + 
  shade_confidence_interval(endpoints = standard_error_ci)
```
![(\#fig:se-ci-viz)Standard error method 95 percent confidence interval.](09-confidence-intervals_files/figure-latex/se-ci-viz-1.pdf) 





## Interpreting confidence intervals {#one-prop-ci}

Now that we've shown you how to construct confidence intervals using a sample drawn from a population, let's now focus on how to interpret their effectiveness. The effectiveness of a confidence interval is judged by whether or not it contains the true value of the population parameter. Going back to our fishing analogy in Section \@ref(ci-build-up), this is like asking "Did our net capture the fish?"

So for example, does our percentile-based confidence interval of (1991.34, 1999.54) "capture" the true mean year $\mu$ of *all* US pennies? Alas, we'll never know, because we don't know what the true value of $\mu$ is. After all, we're sampling to estimate it!

In order to interpret a confidence interval's effectiveness, we need to *know* what the value of the population parameter is. That way we can say whether or not a confidence interval "captured" this value. 

Let's revisit our sampling bowl from Chapter \@ref(sampling). What proportion of the bowl's 2400 balls are red? Let's compute this:


```r
bowl %>% 
  summarize(p_red = mean(color == "red"))
```

```
## # A tibble: 1 x 1
##   p_red
##   <dbl>
## 1 0.375
```


In this case, we *know* what the value of the population parameter is: we know that the population proportion $p$ is 0.375. In other words, we know that 37.5% of the bowl's balls are red. 

As we stated in Subsection \@ref(moral-of-the-story), the sampling bowl exercise doesn't really reflect how sampling is done in real-life, but rather was an *idealized* activity. In real-life, we won't know what the true value of the population parameter is, hence the need for estimation.

Let's now construct confidence intervals for $p$ using our 33 groups of friends' samples from the bowl in Chapter \@ref(sampling). We'll then see if the confidence intervals "captured" the true value of $p$, which we know to be 37.5%. In other words: "Did net capture the fish?"


### Did the net capture the fish? {#ilyas-yohan}

Recall that we had 33 groups of friends each take samples of size 50 from the bowl and then compute the sample proportion of red $\widehat{p}$. This resulted in 33 such estimates of $p$. Let's focus on Ilyas and Yohan's sample, which is saved in the `bowl_sample_1` data frame in the `moderndive` package:


```r
bowl_sample_1
```

```
## # A tibble: 50 x 1
##    color
##    <chr>
##  1 white
##  2 white
##  3 red  
##  4 red  
##  5 white
##  6 white
##  7 red  
##  8 white
##  9 white
## 10 white
## # ... with 40 more rows
```

They observed 21 red balls out of 50 and thus their sample proportion $\widehat{p}$ was 21/50 = 0.42 = 42\%. Think of this as the "spear" from our fishing analogy. 

Let's now follow the `infer` package workflow from Section \@ref(infer-workflow) to create a percentile method based 95% confidence interval for $p$ using Ilyas and Yohan's sample. Think of this as the "net."

#### 1. `specify` variables {-}

First, we `specify()` the `response` variable of interest `color`:


```r
bowl_sample_1 %>% 
  specify(response = color)
```
```
Error: A level of the response variable `color` needs to be specified for the `success`
argument in `specify()`.
```

Whoops! We need to define which event is of interest! `red` or `white` balls? Since we are interested in the proportion red, let's set `success` to be `"red"`:


```r
bowl_sample_1 %>% 
  specify(response = color, success = "red")
```

```
## Response: color (factor)
## # A tibble: 50 x 1
##    color
##    <fct>
##  1 white
##  2 white
##  3 red  
##  4 red  
##  5 white
##  6 white
##  7 red  
##  8 white
##  9 white
## 10 white
## # ... with 40 more rows
```

#### 2. `generate` replicates {-}

Second, we `generate()` 1000 replicates of *bootstrap resampling with replacement* from `bowl_sample_1` by setting `reps = 1000` and `type = "bootstrap"`. 


```r
bowl_sample_1 %>% 
  specify(response = color, success = "red") %>% 
  generate(reps = 1000, type = "bootstrap")
```

```
## Response: color (factor)
## # A tibble: 50,000 x 2
## # Groups:   replicate [1,000]
##    replicate color
##        <int> <fct>
##  1         1 white
##  2         1 white
##  3         1 red  
##  4         1 white
##  5         1 red  
##  6         1 red  
##  7         1 red  
##  8         1 red  
##  9         1 red  
## 10         1 white
## # ... with 49,990 more rows
```

Observe that the resulting data frame has 50,000 rows. This is because we performed resampling of 50 balls with replacement 1000 times and thus 50,000 = 50 $\times$ 1000. The variable `replicate` indicates which resample each row belongs to. So it has the value `1` 50 times, the value `2` 50 times, all the way through to the value `1000` 50 times. 

#### 3. `calculate` summary statistics {-}

Third, we summarize each of 1000 resamples of size 50 with the proportion of "successes". In other words, the proportion of the balls that are `"red"`. We can set the summary statistic to be calculated to be the proportion by setting the `stat` argument to be `"prop"`. Let's save the result in a data frame called `sample_1_bootstrap`:


```r
sample_1_bootstrap <- bowl_sample_1 %>% 
  specify(response = color, success = "red") %>% 
  generate(reps = 1000, type = "bootstrap") %>% 
  calculate(stat = "prop")
sample_1_bootstrap
```


```
## # A tibble: 1,000 x 2
##    replicate  stat
##        <int> <dbl>
##  1         1  0.52
##  2         2  0.5 
##  3         3  0.5 
##  4         4  0.38
##  5         5  0.52
##  6         6  0.44
##  7         7  0.46
##  8         8  0.54
##  9         9  0.4 
## 10        10  0.36
## # ... with 990 more rows
```

Observe there are 1000 rows in this data frame and thus 1000 values of the variable `stat`. These 1000 values of `stat` represent our 1000 replicated values of the proportion, each based on a different resample.

#### 4. `visualize` the results {-}

Fourth and lastly, let's compute the resulting 95% confidence interval. 


```r
percentile_ci_1 <- sample_1_bootstrap %>% 
  get_confidence_interval(level = 0.95, type = "percentile")
percentile_ci_1
```

```
## # A tibble: 1 x 2
##   lower_ci upper_ci
##      <dbl>    <dbl>
## 1     0.28    0.560
```

Let's visualize the bootstrap distribution along with the `percentile_ci_1` percentile-based 95% confidence interval for $p$ in Figure \@ref(fig:shovel-bootstrap-1-infer). We'll adjust the number of bins to better see the resulting shape. Furthermore, we'll add a dashed vertical line at Ilyas and Yohan's observed $\widehat{p}$ = 21/50 = 0.42 = 42\% using `geom_vline()`.


```r
sample_1_bootstrap %>% 
  visualize(bins = 15) + 
  shade_confidence_interval(endpoints = percentile_ci_1) +
  geom_vline(xintercept = 0.375, linetype = "dashed")
```
![(\#fig:shovel-bootstrap-1-infer)Bootstrap distribution.](09-confidence-intervals_files/figure-latex/shovel-bootstrap-1-infer-1.pdf) 

Did Ilyas and Yohan's net capture the fish? In other words, did their 95% confidence interval for $p$ based on their sample contain the true value of $p$ of 0.375? Yes! 0.375 is between the endpoints of our confidence interval (0.28, 0.5605).

However, will *every* 95% confidence interval for $p$ capture this value? In other words, if we had a different sample of  50 balls and constructed a different confidence interval, would it necessarily contain $p$ = 0.375 as well? Let's see!

Let's first take a different sample from the bowl, this time using the computer as we did in Chapter \@ref(sampling):


```r
bowl_sample_2 <- bowl %>% 
  rep_sample_n(size = 50)
bowl_sample_2
```

```
## # A tibble: 50 x 3
## # Groups:   replicate [1]
##    replicate ball_ID color
##        <int>   <int> <chr>
##  1         1     681 red  
##  2         1    2012 red  
##  3         1    1943 red  
##  4         1     887 white
##  5         1    2266 red  
##  6         1     477 white
##  7         1    2225 white
##  8         1    1132 red  
##  9         1    1216 white
## 10         1    2029 white
## # ... with 40 more rows
```

Let's reapply the same `infer` functions on `bowl_sample_2` to generate a different 95% confidence interval for $p$. First we create the new bootstrap distribution and save the results in `sample_2_bootstrap`:


```r
sample_2_bootstrap <- bowl_sample_2 %>% 
  specify(response = color, success = "red") %>% 
  generate(reps = 1000, type = "bootstrap") %>% 
  calculate(stat = "prop")
sample_2_bootstrap
```


```
## # A tibble: 1,000 x 2
##    replicate  stat
##        <int> <dbl>
##  1         1  0.4 
##  2         2  0.28
##  3         3  0.28
##  4         4  0.24
##  5         5  0.3 
##  6         6  0.24
##  7         7  0.26
##  8         8  0.24
##  9         9  0.36
## 10        10  0.3 
## # ... with 990 more rows
```

We once again compute a percentile-based 95% confidence interval for $p$: 


```r
percentile_ci_2 <- sample_2_bootstrap %>% 
  get_confidence_interval(level = 0.95, type = "percentile")
percentile_ci_2
```

```
## # A tibble: 1 x 2
##   lower_ci upper_ci
##      <dbl>    <dbl>
## 1     0.16      0.4
```

Does this new net capture the fish? In other words, does the 95% confidence interval for $p$ based on the new sample contain the true value of $p$ of 0.375? Yes again! 0.375 is between the endpoints of our confidence interval (0.16, 0.4).

Let's now repeat this process 100 more times: we take 100 virtual samples from the bowl and construct 100 95% confidence intervals. Let's visualize the results in Figure \@ref(fig:reliable-percentile) where:

1. We mark the true value of $p$ = 0.375 with a vertical line.
1. We mark each of the 100 95% confidence intervals with horizontal lines. These are the "nets."
1. The horizontal line is colored grey if the confidence interval "captures" the true value of $p$ marked with the vertical line. The horizontal line is colored black otherwise.


```
## Warning: Using alpha for a discrete variable is not advised.
```

![(\#fig:reliable-percentile)100 percentile-based 95 percent confidence intervals for $p$.](09-confidence-intervals_files/figure-latex/reliable-percentile-1.pdf) 

Of the 100 95% confidence intervals, 95 of them captured the true value $p$ = 0.375, whereas 5 of them didn't. In other words, 95 of our nets caught the fish, whereas 5 of our nets didn't. 

This is where the "95% confidence level" we defined in Section \@ref(ci-build-up) comes into play: for every 100 95% confidence intervals, we *expect* that 95 of them will capture $p$ and that 5 of them won't. 

Note that "expect" is a probabilistic statement referring to a long-run average. In other words, for every 100 confidence intervals, we will observe *about* 95 confidence intervals that capture $p$, but not necessarily exactly 95. In Figure \@ref(fig:reliable-percentile) for example, 95 of the confidence intervals capture $p$.

To further accentuate our point about confidence levels, let's generate a figure similar to Figure \@ref(fig:reliable-percentile), but this time constructing 80% standard-error method based confidence intervals instead. Let's visualize the results in Figure \@ref(fig:reliable-se) with the scale on the x-axis being the same as in Figure \@ref(fig:reliable-percentile) to make comparison easy. Furthermore, since all standard-error method 95% confidence intervals for $p$ are centered at their respective point estimates $\widehat{p}$, we mark this value on each line with dots.  


```
## Warning: Using alpha for a discrete variable is not advised.
```

![(\#fig:reliable-se)100 SE-based 80 percent confidence intervals for $p$ with point estimate center marked with dots.](09-confidence-intervals_files/figure-latex/reliable-se-1.pdf) 

Observe how the 80% confidence intervals are narrower than the 95% confidence intervals, reflecting our lower degree of confidence. Think of this as using a smaller "net." We'll explore other determinants of confidence interval width in the upcoming Section \@ref(ci-width).

Furthermore, observe that of the 100 80% confidence intervals, 82 of them captured the population proportion $p$ = 0.375, whereas 18 of them did not. Since we lowered the confidence level from 95% to 80%, we now have a much larger number of confidence intervals that failed to "catch the fish."



### Precise & shorthand interpretation {#shorthand}

\index{confidence interval!interpretation}

Let's return our attention to 95% confidence intervals. The precise and mathematically correct interpretation of a 95% confidence interval is a little long-winded:

> Precise interpretation: If we repeated our sampling procedure a large number of times, we expect about 95% of the resulting confidence intervals to capture the value of the population parameter. 

This is what we observed in Figure \@ref(fig:reliable-percentile). Our confidence interval construction procedure is 95% "reliable." In other words, we can expect our confidence intervals to include the true population parameter about 95% of the time.

A common but incorrect interpretation is: "There is a 95% probability that the confidence interval contains $p$."  Looking at Figure \@ref(fig:reliable-percentile), each of the confidence intervals either does or doesn't contain $p$. In other words, the probability is either a 1 or a 0. 

So if the 95% confidence level only relates to the reliability of the confidence interval construction procedure and not to a given confidence interval itself, what insight can be derived from a given confidence interval? For example, going back to the pennies example, we found that the percentile method 95% confidence interval for $\mu$ was (1991.34, 1999.54) whereas the standard error method 95% confidence interval was (1991.32, 1999.56). What can be said about these two intervals?

Loosely speaking, we can think of these intervals as our "best guess" of a plausible range of values for the mean year $\mu$ of *all* US pennies. For the rest of this book, we'll use the following shorthand summary of the precise interpretation. 

> Short-hand interpretation: We are 95% "confident" that a 95% confidence interval captures the value of the population parameter. 

We use quotation marks around "confident" to emphasize that while 95% relates to the reliability of our confidence interval construction procedure, ultimately a constructed confidence interval is our best guess of an interval that contains the population parameter. In other words, it's our best net.

So returning to our pennies example and focusing on the percentile-method, we are 95% "confident" that the true mean year of pennies in circulation in 2019 is somewhere between 1991.34 and 1999.54.


### Width of confidence intervals {#ci-width}

Now that we know how to interpret confidence intervals, let's go over some factors that determine their width.

#### Impact of confidence level {-}

One factor that determines confidence interval widths is the pre-specified confidence level. For example, in Figures \@ref(fig:reliable-percentile) and \@ref(fig:reliable-se), we compared the widths of 95% and 80% confidence intervals and observed that the 95% confidence intervals were wider. The quantification of the confidence level should match what many expect of the word "confident." In order to be more confident in our best guess of a range of values, we need to widen the range of values.

To elaborate on this, imagine we want to guess the forecasted high temperature in Seoul, South Korea on August 15th. Given Seoul's temperate climate with 4 distinct seasons, we could say somewhat confidently that the high temperature would be between 50&deg;F - 95&deg;F (10&deg;C - 35&deg;C). However, if we wanted a temperature range we were *absolutely* confident about, would we need to widen it. 

We need this wider range to allow for the possibility of anomalous weather, like a freak cold spell or an extreme heat wave. So a range of temperatures we could be near certain about would be between 32&deg;F - 110&deg;F (0&deg;C - 43&deg;C). On the other hand, if could tolerate being a little less confident, we could narrow this range to between 70&deg;F - 85&deg;F (21&deg;C - 30&deg;C). 

Let's revisit our sampling bowl from Chapter \@ref(sampling). Let's compare $10 \times 3 = 30$ confidence intervals for $p$ based on three different confidence levels: 80%, 95%, and 99%. Specifically, we'll first take 30 different random samples of size $n$ = 50 balls from the bowl. Then we'll construct 10 percentile-based confidence intervals using each of the three different confidence levels. Finally, we'll compare the widths of these intervals. We visualize the resulting confidence intervals in Figure \@ref(fig:reliable-percentile-80-95-99) along with a vertical line marking the true value of $p$ = 0.375.





![(\#fig:reliable-percentile-80-95-99)Ten 80, 95, and 99 percent confidence intervals for $p$ based on $n = 50$.](09-confidence-intervals_files/figure-latex/reliable-percentile-80-95-99-1.pdf) 

Observe that as the confidence level increases from 80% to 95% to 99%, the confidence intervals tend to get wider. Let's compare their average widths in Table \@ref(tab:perc-cis-average-width).


```
## `summarise()` ungrouping output (override with `.groups` argument)
```

\begingroup\fontsize{10}{12}\selectfont

\begin{longtable}[t]{lr}
\caption{(\#tab:perc-cis-average-width)Average width of 80, 95, and 99 percent confidence intervals.}\\
\toprule
Confidence level & Mean width\\
\midrule
\endfirsthead
\caption[]{(\#tab:perc-cis-average-width)Average width of 80, 95, and 99 percent confidence intervals. \textit{(continued)}}\\
\toprule
Confidence level & Mean width\\
\midrule
\endhead
\
\endfoot
\bottomrule
\endlastfoot
80\% & 0.162\\
95\% & 0.262\\
99\% & 0.338\\*
\end{longtable}
\endgroup{}

So in order to have a higher confidence level, our confidence intervals must be wider. Ideally, we would have both a high confidence level and narrow confidence intervals. However, we cannot have it both ways. If we want to "be more confident", we need to allow for wider intervals. Conversely, if we would like a narrow interval, we must tolerate a lower confidence level. 

The moral of the story is: \index{confidence interval!impact of confidence level on interval width} **Higher confidence levels tend to produce wider confidence intervals.**  However, when looking at Figure \@ref(fig:reliable-percentile-80-95-99) it is important to keep in mind that we kept the sample size fixed at $n$ = 50. In other words, all $10 \times 3 = 30$ random samples from the `bowl` had the same sample size. 

What happens if instead we took samples of different sizes? Recall that we did this in Section \@ref(different-shovels) using virtual shovels with 25, 50, and 100 slots. We delve into this next.

\pagebreak

#### Impact of sample size {-}

This time, let's fix the confidence level at 95%, but consider three different sample sizes $n$: 25, 50, and 100. Specifically, we'll first take 10 different random samples of size 25, 10 different random samples of size 50, and 10 different random samples of size 100. We'll then construct 95% percentile-based confidence intervals. Finally, we'll compare the widths of these intervals. We visualize the resulting 30 confidence intervals in Figure \@ref(fig:reliable-percentile-n-25-50-100). Note also the vertical line marking the true value of $p$ = 0.375.



![(\#fig:reliable-percentile-n-25-50-100)Ten 95 percent confidence intervals for $p$ based on n = 25, 50, and 100.](09-confidence-intervals_files/figure-latex/reliable-percentile-n-25-50-100-1.pdf) 

Observe that as the confidence intervals are constructed from larger and larger sample sizes, they tend to get narrower. Let's compare the average widths in Table \@ref(tab:perc-cis-average-width-2).


```
## `summarise()` ungrouping output (override with `.groups` argument)
```

\begingroup\fontsize{10}{12}\selectfont

\begin{longtable}[t]{lr}
\caption{(\#tab:perc-cis-average-width-2)Average width of 95 percent confidence intervals based on n = 25, 50, and 100.}\\
\toprule
Sample size & Mean width\\
\midrule
\endfirsthead
\caption[]{(\#tab:perc-cis-average-width-2)Average width of 95 percent confidence intervals based on n = 25, 50, and 100. \textit{(continued)}}\\
\toprule
Sample size & Mean width\\
\midrule
\endhead
\
\endfoot
\bottomrule
\endlastfoot
n = 25 & 0.380\\
n = 50 & 0.268\\
n = 100 & 0.189\\*
\end{longtable}
\endgroup{}

The moral of the story is: \index{confidence interval!impact of sample size on interval width} **Larger sample sizes tend to produce narrower confidence intervals.**   Recall that this was a key message in Section \@ref(moral-of-the-story). As we used larger and larger shovels for our samples, the sample proportions red $\widehat{p}$ tended to vary less. In other words, our estimates got more and more *precise*. 

Recall that we visualized these results in Figure \@ref(fig:comparing-sampling-distributions-3), where we compared the *sampling distributions* for $\widehat{p}$ based on samples of size $n$ equal 25, 50, and 100. We also quantified the sampling variation of these sampling distributions using their standard deviation, which has that special name: the *standard error*. So as the sample size increases, the standard error decreases. 

In fact, the standard error is another related factor in determining confidence interval width. We'll explore this when we discuss theory-based methods for constructing confidence intervals using mathematical formulas. Such methods are an alternative to the computer-based methods we've been using so far. 



## Conclusion {#ci-conclusion}

### Comparing bootstrap and sampling distributions {#bootstrap-vs-sampling}

Let's talk more about the relationship between *sampling distributions* and *bootstrap distributions*.\index{bootstrap!distribution}\index{sampling distributions}

Recall back in Section \@ref(shovel-1000-times), we took 1000 virtual samples from the `bowl` using a virtual shovel, computed 1000 values of the sample proportion red $\widehat{p}$, then visualized their distribution in a histogram. Recall that this distribution is called the *sampling distribution of* $\widehat{p}$ . Furthermore, the standard deviation of the sampling distribution has a special name: the *standard error*.

We also mentioned that this sampling activity does not reflect how sampling is done in real-life. Rather, it was an *idealized version* of sampling so that we could study the effects of sampling variation on estimates, like the proportion of the shovel's balls that are red. In real-life however, one would take a single sample that's as large as possible, much like in the Obama poll we saw in Section \@ref(sampling-case-study). But how can we get a sense of the effect of sampling variation on estimates if we only have one sample and thus only one estimate? Don't we need many samples and hence many estimates?

The workaround to having a *single* sample was to perform *bootstrap resampling with replacement* from the single sample. We did this in the resampling activity in Section \@ref(resampling-tactile) where we focused on the mean year of minting of pennies. We used pieces of paper representing the original sample of 50 pennies from the bank and resampled them with replacement from a hat. We had 35 of our friends perform this activity and visualized the resulting 35 sample means $\overline{x}$ in a histogram in Figure \@ref(fig:tactile-resampling-6). 

This distribution was called the *bootstrap distribution* of $\overline{x}$. We stated at the time that the bootstrap distribution is an *approximation* to the sampling distribution of $\overline{x}$ in the sense that both distributions will have a similar shape and similar spread. \index{bootstrap!distribution!approximation of sampling distribution} Thus the *standard error* of the bootstrap distribution can be used as an approximation to the *standard error* of the sampling distribution. 

Let's show you that this is the case by now compare these two types of distributions. Specifically, we'll compare the

1. The sampling distribution of $\widehat{p}$ based on 1000 virtual samples from the `bowl` from Section \@ref(shovel-1000-times).
1. The bootstrap distribution of $\widehat{p}$ based on 1000 virtual resamples with replacement from Ilyas and Yohan's single sample `bowl_sample_1` from Section \@ref(ilyas-yohan)


#### Sampling distribution {-}

Here is the code you previously saw in Section \@ref(shovel-1000-times) to construct the sampling distribution of $\widehat{p}$, with some small changes to incorporate the statistical terminology relating to sampling you learned in Section \@ref(terminology-and-notation).



```
## `summarise()` ungrouping output (override with `.groups` argument)
```

![(\#fig:sampling-distribution-part-deux)Previously seen sampling distribution of sample proportion red for $n = 1000$.](09-confidence-intervals_files/figure-latex/sampling-distribution-part-deux-1.pdf) 

An important thing to keep in mind is the default value for `replace` is `FALSE` when using `rep_sample_n()`. This is because when sampling 50 balls with a shovel, we are extracting 50 balls one-by-one *without* replacing them. This is in contrast to bootstrap resampling *with* replacement, where we resample a ball and put it back, and repeat this process 50 times. 

Let's quantify the variability in this sampling distribution by calculating the standard deviation of the `propr_red` variable representing 1000 values of the sample proportion $\widehat{p}$. Remember that the standard deviation of the sampling distribution is the *standard error*, frequently denoted as `se`.


```r
sampling_distribution %>% 
  summarize(se = sd(prop_red))
```

```
## # A tibble: 1 x 1
##       se
##    <dbl>
## 1 0.0674
```



#### Bootstrap distribution {-}

Here is the code you previously saw in Section \@ref(ilyas-yohan) to construct the bootstrap distribution of $\widehat{p}$ based on Ilyas and Yohan's original sample of 50 balls saved in `bowl_sample_1`.




```r
# Compute the bootstrap distribution using infer workflow:
bootstrap_distribution <- bowl_sample_1 %>% 
  specify(response = color, success = "red") %>% 
  generate(reps = 1000, type = "bootstrap") %>% 
  calculate(stat = "prop")
```




```
## Warning: Duplicated aesthetics after name standardisation: colour
```

![(\#fig:bootstrap-distribution-part-deux)Bootstrap distribution of sample proportion red for $n = 1000$.](09-confidence-intervals_files/figure-latex/bootstrap-distribution-part-deux-1.pdf) 


```r
bootstrap_distribution %>% 
  summarize(se = sd(stat))
```

```
## # A tibble: 1 x 1
##       se
##    <dbl>
## 1 0.0712
```


#### Comparison {-}

Now that we have computed both the sampling distribution and the bootstrap distributions, let's compare them side-by-side in Figure \@ref(fig:side-by-side). We'll make both histograms have matching scales on the x and y-axes to make them more comparable. Furthermore, we'll add:

1. To the sampling distribution on the top: a solid line denoting the proportion of the bowl's balls that are red $p$ = 0.375. 
1. To the bootstrap distribution on the bottom: a dashed line at the sample proportion $\widehat{p}$ = 21/50 = 0.42 = 42\% that Ilyas and Yohan observed.

![(\#fig:side-by-side)Comparing the sampling and bootstrap distributions of $\widehat{p}$](09-confidence-intervals_files/figure-latex/side-by-side-1.pdf) 

There is a lot going on in Figure \@ref(fig:side-by-side), so let's break down all the comparisons slowly. 

First, observe how the sampling distribution on top is centered at $p$ = 0.375. This is because the sampling is done at random and in an unbiased fashion. So the estimates $\widehat{p}$ are centered at the true value of $p$. 

However, this is not the case with the following bootstrap distribution. The bootstrap distribution is centered at 0.42, which is the proportion red of Ilyas and Yohan's 50 sampled balls. This is because we are resampling from the same sample over and over again. Since the bootstrap distribution is centered at the original sample's proportion, it doesn't necessarily provide a better estimate of $p$ = 0.375. This leads us to our first lesson about bootstrapping:

> The bootstrap distribution will likely not have the same center as the sampling distribution. In other words, bootstrapping cannot improve the quality of an estimate.

Second, let's now compare the spread (in the words the variation) of the two distributions: they are somewhat similar. In the previous code, we computed the standard deviations of both distributions as well. Recall that such standard deviations have a special name: *standard errors*. Let's compare them in Table \@ref(tab:comparing-se).

\begin{table}[!h]

\caption{(\#tab:comparing-se)Comparing standard errors}
\centering
\fontsize{10}{12}\selectfont
\begin{tabular}[t]{lr}
\toprule
Distribution type & Standard error\\
\midrule
Sampling distribution & 0.067\\
Bootstrap distribution & 0.071\\
\bottomrule
\end{tabular}
\end{table}

Notice that the bootstrap distribution's standard error is a rather good *approximation* to the sampling distribution's standard error. This leads us to our second lesson about bootstrapping:

> Even if the bootstrap distribution might not have the same center as the sampling distribution, it will likely have very similar shape and spread. In other words, bootstrapping will give you a good estimate of the *standard error*. 

Thus, using the fact that the bootstrap distribution and sampling distributions have similar spreads, we can build confidence intervals using bootstrapping as we've done all throughout this chapter!


<!--chapter:end:09-confidence-intervals.Rmd-->

# Hypothesis Testing {#hypothesis-testing}  
    
Now that we've studied confidence intervals in Chapter \@ref(confidence-intervals), let's study the commonly used method for statistical inference: hypothesis testing. Hypothesis tests allow us to take a sample of data from a population and infer about the plausibility of competing hypotheses. For example, in the upcoming "promotions" activity in Section \@ref(ht-activity), you'll study the data collected from a psychology study in the 1970's to investigate whether there exists gender-based discrimination in promotion rates in the banking industry. 

The good news is we've already covered many of the necessary concepts to understand hypothesis testing in Chapters \@ref(sampling) and \@ref(confidence-intervals). We will expand further on these ideas here and also provide a general framework for understanding hypothesis tests. By understanding this general framework, you'll be able to adapt it to many different scenarios.

The same can be said for confidence intervals. There was one general framework that applies to *all* confidence intervals and the `infer` package was designed around this framework. While the specifics may change slightly for different types of confidence intervals, the general framework stays the same. We believe that this approach is much better for long-term learning than focusing on specific details for specific confidence intervals and as you'll now see, hypothesis tests as well.




### Needed packages {-}


```r
if (!require("pacman")) install.packages("pacman")
```

```
## Loading required package: pacman
```

```r
pacman::p_load(tidyverse, # All purpose wrangling for dataframes
               readr, # importing and writing data
               readxl,# read and write excel documents
               purrr, # for piping %>%
               corrplot, # for correlation
               knitr,
               moderndive,
               kableExtra,
               nycflights13,
               ggplot2movies,
               cowplot,
               scales,
               viridis,
               infer)
```


## Promotions activity {#ht-activity}

Let's start with an activity studying the effect of gender on promotions at a bank. 

### Does gender affect promotions at bank?

Say you are working at a bank in the 1970's and you are submitting your resume to apply for a promotion. Will your gender affect your chances of getting promoted? To answer this question, we'll focus on data from a study published in the "Journal of Applied Psychology" in 1974. This data is also used in the [OpenIntro](https://www.openintro.org/) series of statistics textbooks. 

To begin the study, 48 bank supervisors were asked to assume the role of a hypothetical director of a bank with multiple branches. Every one of the bank supervisors was given a resume and asked whether or not the candidate on the resume was fit to be promoted to a new position in one of their branches. 

However, each of these 48 resumes were identical in all respects except one: the name of the applicant at the top of the resume. 24 of the supervisors were randomly given resumes with stereotypically "male" names while 24 of the supervisors were randomly given resumes with stereotypically "female" names. Since only (binary) gender varied from resume to resume, researchers could isolate the effect of this variable in promotion rates. 

While many people today (including us, the authors) disagree with such binary views of gender, it is important to remember that this study was conducted at a time where more nuanced views of gender were not as prevalent. Despite this imperfection, we decided to still use this example as we feel it presents ideas still relevant today about how we could study discrimination in the workplace.

The `moderndive` package contains the data on the 48 applicants in the `promotions` data frame. Let’s explore this data first:


```r
promotions
```

```
## # A tibble: 48 x 3
##       id decision gender
##    <int> <fct>    <fct> 
##  1     1 promoted male  
##  2     2 promoted male  
##  3     3 promoted male  
##  4     4 promoted male  
##  5     5 promoted male  
##  6     6 promoted male  
##  7     7 promoted male  
##  8     8 promoted male  
##  9     9 promoted male  
## 10    10 promoted male  
## # ... with 38 more rows
```

The variable `id` acts as an identification variable for all 48 rows, the `decision` variable indicates whether the applicant was selected for promotion or not, while the `gender` variable indicates the gender of the name used on the resume. Recall that this data does not pertain to 24 actual men and 24 actual women, but rather 48 identical resumes of which 24 were assigned stereotypically "male" names and 24 were assigned stereotypical "female" names.

Let's perform an exploratory data analysis of the relationship between the two categorical variables `decision` and `gender`. 


```r
ggplot(promotions, aes(x = gender, fill = decision)) +
  geom_bar() +
  labs(x = "Gender of name on resume")
```


![(\#fig:promotions-barplot)Barplot of relationship between gender and promotion decision.](10-hypothesis-testing_files/figure-latex/promotions-barplot-1.pdf) 

Observe in Figure \@ref(fig:promotions-barplot) that it appears that resumes with female names were much less likely to be accepted for promotion.  Let's quantify these promotion rates by computing the proportion of resumes accepted for promotion for each group using the `dplyr` package for data wrangling:


```r
promotions %>% 
  group_by(gender, decision) %>% 
  summarize(n = n())
```

```
## `summarise()` regrouping output by 'gender' (override with `.groups` argument)
```

```
## # A tibble: 4 x 3
## # Groups:   gender [2]
##   gender decision     n
##   <fct>  <fct>    <int>
## 1 male   not          3
## 2 male   promoted    21
## 3 female not         10
## 4 female promoted    14
```


So of the 24 resumes with male names, 21 were selected for promotion, for a proportion of 21/24 = 0.875 = 87.5%. On the other hand, of the 24 resumes with female names, 14 were selected for promotion, for a proportion of 14/24 = 0.583 = 58.3%. Comparing these two rates of promotion, it appears that resumes with male names were selected for promotion at a rate 0.875 - 0.583 = 0.292 = 29.2% higher than resumes with female names. This is suggestive of an advantage for resumes with a male name on it. 

The question is however, does this provide *conclusive* evidence that there is gender discrimination in promotions at banks? Could a difference in promotion rates of 29.2% still occur by chance, even in a hypothetical world where no gender-based discrimination existed? In other words, what is the role of *sampling variation*? To answer this question, we'll again rely on a computer to run *simulations*. 


### Shuffling once

First, try to imagine a hypothetical universe where no gender discrimination in promotions existed. In such a hypothetical universe, the gender of an applicant would have no bearing on their chances of promotion. Bringing things back to our `promotions` data frame, the `gender` variable would thus be an irrelevant label. If these `gender` labels were irrelevant, then we could randomly reassign them by "shuffling" them to no consequence!

To illustrate this idea, let's narrow our focus to six arbitrarily chosen resumes of the 48 in Table \@ref(tab:compare-six). The `decision` column shows that three resumes resulted in promotion while three didn't. The `gender` column shows what the original gender of the resume name was. 

However, in our hypothesized universe of no gender discrimination, gender is irrelevant and thus it is of no consequence to randomly "shuffle" the values of `gender`. The `shuffled_gender` column shows one such possible random shuffling. Observe how the number of male and female names remains the same at three each, but they are now listed in a different order. 

\begingroup\fontsize{10}{12}\selectfont

\begin{longtable}[t]{rlll}
\caption{(\#tab:compare-six)One example of shuffling gender variable.}\\
\toprule
resume number & decision & gender & shuffled gender\\
\midrule
\endfirsthead
\caption[]{(\#tab:compare-six)One example of shuffling gender variable. \textit{(continued)}}\\
\toprule
resume number & decision & gender & shuffled gender\\
\midrule
\endhead
\
\endfoot
\bottomrule
\endlastfoot
1 & not & male & male\\
2 & not & female & male\\
3 & not & female & female\\
4 & promoted & male & female\\
5 & promoted & male & female\\
\addlinespace
6 & promoted & female & male\\*
\end{longtable}
\endgroup{}

Again, such random shuffling of the gender label only makes sense in our hypothesized universe of no gender discrimination. How could we extend this shuffling of the gender variable to all 48 resumes by hand? One way would be by using standard deck of 52 playing cards, which we display in Figure \@ref(fig:deck-of-cards).

\begin{figure}
\includegraphics[width=1\linewidth]{images/shutterstock/shutterstock_670789453} \caption{Standard deck of 52 playing cards.}(\#fig:deck-of-cards)
\end{figure}

Since half the cards are red and the other half are black, by removing 2 red cards and 2 black cards, we would end up with 24 red cards and 24 black cards. After shuffling these 48 cards as seen in Figure \@ref(fig:shuffling), we can flip the cards over one-by-one, assigning "male" for each red card and "female" for each black card.

\begin{figure}
\includegraphics[width=0.66\linewidth]{images/shutterstock/shutterstock_128283971} \caption{Shuffling a deck of cards.}(\#fig:shuffling)
\end{figure}


We've saved one such shuffling in the `promotions_shuffled` data frame of the `moderndive` package. If you view both the original `promotions` and the shuffled `promotions_shuffled` data frames and compare them, you'll see that while the `decision` variables are identical, the `gender` variables are different.


```r
promotions_shuffled
```

```
## # A tibble: 48 x 3
##       id decision gender
##    <int> <fct>    <fct> 
##  1     1 promoted female
##  2     2 promoted female
##  3     3 promoted male  
##  4     4 promoted female
##  5     5 promoted male  
##  6     6 promoted male  
##  7     7 promoted male  
##  8     8 promoted female
##  9     9 promoted male  
## 10    10 promoted female
## # ... with 38 more rows
```

Let's repeat the same exploratory data analysis we did for the original `promotions` data on our shuffled `promotions_shuffled` data frame. Let's create a barplot visualizing the relationship between `decision` and the new shuffled `gender` variable and compare this to the original unshuffled version in Figure \@ref(fig:promotions-barplot-permuted).


```r
ggplot(promotions_shuffled, aes(x = gender, fill = decision)) +
  geom_bar() +
  labs(x = "Gender of resume name")
```

```
## `summarise()` regrouping output by 'gender' (override with `.groups` argument)
## `summarise()` regrouping output by 'gender' (override with `.groups` argument)
```

![(\#fig:promotions-barplot-permuted)Barplots of relationship of promotion with gender (left) and shuffled gender (right).](10-hypothesis-testing_files/figure-latex/promotions-barplot-permuted-1.pdf) 

It appears the difference in "male names" versus "female names" promotion rates is now different. Compared to the original data in the left barplot, the new "shuffled" data in the right barplot has promotion rates that are much more similar.

Let's also compute the proportion of resumes accepted for promotion for each group:


```r
promotions_shuffled %>% 
  group_by(gender, decision) %>% 
  summarize(n = n())
```

```
## `summarise()` regrouping output by 'gender' (override with `.groups` argument)
```

```
## # A tibble: 4 x 3
## # Groups:   gender [2]
##   gender decision     n
##   <fct>  <fct>    <int>
## 1 male   not          6
## 2 male   promoted    18
## 3 female not          7
## 4 female promoted    17
```


So in this hypothetical universe of no discrimination, 18/24 = 0.75 = 75% of "male" resumes were selected for promotion. On the other hand, 17/24 = 0.708 = 70.8% of "female" resumes were selected for promotion. Comparing these two values, it appears that resumes with male names were selected for promotion at a rate that was 0.75 - 0.708 = 0.042 = 4.2% different that resumes with female names. 

Observe how this difference in rates is different than the difference in rates of 0.292 = 29.2% we originally observed. This is once again due to *sampling variation*. How can we better understand the effect of this sampling variation? By repeating this shuffling several times!


### Shuffling 16 times

We recruited 16 groups of our friends to repeat this shuffling exercise. They recorded these values in a [shared spreadsheet](https://docs.google.com/spreadsheets/d/1Q-ENy3o5IrpJshJ7gn3hJ5A0TOWV2AZrKNHMsshQtiE/); we display a snapshot of the first 10 rows and 5 columns in Figure \@ref(fig:tactile-shuffling)

\begin{figure}
\includegraphics[width=1\linewidth]{images/sampling/promotions/shared_spreadsheet} \caption{Snapshot of shared spreadsheet of shuffling results.}(\#fig:tactile-shuffling)
\end{figure}



For each of these 16 columns of "shuffles", we computed the difference in promotion rates, and in Figure \@ref(fig:null-distribution-1) we display their distribution in a histogram. We also mark the observed difference in promotion rate that happened in real-life of 0.292 = 29.2% with a red line.

![(\#fig:null-distribution-1)Distribution of shuffled differences in promotions.](10-hypothesis-testing_files/figure-latex/null-distribution-1-1.pdf) 

Before we discuss the distribution of the histogram, we emphasize the key thing to remember: this histogram represents differences in promotion rates that one would observe in our *hypothesized universe* of no gender discrimination.

Observe first that the histogram is roughly centered at 0. Saying that the difference in promotion rates is 0 is equivalent to saying that both genders had the same promotion rate. In other words, the center of these 16 values is consistent with what we would expect in our hypothesized universe of no gender discrimination. 

However, while the values are centered at 0, there is variation about 0. This is because even in a hypothesized universe of no gender discrimination, you will still likely observe small differences in promotion rates because of chance *sampling variation*. Looking at the histogram in Figure \@ref(fig:null-distribution-1), such differences could even be as extreme as -0.292 or 0.208.

Turning our attention to what we observed in real-life: the difference of 0.292 = 29.2% is marked with a red line.  Ask yourself: in a hypothesized world of no gender discrimination, how likely would it be that we observe this difference? While opinions may differ, in our opinion not often! Now ask yourself: what does these results say about our hypothesized universe of no gender discrimination?

### What did we just do?

What we just demonstrated in this activity is the statistical procedure known as *hypothesis testing* using a *permutation test*. The term "permutation" \index{permutation} is the mathematical term for "shuffling": take a series of values and reorder them randomly, as you did with the playing cards. 

In fact, permutations are another form of *resampling*, like the bootstrap method you performed in Chapter \@ref(confidence-intervals). While the bootstrap method involves resampling *with* replacement, permutation methods involve resampling *without* replacement. 

Think of our exercise involving the slips of paper representing pennies and the hat in Section \@ref(resampling-tactile): after sampling a penny, you put it back in the hat. Now think of our deck of cards. After drawing a card, you laid it out in front of you, recorded the color, and then you *did not* put it back in the deck.

In our previous example, we tested the validity of the hypothesized universe of no gender discrimination. The evidence contained in our observed sample of 48 resumes was somewhat inconsistent with our hypothesized universe. Thus, we would be inclined to *reject* this hypothesized universe and declare that the evidence suggests there is gender discrimination. 

This time it will be $p_{m} - p_{f}$, where $p_{m}$ is the population proportion of resumes with male names being recommended for promotion and $p_{f}$ is the equivalent for resumes with female names. Recall that this is one of the scenarios for inference we've seen so far in Table \@ref(tab:table-diff-prop).

\begin{table}[!h]

\caption{(\#tab:table-diff-prop)Scenarios of sampling for inference}
\centering
\fontsize{10}{12}\selectfont
\begin{tabular}[t]{>{\raggedleft\arraybackslash}p{0.5in}>{\raggedright\arraybackslash}p{0.7in}>{\raggedright\arraybackslash}p{1in}>{\raggedright\arraybackslash}p{1.1in}>{\raggedright\arraybackslash}p{1in}}
\toprule
Scenario & Population parameter & Notation & Point estimate & Notation.\\
\midrule
1 & Population proportion & $p$ & Sample proportion & $\widehat{p}$\\
2 & Population mean & $\mu$ & Sample mean & $\overline{x}$ or $\widehat{\mu}$\\
3 & Difference in population proportions & $p_1 - p_2$ & Difference in sample proportions & $\widehat{p}_1 - \widehat{p}_2$\\
\bottomrule
\end{tabular}
\end{table}

So based on our sample of $n_m$ = 24 "male" applicants and $n_w$ = 24 "female" applicants, the *point estimate* for $p_{m} - p_{f}$ is the *difference in sample proportions* $\widehat{p}_{m} -\widehat{p}_{f}$ = 0.875 - 0.583 = 0.292 = 29.2%. This difference in favor of "male" resumes of 0.292 is greater than 0, suggesting discrimination in favor of men. 

However the question we asked ourselves was "is this difference meaningfully different than 0?" In other words, is that difference indicative of true discrimination, or can we just attribute it to *sampling variation*? Hypothesis testing allows us to make such distinctions.


## Understanding hypothesis tests {#understanding-ht}

Much like the terminology, notation, and definitions relating to sampling you saw in Section \@ref(sampling-framework), there is a lot of terminology, notation, and definitions related to hypothesis testing. Learning these may seem like a very daunting task at first. However with practice, practice, and practice, anyone can master them. 

First, a **hypothesis** \index{hypothesis} is a statement about the value of an unknown population parameter. In our resume activity, our population parameter of interest is the difference in population proportions $p_{m} - p_{f}$. Hypothesis tests can involve any of the population parameters in Table \@ref(tab:table-ch8) of the 6 inference scenarios we'll cover in this book and more.

Second, a **hypothesis test** \index{hypothesis test} consists of a test between two competing hypotheses: 1) a **null hypothesis** $H_0$ (pronounced "H-naught") versus 2) an **alternative hypothesis** $H_A$ (also denoted $H_1$). 

Generally the null hypothesis \index{hypothesis testing!null hypothesis} is a claim that there is "no effect" or "no difference of interest."  In many cases, the null hypothesis represents the status quo or a situation that nothing interesting is happening. Furthermore, generally the alternative hypothesis \index{hypothesis testing!alternative hypothesis} is the claim the experimenter or researcher wants to establish or find evidence to support. It is viewed as a "challenger" hypothesis to the null hypothesis $H_0$. In our resume activity, an appropriate hypothesis test would be:

$$
\begin{aligned}
H_0 &: \text{men and women are promoted at the same rate}\\
\text{vs } H_A &: \text{men are promoted at a higher rate than women}
\end{aligned}
$$

Note some of the choices we have made. First, we set the null hypothesis $H_0$ to be that there is no difference in promotion rate and the "challenger" alternative hypothesis $H_A$ to be that there is a difference. While it would not be wrong in principle to reverse the two, it is a convention in statistical inference that the null hypothesis is set to reflect a "null" situation where "nothing is going on." As we discussed earlier, in this case, that there is no difference in promotion rates. Furthermore we set $H_A$ to be that men are promoted at a *higher* rate, a subjective choice reflecting a prior suspicion we have that this is the case. We call such alternative hypotheses \index{hypothesis test!one-sided alternative} *one-sided alternatives*. If someone else however does not share such suspicions and only wants to investigate that there is a difference, whether higher or lower, they would set what is known as a \index{hypothesis test!two-sided alternative} *two-sided alternative*.

We can re-express the formulation of our hypothesis test using the mathematical notation for our population parameter of interest, the difference in population proportions $p_{m} - p_{f}$:

$$
\begin{aligned}
H_0 &: p_{m} - p_{f} = 0\\
\text{vs } H_A&: p_{m} - p_{f} > 0
\end{aligned}
$$

Observe how the alternative hypothesis $H_A$ is one-sided $p_{m} - p_{f} > 0$. Had we opted for a two-sided alternative, we would have set $p_{m} - p_{f} \neq 0$. To keep things simple for now, we'll stick with the simpler one-sided alternative. We'll present an example of a two-sided alternative in Section \@ref(ht-case-study).

Third, a **test statistic** \index{hypothesis testing!test statistic} is a *point estimate/sample statistic* formula used for hypothesis testing. Note that a sample statistic is merely a summary statistic based on a sample of observations. Recall that a summary statistic takes in many values and returns only one. Here, the sample would be the $n_m$ = 24 resumes with male names and the $n_f$ = 24 resumes with female names. Hence, the point estimate of interest is the difference in sample proportions $\widehat{p}_{m} - \widehat{p}_{f}$. 

Fourth, the **observed test statistic** \index{hypothesis testing!observed test statistic} is the value of the test statistic that we observed in real-life. In our case, we computed this value using the data saved in the `promotions` data frame. It was the observed difference of $\widehat{p}_{m} -\widehat{p}_{f}$ = 0.875 - 0.583 = 0.292 = 29.2% in favor of resumes with male names.

Fifth, the **null distribution** \index{hypothesis testing!null distribution} is the sampling distribution of the test statistic *assuming the null hypothesis $H_0$ is true*. Ooof! That's a long one! Let's unpack it slowly. The key to understanding the null distribution is that the null hypothesis $H_0$ *assumed* to be true. We're not saying that $H_0$ is true at this point, we're only assuming it to be true for hypothesis testing purposes. In our case, this corresponds to our hypothesized universe of no gender discrimination in promotion rates. Assuming the null hypothesis $H_0$, also stated as "Under $H_0$," how does the test statistic vary due to sampling variation? In our case, how will the difference in sample proportions $\widehat{p}_{m} - \widehat{p}_{f}$ vary due to sampling? Recall from Section \@ref(sampling-definitions) that distributions that display how point estimates vary due to sampling variation are called *sampling distributions*. The only additional thing to keep in mind about null distributions is that they are sampling distributions *assuming the null hypothesis $H_0$ is true*. 

In our case, we previously visualized a null distribution in Figure \@ref(fig:null-distribution-1), which we re-display in Figure \@ref(fig:null-distribution-2) using our new notation and terminology. It is the distribution of the 16 different difference in sample proportions our friends computed *assuming* a hypothetical universe of no gender discrimination. We also mark the value of the observed test statistic of 0.292 with a vertical line.

![(\#fig:null-distribution-2)Null distribution and observed test statistic.](10-hypothesis-testing_files/figure-latex/null-distribution-2-1.pdf) 

Sixth, the **p-value** \index{hypothesis testing!p-value} is the probability of obtaining a test statistic just as extreme or more extreme than the observed test statistic *assuming the null hypothesis $H_0$ is true*. Double ooof! Let's unpack this slowly as well. You can think of the p-value as a quantification of "surprise": assuming $H_0$ is true, how surprised are we with what we observed? Or in our case, in our hypothesized universe of no gender discrimination, how surprised are we that we observed a difference in promotion rates of 0.292? Very surprised? Somewhat surprised? 

The p-value quantifies this probability, or in the case of our 16 differences in sample proportions in Figure \@ref(fig:null-distribution-2), what proportion had a more "extreme" result? Here, extreme is defined in terms of the alternative hypothesis $H_A$ that "male" applicants are promoted at a higher rate than "female" applicants. In other words, how often was the discrimination in favor of men even more pronounced than 0.875 - 0.583 = 0.292 = 29.2%?



In this case, 0 times out of 16 did we obtain a difference in proportion greater than or equal to the observed difference of 0.292 = 29.2%. A very rare outcome! Given the rarity of such a pronounced in difference in promotion rates in our hypothesized universe of no gender discrimination, we're inclined to *reject* \index{hypothesis testing!reject the null hypothesis} our hypothesized universe in favor of one stating there is discrimination in favor of the "male" applicants. In other words, we reject $H_0$ in favor of $H_A$.

Seventh and lastly, in many hypothesis testing procedures, it is commonly recommended to set the **significance level** \index{hypothesis testing!significance level} of the test beforehand.  It is denoted by the Greek letter $\alpha$ (pronounced "alpha"). This value acts as a cutoff on the p-value, where if the p-value falls below $\alpha$, we would "reject the null hypothesis $H_0$." Alternatively, if the p-value does not fall below $\alpha$, we would "fail to reject $H_0$." Note the latter statement is not quite the same as saying we "accept $H_0$." This distinction is rather subtle and not immediately obvious. So we'll revisit it later in Section \@ref(ht-interpretation).

While different fields tend to use different values of $\alpha$, some commonly used values for $\alpha$ are 0.1, 0.01, and 0.05, with 0.05 being the choice people often make without putting much thought into it. We'll talk more about $\alpha$ significance levels in Section \@ref(ht-interpretation), but first let's fully conduct the hypothesis test corresponding to our promotions activity using the `infer` package.






## Conducting hypothesis tests {#ht-infer}

In Section \@ref(bootstrap-process), we showed you how to construct confidence intervals. We first illustrated how to do this using raw `dplyr` data wrangling verbs and the `rep_sample_n()` function from Section \@ref(shovel-1000-times) which we used as a virtual shovel. In particular, we constructed confidence intervals by resampling with replacement by setting the `replace = TRUE` argument to the `rep_sample_n()` function. 

We then showed you how to perform the same task using the `infer` package workflow. While both workflows resulted in the same bootstrap distribution from which we can construct confidence intervals, the `infer` package workflow emphasizes each of the steps in the overall process in Figure \@ref(fig:infer-ci). It does so using function names that are intuitively named with verbs:

1. `specify()` the variables of interest in your data frame.
1. `generate()` replicates of bootstrap resamples with replacement.
1. `calculate()` the summary statistic of interest.
1. `visualize()` the resulting bootstrap distribution and confidence interval.



\begin{figure}
\includegraphics[width=0.8\linewidth]{images/flowcharts/infer/visualize} \caption{Confidence intervals with the infer package.}(\#fig:infer-ci)
\end{figure}

In this section, we'll now show you how to seamlessly modify the previously seen `infer` code for constructing confidence intervals to conduct hypothesis tests. You'll notice that the basic outline of the workflow is almost identical, except for an additional `hypothesize()` step between the `specify()` and `generate()` steps, as can be seen in Figure \@ref(fig:inferht).

\begin{figure}
\includegraphics[width=0.8\linewidth]{images/flowcharts/infer/ht} \caption{Hypothesis testing with the infer package.}(\#fig:inferht)
\end{figure}



Furthermore, we'll use a pre-specified significance level $\alpha$ = 0.001 for this hypothesis test. Let's leave discussion on the choice of this $\alpha$ value until later on in Section \@ref(ht-interpretation). 

### infer package workflow {#infer-workflow-ht}


#### 1. `specify` variables {-}

Recall that we use the `specify()` \index{infer!specify()} verb to specify the response variable and, if needed, any explanatory variables for our study. In this case, since we are interested in any potential effects of gender on promotion decisions, we set `decision` as the response variable and `gender` as the explanatory variable. We do so using a `formula = response ~ explanatory` argument where `response` is the name of the response variable in the data frame and `explanatory` is the name of the explanatory variable. So in our case it is `decision ~ gender`. 

Furthermore, since we are interested in the proportion of resumes `"promoted"`, and not the proportion of resumes `not` promoted, we set the argument `success = "promoted"`.


```r
promotions %>% 
  specify(formula = decision ~ gender, success = "promoted")
```

```
## Response: decision (factor)
## Explanatory: gender (factor)
## # A tibble: 48 x 2
##    decision gender
##    <fct>    <fct> 
##  1 promoted male  
##  2 promoted male  
##  3 promoted male  
##  4 promoted male  
##  5 promoted male  
##  6 promoted male  
##  7 promoted male  
##  8 promoted male  
##  9 promoted male  
## 10 promoted male  
## # ... with 38 more rows
```

Again, notice how the `promotions` data itself doesn't change, but the `Response: decision (factor)` and `Explanatory: gender (factor)` *meta-data* do. This is similar to how the `group_by()` verb from `dplyr` doesn't change the data, but only adds "grouping" meta-data.


#### 2. `hypothesize` the null {-}

In order to conduct hypothesis tests using the `infer` workflow, we need a new step not present for confidence intervals: \index{infer!hypothesize()} `hypothesize()`. Recall from Section \@ref(understanding-ht) that our hypothesis test was

$$
\begin{aligned}
H_0 &: p_{m} - p_{f} = 0\\
\text{vs } H_A&: p_{m} - p_{f} > 0
\end{aligned}
$$

In other words, the null hypothesis $H_0$ corresponding to our "hypothesized universe" stated that there was no difference in gender-based discrimination rates. We set this null hypothesis $H_0$ in our `infer` workflow using the `null` argument of the `hypothesize()` function to either:

- `"point"` for hypotheses involving a single sample or
- `"independence"` for hypotheses involving two samples

In our case, since we have two samples (the resumes with "male" and "female" names), we set `null = "independence"`.


```r
promotions %>% 
  specify(formula = decision ~ gender, success = "promoted") %>% 
  hypothesize(null = "independence")
```

```
## Response: decision (factor)
## Explanatory: gender (factor)
## Null Hypothesis: independence
## # A tibble: 48 x 2
##    decision gender
##    <fct>    <fct> 
##  1 promoted male  
##  2 promoted male  
##  3 promoted male  
##  4 promoted male  
##  5 promoted male  
##  6 promoted male  
##  7 promoted male  
##  8 promoted male  
##  9 promoted male  
## 10 promoted male  
## # ... with 38 more rows
```

Again, the data has not changed yet. This will occur at the upcoming `generate()` step; we're merely setting meta-data for now.

Where do the terms `"point"` and `"independence"` come from? These are two technical statistics terms. The term "point" relates from the fact that for a single group of observations, you will test the value of a single point. Going back to the pennies example from Chapter \@ref(confidence-intervals), say we wanted to test if the mean year of all US pennies was equal to 1993 or not. We would be testing the value of a "point" $\mu$, the mean year of *all* US pennies, as follows

$$
\begin{aligned}
H_0 &: \mu = 1993\\
\text{vs } H_A&: \mu \neq 1993
\end{aligned}
$$

The term "independence" relates to the fact that for two groups of observations, you are testing whether or not the response variable is *independent* of the explanatory variable that assigns the groups. In our case, we are testing whether the `decision` response variable is "independent" of the explanatory variable `gender` that assigns each resume to either of the two groups. 


#### 3. `generate` replicates {-}

After we `hypothesize()` the null hypothesis, we `generate()` replicates of "shuffled" datasets assuming the null hypothesis is true. We do this by repeating the shuffling exercise you performed in Section \@ref(ht-activity) several times. Instead of merely doing it 16 times as our groups of friends did, let's use the computer to repeat this 1000 times by setting `reps = 1000` in the `generate()` \index{infer!generate()} function. However, unlike for confidence intervals where we generated replicates using `type = "bootstrap"` resampling with replacement, we'll now perform shuffles/permutations by setting `type = "permute"`. Recall that shuffles/permutations are a kind of resampling, but unlike the bootstrap method, they involve resampling *without* replacement. 


```r
promotions %>% 
  specify(formula = decision ~ gender, success = "promoted") %>% 
  hypothesize(null = "independence") %>% 
  generate(reps = 1000, type = "permute")
```


```
## Response: decision (factor)
## Explanatory: gender (factor)
## Null Hypothesis: independence
## # A tibble: 48,000 x 3
## # Groups:   replicate [1,000]
##    decision gender replicate
##    <fct>    <fct>      <int>
##  1 promoted male           1
##  2 promoted male           1
##  3 not      male           1
##  4 promoted male           1
##  5 not      male           1
##  6 not      male           1
##  7 promoted male           1
##  8 promoted male           1
##  9 promoted male           1
## 10 not      male           1
## # ... with 47,990 more rows
```

Observe that the resulting data frame has 48,000 rows. This is because we performed shuffles/permutations of the 48 values of `gender` 1000 times and 48,000 = 1000 $\times$ 48. The variable `replicate` indicates which resample each row belongs to. So it has the value `1` 48 times, the value `2` 48 times, all the way through to the value `1000` 48 times. 


#### 4. `calculate` summary statistics {-}

Now that we have generated 1000 replicates of "shuffles" assuming the null hypothesis is true, let's `calculate()` \index{infer!calculate()} the appropriate summary statistic for each of our 1000 shuffles. Recall from Section \@ref(understanding-ht) that point estimates/summary statistics related to hypothesis testing have a specific name: *test statistics*. Since the unknown population parameter of interest is the difference in population proportions $p_{m} - p_{f}$, the test statistic of interest here is the difference in sample proportions $\widehat{p}_{m} - \widehat{p}_{f}$. 

For each of our 1000 shuffles, we can calculate this test statistic by setting `stat = "diff in props"`. Furthermore, since we are interested in $\widehat{p}_{m} - \widehat{p}_{f}$ we set `order = c("male", "female")`. As we stated earlier, the order of the subtraction does not matter, so long as you stay consistent throughout your analysis and tailor your interpretations accordingly. 

Let's save the result in a data frame called `null_distribution`:


```r
null_distribution <- promotions %>% 
  specify(formula = decision ~ gender, success = "promoted") %>% 
  hypothesize(null = "independence") %>% 
  generate(reps = 1000, type = "permute") %>% 
  calculate(stat = "diff in props", order = c("male", "female"))
null_distribution
```


```
## # A tibble: 1,000 x 2
##    replicate    stat
##        <int>   <dbl>
##  1         1 -0.125 
##  2         2 -0.0417
##  3         3 -0.0417
##  4         4 -0.0417
##  5         5 -0.0417
##  6         6  0.208 
##  7         7 -0.125 
##  8         8  0.125 
##  9         9 -0.0417
## 10        10  0.208 
## # ... with 990 more rows
```


Observe that we have 1000 values of `stat`, each representing one  instance of $\widehat{p}_{m} - \widehat{p}_{f}$ in a hypothesized world of no gender discrimination. Observe as well we chose the name of this data frame carefully: `null_distribution`. Recall once again from Section \@ref(understanding-ht) that sampling distributions when the null hypothesis $H_0$ is assumed to be true have a special name: the *null distribution*. 

But wait! What happened in real-life? What was the *observed* difference in promotion rates? In other words, what was the *observed test statistic* $\widehat{p}_{m} - \widehat{p}_{f}$? Recall from Section \@ref(ht-activity) that we computed this observed difference by hand to be 0.875 - 0.583 = 0.292 = 29.2%. 

We can also compute this value using the previous `infer` code but with the `hypothesize()` and `generate()` steps removed. Let's save this in `obs_diff_prop`


```r
obs_diff_prop <- promotions %>% 
  specify(decision ~ gender, success = "promoted") %>% 
  calculate(stat = "diff in props", order = c("male", "female"))
obs_diff_prop
```

```
## # A tibble: 1 x 1
##    stat
##   <dbl>
## 1 0.292
```


#### 5. `visualize` the p-value {-}

The final step is to measure how surprised we are by a promotion difference of 29.2% in a hypothesized universe of no gender discrimination. If the observed difference of 0.292 is highly unlikely, then we would be inclined to reject the validity of our hypothesized universe. 

We start by visualizing the *null distribution* of our 1000 values of $\widehat{p}_{m} - \widehat{p}_{f}$ using `visualize()` \index{infer!visualize()} in Figure \@ref(fig:null-distribution-infer). Recall that these are values of the difference in promotion rates assuming $H_0$ is true, in other words in our hypothesized universe of no gender discrimination.


```r
visualize(null_distribution, binwidth = 0.1)
```

![(\#fig:null-distribution-infer)Null distribution](10-hypothesis-testing_files/figure-latex/null-distribution-infer-1.pdf) 

Let's now add what happened in real-life to Figure \@ref(fig:null-distribution-infer), the observed difference in promotion rates of 0.875 - 0.583 = 0.292 = 29.2%. However, instead of merely adding a vertical line using `geom_vline()`, let's use the \index{infer!shade\_p\_value()} `shade_p_value()` function with `obs_stat` set to the observed test statistic value we saved in `obs_diff_prop`. 

Furthermore, we'll set the `direction = "right"` reflecting our alternative hypothesis $H_A: p_{m} - p_{f} > 0$. Recall our alternative hypothesis $H_A$ is that $p_{m} - p_{f} > 0$, stating that there is a difference in promotion rates in favor of resumes with male names. "More extreme" here corresponds to differences that are "bigger" or "more positive" or "more to the right." Hence we set the `direction` argument of `shade_p_value()` to be `"right"`. 

On the other hand, had our alternative hypothesis $H_A$ been the other possible one-sided alternative $p_{m} - p_{f} < 0$, suggesting discrimination in favor of resumes with female names, we would've set `direction = "left"`.  Had our alternative hypothesis $H_A$ been two-sided $p_{m} - p_{f} \neq 0$, suggesting discrimination in either direction, we would've set `direction = "both"`.


```r
visualize(null_distribution, bins = 10) + 
  shade_p_value(obs_stat = obs_diff_prop, direction = "right")
```

![(\#fig:null-distribution-infer-2)Shaded histogram to show p-value.](10-hypothesis-testing_files/figure-latex/null-distribution-infer-2-1.pdf) 

In the resulting Figure \@ref(fig:null-distribution-infer-2), the solid red line marks 0.292 = 29.2%. However, what does the shaded-region correspond to? This is the *p-value*. Recall the definition of the p-value from Section \@ref(understanding-ht):

> A p-value is the probability of obtaining a test statistic just as or more extreme than the observed test statistic *assuming the null hypothesis $H_0$ is true*.

So judging by the shaded region in Figure \@ref(fig:null-distribution-infer-2), it seems we would somewhat rarely observe differences in promotion rates of 0.292 = 29.2% or more in a hypothesized universe of no gender discrimination. In other words, the p-value is somewhat small. Hence, we would be inclined to reject this hypothesized universe, or using statistical language we would "reject $H_0$."

What fraction of the null distribution is shaded? In other words, what is the exact value of the p-value? We can compute it using the `get_p_value()` \index{infer!get\_p\_value()} function with the same arguments as the previous `visualize()` code:


```r
null_distribution %>% 
  get_p_value(obs_stat = obs_diff_prop, direction = "right")
```

```
## # A tibble: 1 x 1
##   p_value
##     <dbl>
## 1   0.024
```


Keeping the definition of a p-value in mind, the probability of observing a difference in promotion rates as large as 0.292 = 29.2% due to sampling variation alone is 0.024 = 2.4%. 

Since this p-value is greater than our pre-specified significance level $\alpha$ = 0.001, we fail to reject the null hypothesis $H_0: p_{m} - p_{f} = 0$. In other words, this p-value wasn't sufficiently small to reject our hypothesized universe of no gender discrimination.

Observe that whether we reject the null hypothesis $H_0$ or not depends in large part on our choice of significance level $\alpha$. We'll discuss this more in Section \@ref(choosing-alpha).

### Comparison with confidence intervals {#comparing-infer-workflows}

One of the great things about the `infer` package is that we can jump seamlessly between conducting hypothesis tests and constructing confidence intervals with minimal changes! Recall the code from the previous section that creates the null distribution, which in turn is needed to compute the p-value:


```r
null_distribution <- promotions %>% 
  specify(formula = decision ~ gender, success = "promoted") %>% 
  hypothesize(null = "independence") %>% 
  generate(reps = 1000, type = "permute") %>% 
  calculate(stat = "diff in props", order = c("male", "female"))
```

To create the corresponding bootstrap distribution needed to construct a 95% confidence interval for $p_{m} - p_{f}$, we only need to make two changes. \index{infer!switching between tests and confidence intervals} First, we remove the `hypothesize()` step since we are no longer assuming a null hypothesis $H_0$ is true. We can do this by deleting or commenting out the `hypothesize()` line of code. Second, we switch the `type` of resampling in the `generate()` step to be `"bootstrap"` instead of `"permute"`.


```r
bootstrap_distribution <- promotions %>% 
  specify(formula = decision ~ gender, success = "promoted") %>% 
  # Change 1 - Remove hypothesize():
  # hypothesize(null = "independence") %>% 
  # Change 2 - Switch type from "permute" to "bootstrap":
  generate(reps = 1000, type = "bootstrap") %>% 
  calculate(stat = "diff in props", order = c("male", "female"))
```



Using this `bootstrap_distribution`, let's first compute the percentile-based confidence intervals, as we did in Section \@ref(bootstrap-process):


```r
percentile_ci <- bootstrap_distribution %>% 
  get_confidence_interval(level = 0.95, type = "percentile")
percentile_ci
```

```
## # A tibble: 1 x 2
##   lower_ci upper_ci
##      <dbl>    <dbl>
## 1   0.0380    0.522
```

Using our shorthand interpretation for 95% confidence intervals from Section \@ref(shorthand), we are 95% "confident" that the true difference in population proportions $p_{m} - p_{f}$ is between (0.038, 0.522). Let's visualize `bootstrap_distribution` and this percentile-based 95% confidence interval for $p_{m} - p_{f}$ in Figure \@ref(fig:bootstrap-distribution-two-prop-percentile).


```r
visualize(bootstrap_distribution) + 
  shade_confidence_interval(endpoints = percentile_ci)
```
![(\#fig:bootstrap-distribution-two-prop-percentile)Percentile-based 95 percent confidence interval.](10-hypothesis-testing_files/figure-latex/bootstrap-distribution-two-prop-percentile-1.pdf) 

Notice a key value that is not included in the 95% confidence interval for $p_{m} - p_{f}$: the value 0. In other words, a difference of 0 is not included in our net, suggesting that $p_{m}$ and $p_{f}$ are truly different! Furthermore, observe how the entirety of the 95% confidence interval for $p_{m} - p_{f}$ lies above 0, suggesting that this difference is in favor of men.

Since the bootstrap distribution appears to be roughly normally shaped, we can also use the standard error method as we did in Section \@ref(bootstrap-process).

In this case, we must specify the `point_estimate` argument as the observed difference in promotion rates 0.292 = 29.2% saved in `obs_diff_prop`. This value acts as the center of the confidence interval.


```r
se_ci <- bootstrap_distribution %>% 
  get_confidence_interval(level = 0.95, type = "se", 
                          point_estimate = obs_diff_prop)
se_ci
```

```
## # A tibble: 1 x 2
##   lower_ci upper_ci
##      <dbl>    <dbl>
## 1   0.0522    0.531
```

Let's visualize `bootstrap_distribution` again, but now the standard error based 95% confidence interval for $p_{m} - p_{f}$ in Figure \@ref(fig:bootstrap-distribution-two-prop-se). Again, notice how the value 0 is not included in our confidence interval, again suggesting that $p_{m}$ and $p_{f}$ are truly different!


```r
visualize(bootstrap_distribution) + 
  shade_confidence_interval(endpoints = se_ci)
```
![(\#fig:bootstrap-distribution-two-prop-se)Standard error-based 95 percent confidence interval.](10-hypothesis-testing_files/figure-latex/bootstrap-distribution-two-prop-se-1.pdf) 


### "There is only one test" {#only-one-test}

Let's recap the steps necessary to conduct a hypothesis test using the terminology, notation, and definitions related to sampling you saw in Section \@ref(understanding-ht) and the `infer` workflow from Section \@ref(infer-workflow-ht):

1. `specify()` the variables of interest in your data frame.
1. `hypothesize()` the null hypothesis $H_0$. In other words, set a "model for the universe" assuming $H_0$ is true.
1. `generate()` shuffles assuming $H_0$ is true. In other words, *simulate* data assuming $H_0$ in true. 
1. `calculate()` the *test statistic* of interest, both for the observed data and your *simulated* data. 
1. `visualize()` the resulting *null distribution* and compute the *p-value* by comparing the null distribution to the observed test statistic. 

While this is a lot to digest, especially the first time you encounter hypothesis testing, the nice thing is that once you understand this general framework, then you can understand *any* hypothesis test. In a famous blog post, computer scientist Allen Downey called this the  ["There is only one test"](http://allendowney.blogspot.com/2016/06/there-is-still-only-one-test.html) framework, for which he created the flowchart displayed in Figure \@ref(fig:htdowney). 

\begin{figure}
\includegraphics[width=0.9\linewidth]{images/copyright/there_is_only_one_test} \caption{Allan Downey's hypothesis testing framework.}(\#fig:htdowney)
\end{figure}

Notice its similarity with the "hypothesis testing via `infer`" diagram you saw in Figure \@ref(fig:inferht). That's because the `infer` package was explicitly designed to match the "There is only one test" framework. So if you can understand the framework, you can easily generalize these ideas for all hypothesis testing scenarios. 







## Interpreting hypothesis tests {#ht-interpretation}

Interpreting the results of hypothesis tests are one of the more challenging aspects of this method for statistical inference. In this section, we'll focus on ways to help with deciphering the process and address some common misconceptions. 

### Two possible outcomes {#trial}

In Section \@ref(understanding-ht), we mentioned that given a pre-specified significance level $\alpha$ there are two possible outcomes of a hypothesis test:

* If the p-value is less than $\alpha$, then we *reject* the null hypothesis $H_0$ in favor of $H_A$.
* If the p-value is greater than or equal to $\alpha$, we *fail to reject* the null hypothesis $H_0$.

Unfortunately, the latter result is often misinterpreted as "accepting the null hypothesis $H_0$." While at first glance it may seem that the statements "failing to reject $H_0$" and "accepting $H_0$" are equivalent, there actually is a subtle difference. Saying that we "accept the null hypothesis $H_0$" is equivalent to stating "we think the null hypothesis $H_0$ is true." However, saying that we "fail to reject the null hypothesis $H_0$" is saying something else: "While $H_0$ might still be false, we don't have enough evidence to say so." In other words, there is an absence of enough proof. However, the absence of proof is not proof of absence. 

To further shed light on this distinction, \index{hypothesis testing!US criminal trial analogy} let's use the United States criminal justice system as an analogy. A criminal trial in the United States is a similar situation to hypothesis tests whereby a choice between two contradictory claims must be made about a defendant who is on trial:

1. The defendant is truly either "innocent" or "guilty."
1. The defendant is presumed "innocent until proven guilty." 
1. The defendant is found guilty only if there is *strong evidence* that the defendant is guilty. The phrase "beyond a reasonable doubt" is often used as a guideline for determining a cutoff for when enough evidence exists to find the defendant guilty.
1. The defendant is found to be either "not guilty" or "guilty" in the ultimate verdict.

In other words, "not guilty" verdicts are not suggesting the defendant is "innocent", but instead that "while the defendant may still actually be guilty, there wasn't enough evidence to prove this fact." Now let's make the connection with hypothesis tests:

1. Either the null hypothesis $H_0$ or the alternative hypothesis $H_A$ is true.
1. Hypothesis tests are always conducted assuming the null hypothesis $H_0$ is true.
1. We reject the null hypothesis $H_0$ in favor of $H_A$ only if the evidence found in the sample suggests that $H_A$ is true. The significance level $\alpha$ is used as a guideline to set the threshold on how strong evidence we require. 
1. We ultimately decide to either "fail to reject $H_0$" or "reject $H_0$." 

So while gut instinct may suggest "failing to reject $H_0$" and "accepting $H_0$" are equivalent statements, they are not. "Accepting $H_0$" is equivalent to finding a defendant innocent. However, courts do not defendants "innocent," but rather they find them "not guilty." Putting things differently, defense attorneys do not need to prove that their clients are innocent, rather they only need to prove that clients are "not guilty beyond a reasonable doubt".

So going back to our resumes activity in Section \@ref(ht-infer), recall that our hypothesis test was $H_0: p_{m} - p_{f} = 0$ versus $H_A: p_{m} - p_{f} > 0$ and that we used a pre-specified significance level of $\alpha$ = 0.001.  We found a p-value of 0.024. Since the p-value was greater than $\alpha$ = 0.001, we failed to reject $H_0$. In other words, we didn't find any evidence in this particular sample to say that $H_0$ is false at the $\alpha$ = 0.001 significance level. We also state this conclusion using non-statistical language: we didn't find enough evidence in this data to suggest that there was no gender discrimination.


### Types of errors

Unfortunately, there is some chance a jury or a judge can make an incorrect decision in a criminal trial by reaching the wrong verdict. For example, finding a truly innocent defendant "guilty". Or on the other hand, finding a truly guilty defendant "not guilty." This can often stem from the fact that prosecutors don't have access to all the relevant evidence, but instead are limited to whatever evidence the police can find. 

The same holds for hypothesis tests. We can make incorrect decisions about a population parameter because we only have a sample of data from the population and thus sampling variation can lead us to incorrect conclusions. 

There are two possible erroneous conclusions in a criminal trial: either 1) a truly innocent person is found guilty or 2) a truly guilty person is found not guilty. Similarly, there are two possible errors in a hypothesis test: either 1) rejecting $H_0$ when in fact $H_0$ is true, called a **Type I error** \index{hypothesis testing!Type I error} or 2) failing to reject $H_0$ when in fact $H_0$ is false, called a \index{hypothesis testing!Type II error} **Type II error**. Another term used for "Type I error" is "false positive" while another term for "Type II error" include "false negative."

This risk of error is the price researchers pay for basing inference on a sample instead of performing a census on the entire population. But as we've seen in our numerous examples and activities so far, censuses are often very expensive and other times impossible, and thus researchers have no choice but to use a sample. 

Thus in any hypothesis test based on a sample, we have no choice but to tolerate the chance that a Type I error will be made and some chance that a Type II error will occur.

Thus a Type I error corresponds to incorrectly putting a truly innocent person in jail whereas a Type II error corresponds to letting a truly guilty person go free. Let's show the corresponding table for hypothesis tests


\begin{figure}
\includegraphics[width=0.9\linewidth]{images/gt_error_table_ht} \caption{Type I and Type II errors in hypothesis tests.}(\#fig:trial-errors-table-ht)
\end{figure}


### How do we choose alpha? {#choosing-alpha}

If we are using a sample to make inferences about a population, we run the risk of making errors. For confidence intervals, a corresponding "error" would be constructing a confidence interval that does not contain the true value of the population parameter. For hypothesis tests, this would be making either a Type I or Type II error. Obviously, we want to minimize the probability of either error; we want a small probability of making an incorrect conclusion:

- The probability of a Type I Error occurring is denoted by $\alpha$. The value of $\alpha$ is called the *significance level* of the hypothesis test, which we defined in Section \@ref(understanding-ht)
- The probability of a Type II Error is denoted by $\beta$. The value of $1-\beta$ is known as the *power* of the hypothesis test. 

In other words, $\alpha$ corresponds to the probability of incorrectly rejecting $H_0$ when in fact $H_0$ is true. On the other hand, $\beta$ corresponds to the probability of incorrectly failing to reject $H_0$ when in fact $H_0$ is false.

Ideally, we want $\alpha = 0$ and $\beta = 0$, meaning that the chance of making either error is 0. However, this can never be the case in any situation where we are sampling for inference. There will always be the possibility of making either error when we use sample data. Furthermore, these two error probabilities are inversely related. As the probability of a Type I error goes down, the probability of a Type II error goes up. 

What is typically done in practice is to fix the probability of a Type I error by pre-specifying a significance level $\alpha$ and then try to minimize $\beta$. In other words, we will tolerate a certain fraction of incorrect rejections of the null hypothesis $H_0$, and then try to minimize the fraction of incorrect non-rejections of $H_0$. 

So for example if we used $\alpha$ = 0.01, we would be using a hypothesis testing procedure that in the long run would incorrectly reject the null hypothesis $H_0$ one percent of the time. This is analogous to setting the confidence level of a confidence interval. 

So what value should you use for $\alpha$? \index{hypothesis testing!tradeoff between alpha and beta} Different fields have different conventions, but some commonly used values include 0.10, 0.05, 0.01, and 0.001. However, it is important to keep in mind that if you use a relatively small value of $\alpha$ then all things being equal, p-values will have a harder time being less than $\alpha$. Thus we would reject the null hypothesis less often. In other words, we would reject the null hypothesis $H_0$ only if we have *very strong* evidence to do so. This is known as a "conservative" test. 

On the other hand, if we used a relatively large value of $\alpha$ then all things being equal, p-values will have an easier time being less than $\alpha$. Thus we would reject the null hypothesis more often. In other words, we would reject the null hypothesis $H_0$ even if we only have *mild* evidence to do so. This is known as a "liberal" test. 

## Case study: Are action or romance movies rated higher? {#ht-case-study}

Let's apply our knowledge of hypothesis testing to answer the question: "Are action or romance movies rated higher on IMDb?" [IMDb](https://www.imdb.com/) is a database on the internet providing information on movie and television show casts, plot summaries, trivia, and ratings. We'll investigate if, on average, action or romance movies get higher ratings on IMDb.

### IMDb ratings data {#imdb-data}

The `movies` dataset in the `ggplot2movies` package contains information on 58,788 movies that have been rated by users of IMDB.com. 


```r
movies
```

```
## # A tibble: 58,788 x 24
##    title  year length budget rating votes    r1    r2    r3    r4    r5    r6
##    <chr> <int>  <int>  <int>  <dbl> <int> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl>
##  1 $      1971    121     NA    6.4   348   4.5   4.5   4.5   4.5  14.5  24.5
##  2 $100~  1939     71     NA    6      20   0    14.5   4.5  24.5  14.5  14.5
##  3 $21 ~  1941      7     NA    8.2     5   0     0     0     0     0    24.5
##  4 $40,~  1996     70     NA    8.2     6  14.5   0     0     0     0     0  
##  5 $50,~  1975     71     NA    3.4    17  24.5   4.5   0    14.5  14.5   4.5
##  6 $pent  2000     91     NA    4.3    45   4.5   4.5   4.5  14.5  14.5  14.5
##  7 $win~  2002     93     NA    5.3   200   4.5   0     4.5   4.5  24.5  24.5
##  8 '15'   2002     25     NA    6.7    24   4.5   4.5   4.5   4.5   4.5  14.5
##  9 '38    1987     97     NA    6.6    18   4.5   4.5   4.5   0     0     0  
## 10 '49-~  1917     61     NA    6      51   4.5   0     4.5   4.5   4.5  44.5
## # ... with 58,778 more rows, and 12 more variables: r7 <dbl>, r8 <dbl>,
## #   r9 <dbl>, r10 <dbl>, mpaa <chr>, Action <int>, Animation <int>,
## #   Comedy <int>, Drama <int>, Documentary <int>, Romance <int>, Short <int>
```

We'll focus on a random sample of 68 movies that are classified as either "action" or "romance" movies but not both. We disregard movies that are classified as both so that we can assign all 68 movies into either category. Furthermore, since the original `movies` dataset was a little messy, we provide a pre-wrangled version of our data in the `movies_sample` data frame included in the `moderndive` package. If you're curious, you can look at the necessary data wrangling code to do this on [GitHub](https://github.com/moderndive/moderndive/blob/master/data-raw/process_data_sets.R#L14).


```r
movies_sample
```

```
## # A tibble: 68 x 4
##    title                     year rating genre  
##    <chr>                    <int>  <dbl> <chr>  
##  1 Underworld                1985    3.1 Action 
##  2 Love Affair               1932    6.3 Romance
##  3 Junglee                   1961    6.8 Romance
##  4 Eversmile, New Jersey     1989    5   Romance
##  5 Search and Destroy        1979    4   Action 
##  6 Secreto de Romelia, El    1988    4.9 Romance
##  7 Amants du Pont-Neuf, Les  1991    7.4 Romance
##  8 Illicit Dreams            1995    3.5 Action 
##  9 Kabhi Kabhie              1976    7.7 Romance
## 10 Electric Horseman, The    1979    5.8 Romance
## # ... with 58 more rows
```

The variables include the `title` and `year` the movie was filmed. Furthermore, we have a numerical variable `rating`, which is the IMDb rating out of 10 stars, and a binary categorical variable `genre` indicating if the movie was an `Action` or `Romance` movie. We are interested in whether `Action` or `Romance` movies got a higher `rating` on average.

Let's perform an exploratory data analysis of this data. Recall that a boxplot is a visualization we can use to show the relationship between a numerical and a categorical variable. Another option y would be to use a faceted histogram. However in the interest of brevity, let's only present the boxplot in Figure \@ref(fig:action-romance-boxplot).


```r
ggplot(data = movies_sample, aes(x = genre, y = rating)) +
  geom_boxplot() +
  labs(y = "IMDb rating")
```

![(\#fig:action-romance-boxplot)Boxplot of IMDb rating vs genre.](10-hypothesis-testing_files/figure-latex/action-romance-boxplot-1.pdf) 

Eyeballing Figure \@ref(fig:action-romance-boxplot), it appears that romance movies have a higher median rating. Do we have reason to believe however, that there is a *significant* difference between the mean `rating` for action movies compared to romance movies?  It's hard to say just based on the plot. The boxplot does show that the median sample rating is higher for romance movies. However, there is a large amount of overlap between the boxes.  

Let's calculate some summary statistic split by the binary categorical variable `genre`: the number of movies, the mean rating, and the standard deviation split.  We'll do this using `dplyr` data wrangling verbs. Notice in particular how we count the number of each type of movie using the `n()` summary function. 


```r
movies_sample %>% 
  group_by(genre) %>% 
  summarize(n = n(), mean_rating = mean(rating), std_dev = sd(rating))
```

```
## `summarise()` ungrouping output (override with `.groups` argument)
```

```
## # A tibble: 2 x 4
##   genre       n mean_rating std_dev
##   <chr>   <int>       <dbl>   <dbl>
## 1 Action     32        5.28    1.36
## 2 Romance    36        6.32    1.61
```

```
## `summarise()` ungrouping output (override with `.groups` argument)
```

Observe that we have 36 movies with an average rating of 6.32 stars and 32 movies with an average rating of 5.28 stars. The difference in these average ratings is thus 6.32 - 5.28 = 1.05. So there appears to be an edge of 1.05 stars in favor of romance movies. The question is however, are these results indicative of a true difference for *all* romance and action movies? Or could we attribute this difference to chance *sampling variation*? 


### Sampling scenario

Let's now revisit this study in terms of terminology and notation related to sampling we studied in Section \@ref(terminology-and-notation). 

The *study population* is all movies in the IMDb database that are either action or romance (but not both). The *sample* from this population is the 68 movies included in the `movies_sample` dataset. Since this sample was randomly taken from the population `movies`, it is representative of all romance and action movies on IMDb. Thus, any analysis and results based on `movies_sample` can generalize to the entire population.

What are the relevant *population parameter* and *point estimates*? We introduce the fourth sampling scenario in Table \@ref(tab:summarytable-ch10). 

\begin{table}[!h]

\caption{(\#tab:summarytable-ch10)Scenarios of sampling for inference}
\centering
\fontsize{10}{12}\selectfont
\begin{tabular}[t]{>{\raggedleft\arraybackslash}p{0.5in}>{\raggedright\arraybackslash}p{0.7in}>{\raggedright\arraybackslash}p{1in}>{\raggedright\arraybackslash}p{1.1in}>{\raggedright\arraybackslash}p{1in}}
\toprule
Scenario & Population parameter & Notation & Point estimate & Notation.\\
\midrule
1 & Population proportion & $p$ & Sample proportion & $\widehat{p}$\\
2 & Population mean & $\mu$ & Sample mean & $\overline{x}$ or $\widehat{\mu}$\\
3 & Difference in population proportions & $p_1 - p_2$ & Difference in sample proportions & $\widehat{p}_1 - \widehat{p}_2$\\
4 & Difference in population means & $\mu_1 - \mu_2$ & Difference in sample means & $\overline{x}_1 - \overline{x}_2$\\
\bottomrule
\end{tabular}
\end{table}

So whereas the sampling bowl exercise in Section \@ref(sampling-activity) concerned *proportions*, the pennies exercise in Section \@ref(resampling-tactile) concerned *means* and the promotions activity in Section \@ref(ht-activity) concerned *differences in proportions*, we are now concerned with *differences in means*. 

In other words, the population parameter of interest is the difference in population mean ratings $\mu_a - \mu_r$, where $\mu_a$ is the mean rating of all action movies on IMDb and similarly $\mu_r$ is the mean rating of all romance movies. Additionally the point estimate/sample statistic of interest is the difference in sample means $\overline{x}_a - \overline{x}_r$, where $\overline{x}_a$ is the mean rating of the $n_a$ = 32 movies in our sample and $\overline{x}_r$ is the mean rating of the $n_r$ = 36 in our sample. Based on our earlier exploratory data analysis, our estimate $\overline{x}_a - \overline{x}_r$ is 5.28 - 6.32 = -1.05. 

So there appears to be a slight difference of -1.05 in favor of romance movies. The question is however, could this difference of -1.05 be merely due to chance and sampling variation? Or are these results indicative of a true difference in mean ratings for *all* romance and action movies on IMDb?  To answer this question, we'll use hypothesis testing. 


### Conducting the hypothesis test

We'll be testing:

$$
\begin{aligned}
H_0 &: \mu_a - \mu_r = 0\\
\text{vs } H_A&: \mu_a - \mu_r \neq 0
\end{aligned}
$$

In other words, the null hypothesis $H_0$ suggests that both romance and action movies have the same mean rating. This is the "hypothesized universe" we'll *assume* is true. On the other hand, the alternative hypothesis $H_A$ suggests that there is a difference. Unlike the one-sided alternative we used in the promotions exercise $H_a: p_m - p_f > 0$, we are now considering a two-sided alternative of $H_A: \mu_a - \mu_r \neq 0$. 

Furthermore, we'll pre-specify a relatively high significance level of $\alpha$ = 0.2. By setting this value high, all things being equal, there is a higher chance that the p-value will be less than $\alpha$. Thus there is a higher chance that we'll reject the null hypothesis $H_0$ in favor of the alternative hypothesis $H_A$. In other words, we'll reject the hypothesis that there is no difference in mean ratings for all action and romance movies, even if we only have mild evidence. 


#### 1. `specify` variables {-}

Let's now perform all the steps of the `infer` workflow. We first `specify()` the variables of interest in the `movies_sample` data frame using the formula `rating ~ genre`. This tells `infer` that the numerical variable `rating` is the outcome variable while the binary categorical variable `genre` is the explanatory variable. Note than unlike when we were previously interested in proportions, since we are now interested in the mean of a numerical variable, we do not need to set the `success` argument.


```r
movies_sample %>% 
  specify(formula = rating ~ genre)
```

```
## Response: rating (numeric)
## Explanatory: genre (factor)
## # A tibble: 68 x 2
##    rating genre  
##     <dbl> <fct>  
##  1    3.1 Action 
##  2    6.3 Romance
##  3    6.8 Romance
##  4    5   Romance
##  5    4   Action 
##  6    4.9 Romance
##  7    7.4 Romance
##  8    3.5 Action 
##  9    7.7 Romance
## 10    5.8 Romance
## # ... with 58 more rows
```

Observe at this point that the data in `movies_sample` has not changed. The only change so far is the newly defined `Response: rating (numeric)` and `Explanatory: genre (factor)` *meta-data*.

#### 2. `hypothesize` the null {-}

We set the null hypothesis $H_0: \mu_a - \mu_r = 0$ by using the `hypothesize()` function. Since we have two samples, action and romance movies, we set `null = "independence"` as we described in Section \@ref(ht-infer).


```r
movies_sample %>% 
  specify(formula = rating ~ genre) %>% 
  hypothesize(null = "independence")
```

```
## Response: rating (numeric)
## Explanatory: genre (factor)
## Null Hypothesis: independence
## # A tibble: 68 x 2
##    rating genre  
##     <dbl> <fct>  
##  1    3.1 Action 
##  2    6.3 Romance
##  3    6.8 Romance
##  4    5   Romance
##  5    4   Action 
##  6    4.9 Romance
##  7    7.4 Romance
##  8    3.5 Action 
##  9    7.7 Romance
## 10    5.8 Romance
## # ... with 58 more rows
```

#### 3. `generate` replicates {-}

After we have set the null hypothesis, we generate "shuffled" replicates assuming the null hypothesis is true by repeating the shuffling/permutation exercise you performed in Section \@ref(ht-activity). We'll repeat this resampling without replacement of `type = "permute"` a total of `reps = 1000` times . 


```r
movies_sample %>% 
  specify(formula = rating ~ genre) %>% 
  hypothesize(null = "independence") %>% 
  generate(reps = 1000, type = "permute")
```


```
## Response: rating (numeric)
## Explanatory: genre (factor)
## Null Hypothesis: independence
## # A tibble: 68,000 x 3
## # Groups:   replicate [1,000]
##    rating genre   replicate
##     <dbl> <fct>       <int>
##  1    7.1 Action          1
##  2    4.8 Romance         1
##  3    4   Romance         1
##  4    7.3 Romance         1
##  5    5.9 Action          1
##  6    5.8 Romance         1
##  7    7.1 Romance         1
##  8    7.4 Action          1
##  9    9.6 Romance         1
## 10    7.1 Romance         1
## # ... with 67,990 more rows
```

Observe that the resulting data frame has 68,000 rows. This is because we performed resampling of 68 movies with replacement 1000 times and 68,000 = 68 $\times$ 1000. The variable `replicate` indicates which resample each row belongs to. So it has the value `1` 68 times, the value `2` 68 times, all the way through to the value `1000` 68 times. 


#### 4. `calculate` summary statistics {-}

Now that we have 1000 replicated "shuffles" assuming the null hypothesis $H_0$ that both `Action` and `Romance` movies on average have the same ratings on IMDb, let's `calculate()` the appropriate summary statistic for these 1000 replicated shuffles. Recall from Section \@ref(understanding-ht) that point estimates/summary statistics relating to hypothesis testing have a specific name: *test statistics*. Since the unknown population parameter of interest is the difference in population means $\mu_{a} - \mu_{r}$, the test statistic of interest here is the difference in sample means $\overline{x}_{a} - \overline{x}_{r}$. 

For each of our 1000 shuffles, we can calculate this test statistic by setting `stat = "diff in means"`. Furthermore, since we are interested in $\overline{x}_{a} - \overline{x}_{r}$, we set `order = c("Action", "Romance")`. Let's save the results in a data frame called `null_distribution_movies`:


```r
null_distribution_movies <- movies_sample %>% 
  specify(formula = rating ~ genre) %>% 
  hypothesize(null = "independence") %>% 
  generate(reps = 1000, type = "permute") %>% 
  calculate(stat = "diff in means", order = c("Action", "Romance"))
null_distribution_movies
```


```
## # A tibble: 1,000 x 2
##    replicate   stat
##        <int>  <dbl>
##  1         1 -0.321
##  2         2 -0.109
##  3         3  0.293
##  4         4  0.104
##  5         5  0.375
##  6         6  0.564
##  7         7 -0.357
##  8         8  0.576
##  9         9  0.493
## 10        10  0.175
## # ... with 990 more rows
```

Observe that we have 1000 values of `stat`, each representing one instance of $\overline{x}_{a} - \overline{x}_{r}$. The 1000 values form the *null distribution*, which is the technical term for the sampling distribution of the difference in sample means $\overline{x}_{a} - \overline{x}_{r}$ assuming $H_0$ is true. 

But wait! What happened in real-life? What was the observed difference in promotion rates? In other words, what was the *observed test statistic* $\overline{x}_{a} - \overline{x}_{r}$? Recall that our earlier data wrangling from earlier, this observed difference in means was 5.28 - 6.32 = -1.05.  

We can also achieve this using the code that constructed the null distribution `null_distribution_movies` but with the `hypothesize()` and `generate()` steps removed. Let's save this in `obs_diff_means`:


```r
obs_diff_means <- movies_sample %>% 
  specify(formula = rating ~ genre) %>% 
  calculate(stat = "diff in means", order = c("Action", "Romance"))
obs_diff_means
```

```
## # A tibble: 1 x 1
##    stat
##   <dbl>
## 1 -1.05
```

#### 5. `visualize` the p-value {-}

Lastly, in order to compute the p-value, we have to assess how "extreme" the observed difference in means of -1.05 is. We do this by comparing -1.05 to our null distribution, which was constructed in a hypothesized universe of no true difference in movie ratings. 

Let's visualize both the null distribution and the p-value in Figure \@ref(fig:null-distribution-movies-2). However, unlike our example in Section \@ref(infer-workflow-ht) involving promotions, since we have a two-sided alternative hypothesis $H_A: \mu_a - \mu_r \neq 0$, we have to allow for both possibilities for "more extreme", so we set `direction = "both"`.


```r
visualize(null_distribution_movies, bins = 10) + 
  shade_p_value(obs_stat = obs_diff_means, direction = "both")
```

![(\#fig:null-distribution-movies-2)Null distribution, observed test statistic, and p-value.](10-hypothesis-testing_files/figure-latex/null-distribution-movies-2-1.pdf) 

Let's go over the elements of this plot. First, the histogram is the *null distribution*. Second, the solid line is the *observed test statistic*, or the difference in sample means we observed in real-life of 5.28 - 6.32 = -1.05. Third, the two shaded areas of the histogram form the *p-value*, or the probability of obtaining a test statistic just as or more extreme than the observed test statistic *assuming the null hypothesis $H_0$ is true*.

What proportion of the null distribution is shaded? In other words, what is the numerical value of the p-value? We use the `get_p_value()` function to compute this value:


```r
null_distribution_movies %>% 
  get_p_value(obs_stat = obs_diff_means, direction = "both")
```

```
## # A tibble: 1 x 1
##   p_value
##     <dbl>
## 1   0.006
```


This p-value of 0.006 is somewhat small. In other words, there is a somewhat small chance that we'd observe a difference of 5.28 - 6.32 = -1.05 in a hypothesized universe where there was truly no difference in ratings. 

This p-value is in fact much smaller than our pre-specified $\alpha$ significance level of 0.2. Thus, we are very inclined to reject the null hypothesis $H_0: \mu_a - \mu_r = 0$, in favor of the alternative hypothesis $H_A: \mu_a - \mu_r \neq 0$. In non-statistical language, the conclusion is: the evidence in this sample of data suggests that we should reject the hypothesis that there is no difference in mean IMDb ratings between romance and action movies in favor of the hypothesis that there is a difference. 



## Conclusion

### Theory-based hypothesis tests {#theory-hypo}

Much as when we showed you a theory-based method for constructing confidence intervals that involved mathematical formulas, we now present an example of a traditional theory-based method to conduct hypothesis tests. This method relies on probability models, probability distributions, and a few assumptions to construct the null distribution. This is in contrast to the approach we've been using throughout this book where we relied on computer simulations to construct the null distribution.

These traditional theory-based methods have been used for decades mostly because researchers didn't have access to computers that could run thousands of calculations quickly and efficiently. Now that computing power is much cheaper and more accessible, simulation-based methods are much more feasible. However researchers in many fields continue to use theory-based methods. Hence we make it a point to include an example here.

As we'll show in this section, any theory-based method is ultimately an approximation to the simulation-based method. The theory-based method we'll focus on is known as the *two-sample $t$-test* for testing differences in sample means. However, the test statistic we'll use won't be the difference in sample means $\overline{x}_1 - \overline{x}_2$, but rather the related  *two-sample $t$-statistic*. The data we'll use will once again be the `movies_sample` data of action and romance movies from Section \@ref(ht-case-study).


#### Two-sample t-statistic {-}

A common task in statistics is the process of "standardizing a variable." By standardizing different variables, we make them more comparable. For example, say you are interested in studying the distribution of temperature recordings from Portland, Oregon, USA with temperature recordings in Montreal, Quebec, Canada. Given that US temperatures are generally recorded in degrees Fahrenheit and Canadian temperatures are generally recorded in degrees Celsius, how can we make them comparable? 

One approach would be to convert degrees Fahrenheit into Celsius, or vice versa. Another approach would be to convert them both to a common "standardized" scale, like degrees Kelvin. One common method for standardizing a variable from probability theory is to compute the \index{z-score} $z$-score:

$$z = \frac{x - \mu}{\sigma}$$

where $x$ represents one value of a variable, $\mu$ represents the mean of that variable, and $\sigma$ represents that standard deviation of the variable. 

You first subtract the mean $\mu$ from each value of $x$ and then divide $x - \mu$ by the standard deviation $\sigma$. These operations will have the effect of "re-centering" your variable around 0 and "re-scaling" your variable $x$ so that they have what are known as "standard units."

Thus for every value that your variable can take, it has a corresponding $z$-score that gives how many standard units away that value is from the mean $\mu$. $z$-scores are normally distributed with mean 0 and standard deviation 1.  Such a curve is called a "$z$-distribution" as well a "standard normal" curve and they have the common, bell-shaped pattern from Figure \@ref(fig:zcurve). 

\begin{figure}
\includegraphics[width=0.8\linewidth]{10-hypothesis-testing_files/figure-latex/zcurve-1} \caption{Standard normal z curve.}(\#fig:zcurve)
\end{figure}

Bringing these back to the difference of sample mean ratings $\overline{x}_a - \overline{x}_r$ of action versus romance movies, how would we standardize this variable? By once again subtracting its mean and dividing by its standard deviation. Recall two facts from Section \@ref(moral-of-the-story). First, if the sampling was done in a representative fashion, then the sampling distribution of $\overline{x}_a - \overline{x}_r$ will be centered at the true population parameter $\mu_a - \mu_r$. Second, the standard deviation of point estimates like $\overline{x}_a - \overline{x}_r$ have a special name: the standard error

Applying these ideas, we present the *two-sample $t$-statistic*\index{two-sample t-statistic}:

$$t = \dfrac{ (\bar{x}_a - \bar{x}_r) - (\mu_a - \mu_r)}{ \text{SE}_{\bar{x}_a - \bar{x}_r} } = \dfrac{ (\bar{x}_a - \bar{x}_r) - (\mu_a - \mu_r)}{ \sqrt{\dfrac{{s_a}^2}{n_a} + \dfrac{{s_r}^2}{n_r}}  }$$

Oofda! There is a lot to try to unpack here! Let's go slowly. In the numerator $\bar{x}_a-\bar{x}_r$ is the difference in sample means while $\mu_a - \mu_r$ is the difference in population means. 

In the denominator $s_a$ and $s_r$ are the *sample standard deviations* of the action and romance movies in our sample `movies_sample`. Lastly, $n_a$ and $n_r$ are the sample sizes of the action and romance movies. Putting this together gives us the standard error $\text{SE}_{\bar{x}_a - \bar{x}_r}$.
    
Observe that the formula for $\text{SE}_{\bar{x}_a - \bar{x}_r}$ has the sample sizes $n_a$ and $n_r$ in them. So as the sample sizes increase, the standard error goes down. We've seen this concept numerous times now, in particular in our simulations using the three virtual shovels with $n$ = 25, 50, and 100 slots in Figure \@ref(fig:comparing-sampling-distributions-3) and in Section \@ref(ci-width) where we studied the effect of using larger sample sizes on the widths of confidence intervals. 

So how can we use the two-sample $t$-statistic as a test statistic in our hypothesis test? First, assuming the null hypothesis $H_0: \mu_a - \mu_r = 0$ is true, the right-hand side of the numerator, $\mu_a - \mu_r$, becomes 0. Second, similarly to how the Central Limit Theorem states that sample means follow a normal distribution, it can be mathematically proven that the two-sample $t$-statistic follows a *$t$ distribution with degrees of freedom* "roughly equal" to $df = n_a + n_r - 2$.  

We display three examples of $t$-distributions in Figure \@ref(fig:t-distributions) along with the standard normal $z$ curve.


![(\#fig:t-distributions)Examples of t-distributions and the z curve.](10-hypothesis-testing_files/figure-latex/t-distributions-1.pdf) 

Begin by looking at the center of the plot at 0 on the horizontal axis. As you move up from the value of 0, follow along with the labels and note that the bottom curve corresponds to 1 degree of freedom, the curve above it is for 3 degrees of freedom, the curve above that is for 10 degrees of freedom, and lastly the dashed curve is the standard normal $z$ curve.

Observe that all four curves have a bell shape, are centered at 0, and that as the degrees of freedom increase, the $t$-distribution more and more resembles the standard normal $z$ curve. The "degrees of freedom" \index{degrees of freedom} measures how different the $t$ distribution will be from a normal distribution. $t$-distributions tend to have more values in the tails of their distributions than the standard normal $z$ curve.

This "roughly equal" statement indicates that the equation $df = n_a + n_r - 2$ is a "good enough" approximation to the true degrees of freedom. The true [formula](https://en.wikipedia.org/wiki/Student%27s_t-test#Equal_or_unequal_sample_sizes,_unequal_variances) is a bit more complicated than this simple expression, but we've found the formula to be beyond the reach of those new to statistical inference and it does little to build the intuition of the $t$-test. The message to retain however is that small sample sizes lead to small degrees of freedom and thus small sample sizes lead to $t$-distributions that are different than the $z$ curve. On the other hand, large sample sizes lead to large degrees of freedom and thus lead to $t$ distributions that closely align with the standard normal $z$-curve.
  
So, assuming the null hypothesis $H_0$ is true, our formula for the test statistic simplifies a bit:

$$t = \dfrac{ (\bar{x}_a - \bar{x}_r) - 0}{ \sqrt{\dfrac{{s_a}^2}{n_a} + \dfrac{{s_r}^2}{n_r}}  } = \dfrac{ \bar{x}_a - \bar{x}_r}{ \sqrt{\dfrac{{s_a}^2}{n_a} + \dfrac{{s_r}^2}{n_r}}  }$$

Let's compute the values necessary for this two-sample $t$-statistic. Recall the summary statistics we computed during our exploratory data analysis in Section \@ref(imdb-data).


```r
movies_sample %>% 
  group_by(genre) %>% 
  summarize(n = n(), mean_rating = mean(rating), std_dev = sd(rating))
```

```
## `summarise()` ungrouping output (override with `.groups` argument)
```

```
## # A tibble: 2 x 4
##   genre       n mean_rating std_dev
##   <chr>   <int>       <dbl>   <dbl>
## 1 Action     32        5.28    1.36
## 2 Romance    36        6.32    1.61
```


Using these values, the observed two-sample $t$-test statistic is 

$$
\dfrac{ \bar{x}_a - \bar{x}_r}{ \sqrt{\dfrac{{s_a}^2}{n_a} + \dfrac{{s_r}^2}{n_r}}  } = 
\dfrac{5.28 - 6.32}{ \sqrt{\dfrac{{1.36}^2}{32} + \dfrac{{1.61}^2}{36}}  } = 
-2.906
$$

Great! How can we compute the p-value using this theory-based test statistic? We need to compare it to a null distribution, which we construct next.


#### Null distribution {-}
  
Let's revisit the null distribution for the test statistic $\bar{x}_a - \bar{x}_r$ we constructed in Section \@ref(ht-case-study). Let's visualize this in the left-hand plot of Figure \@ref(fig:comparing-diff-means-t-stat)


```r
# Construct null distribution of xbar_a - xbar_m:
null_distribution_movies <- movies_sample %>% 
  specify(formula = rating ~ genre) %>% 
  hypothesize(null = "independence") %>% 
  generate(reps = 1000, type = "permute") %>% 
  calculate(stat = "diff in means", order = c("Action", "Romance"))
visualize(null_distribution_movies, bins = 10)
```

The `infer` package also includes some built-in theory-based test statistics as well. So instead of calculating the test statistic of interest as the `"diff in means"` $\bar{x}_a - \bar{x}_r$, we can calculate this defined two-sample $t$-statistic by setting `stat = "t"`. Let's visualize this in the right-hand plot of Figure \@ref(fig:comparing-diff-means-t-stat)


```r
# Construct null distribution of t:
null_distribution_movies_t <- movies_sample %>% 
  specify(formula = rating ~ genre) %>% 
  hypothesize(null = "independence") %>% 
  generate(reps = 1000, type = "permute") %>% 
  # Notice we switched stat from "diff in means" to "t"
  calculate(stat = "t", order = c("Action", "Romance"))
visualize(null_distribution_movies_t, bins = 10)
```



\begin{figure}

{\centering \includegraphics[width=1\linewidth]{10-hypothesis-testing_files/figure-latex/comparing-diff-means-t-stat-1} 

}

\caption{Comparing the null distributions of two test statistics.}(\#fig:comparing-diff-means-t-stat)
\end{figure}

Observe that while the shape of the null distributions of both the difference in means $\bar{x}_a - \bar{x}_r$ and the two-sample $t$-statistic are similar, the scales on the x-axis are different. The two-sample $t$-statistic are spread out over a larger range.

However, a traditional theory-based $t$-test doesn't look at the simulated histogram in `null_distribution_movies_t`, but instead it looks at the $t$-distribution curve with degrees of freedom equal to roughly 65.8496. This calculation is based on the complicated formula referenced previously, which we approximated with $df = n_a + n_r - 2$ = 32 + 36 - 2 = 66. Let's overlay this $t$-distribution curve over the top of our simulated two-sample $t$-statistics using the `method = "both"` argument in `visualize()`.


```r
visualize(null_distribution_movies_t, bins = 10, method = "both")
```

```
## Warning: Check to make sure the conditions have been met for the theoretical
## method. {infer} currently does not check these for you.
```

\begin{figure}

{\centering \includegraphics[width=1\linewidth]{10-hypothesis-testing_files/figure-latex/t-stat-3-1} 

}

\caption{Null distribution using t-statistic and t-distribution.}(\#fig:t-stat-3)
\end{figure}

Observe that the curve does a good job of approximating the histogram here. To calculate the $p$-value in this case, we need to figure out how much of the total area under the $t$-distribution curve is equal or "more extreme" our observed two-sample $t$-statistic. Since our alternative hypothesis $H_A: \mu_a - \mu_r \neq 0$ is a two-sided alternative, we need to add up the areas in both tails. 

We first compute the observed two-sample $t$-statistic using `infer` verbs:


```r
obs_two_sample_t <- movies_sample %>% 
  specify(formula = rating ~ genre) %>% 
  calculate(stat = "t", order = c("Action", "Romance"))
obs_two_sample_t
```

```
## # A tibble: 1 x 1
##    stat
##   <dbl>
## 1 -2.91
```

So we are interested in finding the percentage of values that are at or above `obs_two_sample_t` = -2.906 or at or below `-obs_two_sample_t` = 2.906. We do this using the `shade_p_value()` function with the `direction` argument set to `"both"`:


```r
visualize(null_distribution_movies_t, method = "both") +
  shade_p_value(obs_stat = obs_two_sample_t, direction = "both")
```

```
## Warning: Check to make sure the conditions have been met for the theoretical
## method. {infer} currently does not check these for you.
```

\begin{figure}

{\centering \includegraphics[width=1\linewidth]{10-hypothesis-testing_files/figure-latex/t-stat-4-1} 

}

\caption{Null distribution using t-statistic and t-distribution with p-value shaded.}(\#fig:t-stat-4)
\end{figure}

(We'll discuss this warning message shortly.) What is the p-value? We apply `get_p_value()` to our null distribution saved in `null_distribution_movies_t`:


```r
null_distribution_movies_t %>% 
  get_p_value(obs_stat = obs_two_sample_t, direction = "both")
```

```
## # A tibble: 1 x 1
##   p_value
##     <dbl>
## 1   0.004
```

We have a very small p-value, and thus it is very unlikely that these results are due to *sampling variation*. Thus, we are inclined to reject $H_0$. 

Let's come back to that earlier warning message: `Check to make sure the conditions have been met for the theoretical method. {infer} currently does not check these for you.` To be able to use the $t$-test and other such theoretical methods, there are always a few conditions to check. The `infer` package does not automatically check these conditions, hence the warning message we received. These conditions are necessary so that the underlying mathematical theory holds. In order for the results of our two-sample $t$-test to be valid, three conditions must be met:

1. Nearly normal populations or large sample sizes. A general rule of thumb that works in many (but not all) situations is that the sample size $n$ should be greater than 30.
2. Both samples are selected independently of each other.
3. All observations are independent from each other.

Let's see if these conditions hold for our `movies_sample` data:

1. This is met since $n_a$ = 32 and $n_r$ = 36 are both larger than 30, satisfying our rule of thumb.
1. This is met since we sampled the action and romance movies at random and in an unbiased fashion from the database of all IMDb movies.
1. Unfortunately, we don't know how IMDb computes the ratings. For example, if the same person rated multiple movies, then those observations would be related and hence not independent.

Assuming all three conditions are met, we can be reasonably certain that the theory-based $t$-test results are valid. If any of the conditions were not met, we couldn't put as much faith into any conclusions.


<!--chapter:end:10-hypothesis-testing.Rmd-->

# (PART) Worked example {-} 

# Is ankle strength different between two groups at baseline

## Download and load libraries {-}


```r
if (!require("pacman")) install.packages("pacman")
pacman::p_load(tidyverse, # All purpose wrangling for dataframes
               readr, # importing and writing data
               openxlsx, # writing excel documents
               purrr, # for piping %>%
               knitr,
               moderndive,
               kableExtra,
               infer)
```

## Import data {-}


```r
subjdat <-  read_delim (file = "data/SubjectData.txt", # file name placed into a folder called data
                        delim = "\t", # file separater
                        col_names = TRUE) # the first row of the data is a header row

scalfac <-  read_delim (file = "data/ScaleFact.txt", # file name
                        delim = "\t", # file separater
                        col_names = TRUE) # the first row of the data is a header row

strn <-  read.xlsx (xlsxFile = "data/STRENGTH.xlsx")
```

## Data manipulation

1. Convert all colnames to lower cases. **Rationale:** Simply to make my life easier.


```r
colnames (strn) <-  tolower(colnames (strn))
colnames (subjdat) <-  tolower(colnames (subjdat))
```

2. Check column names for each dataframe. **Rationale:** I want to combined the two dataframes of `strn` and `subjdat`, and I need to make sure that the common columns are identically labelled. 


```r
colnames (strn) 
```

```
##  [1] "subj"     "group"    "time"     "side"     "set"      "rep"     
##  [7] "aexttorq" "aextwork" "aextpow"  "kexttorq" "kextwork" "kextpow"
```

```r
colnames (subjdat)
```

```
##  [1] "subj"              "group"             "age"              
##  [4] "wt"                "ht"                "bmi"              
##  [7] "runexp "           "runfreq6wks"       "runfreq12mths"    
## [10] "rundistwkly6wks"   "rundistwkly12mths" "loadrunexp"       
## [13] "runload"           "hxload"            "wttrainfreq6wks"  
## [16] "wttrainfreq12mths" "wttrainstatus"
```

When doing statistics, you need to know the end in sight. I need a dataframe which contains the subject identifier, time, group, and ankle strength `aexttorq` which is normalized to each participant's body mass.

3. Keep the columns you want by creating two additional objects: `subjdat.sub` and `strn.sub`. Combine the two new objects into a final dataframe `new.df`.


```r
# I need subj, and body mass from the subjdat dataframe
subjdat.sub <- subjdat %>%
  select (subj, wt)

# I need subj, time, group, side and aexttorq from the strn dataframe
strn.sub <- strn %>%
  select (subj, time, group, side, set, rep, aexttorq)

new.df <- strn.sub %>%
  inner_join(subjdat.sub, by = c("subj"))

# Have a look at the new dataframe
head (new.df)
```

```
##   subj time group side set rep aexttorq    wt
## 1    1  PRE     G    R   1   1       70 82.26
## 2    1  PRE     G    R   1   2       72 82.26
## 3    1  PRE     G    R   1   3       73 82.26
## 4    1  PRE     G    R   1   4       73 82.26
## 5    1  PRE     G    R   2   1       72 82.26
## 6    1  PRE     G    R   2   2       72 82.26
```

4. Divide `aexttorq` by `wt` to get normalized ankle strength


```r
new.df <- new.df %>%
  mutate (atorq.norm = aexttorq/wt)

head (new.df)
```

```
##   subj time group side set rep aexttorq    wt atorq.norm
## 1    1  PRE     G    R   1   1       70 82.26  0.8509604
## 2    1  PRE     G    R   1   2       72 82.26  0.8752735
## 3    1  PRE     G    R   1   3       73 82.26  0.8874301
## 4    1  PRE     G    R   1   4       73 82.26  0.8874301
## 5    1  PRE     G    R   2   1       72 82.26  0.8752735
## 6    1  PRE     G    R   2   2       72 82.26  0.8752735
```

5. Keep only strength values at baseline `time == "PRE"`


```r
new.df <- new.df %>%
  filter (time == "PRE")

head (new.df)
```

```
##   subj time group side set rep aexttorq    wt atorq.norm
## 1    1  PRE     G    R   1   1       70 82.26  0.8509604
## 2    1  PRE     G    R   1   2       72 82.26  0.8752735
## 3    1  PRE     G    R   1   3       73 82.26  0.8874301
## 4    1  PRE     G    R   1   4       73 82.26  0.8874301
## 5    1  PRE     G    R   2   1       72 82.26  0.8752735
## 6    1  PRE     G    R   2   2       72 82.26  0.8752735
```

6. Because I am interested in a simple analysis of is group 1 different from group 2, and I measured each person multiple times on each side, I want to create a very simple dataframe where one subject has one strength value. So I need to take the mean strength for each individual


```r
new.df <- new.df %>%
  group_by (subj, group) %>%
  summarize (atorq.norm = mean (atorq.norm)) %>%
  ungroup()
```

```
## `summarise()` regrouping output by 'subj' (override with `.groups` argument)
```

```r
head (new.df)
```

```
## # A tibble: 6 x 3
##    subj group atorq.norm
##   <dbl> <chr>      <dbl>
## 1     1 G          0.831
## 2     2 G          1.10 
## 3     3 T          0.686
## 4     4 G          0.760
## 5     5 T          0.965
## 6     6 T          1.17
```

7. Let's get some summary statistics per group. **Can you guess** if ankle strength is different in group `G` compared to `T`?


```r
# grouped summaries
new.df %>%
  group_by(group) %>%
  summarize (Mean = mean (atorq.norm, na.rm = T),
             Median = median (atorq.norm, na.rm = T),
             Max = max (atorq.norm, na.rm = T),
             Min = min (atorq.norm, na.rm = T),
             Sd = sd (atorq.norm, na.rm = T),
             Iqr = IQR (atorq.norm, na.rm = T),
             quant25 = quantile (atorq.norm, probs = 0.25, na.rm = T),
             quant75 = quantile (atorq.norm, probs = 0.75, na.rm = T))
```

```
## `summarise()` ungrouping output (override with `.groups` argument)
```

```
## # A tibble: 2 x 9
##   group  Mean Median   Max   Min    Sd   Iqr quant25 quant75
##   <chr> <dbl>  <dbl> <dbl> <dbl> <dbl> <dbl>   <dbl>   <dbl>
## 1 G      1.09   1.13  1.33 0.760 0.194 0.334   0.938    1.27
## 2 T      1.06   1.15  1.31 0.686 0.202 0.276   0.962    1.24
```

7. Visualize the individual points of the data, so I will create a cleaveland dotplot. Are the values reasonable?


```r
ggplot(data = new.df) + 
  geom_point(aes(y = seq(1,nrow(new.df),1), x = atorq.norm)) +
  ylab ("row number") + # Label as you like
  xlab ("ankle torque") # Label as you like
```

![](11-compare2groups_files/figure-latex/unnamed-chunk-11-1.pdf)<!-- --> 

8. Create a bar plot with error bars to see if differences stand out already.


```r
# generate a summarized dataframe 
df.plot = new.df %>%
  group_by(group) %>%
  summarize (Mean = mean (atorq.norm, na.rm = T), 
             Sd = sd (atorq.norm, na.rm = T)) %>%
  ungroup()

# Combined plot
ggplot(data = df.plot) + 
geom_bar (aes(y = Mean, x = group), stat = "identity") +
geom_errorbar(aes(ymin=Mean -Sd, ymax=Mean +Sd, x = group), 
            width=.2) +
ylab ("Normalized ankle torque") +
xlab ("Group")
```

![(\#fig:unnamed-chunk-12)ankle torque by group](11-compare2groups_files/figure-latex/unnamed-chunk-12-1.pdf) 

## Hypothesis testing

1. Get the null distribution in a world where two groups have identical mean strength


```r
null_distribution <-new.df %>%
  specify (formula = atorq.norm ~ group)%>% # outcome ~ independent variable
  hypothesize(null = "independence") %>% # independence means identical 
  generate(reps = 1000, type = "permute") %>% 
  calculate(stat = "diff in means", order = c("G", "T"))

head (null_distribution)
```

```
## # A tibble: 6 x 2
##   replicate     stat
##       <int>    <dbl>
## 1         1  0.0259 
## 2         2  0.0930 
## 3         3  0.0396 
## 4         4  0.0912 
## 5         5  0.00911
## 6         6 -0.0343
```

2. Get the observed difference in strength between two groups. This is just a simple subtraction of the means of the two groups


```r
obs_diff <-new.df %>%
  specify (formula = atorq.norm ~ group)%>% 
  calculate(stat = "diff in means", order = c("G", "T"))

obs_diff
```

```
## # A tibble: 1 x 1
##     stat
##    <dbl>
## 1 0.0259
```

3. visualize the p-value 


```r
visualize(null_distribution, binwidth = 0.05)
```

![](11-compare2groups_files/figure-latex/unnamed-chunk-15-1.pdf)<!-- --> 


```r
visualize(null_distribution, binwidth = 0.05)+ 
  shade_p_value(obs_stat = obs_diff, direction = "greater")
```

![](11-compare2groups_files/figure-latex/unnamed-chunk-16-1.pdf)<!-- --> 


```r
get_p_value(null_distribution, obs_stat = obs_diff, direction = "greater")
```

```
## # A tibble: 1 x 1
##   p_value
##     <dbl>
## 1   0.372
```

4. Calculate the mean difference in strength between the two groups and its confidence interval.


```r
bootstrap_distribution <- new.df %>%
  specify (formula = atorq.norm ~ group)%>% 
  generate(reps = 1000, type = "bootstrap") %>% # change this from permute to bootstreap
  calculate(stat = "diff in means", order = c("G", "T"))
```


```r
percentile_ci <- bootstrap_distribution %>% 
  get_confidence_interval(level = 0.95, type = "percentile")
percentile_ci
```

```
## # A tibble: 1 x 2
##   lower_ci upper_ci
##      <dbl>    <dbl>
## 1   -0.110    0.158
```


```r
visualize(bootstrap_distribution) + 
  shade_confidence_interval(endpoints = percentile_ci)
```

![](11-compare2groups_files/figure-latex/unnamed-chunk-20-1.pdf)<!-- --> 

<!--chapter:end:11-compare2groups.Rmd-->


# Is knee strength change over time between two groups different

## Download and load libraries {-}


```r
if (!require("pacman")) install.packages("pacman")
pacman::p_load(tidyverse, # All purpose wrangling for dataframes
               readr, # importing and writing data
               openxlsx, # writing excel documents
               purrr, # for piping %>%
               knitr,
               moderndive,
               kableExtra,
               infer)
```

## Import data {-}


```r
subjdat <-  read_delim (file = "data/SubjectData.txt", # file name placed into a folder called data
                        delim = "\t", # file separater
                        col_names = TRUE) # the first row of the data is a header row

scalfac <-  read_delim (file = "data/ScaleFact.txt", # file name
                        delim = "\t", # file separater
                        col_names = TRUE) # the first row of the data is a header row

strn <-  read.xlsx (xlsxFile = "data/STRENGTH.xlsx")
```

## Data manipulation

I need a dataframe which contains the subject identifier, time, group, and knee strength `kexttorq` which is normalized to each participant's body mass.

1. Convert all colnames to lower cases. **Rationale:** Simply to make my life easier.


```r
colnames (strn) <-  tolower(colnames (strn))
colnames (subjdat) <-  tolower(colnames (subjdat))
```

2. Check column names for each dataframe. **Rationale:** I want to combined the two dataframes of `strn` and `subjdat`, and I need to make sure that the common columns are identically labelled. 


```r
colnames (strn) 
```

```
##  [1] "subj"     "group"    "time"     "side"     "set"      "rep"     
##  [7] "aexttorq" "aextwork" "aextpow"  "kexttorq" "kextwork" "kextpow"
```

```r
colnames (subjdat)
```

```
##  [1] "subj"              "group"             "age"              
##  [4] "wt"                "ht"                "bmi"              
##  [7] "runexp "           "runfreq6wks"       "runfreq12mths"    
## [10] "rundistwkly6wks"   "rundistwkly12mths" "loadrunexp"       
## [13] "runload"           "hxload"            "wttrainfreq6wks"  
## [16] "wttrainfreq12mths" "wttrainstatus"
```


3. Keep the columns you want by creating two additional objects


```r
# I need subj, and body mass from the subjdat dataframe
subjdat.sub <- subjdat %>%
  select (subj, wt)

# I need subj, time, group, side and kexttorq from the strn dataframe
strn.sub <- strn %>%
  select (subj, time, group, side, set, rep, kexttorq)

new.df <- strn.sub %>%
  inner_join(subjdat.sub, by = c("subj"))

head (new.df)
```

```
##   subj time group side set rep kexttorq    wt
## 1    1  PRE     G    R   1   1      111 82.26
## 2    1  PRE     G    R   1   2      137 82.26
## 3    1  PRE     G    R   1   3      160 82.26
## 4    1  PRE     G    R   1   4      137 82.26
## 5    1  PRE     G    R   2   1      160 82.26
## 6    1  PRE     G    R   2   2      163 82.26
```

4. Divide `kexttorq` by `wt` to get normalized knee strength


```r
new.df <- new.df %>%
  mutate (ktorq.norm = kexttorq/wt)
```

5. Because I am interested in the change in `kexttorq.norm` between `PRE` and `POST`, I need to take create two variables ->  `kexttorq.norm.pre` and `kexttorq.norm.post`. To make life simpler, I will create one`kexttorq.norm` value for each subject at each time point.  


```r
new.df <- new.df %>%
  group_by (subj, time, group) %>%
  summarize (ktorq.norm = mean (ktorq.norm)) %>%
  ungroup()
```

```
## `summarise()` regrouping output by 'subj', 'time' (override with `.groups` argument)
```

```r
head (new.df)
```

```
## # A tibble: 6 x 4
##    subj time  group ktorq.norm
##   <dbl> <chr> <chr>      <dbl>
## 1     1 POST  G           1.83
## 2     1 PRE   G           1.85
## 3     2 POST  G           2.61
## 4     2 PRE   G           2.36
## 5     3 POST  T           1.43
## 6     3 PRE   T           1.44
```

6. I will than spread the data to make it wide.


```r
new.df <- new.df %>%
  spread (key = time, value = ktorq.norm)

head (new.df)
```

```
## # A tibble: 6 x 4
##    subj group  POST   PRE
##   <dbl> <chr> <dbl> <dbl>
## 1     1 G      1.83  1.85
## 2     2 G      2.61  2.36
## 3     3 T      1.43  1.44
## 4     4 G      1.83  1.36
## 5     5 T      2.09  1.75
## 6     6 T      2.26  2.50
```

7. I want to create a new variable that is the difference in `kexttorq.norm` which is `POST` strength minus `PRE` strength


```r
new.df <- new.df %>%
  mutate (diff = POST - PRE)

head (new.df)
```

```
## # A tibble: 6 x 5
##    subj group  POST   PRE     diff
##   <dbl> <chr> <dbl> <dbl>    <dbl>
## 1     1 G      1.83  1.85 -0.0175 
## 2     2 G      2.61  2.36  0.251  
## 3     3 T      1.43  1.44 -0.00829
## 4     4 G      1.83  1.36  0.470  
## 5     5 T      2.09  1.75  0.337  
## 6     6 T      2.26  2.50 -0.242
```


7. Let's get some summary statistics per group.**Can you guess** if `diff` is different in group `G` compared to `T`?



```r
# grouped summaries
new.df %>%
  group_by(group) %>%
  summarize (Mean = mean (diff, na.rm = T),
             Median = median (diff, na.rm = T),
             Max = max (diff, na.rm = T),
             Min = min (diff, na.rm = T),
             Sd = sd (diff, na.rm = T),
             Iqr = IQR (diff, na.rm = T),
             quant25 = quantile (diff, probs = 0.25, na.rm = T),
             quant75 = quantile (diff, probs = 0.75, na.rm = T))
```

```
## `summarise()` ungrouping output (override with `.groups` argument)
```

```
## # A tibble: 2 x 9
##   group  Mean Median   Max    Min    Sd   Iqr quant25 quant75
##   <chr> <dbl>  <dbl> <dbl>  <dbl> <dbl> <dbl>   <dbl>   <dbl>
## 1 G     0.253 0.271  0.685 -0.158 0.218 0.329  0.0765   0.405
## 2 T     0.120 0.0793 0.494 -0.607 0.297 0.368 -0.0173   0.351
```

7. Visualize the individual points of the data, so I will create a cleaveland dotplot


```r
ggplot(data = new.df) + 
  geom_point(aes(y = seq(1,nrow(new.df),1), x = diff)) +
  ylab ("row number") + # Label as you like
  xlab ("ankle torque") # Label as you like
```

![](12-comparechange2groups_files/figure-latex/unnamed-chunk-12-1.pdf)<!-- --> 

8. Create a bar plot with error bars to see if differences stand out already.



```r
# generate a summarized dataframe 
df.plot = new.df %>%
  group_by(group) %>%
  summarize (Mean = mean (diff, na.rm = T), 
             Sd = sd (diff, na.rm = T)) %>%
  ungroup()

# Combined plot
ggplot(data = df.plot) + 
geom_bar (aes(y = Mean, x = group), stat = "identity") +
geom_errorbar(aes(ymin=Mean -Sd, ymax=Mean +Sd, x = group), 
            width=.2) +
ylab ("Normalized Knee torque change") +
xlab ("Group")
```

![(\#fig:unnamed-chunk-13)ankle torque by group](12-comparechange2groups_files/figure-latex/unnamed-chunk-13-1.pdf) 

## Hypothesis testing

1. Get the null distribution in a world where two groups have identical change in knee strength


```r
null_distribution <-new.df %>%
  specify (formula = diff ~ group)%>% 
  hypothesize(null = "independence") %>% 
  generate(reps = 1000, type = "permute") %>% 
  calculate(stat = "diff in means", order = c("G", "T"))

head (null_distribution)
```

```
## # A tibble: 6 x 2
##   replicate      stat
##       <int>     <dbl>
## 1         1 -0.149   
## 2         2  0.0587  
## 3         3  0.0148  
## 4         4  0.130   
## 5         5 -0.160   
## 6         6  0.000400
```

2. Get the observed difference in change in strength between two groups


```r
obs_diff <-new.df %>%
  specify (formula = diff ~ group)%>% 
  calculate(stat = "diff in means", order = c("G", "T"))

obs_diff
```

```
## # A tibble: 1 x 1
##    stat
##   <dbl>
## 1 0.132
```

3. visualize the p-value 



```r
visualize(null_distribution, binwidth = 0.05)
```

![](12-comparechange2groups_files/figure-latex/unnamed-chunk-16-1.pdf)<!-- --> 


```r
visualize(null_distribution, binwidth = 0.05)+ 
  shade_p_value(obs_stat = obs_diff, direction = "greater")
```

![](12-comparechange2groups_files/figure-latex/unnamed-chunk-17-1.pdf)<!-- --> 

Get the p-value


```r
get_p_value(null_distribution, obs_stat = obs_diff, direction = "greater")
```

```
## # A tibble: 1 x 1
##   p_value
##     <dbl>
## 1   0.082
```

4. Calculate the mean difference in change in strength between the two groups and its confidence interval.


```r
bootstrap_distribution <- new.df %>%
  specify (formula = diff ~ group)%>% 
  generate(reps = 1000, type = "bootstrap") %>% # change this from permute to bootstreap
  calculate(stat = "diff in means", order = c("G", "T"))
```

get the CI


```r
percentile_ci <- bootstrap_distribution %>% 
  get_confidence_interval(level = 0.95, type = "percentile")
percentile_ci
```

```
## # A tibble: 1 x 2
##   lower_ci upper_ci
##      <dbl>    <dbl>
## 1  -0.0355    0.319
```


```r
visualize(bootstrap_distribution) + 
  shade_confidence_interval(endpoints = percentile_ci)
```

![](12-comparechange2groups_files/figure-latex/unnamed-chunk-21-1.pdf)<!-- --> 

<!--chapter:end:12-comparechange2groups.Rmd-->

