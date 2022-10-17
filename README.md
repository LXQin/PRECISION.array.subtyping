# PRECISION.array.subtyping
R package for evaluating the performance of microarray data normalization and batch effects correction in tumor subtyping using microRNA data.


## Contents

- [Repo Contents](#repo-contents)
- [Software dependencies](#software-dependencies)
- [Installation Guide](#installation-guide)
- [Demo](#demo)

# Repo Contents

- [R](./R): `R` code.
- [data](./data): the example data for the demo.
- [man](./man): help manual.

# Software dependencies

Before installing the `PRECISION.array.subtyping` package, users should have installed `R` with version 3.5.0 or higher.


### Package dependencies

Users should install the following packages prior to installing `PRECISION.array.subtyping`, from an `R` session:

```
if (!require("BiocManager", quietly = TRUE))
    install.packages("BiocManager")
BiocManager::install("sva")
BiocManager::install("vsn")
```

# Installation Guide

From an `R` session, type:

```
require(devtools)
install_github("LXQin/PRECISION.array.subtyping") 
```


# Demo

Please check the [user's guide](./PRECISION.array.subtyping_0.99.0.pdf) for the detailed instructions on how to use the functions in the package. You may also run the following code in the `R` session:

```
library(PRECISION.array.subtyping)

data("example_data", package = "PRECISION.array.subtyping")

uni_true_cluster = rep(NA,dim(example_data)[2])
uni_true_cluster[which(substr(colnames(example_data),7,7)=="E")] = 1
uni_true_cluster[which(substr(colnames(example_data),7,7)=="V")] = 2

results = cluster_other(dat = example_data, true_cluster = uni_true_cluster, 
						clust_method = "kmeans")
						
str(results)
```
