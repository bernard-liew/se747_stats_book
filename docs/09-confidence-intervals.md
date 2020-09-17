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

