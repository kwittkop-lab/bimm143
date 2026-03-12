# Class 6: R functions
Kyle Wittkop (A18592410)

- [Backround](#backround)
- [Our first function](#our-first-function)
- [A second function](#a-second-function)
- [A protein generating function](#a-protein-generating-function)

## Backround

All functions in R have at least 3 things :

- A **name** that we use to call the function

- Has one or more input **arguments**

- The **body**: the lines of R code that do the work

## Our first function

Lets write a silly wee function called `add()` to add to add some
numbers (the input function)

``` r
add <- function(x,y) {
  x + y 
} 
```

Now we can use this function

``` r
add(100,1)
```

    [1] 101

``` r
add(x=10,y=10)
```

    [1] 20

``` r
add( x=c(100,1,100), y=(1))
```

    [1] 101   2 101

``` r
add(x=c(100,1), y=c(1,100))
```

    [1] 101 101

What if i give a multiple element vector to x and y

``` r
add(x=c(100,1), y=c(1,100))
```

    [1] 101 101

Q. what if i give three inputs to the function

``` r
#add(x=c(100,1,y=1,z=1))
```

Q. What if i give only 1 input to the add function?

``` r
#add(x=100)
addnew <-function(x,y=1){
  x+y
}
```

``` r
addnew(x=100)
```

    [1] 101

``` r
addnew(x=100,y=200)
```

    [1] 300

If we write out function with input arguments having no default value
than the user will be required to set them when they use the function.
we can give our input arguments defualt values by setting them equal to
some sensible value e.g. y=1

## A second function

Lets make something more interesting: make a sequence generating tool…

The `sample()` function can be a useful starting point

``` r
sample(1:10, size=4)
```

    [1] 6 4 1 2

> Q. Generate 9 random numbers from the input vector from 1 to 10

``` r
sample(1:10, size=9)
```

    [1]  8  5 10  2  6  7  3  4  1

> Q. Generate 12 random numbers from the input vector from 1 to 10?

``` r
sample(1:10, size =12, replace=TRUE)
```

     [1]  1  8 10  5  4  7  7  6  6 10  5  1

> Q. Write code for the sample function that generates nucleotide
> sequences of length 6?

``` r
sample(c("A","T","C","G"), size = 6, replace = TRUE)
```

    [1] "A" "C" "A" "C" "G" "C"

> Q. Write a first function `generate_DNA()` that returns a user
> specified length DNA sequence:

``` r
generate_DNA <-function(x=6) {
 sample(c("A","T","C","G"), size=x, replace = TRUE)
}
```

``` r
generate_DNA()
```

    [1] "G" "A" "A" "A" "G" "T"

``` r
generate_DNA(100)
```

      [1] "T" "A" "G" "G" "C" "A" "T" "T" "A" "A" "T" "G" "C" "C" "C" "T" "G" "G"
     [19] "G" "G" "C" "G" "G" "A" "C" "G" "T" "A" "G" "C" "T" "A" "G" "C" "C" "T"
     [37] "C" "C" "C" "T" "A" "C" "G" "A" "C" "G" "G" "C" "C" "T" "A" "G" "C" "T"
     [55] "G" "G" "A" "G" "C" "C" "C" "A" "T" "G" "C" "T" "G" "C" "A" "T" "G" "G"
     [73] "T" "A" "C" "G" "C" "C" "A" "C" "T" "C" "A" "T" "C" "C" "T" "A" "G" "C"
     [91] "A" "C" "T" "G" "A" "G" "T" "C" "A" "T"

``` r
generate_DNA(10)
```

     [1] "C" "C" "G" "G" "C" "G" "C" "A" "C" "G"

**KEY POINTS**

Every function in R looks fundamentally the same in terms of its
structure, Basically 3 things : name, input, body

    name <- function(input) {
      Body 
    }

Functions can have multiple inputs. These can be required arguments or
“optional” with optional arguments having a set of default values.

> Q. Modify and improve our generate_DNA function to return its
> generated sequence in a more standard format like “ATGACA” rather than
> the vector “A”,“C”,“G”,“A”

``` r
generate_DNA <-function(x=6, fasta=TRUE) {
 ans <- sample(c("A","T","C","G"), 
        size=x,  replace = TRUE)
 if(fasta)
   cat("Single-element vector output ")
ans <- paste(ans, collapse="")
  return(ans)
}

generate_DNA(fasta=FALSE)
```

    [1] "TGATCG"

the `paste()` function, its job is to join up or stick together (a.k.a
paste) input strings together

``` r
paste(c("alice","barry"), "love R", sep = " Does not ")
```

    [1] "alice Does not love R" "barry Does not love R"

``` r
?paste
```

Flow control means where the R brain goes in your code

``` r
good_mood <- FALSE

if(good_mood) {
  cat("Great!")
} else{ 
  cat("Bummer")
}
```

    Bummer

## A protein generating function

> Q. Write a function that generates a user specified length protein
> sequence.

``` r
Generate_Prot <-function(x) {
 ans <- sample(c("A","R","N","D","C","Q","E","G","H","I","L","K","M","F","P","S","T","W","Y","V"), 
        size=x,  replace = TRUE)
 ans <- paste(ans,collapse="" )
  return(ans)
}
Generate_Prot(6)
```

    [1] "CPEARI"

> Q. Use that function to generate random protien sequences between 6
> and 12

``` r
Generate_Prot(6)
```

    [1] "YPMKIL"

``` r
Generate_Prot(12)
```

    [1] "FHLATCHGWCPQ"

``` r
for(i in 6:12) {
  cat(">",i, sep="", "\n")
  cat(Generate_Prot(i), "\n")
}
```

    >6
    NMASEH 
    >7
    IMGEMVT 
    >8
    CKRWYHSV 
    >9
    NMYPGFMNC 
    >10
    WLINKYCCYW 
    >11
    YVTADHNYAGV 
    >12
    NNPFDSVSFNCW 

> Q. are any of your sequences unique i.e not found in nature

Yes, sequences that were 8 amino acids or greater were unique in nature.
