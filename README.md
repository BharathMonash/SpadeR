<!-- README.md is generated from README.Rmd. Please edit that file -->



SpadeR (R package)
=====
<h4 style="text-align: right;">Most recent update time: July 21, 2015    

by Anne Chao, K. H., Ma and T. C., Hsieh.

Institute of Statistics, National Tsing Hua University, Hsin-Chu, Taiwan 30043</h4>


The program SpadeR (Species Prediction And Diversity Estimation) is an updated R package from the original version SPADE from Chao and Shen (2010).

Like [SPADE](http://chao.stat.nthu.edu.tw/blog/software-download/spade/), the program SpadeR computes various biodiversity indices based on two types of sample data (abundance data and incidence data) from one or multiple communities. This user guide attempts to explain how to use this program in an easily accessible way using numerical examples and explanations.


### Software needed to run the development version

-   Required: [R](http://cran.rstudio.com/)
-   Suggested: [RStudio IDE](http://www.rstudio.com/ide/download/)

### How to run
start R(Studio) and copy-and-paste the following commands:


```r
## install the latest version from github
install.packages('devtools')
library(devtools)
install_github('AnneChao/SpadeR')
library(SpadeR)
```

Remark that in order to install `devtools` package, you should update R
to the last version. Further, to get `install_github` to work, you
should install the `httr` package.

### The program is divided into five parts:

- Part I: Species (estimating species richness for one community based on abundance data or incidence data.


```r
# Example1: (abundance data)
data(ChaoSpeciesDemoAbu)
ChaoSpecies(ChaoSpeciesDemoAbu, datatype="abundance", k=10, conf=0.95)

# Example2: (incidence data)
data(ChaoSpeciesDemoInci)
ChaoSpecies(ChaoSpeciesDemoInci, datatype="incidence", k=10, conf=0.95) 

```

- Part II: Shared Species (estimating the number of shared species for two communities based on abundance frequency data or multiple incidence data)

```r
# Example1: (abundance data)
data(ChaoSharedDemoAbu)
ChaoShared(ChaoSharedDemoAbu, datatype="abundance", se=TRUE, nboot=200, conf=0.95) 

# Example2: (incidence data)
data(ChaoSharedDemoInci)
ChaoShared(ChaoSharedDemoInci, datatype="incidence", se=TRUE, nboot=200, conf=0.95) 

```

- Part III: Diversity Profile Estimation (estimating a continuous diversity profile including species richness, Shannon's entropy and Gini-Simpson's index as well as their effective numbers of species based on sample abundance or incidence data). This part is an expanded version of the original Diversity Index part in SPADE. 

```r
# Example: (abundance data)
data(DiversityDemoAbu)
Diversity(DiversityDemoAbu, datatype= "abundance")

# Example2: (incidence data)
data(ChaoSpeciesDemoInci)
Diversity(ChaoSpeciesDemoInci, datatype= "incidence")

```

- Part IV: Two-Community Similarity Index (estimating various similarity indices for two assemblages based on abundance data or incidence data. The incidence-based indices include the classic Jaccard, Sorensen and Lennon et al. (2001) indices; the abundance-based indices include the Bray-Curtis, Morisita-Horn, Horn and two abundance-based Jaccard and Sorensen indices.)


```r
# Example1: (abundance data)
data(SimilarityPairDemoAbu)
SimilarityPair(SimilarityPairDemoAbu, datatype="abundance")

# Example2: (incidence data)
data(SimilarityPairDemoInci)
SimilarityPair(SimilarityPairDemoInci, datatype="incidence")
```

- Part V: Multiple-Community Diversity Measure (estimating N-community Sorensen, Horn, and Morisita similarity /dissimilarity indices for more than two communities.)


```r
# Example: (abundance data)
data(SimilarityMultDemoAbu)
SimilarityMult(SimilarityMultDemoAbu, q=2, nboot=200)
```



### How to cite

If you publish your work based on results from `SpadeR`, please make references to our relevant papers mentioned in the following sections and also use the following reference for citing SpadeR:

> Anne Chao, K. H. Ma and T. C. Hsieh (2015). SpadeR: Species Prediction and Diversity Estimation with R. R package version 0.1.0. URL http://chao.stat.nthu.edu.tw/blog/software-download/

### License

The iNEXT package is licensed under the GPLv3. To help refine `SpadeR`, your comments or feedbacks would be welcome (please send them to [Anne Chao](chao@stat.nthu.edu.tw)).
