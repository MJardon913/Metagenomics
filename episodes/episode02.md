---
title: $\alpha$ and $\beta$ diversity analysis in R.

---

$\alpha$-diversity measures the "richness" of taxa within a community. $\beta$-diversity on the other hand measures how different the comunities are in their richness. These analyses will be performed on the 5 samples of maize rhizosphere of the project BioProject:PRJNA645385. 


## Load libraries and data for analyses.

~~~

>library(vegan)
>library(ggplot2)
>library(phyloseq)
~~~
{: .output}


##cargar bioms como variable

SRR121928_metagenomes <- import_biom('Metagenomics/Data/bracken_biom/SRR121928_bracken.biom')


## Cálculo de la diversidad-$\alpha$


plot_richness(physeq = SRR121928_metagenomes, 
              measures = "Shannon") 



##calcular índice de shannon

shan_indexSRR12192848 <- diversity(SRR121928_metagenomes@otu_table@.Data[,'SRR12192848_bracken_species'])

##calcular índice de pielou

evennessSRR12192848 <- shan_indexSRR12192848/log(specnumber(SRR121928_metagenomes@otu_table@.Data[,'SRR12192848_bracken_species']))


## Cálculo de diversidad-$\beta$

PCoA

data_otu_SRR121928 <- data.frame(otu_table(SRR121928_metagenomes))

dist_bc_SRR121928 <- as.matrix(vegdist(data_otu_SRR121928, method = "bray"))

pcoa_bc = ordinate(SRR121928_metagenomes, "PCoA", "bray")


plot_ordination(SRR121928_metagenomes, pcoa_bc, color = "site") + 
  geom_point(size = 3)
