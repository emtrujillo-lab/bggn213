Transcriptomics
================

## GitHub Documents

This is an R Markdown format used for publishing markdown documents to
GitHub. When you click the **Knit** button all R code chunks are run and
a markdown file (.md) suitable for publishing to GitHub is generated.

## reasd the files you downloaded (countData and colDATA)

\#\#now read the import countDATA and colData

``` r
counts <- read.csv("airway_scaledcounts.csv", stringsAsFactors = FALSE)
metadata <-  read.csv("airway_metadata.csv", stringsAsFactors = FALSE)
```

\#\#how many genes do we have in thei dataset? `nrow(counts)`

``` r
nrow(counts)
```

    ## [1] 38694

\#\#in order to compare the treatment patients to the control groups
data … we have to find the mean of the `control` first

\#\#`dex` column has the `control` and `treatment` groups.

``` r
metadata$dex =="control"
```

    ## [1]  TRUE FALSE  TRUE FALSE  TRUE FALSE  TRUE FALSE

``` r
control <- metadata[metadata$dex =="control",]
```

\#\#now we need to just choose the `control`. NOw choose for the rows
that are `control`. i.e. which ones from the `dex` columnn are
`control`?

\#\#this is an alternative to print out the rows that are `control`

\#now you have to access the `id`

``` r
metadata[metadata$dex =="control", "id"]
```

    ## [1] "SRR1039508" "SRR1039512" "SRR1039516" "SRR1039520"

\#\#this is an alternative to getting `id`

``` r
metadata[metadata$dex =="control",]$id
```

    ## [1] "SRR1039508" "SRR1039512" "SRR1039516" "SRR1039520"

\#\#this is the 3rd and last alternative to get `id`

``` r
metadata[metadata$dex =="control", 1]
```

    ## [1] "SRR1039508" "SRR1039512" "SRR1039516" "SRR1039520"

\#\#accesss the count columns with `control$id` \#this should print out
the 4 `control` columns

\#\#to get the mean we have to use `rowSums()` and divide by the number
of columns which is `4`

\#\#ithis is an alternative way to calculate the `mean`

``` r
control <- metadata[metadata[,"dex"]=="control",]
```

``` r
control.mean <- rowSums( counts[ ,control$id] )/4 #we divide this by four because there are 4 control groups
```

``` r
names(control.mean) <- counts$ensgene
```

\#\#now do the same for the control

\#\#make a new vector called `treated` from this data above

``` r
treated <- metadata[metadata[,"dex"]=="treated",]
```

\#\#find the mean of `treated`

``` r
treated.mean <- rowMeans( counts[ ,treated$id] )/4
```

\#\#now we need to combine our meancount data for bookeeping purposes

``` r
mycounts <- data.frame(control.mean, treated.mean)
```

\#\#plot `control` vs `treated`

``` r
plot(mycounts) #this plots the 1st column vs the 2nd column 
```

![](class15_files/figure-gfm/unnamed-chunk-25-1.png)<!-- -->

``` r
nrow(mycounts)
```

    ## [1] 38694

\#\#where is all the data … so now use a `histogram` and choose the
control

``` r
hist(mycounts$control.mean)
```

![](class15_files/figure-gfm/unnamed-chunk-27-1.png)<!-- -->

\#\#get more bars (i.e. 300 of them)

``` r
hist(mycounts$control.mean, breaks = 300)
```

![](class15_files/figure-gfm/unnamed-chunk-28-1.png)<!-- -->

\#\#change scatterplot to `log log` you wast x axis to be log and y axis

``` r
plot(mycounts, log="xy")
```

    ## Warning in xy.coords(x, y, xlabel, ylabel, log): 15032 x values <= 0 omitted
    ## from logarithmic plot

    ## Warning in xy.coords(x, y, xlabel, ylabel, log): 15281 y values <= 0 omitted
    ## from logarithmic plot

![](class15_files/figure-gfm/unnamed-chunk-29-1.png)<!-- -->

\#\#remove the `zero count genes` from your data b/c we can’t say
anything about them from this dataset

\#\#example

``` r
x <- c(1, 3, 10, 0)
x == 0  
```

    ## [1] FALSE FALSE FALSE  TRUE

``` r
which(x == 0) #will tell me which ones are the TRUE ones
```

    ## [1] 4

``` r
x <- data.frame(c(1, 3, 10, 0), c(1, 3, 0 , 0))

x == 0
```

    ##      c.1..3..10..0. c.1..3..0..0.
    ## [1,]          FALSE         FALSE
    ## [2,]          FALSE         FALSE
    ## [3,]          FALSE          TRUE
    ## [4,]           TRUE          TRUE

``` r
#which(x==0)
```

``` r
x <- data.frame(c(1, 3, 10, 0), c(1, 3, 0, 0))

which(x==0) #scans the numbers and says which are TRUEly `zero`
```

    ## [1] 4 7 8

