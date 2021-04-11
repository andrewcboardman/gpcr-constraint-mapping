# Mapping patterns of mutational constraint in GPCR drug targets
## Methods
** Selection and annotation of GPCR genes **
* A set of 394 non-olfactory protein-coding GPCR genes in humans was selected using the GPCRdb and IUPhar Guide To Pharmacology databases. 
* 66 GPCR genes which are associated with heritable traits in humans due to loss and gain of function mutations were annotated using OMIM data and the Schoeneberg paper. 15 GPCRs are associated with genetic diseases due to gain-of-function mutations; 51 genes are associated with genetic diseases due to loss-of-function mutations. 10 genes are associated with diseases due to both gain-of-function and loss-of-function.
* 98 GPCR genes which are the targets of FDA-approved drugs were annotated using the Congreve paper, including 75 targets of activating drugs (partial or full agonist, PAM) and 61 targets of inactivating drugs (antagonist, inverse agonist, NAM). 35 GPCR genes are the targets of both activating and inactivating drugs.
** Extraction of GPCR variants in the human population from gnomAD **
* For each gene, summary statistics were extracted from the precomputed gnomAD analysis results. The upper bound of the obs/exp ratio for pLoF variants was used, and the point estimate of the obs/exp ratio for missense variants annotated as damaging by PolyPhen2 was used.
* To enable finer-grained analysis of mutants in each gene, the genomic region (chromosome, gene start position, and gene end position) corresponding to each of these genes in the Grch37 genome assembly was downloaded from Ensembl using the BioMart package in R, and all observed population genetic variants in these regions were downloaded from the gnomAD database hosted on BigQuery (version 2.1.1 using Grch37-mapped exome data), together with the effects of these variants on the canonical transcript for each GPCR gene (identified using Uniprot).
* Sequences of all class A GPCRs annotated with generic residue labels were downloaded from GPCRdb and manually curated. 58803 missense variants for class A GPCRs were annotated with GPCRdb residue labels based on sequence position.
** Calculation of constraint **
