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

