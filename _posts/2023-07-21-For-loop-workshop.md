---
layout: post
title: For loop workshop
date: '2023-07-21'
categories: workshop
tags: NOAA Rclub workshop forloop R
---

# For. Loop. Fun.

**Objective**

-   learn base commands to call key components of your data (`nrow`, `ncol`, `$`, `[,]`,`c()`, etc.)

-   use base syntax to explore the logic behind `for`loops

## Using a mock dataset 'ToothGrowth'

### Mock data in baseR

-   R has plenty of dataframes and matrices to play with, take a look below!

```{r lets look at data}
data() # wow! these are all mock datasets in base R!  
```

`ToothGrowth` contains data on the effects of vitamin C on tooth growth in 60 Guinea pigs. Each animal received one of three dose levels of vitamin C (0.5, 1, and 2 mg/day) by one of two delivery methods, orange juice or ascorbic acid (vitamin C as `VC`).

## Before getting started..

Lets assign `DF_tooth` as our working version of ToothGrowth in our exercises

```{r}
DF_tooth <- ToothGrowth # lets call it something else
```

## Add some base commands to your tool belt!

Explore the data a bit - while we're at it **walk through some core commands**

-   `View()` - open the whole dataframe in a window

    ```{r view}
    View(DF_tooth) # opens a window with the data
    ```

<!-- -->

-   `head` - shows you the first rows of your dataframe

    ```{r the first few}
    head(DF_tooth) # head shows your the first rows of the dataframe
    ```

    ```{r the first two}
    head(DF_tooth, 2) # tell it how many rows you want to see
    ```

-   `tail` - shows you the last rows of your dataframe

    ```{r the last of 'em'}
    tail(DF_tooth) # tail shows you the last rows of the dataframe
    ```

    ```{r the last one}

    tail(DF_tooth, 1) # tell it how many rows you want to see
    ```

-   `nrow` - count the number of rows

    ```{r}
    nrow(DF_tooth) # prints a single integer for your object
    ```

-   `ncol` - count the number of columns

    ```{r how many columns are there}

    ncol(DF_tooth) # prints a single integer for your object
    ```

-   `dim` - dimensions of your object

    ```{r}
    dim(DF_tooth) # 60 rows and 3 columns!
    ```

-   `[,]` - use brackets to call the "x and y" coordinates of your object, being your [row, column]

    ```{r call it out}

    tail(DF_tooth, 1) # look at the last row again, we see the row number is 60 and there are three columns

    # last row is 60 and the first column is len - below == 23!
    DF_tooth[60,1] # 23

    # last row is 60 and the second column is supp
    DF_tooth[60,2] # 'OJ'

    # last row is 60 and the third column is dose
    DF_tooth[60,3] # 2

    ```

-   `c()` - concatenate, used to extract rows and columns or list values!

    ```{r combine}

    c(1:5) # with integers!

    c('one', 'of', 'me', 'is', 'order', 'out', 'of') # with strings!
    ```

    **Activity**: Print the first five rows of the 'len' column in `DF_tooth`

-   use the commands above to solve

    ```{r try it out}

    head(DF_tooth) # we just want to print `4.2, 11.5, 7.3, 5.8, 6.4`

    # try it below!

    ```

# Loops, what are they good *for*? .. *absolutely somethin'!*

**About** for-loops iterate over a collection of objects, such as a vector, a list, a matrix, or a dataframe, and apply the same set of operations on each item of a given data structure.

**Why join the *for-*ce?**

-   keep your code clean, remove unnecessary repetitive code blocks

    -   streamline you QC, statistics, sanity checks, and more!

-   honest data carpentry - start with raw data to form something new & reproducible!

    -   create new columns based on unique criteria

    -   comment as you go, keep a bread crumb trail from old to new data files

-   (my opinion) keeps coding logic fresh!

**How to do it**

-   `for` to open your for loop

-   `()` set your identifier and call collection of objects

-   `{}` open and close - write what you want to apply to each object!

`for` (<unique identifier> in <a collection of objects>) {

apply what is written here to each object

} close the loop

## Example #1 (custom column): *Next time floss the pigs*

Turns out the students fed the Guinea pigs orange juice (supp = 'OJ') with extra pulp! It was on sale at Aldi and they couldn't beat the bargin.

Unfortunately, OJ accumulated on the teeth and artificially inflated length measurements by 10%.

Let's use a for loop to make a new `len` column `len_new`

-   `for` to open your for loop

-   `()` set your identifier and call collection of objects

    -   `(i in 1:nrow(DF_tooth))` - our collection of objects are row-wise, meaning that the for loop with iterate commands for each row `i` of `DF_tooth`

