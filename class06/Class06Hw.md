# Class 6 Function Homework
Kyle Wittkop (A18592410)

> Q Write a function of the supplied code.

## Supplied code :

``` r
library(bio3d)
s1 <- read.pdb("4AKE") # kinase with drug
```

      Note: Accessing on-line PDB file

``` r
s2 <- read.pdb("1AKE") # kinase no drug
```

      Note: Accessing on-line PDB file
       PDB has ALT records, taking A only, rm.alt=TRUE

``` r
s3 <- read.pdb("1E4Y") # kinase with drug
```

      Note: Accessing on-line PDB file

``` r
s1.chainA <- trim.pdb(s1, chain="A", elety="CA")
s2.chainA <- trim.pdb(s2, chain="A", elety="CA")
s3.chainA <- trim.pdb(s1, chain="A", elety="CA")
s1.b <- s1.chainA$atom$b
s2.b <- s2.chainA$atom$b
s3.b <- s3.chainA$atom$b
plotb3(s1.b, sse=s1.chainA, typ="l", ylab="Bfactor")
```

![](Class06Hw_files/figure-commonmark/unnamed-chunk-1-1.png)

``` r
plotb3(s2.b, sse=s2.chainA, typ="l", ylab="Bfactor")
```

![](Class06Hw_files/figure-commonmark/unnamed-chunk-1-2.png)

``` r
plotb3(s3.b, sse=s3.chainA, typ="l", ylab="Bfactor")
```

![](Class06Hw_files/figure-commonmark/unnamed-chunk-1-3.png)

# Can you improve this analysis code?

## Assignment :

``` r
Plot_Bfactor <- function(pdb) {
  
  #the input to this function is pdb, the 4 Character pdb ID (e.g. "4AKE")
  
  ans <- read.pdb(pdb)
  ans <- trim.pdb(ans, chain = "A", elety = "CA")
  
  # repeated parts of code taken and applied to ans 
  
  # 1) Function now reads input pdbfile
  # 2) trims to chain A and alpha carbon atoms 
  # 3) applies both to ans 


  
  b <- ans$atom$b
  
  # B factors are extracted out of our trimmed pdb file , set to b 
  
  
  plotb3(b, sse = ans, type="l", ylab = "Bfactor")
  
  # produces plot using : 
  # B factors (b)
  # our trimmed, input pdb file (ans) 
  # same parameters as original code 

}

#Function output : 
# Plot of B-factors vs residues
# Set to our input pdbfile 


Plot_Bfactor("4AKE")
```

      Note: Accessing on-line PDB file

    Warning in get.pdb(file, path = tempdir(), verbose = FALSE):
    /var/folders/gp/8szl16kd5bq7qnbbt4s9l44m0000gn/T//RtmpE6S5gw/4AKE.pdb exists.
    Skipping download

![](Class06Hw_files/figure-commonmark/unnamed-chunk-2-1.png)

``` r
#This is an example of the function reading in the "4AKE" pdb file
# Returns a B-factor plot for the protein. 
```
