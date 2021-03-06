# MouseCortex
Welcome to the GitHub repository associated with **Loo, Simon _et al._**, "**Single-cell transcriptomic catalog of mouse cortical development**", bioRxiv 2017: https://www.biorxiv.org/content/early/2017/10/25/208744

## Abstract
We generated a single-cell transcriptomic catalog of the developing mouse cerebral cortex that includes numerous classes of neurons, progenitors, and glia, their proliferation, migration, and activation states, and their relatedness within and across timepoints. Cell expression profiles stratified neurological disease-associated genes into distinct subtypes. Complex neurodevelopmental processes can be reconstructed with single-cell transcriptomics data, permitting a deeper understanding of cortical development and the cellular origins of brain diseases.

## What you'll find here
* `class.R`: Additions and modifications to **Shekhar _et al._'s** `class.R` file inititally published [here](https://github.com/broadinstitute/BipolarCell2016) 
* `E14_processing.R`: A detailed, fully documented summary of the processing steps performed for the E14.5 cortex.
	* Requires `class.R` to access the functions necessary for data analysis
	* All processing steps and parameters for analysis of the P0 cortex were identical to those illustrated in this template
* `E14_combined_matrix.txt.gz`: The main gene expression matrix for E14.5 cortex.
	* Rows are genes, columns are cells. 
	* Each biological replicate is represented here.
* `E14_tSNE.py`: Code for visualizing the data using `t-SNE`, in Python
* `P0_combined_matrix.txt.gz`: The main gene expression matrix for P0 cortex.
	* Rows are genes, columns are cells.
	* Each biological replicate is represented here.

We also created web-based tools for visualizing our data, these can be found at:
http://zylkalab.org/data

## Required R libraries
* genefilter
* sva
* igraph
* ggplot2
* Matrix
* gmodels
* RANN
* reshape
* cluster
* SLICER
* gplots

## Required Python libraries (for t-SNE visualization)
* scikit-learn
* matplotlib
* pandas

## Change log compared to Shekhar version:
* Added several new slots to S4 object, including `pca.eigenvalues`, `sils`, and `numclust`
* Added new function called `perform_refined_clustering`, which iteratively runs `doGraph_clustering` to optimize the number of nearest neighbors, then iteratively runs `doGraph_clustering` again to refine the cluster assignments using computed Silhouette widths
* Computes eigenvalues as part of `doPCA` and stores these values for the permutation test
* Adds a legend to t-SNE plots
* Modifies the `binomcount.test` function to compute log-fold-change as `(x+1)/(y+1)` to avoid NA/Inf values
* Adds checks to the `binomcount.test` to ensure that `effect.size` isn't NA
* Modifies cluster naming on `dot.plot`
* Prevents the usage of "Dingbats" font class in `ggplot` calls

## Questions/Issues
Please direct any questions or issues with the code published here to `jeremy [underscore] simon (at) med [dot] unc [dot] edu`
