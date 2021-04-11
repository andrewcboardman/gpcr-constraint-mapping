# Mapping patterns of mutational constraint in GPCR drug targets
## Methods
**Selection and annotation of GPCR genes**

* A set of 394 non-olfactory protein-coding GPCR genes in humans was selected using the GPCRdb and IUPhar Guide To Pharmacology databases. 
* 66 GPCR genes which are associated with heritable traits in humans due to loss and gain of function mutations were annotated using OMIM data and Schoeneberg et al [3], including 15 GPCR genes associated with genetic diseases due to gain-of-function mutations and 51 GPCR genes were associated with genetic diseases due to loss-of-function mutations. 10 genes are associated with diseases due to both gain-of-function and loss-of-function.
* 98 GPCR genes which are the targets of FDA-approved drugs were annotated using data from Congreve et al [4], including 75 targets of activating drugs (partial/full agonist or PAM) and 61 targets of inactivating drugs (antagonist, inverse agonist or NAM). 35 GPCR genes are the targets of both activating and inactivating drugs.

**Extraction of GPCR variants**

* For each gene, summary statistics were extracted from the precomputed gnomAD analysis results. We chose to use the upper bound of the obs/exp ratio for pLoF variants, and the point estimate of the obs/exp ratio for missense variants annotated as damaging by PolyPhen2.
* To enable finer-grained analysis of mutants in each gene, the genomic region (chromosome, gene start position, and gene end position) corresponding to each of these genes in the Grch37 genome assembly was downloaded from Ensembl using the BioMart package in R, and all observed population genetic variants in these regions were downloaded from the gnomAD database hosted on BigQuery (version 2.1.1 using Grch37-mapped exome data), together with the effects of these variants on the canonical transcript for each GPCR gene (identified using Uniprot) [1,2].
* Sequences of all class A GPCRs annotated with generic residue labels were downloaded from GPCRdb and manually curated. 58803 missense variants for class A GPCRs were annotated with GPCRdb residue labels based on sequence position.
* For each generic position, the average missense constraint was calculated as the ratio of observed missense variants in that positions to the number expected. The number of expected variants were calculated by dividing the number of synonymous variants in the gene by the protein length and multiplying by two.

**Analysis**

* The association between constraint and disease annotations was tested by training linear models on the ranks of the pLoF constraint and on the value of the damaging missense constraint. Loss-of-function and gain-of-function diseases were treated separately; for gain-of-function diseases, no significant difference was observed, while for loss-of-function diseases a significant difference was observed. A similar analysis was carried out for genes which are the targets of FDA-approved drugs.
* The position of R3x50 in the structure of the A2A receptor was visualised using Pymol.

## References

[1] K. J. Karczewski et al., ‘The mutational constraint spectrum quantified from variation in 141,456 humans’, Nature, 581, pp. 434–
443, 2020, doi :10.1038/s41586-020-2308-7
[2] E. V. Minikel et al., ‘Evaluating drug targets through human loss-of-function genetic variation’, Nature, 581, pp. 459–464, 2020,
doi: 10.1038/s41586-020-2267-z.
[3] T. Schöneberg and I. Liebscher, ‘Mutations in G Protein–Coupled Receptors: Mechanisms, Pathophysiology and Potential
Therapeutic Approaches’, Pharmacological Reviews, 73, pp. 89-119, 2021, doi: https://doi.org/10.1124/pharmrev.120.000011
[4] M. Congreve, C. de Graaf, N. A. Swain, and C. G. Tate, ‘Impact of GPCR Structures on Drug Discovery’, Cell, 181, pp. 81–91,
2020, doi: 10.1016/j.cell.2020.03.003