``` r
x <- data.frame(c(1, 3, 10, 0), c(1, 3, 0, 0))

which(x==0, arr.ind = TRUE) #tells me which genes are zero
```

    ##      row col
    ## [1,]   4   1
    ## [2,]   3   2
    ## [3,]   4   2

``` r
x <- data.frame(c(1, 3, 10, 0), c(1, 3, 0, 0))

unique(which(x==0, arr.ind = TRUE)[ , "row"]) #made it unique() to find the rows that have `zero`
```

    ## [1] 4 3

\#\#find `zero` rows in our mycounts object

\#\#store this as `to.rm`

``` r
to.rm <- unique(which(mycounts==0, arr.ind = TRUE)[ , "row"])
```

\#\#but we want all the ones that are `NOT ZERO`

``` r
newcounts <- mycounts[-to.rm,]
```

\#\#how many genes do you have that are not `zero`

``` r
nrow(newcounts)
```

    ## [1] 21817

\#\#use `log` so that you can calculate the `fold change`. but here we
use `log2` (the log-ratio of a gene’s or a transcript’s expression
values in two different conditions. While comparing two conditions each
feature you analyse gets (normalised) expression values. This value can
be zero and thus lead to undefined ratios)

``` r
newcounts$log2fc <-log2(newcounts[,"treated.mean"]/newcounts[,"control.mean"])
```

\#\#negative means its going down in the treatment . positive means its
going up in the treatment. IF its +2 then its upregulated. IF its -2
then its downregulated.

\#\#common rule of thumb in the field is to use a log2fc (log2 fold
change). How many of our genes are upregulated from this?

``` r
sum(newcounts$log2fc > 2)
```

    ## [1] 16

\#how many are downregulated in this threshold

``` r
sum(newcounts$log2fc < -2)
```

    ## [1] 13605

\#\#let’s use DESeq2

``` r
library(DESeq2)
```

    ## Loading required package: S4Vectors

    ## Loading required package: stats4

    ## Loading required package: BiocGenerics

    ## Loading required package: parallel

    ## 
    ## Attaching package: 'BiocGenerics'

    ## The following objects are masked from 'package:parallel':
    ## 
    ##     clusterApply, clusterApplyLB, clusterCall, clusterEvalQ,
    ##     clusterExport, clusterMap, parApply, parCapply, parLapply,
    ##     parLapplyLB, parRapply, parSapply, parSapplyLB

    ## The following objects are masked from 'package:stats':
    ## 
    ##     IQR, mad, sd, var, xtabs

    ## The following objects are masked from 'package:base':
    ## 
    ##     anyDuplicated, append, as.data.frame, basename, cbind, colnames,
    ##     dirname, do.call, duplicated, eval, evalq, Filter, Find, get, grep,
    ##     grepl, intersect, is.unsorted, lapply, Map, mapply, match, mget,
    ##     order, paste, pmax, pmax.int, pmin, pmin.int, Position, rank,
    ##     rbind, Reduce, rownames, sapply, setdiff, sort, table, tapply,
    ##     union, unique, unsplit, which, which.max, which.min

    ## 
    ## Attaching package: 'S4Vectors'

    ## The following object is masked from 'package:base':
    ## 
    ##     expand.grid

    ## Loading required package: IRanges

    ## 
    ## Attaching package: 'IRanges'

    ## The following object is masked from 'package:grDevices':
    ## 
    ##     windows

    ## Loading required package: GenomicRanges

    ## Loading required package: GenomeInfoDb

    ## Loading required package: SummarizedExperiment

    ## Loading required package: Biobase

    ## Welcome to Bioconductor
    ## 
    ##     Vignettes contain introductory material; view with
    ##     'browseVignettes()'. To cite Bioconductor, see
    ##     'citation("Biobase")', and for packages 'citation("pkgname")'.

    ## Loading required package: DelayedArray

    ## Loading required package: matrixStats

    ## 
    ## Attaching package: 'matrixStats'

    ## The following objects are masked from 'package:Biobase':
    ## 
    ##     anyMissing, rowMedians

    ## Loading required package: BiocParallel

    ## 
    ## Attaching package: 'DelayedArray'

    ## The following objects are masked from 'package:matrixStats':
    ## 
    ##     colMaxs, colMins, colRanges, rowMaxs, rowMins, rowRanges

    ## The following objects are masked from 'package:base':
    ## 
    ##     aperm, apply, rowsum

\#design: where in the data

``` r
dds <- DESeqDataSetFromMatrix(countData=counts, colData=metadata, design=~dex, tidy=TRUE)
```

    ## converting counts to integer mode

    ## Warning in DESeqDataSet(se, design = design, ignoreRank): some variables in
    ## design formula are characters, converting to factors

