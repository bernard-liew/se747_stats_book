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
