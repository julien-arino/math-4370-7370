---
marp: true
title: A crash course in R
description: Julien Arino - MATH 4370-7370 - A crash course in R
theme: default
paginate: false
math: mathjax
size: 4K
---

<style>
  .theorem {
    text-align:justify;
    background-color:#16a085;
    border-radius:20px;
    padding:10px 20px 10px 20px;
    box-shadow: 0px 1px 5px #999;  margin-bottom: 10px;
  }
  .definition {
    text-align:justify;
    background-color:#ededde;
    border-radius:20px;
    padding:10px 20px 10px 20px;
    box-shadow: 0px 1px 5px #999;
    margin-bottom: 10px;
  }
  img[alt~="center"] {
    display: block;
    margin: 0 auto;
  }
</style>

<!-- _backgroundImage: "linear-gradient(to top, #85110d, 3%, white)" -->
# A crash course in R

Fall 2023

Julien Arino [![width:32px](https://raw.githubusercontent.com/julien-arino/presentations/main/FIGS/icons/email-round.png)](mailto:Julien.Arino@umanitoba.ca) [![width:32px](https://raw.githubusercontent.com/julien-arino/presentations/main/FIGS/icons/world-wide-web.png)](https://julien-arino.github.io/) [![width:32px](https://raw.githubusercontent.com/julien-arino/presentations/main/FIGS/icons/github-icon.png)](https://github.com/julien-arino)

Department of Mathematics & Data Science Nexus
University of Manitoba*

<div style = "font-size:18px; margin-top:-10px; padding-bottom:30px;"></div>

Canadian Centre for Disease Modelling
NSERC-PHAC EID Modelling Consortium (CANMOD, MfPH, OMNI/RÉUNIS)

<div style = "text-align: justify; position: relative; bottom: -5%; font-size:18px;">
* The University of Manitoba campuses are located on original lands of Anishinaabeg, Cree, Oji-Cree, Dakota and Dene peoples, and on the homeland of the Métis Nation.</div>

---

<!-- _backgroundImage: "radial-gradient(white,80%,#f1c40f)" -->
# Outline

- Foreword: the R language
- Data types and data structures
- Flow control
- Functions
- Rmarkdown, Sweave and Quarto

---

<!-- _backgroundImage: "linear-gradient(to bottom, #f1c40f, 20%, white)" -->
# <!--fit-->Foreword: the R language

---

# R was originally for stats but is now more

- Open source version of S
- Appeared in 1993
- Now (Fall 2023) version 4.3
- One major advantage in my view: uses a lot of C and Fortran code. E.g., `deSolve`:
> The functions provide an interface to the FORTRAN functions 'lsoda', 'lsodar', 'lsode', 'lsodes' of the 'ODEPACK' collection, to the FORTRAN functions 'dvode', 'zvode' and 'daspk' and a C-implementation of solvers of the 'Runge-Kutta' family with fixed or variable time steps
- Very active community on the web, easy to find solutions (same true of Python, I just prefer R)

---

# Development environments

- Terminal version, not very friendly
- Nicer terminal: [radian](https://github.com/randy3k/radian)
- Execute R scripts by using `Rscript name_of_script.R`. Useful to run code in `cron`, for instance
- Use IDEs:
    - [RStudio](https://www.rstudio.com/products/rstudio/) has become the reference
    - [RKWard](https://invent.kde.org/education/rkward) is useful if you are for instance using an ARM processor (Raspberry Pi, some Chromebooks..)
- Integrate into jupyter notebooks

---

# Going further

- [RStudio server](https://www.rstudio.com/products/rstudio/#rstudio-server): run RStudio on a Linux server and connect via a web interface
- Shiny: easily create an interactive web site running R code
- [Shiny server](https://www.rstudio.com/products/shiny/shiny-server/): run Shiny apps on a Linux server
- Rmarkdown: markdown that incorporates R commands. Useful for generating reports in html or pdf, can make slides as well..
- RSweave: LaTeX incorporating R commands. Useful for generating reports. Not used as much as Rmarkdown these days but very useful if you are a $\LaTeX$ user, e.g., to make Beamer slides
- Quarto: intended successor to RSweave and Rmarkdown; personally, I am not yet sure what the intent is...

---

# R is a scripted language

- Interactive
- Allows you to work in real time
    - Be careful: what is in memory might involve steps not written down in a script
    - If you want to reproduce your steps, it is good to write all the steps down in a script and to test from time to time running using `Rscript`: this will ensure that all that is required to run is indeed loaded to memory when it needs to, i.e., that it is not already there..

---

<!-- _backgroundImage: "linear-gradient(to bottom, #f1c40f, 20%, white)" -->
# <!--fit-->Data types and data structures

---

# Data types

- character: "a", "truc"
- numeric (real or decimal): 3, 12.5
- integer: 3L (the L forces the type to be integer)
- logical: TRUE, FALSE (or T, F)
- complex: 1-2i

---

# Assignment

Two ways:

```R
X <- 10
```

or

```R
X = 10
```

First version is preferred by R purists.. I don't really care

---

# Vectors

```R
x = 1:10
y <- c(x, 12)
> y
 [1]  1  2  3  4  5  6  7  8  9 10 12
z = c("red", "blue")
> z
[1] "red"  "blue"
z = c(z, 1)
> z
[1] "red"  "blue" "1"
```
Note that in `z`, since the first two entries are characters, the added entry is also a character. Vectors have all entries of the same type, so whatever you put in there first is what it is

---

# Adding entries to a vector

Let us do something inefficacious but illustrative

```R
x = c()
for (i in 1:10) {
    x = c(x, i)
}
```
would give us the same as `x = 1:10`

---

# Vector operations

Vector addition can be frustrating. Say you write `x=1:10`, i.e., make the vector
```R
> x
 [1]  1  2  3  4  5  6  7  8  9 10
```
Then `x+1` gives
```R
> x+1
 [1]  2  3  4  5  6  7  8  9 10 11
 ```
 i.e., adds 1 to all entries in the vector

 Beware of this in particular when addressing sets of indices in lists, vectors or matrices

---

# Matrices

Matrix (or vector) of size $\text{nr}\times\text{nc}$ full of zeros
```R
A <- mat.or.vec(nr = 2, nc = 3)
```

Matrix with prescribed entries

```R
B <- matrix(c(1,2,3,4), nr = 2, nc = 2)
> B
     [,1] [,2]
[1,]    1    3
[2,]    2    4
C <- matrix(c(1,2,3,4), nr = 2, nc = 2, byrow = TRUE)
> C
     [,1] [,2]
[1,]    1    2
[2,]    3    4
```

Remark that here and elsewhere, naming the arguments (e.g., `nr = 2`) allows to use arguments in any order

---

# Matrix multiplication

Probably the biggest annoyance in R compared to other languages

- The notation `A*B` is the *Hadamard product* $A\circ B$ (what would be denoted `A.*B` in matlab), not the standard matrix multiplication
- Matrix multiplication is written `A %*% B`

---

# For the matlab-ers here

- R does not have the keyword `end` to access the last entry in a matrix/vector/list..
- Use `length` (lists or vectors), `nchar` (character chains), `dim` (matrices.. careful, of course returns 2 values)

---

# Accessing entries in a matrix

```R
A[i,j]                 # Entry (i,j)
A[i,]                  # Row i
A[,j]                  # Column j
A[i,dim(A)[2]]         # Last entry in row i
A[dim(A)[1],dim(A)[2]] # Last entry in matrix
```

---

# Adding/replacing rows/columns in a matrix

```R
A[i,] <- c(1,2,3) # Replace row i by 1,2,3
B[,j] <- c(1,2)   # Replace column j by 1,2
```
Beware, in this case, the dimensions must make sense.. the above operations will fail if $A$ is not $N\times 3$ and $B$ is not $2\times N$

---

# Data frames

- Data frames are matrices on steroids..
- Matrices have all entries of the same type, data frames do not
- This leads to quite a lot of frustration, e.g., when you want to make a matrix out of a data frame or if you want to add a column to a matrix with a different entry type and forget about this difference...

---

# Useful functions for data frames and matrices

- `head()` - shows first 6 rows; override with, e.g., `head(dataframe, n = 10)`
- `tail()` - shows last 6 rows
- `dim()` - returns number of rows and number of columns
- `nrow()` - number of rows
- `ncol()` - number of columns
- `str()` - structure of data frame - name, type and preview of data in each column
- `names()` or `colnames()` - show the names attribute for a data frame
- `sapply(dataframe, class)` - shows the class of each column in the data frame

---

# Lists

A very useful data structure, quite flexible and versatile. Empty list: `L <- list()`. Convenient for things like parameters. For instance

```R
L <- list()
L$a <- 10
L$b <- 3
L[["another_name"]] <- "Plouf plouf"
```

```R
> L[1]
$a
[1] 10
> L[[2]]
[1] 3
> L$a
[1] 10
> L[["b"]]
[1] 3
> L$another_name
[1] "Plouf plouf"
```


---

# Checking data types and data typing

`is.type` functions (e.g., `is.numeric`, `is.character`, `is.matrix`, `is.list`) allow to check the type of an object, `as.type` functions (e.g., `as.numeric`, `as.character`, `as.matrix`, `as.list`) allow to convert an object to a given type

The result of data typing can be weird, so it may take a few tries to get things right

---

# Logical statements

In `if` statements (see later) and many other places, you need to evaluate the truth value of a statement. Use `==` for equality, `!=` for inequality, `>`, `<`, `>=`, `<=` for the obvious. `&` is the logical `and`, `|` is the logical `or`, `!` is the logical `not`

---

# Logical tests on vector entries and `which`

Make a vector of 5 uniformly distributed numbers (by default in $[0,1]$)
```R
> v = runif(5)
> v
[1] 0.682311734 0.612788785 0.681121278 0.003132367 0.842270188
```
Then using logical statements and `which` helps for selection
```R
> v <= 0.5
[1] FALSE FALSE FALSE  TRUE FALSE
> which(v <= 0.5)
[1] 4
```
(`which` returns indices for which the statement is `TRUE`)

---

# Logical tests on matrix entries and `which` (1)

Make a matrix of 9 uniformly distributed numbers
```R
> A = matrix(data = runif(9), nr = 3)
> A
          [,1]       [,2]      [,3]
[1,] 0.1605460 0.18508003 0.6043105
[2,] 0.7762981 0.02225763 0.3739177
[3,] 0.8170578 0.88845646 0.5842683
```
Then using logical statements and `which` helps for selection
```R
> A <= 0.5
      [,1]  [,2]  [,3]
[1,]  TRUE  TRUE FALSE
[2,] FALSE  TRUE  TRUE
[3,] FALSE FALSE FALSE
```

---

# Logical tests on matrix entries and `which` (2)

Note that by default, `which` returns indices of the matrix enumerated column-wise (1-3 are first column, 4-6 are second, etc.)
```R
> which(A <= 0.5)
[1] 1 4 5 8
```

If you want "proper" matrix indices, use
```R
> which(A <= 0.5, arr.ind = TRUE)
     row col
[1,]   1   1
[2,]   1   2
[3,]   2   2
[4,]   2   3
```


---

# <!--fit-->Using `which` to set vector/matrix entries

Make a vector of 5 / matrix of 9 uniformly distributed numbers (by default in $[0,1]$) and set all those with value $<0.5$ to zero
```R
> v = runif(5)
> v[which(v<0.5)] = 0
> v
[1] 0.8877751 0.9500462 0.0000000 0.0000000 0.0000000

> A = matrix(data = runif(9), nr = 3)
> A[which(A<0.5)] = 0
> A
          [,1]      [,2]      [,3]
[1,] 0.9365261 0.0000000 0.0000000
[2,] 0.8927255 0.0000000 0.0000000
[3,] 0.7267821 0.8341371 0.6286996
```

---

<!-- _backgroundImage: "linear-gradient(to bottom, #f1c40f, 20%, white)" -->
# <!--fit-->Flow control

---

# If statements

```R
if (condition is true) {
  list of stuff to do
}
```

Even if `list of stuff to do` is a single instruction, best to use curly braces

```R
if (condition is true) {
  list of stuff to do
} else if (another condition) {
  ...
} else {
    # This is the default if none of the above conditions are true
  ...
}
```

---

# For loops

`for` applies to lists or vectors

```R
for (i in 1:10) {
  something using integer i
}
for (j in c(1,3,4)) {
  something using integer j
}
for (n in c("truc", "muche", "chose")) {
  something using string n
}
for (m in list("truc", "muche", "chose", 1, 2)) {
  something using string n or integer n, depending
}
```

---

# lapply

Very useful function (a few others in the same spirit: `sapply`, `vapply`, `mapply`)

Applies a function to each entry in a list/vector/matrix

Because there is a parallel version (`parLapply`) that we will see later, worth learning

```R
l = list()
for (i in 1:10) {
        l[[i]] = runif(i)
}
lapply(X = l, FUN = mean)
```

or, to make a vector

```R
unlist(lapply(X = l, FUN = mean))
```

or `sapply(X = l, FUN = mean)`

---

# "Advanced" lapply

Can "pick up" nontrivial list entries

```R
l = list()
for (i in 1:10) {
        l[[i]] = list()
        l[[i]]$a = runif(i)
        l[[i]]$b = runif(2*i)
}
sapply(X = l, FUN = function(x) length(x$b))
```

gives

```R
[1]  2  4  6  8 10 12 14 16 18 20
```

Just recall: the argument to the function you define is a list entry (`l[[1]]`, `l[[2]]`, etc., here)

---

# <!--fit-->Avoid parameter variation loops with expand.grid

```R
# Suppose we want to vary 3 parameters
variations = list(
    p1 = seq(1, 10, length.out = 10),
    p2 = seq(0, 1, length.out = 10),
    p3 = seq(-1, 1, length.out = 10)
)

# Create the list
tmp = expand.grid(variations)
PARAMS = list()
for (i in 1:dim(tmp)[1]) {
    PARAMS[[i]] = list()
    for (k in 1:length(variations)) {
        PARAMS[[i]][[names(variations)[k]]] = tmp[i, k]     
    }
}
```

There is still a loop, but you can split this list, use it on different machines, etc. And can use `parLapply`

---

<!-- _backgroundImage: "linear-gradient(to bottom, #f1c40f, 20%, white)" -->
# <!--fit-->Functions

---

# Why make your own functions?

- Like most programming languages, additionally to built-in functions and functions provided by libraries, you can make your own functions 
- This is useful to avoid duplicated (or multiplicated) code when you are performing the same type of operation repeatedly
- Allows also to have one place debugging and editing

---

# Defining a function

A function needs three things
- A name by which to be called
- Argument(s) on which to operate (optional)
- Something to return (optional)

Generic form ([ ] indicates something optional)
```R
function_name <- function([arguments]) {
  set of instructions
  [return value]
}
```

---

# Function (and variables) naming conventions

- No super specific instructions, except that the name cannot contain dashes and other special characters. `_` is allowed and often used for space
- Read a bit about naming conventions for instance [here](https://curc.readthedocs.io/en/latest/programming/coding-best-practices.html). The main ones:
  - camel case: `firstName`, `lastName`
  - pascal case: `FirstName`, `LastName`
  - snake case: `first_name`, `last_name`
  - kebab case: `first-name`, `last-name`. **Not allowed** in `R`!
- The same is true for variables
- Not important which one you choose (unless specific instructions are given), but it is good to try to stick to one form

---

# What's a good function name?

- Everyone has different ideas about this
- In an advanced project, you will have multiple functions, so a function name should be informative
- However, the name should also not be too long

---

# Arguments - No arguments

A function can have no arguments, in which case it looks like this
```R
function_name <- function() {
  set of instructions
  [return value]
}
```
and is used by calling as `function_name()`. E.g.,
```R
print_date = function() {
  print(Sys.Date())
}
```
is used as
```R
> print_date()
[1] "2023-10-13"
```

---

# Arguments

- Arguments can be grouped together in vector or a list, or enumerated individually
- Each has pros and cons

---

# Default values for arguments

You can (and should when possible) set default values for arguments to a function
```R
print_date = function(date_format = "YYYY-MM-DD") {
  date = as.character(Sys.Date())
  tmp = strsplit(date, "-")
  YYYY = tmp[[1]][1]
  MM = tmp[[1]][2]
  DD = tmp[[1]][3]
  if (date_format == "MM-DD-YYYY") {
    OUT = sprintf("%s-%s-%s", MM, DD, YYYY)
  } else if (date_format == "DD-MM-YYYY") {
    OUT = sprintf("%s-%s-%s", DD, MM, YYYY)
  } else {
    OUT = date
  }
  return(OUT)
}
> print_date()
[1] "2023-10-13"
> print_date("DD-MM-YYYY")
[1] "13-10-2023"
```

---

# <!--fit-->Using a function of several variables as a function of one variable

Often, you will create a function of several variables, but will want to use it as a function of fewer, e.g., in a minimisation routine

```R
my_silly_function = function(x,y) {
  return(x+y)
}
```
To use as a function of, say, `x` with `y=5`,
```R
function(t) my_silly_function(x = t, y = 5)
```
whereas to use as a function of `y` with `x=2`
```R
function(t) my_silly_function(x = 2, y = t)
```
You can use any letter in the call to `function`; I am not using `x` here to make it obvious, but you could do `function(x) my_silly_function(x = x, y = 5)`

---

<!-- _backgroundImage: "linear-gradient(to bottom, #f1c40f, 20%, white)" -->
# <!--fit-->Rmarkdown, Sweave and Quarto

---

- Rmarkdown, Sweave and Quarto are notebook-type document generating mechanisms
- The idea is to weave together "regular text" and `R` commands
- When `R` is run, it goes through the document.. text is formated as prescribed by the type of program used (markdown for Rmarkdown and Quarto, $\LaTeX$ for Sweave), and `R` commands are run, with the output incorporated to the text
- This is a good way to produce dynamic documents, if for instance you are getting some of the data used for your computations from a dynamic website

---

# Rmarkdown

- Uses markdown to typeset text. Markdown is a very simple text formatting language. See, e.g., [here](https://daringfireball.net/projects/markdown/syntax) for a summary of commands. The most common
```markdown
# Section
## Subsection
### Subsubsection
**bold text**
*italicised text*
[linked text](https://www.google.ca/)
```

---

# R code within Rmarkdown

- `R` **code chunks** are included in the text as
````R
```{r}
Some R code
```
````

You **must** use `{r}` after the first three backticks. Blocks like

````R
```R
Some R code
```
````
or
````
```
Some R code
```
````
are **pure markdown** code blocks, `R` does not execute the `R` commands there

---

# Chunk names

It is a good idea to name chunks: when your code gets lengthy or complicated, debugging is greatly facilitated with named chunks, since errors will refer to the chunk name; with unnamed chunks, they will just refer to chunk number... RStudio also shows chunk names in the quick selection box

Chunk names appear in the `{r}` statement at the beginning of a chunk, e.g., in the RStudio `Rmd` skeleton file, the first chunk

````R
```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```
````
is named `setup`

---

# Chunk options

Chunk options follow the chunk name, if any, separated with commas. For instance, in the RStudio `Rmd` skeleton file, the first chunk

````R
```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```
````

is set with `include=FALSE`, which prevents the code and results to show in the rendered file. See a list of options [here](https://yihui.org/knitr/options/)

---

# Global chunk options

Note that the RStudio skeleton file includes the statement
```R
knitr::opts_chunk$set(echo = TRUE)
```
which sets the chunk options globally (unless overridden in a specific chunk). For instance, if you want the default behaviour to be that your code is not shown, you could do

````R
```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = FALSE)
```
````
and override this in a specific chunk with
````R
```{r some name, echo=TRUE}
Some commands
```
````


---

# Inline R code within Rmarkdown

- The syntax on the previous slides will display your `R` code as a code block (unless you choose to hide the code or the output)
- You can also use `R` "inline", that is, within a regular markdown statement instead of a code chunk, using `` `r r-command` ``, where `r-command` is the `R` command you want to use

For example, the default `Rmd` file generated by RStudio uses the `R` example dataset `cars`. To show the number of rows in a regular sentence, outside of a code chunk, you could write

```markdown
The cars dataset contains `r dim(cars)[1]` rows.
```
which renders as
> The cars dataset contains 50 rows.

---

# Output type

- Rmarkdown can render your file in `html`, `pdf` or as a Word file
- To generate a `pdf`, you need to have $\LaTeX$ installed