``` r
dds
```

    ## class: DESeqDataSet 
    ## dim: 38694 8 
    ## metadata(1): version
    ## assays(1): counts
    ## rownames(38694): ENSG00000000003 ENSG00000000005 ... ENSG00000283120
    ##   ENSG00000283123
    ## rowData names(0):
    ## colnames(8): SRR1039508 SRR1039509 ... SRR1039520 SRR1039521
    ## colData names(4): id dex celltype geo_id

``` r
dds <- DESeq(dds)
```

    ## estimating size factors

    ## estimating dispersions

    ## gene-wise dispersion estimates

    ## mean-dispersion relationship

    ## final dispersion estimates

    ## fitting model and testing

``` r
res <- results (dds)
res
```

    ## log2 fold change (MLE): dex treated vs control 
    ## Wald test p-value: dex treated vs control 
    ## DataFrame with 38694 rows and 6 columns
    ##                          baseMean     log2FoldChange             lfcSE
    ##                         <numeric>          <numeric>         <numeric>
    ## ENSG00000000003  747.194195359907 -0.350703020686589 0.168245681332903
    ## ENSG00000000005                 0                 NA                NA
    ## ENSG00000000419  520.134160051965  0.206107766417874 0.101059218008481
    ## ENSG00000000457  322.664843927049 0.0245269479387461 0.145145067649738
    ## ENSG00000000460   87.682625164828 -0.147142049222083 0.257007253995456
    ## ...                           ...                ...               ...
    ## ENSG00000283115                 0                 NA                NA
    ## ENSG00000283116                 0                 NA                NA
    ## ENSG00000283119                 0                 NA                NA
    ## ENSG00000283120 0.974916032393564 -0.668258460516795  1.69456285242458
    ## ENSG00000283123                 0                 NA                NA
    ##                               stat             pvalue              padj
    ##                          <numeric>          <numeric>         <numeric>
    ## ENSG00000000003  -2.08446967499072 0.0371174658436988 0.163034808643509
    ## ENSG00000000005                 NA                 NA                NA
    ## ENSG00000000419   2.03947517583776 0.0414026263009679  0.17603166488093
    ## ENSG00000000457  0.168982303952169  0.865810560624016 0.961694238404893
    ## ENSG00000000460 -0.572520996721302  0.566969065259218  0.81584858763974
    ## ...                            ...                ...               ...
    ## ENSG00000283115                 NA                 NA                NA
    ## ENSG00000283116                 NA                 NA                NA
    ## ENSG00000283119                 NA                 NA                NA
    ## ENSG00000283120 -0.394354484733718  0.693319342567684                NA
    ## ENSG00000283123                 NA                 NA                NA

\#make a volcano plot

Lot of log2fc vs p-value

``` r
plot(res$log2FoldChange, res$padj)
```

![](class15_files/figure-gfm/unnamed-chunk-53-1.png)<!-- -->

``` r
plot(res$log2FoldChange, log(res$padj))
```

![](class15_files/figure-gfm/unnamed-chunk-54-1.png)<!-- -->

\#add a `negative` to the *log*

``` r
plot(res$log2FoldChange, -log(res$padj))
```

![](class15_files/figure-gfm/unnamed-chunk-55-1.png)<!-- -->

\#\#add some colors

``` r
plot(res$log2FoldChange, -log(res$padj))
abline(v=c(-2,2), lty=2)
```

![](class15_files/figure-gfm/unnamed-chunk-56-1.png)<!-- -->

``` r
plot(res$log2FoldChange, -log(res$padj), col="gray")
abline(v=c(-2,2), lty=2)
```

![](class15_files/figure-gfm/unnamed-chunk-57-1.png)<!-- -->

\#\#want genes that are significant. `v` is for vertical and `h` is for
horizontal

``` r
plot(res$log2FoldChange, -log(res$padj), col="gray")
abline(v=c(-2,2), lty=2)
abline(h=log(0.05), lty=2)
```

![](class15_files/figure-gfm/unnamed-chunk-58-1.png)<!-- -->

``` r
# Setup our custom point color vector 
mycols <- rep("gray", nrow(res))
mycols[ abs(res$log2FoldChange) > 2 ]  <- "red" 

inds <- (res$padj < 0.01) & (abs(res$log2FoldChange) > 2 )
mycols[ inds ] <- "blue"

# Volcano plot with custom colors 
plot( res$log2FoldChange,  -log(res$padj), 
 col=mycols, ylab="-Log(P-value)", xlab="Log2(FoldChange)" )

# Cut-off lines
abline(v=c(-2,2), col="gray", lty=2)
abline(h=-log(0.1), col="gray", lty=2)
```

![](class15_files/figure-gfm/unnamed-chunk-59-1.png)<!-- -->

\#\#that’s all folks
