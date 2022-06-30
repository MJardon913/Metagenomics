# Pipeline iNAP 

Reference:

Feng, K., Peng, X., Zhang, Z., Gu, S., He, Q., Shen, W., ... & Deng, Y. (2022). 
iNAP: An integrated network analysis pipeline for microbiome studies. iMeta, e13.
[DOI: 10.1002/imt2.13](https://onlinelibrary.wiley.com/doi/10.1002/imt2.13)
## Description:

This pipeline describes the process for the generation of an integrated 
network with iNAP from the metagenomic data

## Data: 
The files for the test can be found in the git [MJardib913](https://github.com/MJardon913) in directory 
[Metagenomics/Data/Data_for_iNAP](https://github.com/MJardon913/Metagenomics/tree/main/Data/Data_for_iNAP)

And in this case the galaxy [iNAP](https:// mem.rcees.ac.cn:8081) online platform will be used.

### Upload information to iNAP

The files mentioned above are uploaded in Data for iNAP, in the upload data section.
This is the iNAP tutorial [video](https://www.youtube.com/watch?v=lCb-Nsp5bwM) with test data 

### Method 1: SparCC

#### *1.1 Majority selection*. Manually filtration the input table by removing the lower detected OTUs or species.  
On the left side, Majority selection is selected

Section:

>-Microbial data; **bac_16S_test.txt**.
>
>-Number of species groupo for network analysis; two groups of species.
>
>-Plant table (2nd Group); **plant_test.txt**.

*the other options are left as default.*

**EXECUTE**

**NOTE:** The majority is to filter the species or OTUs which were less detected among all samples. The integer of this value is recommended as the 80% of the sample numbers.

Result:Filtered_OTU_table

#### *1.2 SparCC correlation and p-value calculation* Computing correlations in compositional data (16S, metagenomics, etc) and estimating pseudo p-values via a bootstrap procedure.

Section:

>-Input table for SparCC pseudo p-value calculation:**Filtered_OTU_table**  

*the other options are left as default.*

**EXECUTE**

**NOTE:** Genomic survey data, such as those obtained from 16S rRNA gene sequencing, are subject to underappreciated mathematical difficulties that can undermine standard data analysis techniques. We show that these effects can lead to erroneous correlations among taxa within the human microbiome despite the statistical significance of the associations. To overcome these difficulties, we developed SparCC; a novel procedure, tailored to the properties of genomic survey data, that allow inference of correlations between genes or species. We use SparCC to elucidate networks of interaction among microbial species living in or on the human body. This process is the most time consuming computation required. 

#### *1.3 Generate networks from SparCC* Bipartite network matrix and output for visualization from SparCC results

Section:

>-SparCC correlation matrix:**SparCC correlation for each pairwise**.
>
>-Threshold value to filter the SparCC result:0.2
>
>-SparCC pseudo p value matrix after permutation:**SparCC pseudo two_sided side p-value**

*the other options are left as default.*

**EXECUTE**

**NOTE:** This step will generate three output files, including bipartite network matrix, visualization input (for Cytoscape or Gephi) and associated edge attributes if needed.

### Method 2: SPIEC-EASI.

#### *2.1 SpiecEasi calculation*. Generate inverse covariance matrix or coefficient matrix from SpiecEasi 

Section:

>-Microbial data:**bac_16S_test.txt**.
>
>-Plant table:**plant_test.txt**.
>
>-Number of subsamples for StARS:10

*the other options are left as default.*

**NOTE:** Sparse InversE Covariance estimation for Ecological Association and Statistical Inference. Please see more in






