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

#### Method 1: SparCC

#### *Majority selection*.  
On the left side, Majority selection is selected

Section:

-Microbial data; **bac_16S_test.txt**

-Number of species groupo for network analysis; two groups of species

-Plant table (2nd Group); **plant_test.txt**

the other options are left as default.

**EXECUTE**

Result:Filtered_OTU_table

#### *SparCC correlation and p-value calculation*

Section:

-Input table for SparCC pseudo p-value calculation:Filtered_OTU_table  

*the other options are left as default.*

Note: This process is the most time consuming computation required. 

**EXECUTE**


