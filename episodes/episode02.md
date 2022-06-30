## ibrerías necesarias


library(vegan)
library(ggplot2)
library(phyloseq)

##cargar bioms como variable

SRR121928_metagenomes <- import_biom('bracken_shaday/SRR121928.biom')

##calcular índice de shannon

shan_indexSRR12192848 <- diversity(SRR121928_metagenomes@otu_table@.Data[,'SRR12192848_bracken_species'])

##calcular índice de pielou

evennessSRR12192848 <- shan_indexSRR12192848/log(specnumber(SRR121928_metagenomes@otu_table@.Data[,'SRR12192848_bracken_species']))


##PCoA

data_otu_SRR121928 <- data.frame(otu_table(SRR121928_metagenomes))

dist_bc_SRR121928 <- as.matrix(vegdist(data_otu_SRR121928, method = "bray"))

pcoa_bc = ordinate(SRR121928_metagenomes, "PCoA", "bray")


plot_ordination(SRR121928_metagenomes, pcoa_bc, color = "site") + 
  geom_point(size = 3)

