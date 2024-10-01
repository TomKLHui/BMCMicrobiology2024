# Metagenomic analysis of gut microbiome illuminates the mechanisms and evolution of lignocellulose degradation in mangrove herbivorous crabs.

[Access this dataset on ncbi SRA, TSA and github](https://doi.org/10.5061/dryad.s7h44j1d4) (PRJNA1017629)
[Access this paper on BMC Microbiology](https://bmcmicrobiol.biomedcentral.com/articles/10.1186/s12866-024-03209-4)
This dataset contains the assembled metagenomes of 43 gut microbiome biological samples in 23 species of mangrove crabs in Hong Kong collected during 2019-2021. The raw metagenomic reads are available at NCBI SRA under accession PRJNA1017629. The assembly was conducted using MEGAHIT 1.2.9, and available in NCBI TSA. The unnormalized bacterial read counts tables on bacterial phyla and functional features in CAZy (release V10, 07292021) and KEGG databases (release v58) were generated using an integrated pipeline SqueezeMeta v1.4.0, which includes ORF prediction with Prodigal v2.6.3, taxonomic/functional read annotation with DIAMOND v2.0.8.146, and read mapping to annotations with Bowtie2 v2.3.4.1.

The raw count table were further processed using SQMtools to filter only bacterial read counts. To repeat the analysis, CoDaSeq package should be used to remove features with average <1000 counts.

## Description of the data and file structure

The metagenomic assemblies were under following naming convention
\[Abbreviated 6 character species name].megahit.fasta

The functional/ taxonomic read counts were under following naming convention
prok_function_[cazy|KEGG]*abund.txt
prok_taxa*{taxa level}_abund.txt

\|- README.md
\|- LICENSE
\|- .gitignore
\|- prok_function_cazy_abund.txt
\|- prok_function_KEGG_abund.txt
\|- prok_taxa_class_abund.txt
\|- prok_taxa_family_abund.txt
\|- prok_taxa_genus_abund.txt
\|- prok_taxa_order_abund.txt
\|- prok_taxa_phylum_abund.txt
\|- prok_taxa_species_abund.txt

## Sharing/Access information

Data was derived from the following sources:

*   Bioproject accession PRJNA1017629 ([https://www.ncbi.nlm.nih.gov/bioproject/?term=PRJNA1017629](https://www.ncbi.nlm.nih.gov/bioproject/?term=PRJNA1017629))

## Code/Software

Squeezemeta ([https://github.com/jtamames/SqueezeMeta](https://github.com/jtamames/SqueezeMeta))
CoDaSeq ([https://github.com/ggloor/CoDaSeq](https://github.com/ggloor/CoDaSeq))

To filter tables by read counts (and occurrence) threshold in R:

```
library(CoDaSeq)
codaSeq.filter(f, min.reads=1000, min.occurrence=0.99, samples.by.row=FALSE)
```

For downstream DA analyses please refer to the supplementary .Rmd from Gloor, Macklaim, Pawlowsky-Glahn & Egozcue (2017)(
[https://www.frontiersin.org/journals/microbiology/articles/10.3389/fmicb.2017.02224/full](https://www.frontiersin.org/journals/microbiology/articles/10.3389/fmicb.2017.02224/full)
[https://github.com/ggloor/Frontiers_2017](https://github.com/ggloor/Frontiers_2017)), as well as documentations from DeSeq2 ([https://bioconductor.org/packages/release/bioc/vignettes/DESeq2/inst/doc/DESeq2.html#plot-counts](https://bioconductor.org/packages/release/bioc/vignettes/DESeq2/inst/doc/DESeq2.html#plot-counts)) and ANCOM-BC ([https://www.bioconductor.org/packages/release/bioc/vignettes/ANCOMBC/inst/doc/ANCOMBC.html](https://www.bioconductor.org/packages/release/bioc/vignettes/ANCOMBC/inst/doc/ANCOMBC.html))