-   `{}` - inserted below is an `if` `else` conditional statement to call row-wise boolean value before either calculating the new value when supplemented OJ or simply outputting the same length value when supplemented vitamin C.

```{r large pulp teeth, error = FALSE}

for (i in 1:nrow(DF_tooth)) { # open for loop, for i equal to 1:60

  # do the following for when i is equal to 1, 2, 3, ..60

  # this is one possible solution using a if else conditional statement!

  if (DF_tooth[i,2] == 'OJ') { # if row i in the second column == 'OJ'

    DF_tooth$len_new[i] <- DF_tooth[i,1] + DF_tooth[i,1]*(0.1) # new row 'len_new' calculated

  } else { # FALSE, second column == 'VC'

    DF_tooth$len_new[i] <- DF_tooth[i,1] # 'len_new' row is the same as len

  } # end if statment

} # close  for loop

View(DF_tooth) # look at the data!
```

## There's an ~~app~~ package for that!

-   `dplyr` has a nifty one liner that does the exact purpose as the for loop above!

-   input a conditional statement and the output if TRUE or FALSE using the command `if_else`

    -   `if_else(condition, TRUE, FALSE)`

```{r large pulp teeth, error = FALSE}
if ("dplyr" %in% rownames(installed.packages()) == 'FALSE') install.packages('dplyr')

library(dplyr) # load the library


?if_else # review the command page

# input the criteria - same as the for loop above

DF_tooth$len_new2 <- if_else(DF_tooth$supp == 'OJ',
                            (DF_tooth$len + DF_tooth$len*(0.1)), # TRUE
                            (DF_tooth$len)) # FALSE

View(DF_tooth)
```

## Example #2 (plot loop): *Flower power*

Looping through data columns is an efficient method to plot large data sets, especially if you have custom plotting code! Below is a simple example outputing plots.

-   `for` to open your for loop

-   `()` set your identifier and call collection of objects

    -   `(i in 1:(ncol(iris)-1))` - our collection of objects are column-wise, the for loop will iterate commands for each column `i` of `iris` except for the last column

-   `{}` - inserted below is an `ggplot` `geom_boxplot` for each column with numeric data

```{r plotting flower, error = FALSE}
if ("ggplot2" %in% rownames(installed.packages()) == 'FALSE') install.packages('ggplot2')

library(ggplot2) # load the library



iris # take a look at the dataset!

dim(iris) # 150 rows and 5 columns

head(iris) # first four rows are numeric data and last row is categorical 'Species'


# below we loop thorugh each iris numeric column and plot by species

for (i in 1:(ncol(iris)-1)) { # open for loop, for i equal to 1 - 4

    loop_measurement_name <- colnames(iris[i]) # string to name the plot and y axis

    plot <- ggplot(data = iris, aes(x=Species, y=iris[,i]), fill=Species) +
      geom_boxplot() +
      geom_jitter() +
      ylab(loop_measurement_name) + # name the y axis w
      ggtitle(loop_measurement_name) + # name the plot
      theme_classic()

    print(plot)

} # close  for loop

# clock below to see the four unique boxplots!
```

-   Note: as opposed to `print()` we could use the unique identifier 'loop_measurement_name' to name and output pdfs or jpegs onto your computer!

## Activity! *For, if, else, case_when, Oh My!*

**About**: Tackle the puzzle below using (1) raw base R syntax using `for` with `if` and `else` conditional statements and (2) the dplyr alternative

A greenhouse experiment was originally planned to breed hybrid strains from each of the three iris species. However, the off-brand fertilizer you used caused each species to grow a trait unknown to iris ..ologists(?)!! Paying homage to the man-eating plant from Little Shop of Horrors, you name this discovery `Audrey_III`.

The allometric relationship of `Audrey_III.Length` with Pedal.Length is different for each species

-   setosa - `Audrey_III.Length`= Pedal.Length\^2.4

-   versicolor: `Audrey_III.Length`= Pedal.Length\^4.0

-   virginica: `Audrey_III.Length`= Pedal.Length\^3.0

**Objective**: create a new column `Audrey_III.Length` based on the relationship with Pedal.Length for each iris species

```{r for loop}

for () { # open for loop


      if () {        # condition

                     # if TRUE


      ) else if () { # next condition

                     # if TRUE for else if only

      } else {  

                     # if FALSE for all conditions

      } # end if statment


} # close  for loop

View(iris) # look at the data!
```

**Objective**: create a new column `Audrey_III.Length` based on the relationship with Pedal.Length for each iris species

```{r case_when}
?case_when

iris$Audrey_III.Length_NOloop <- # use case_when to take it!


View(iris) # when you finish, compare your Audrey_III results

```
