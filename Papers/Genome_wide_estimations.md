
# Genome wide estimations 

## Common SNPs explain a large proportion of the heritability for human height

[Link to paper](https://www.nature.com/articles/ng.608)

## Quantifying Missing Heritability at Known GWAS Loci

[Link to paper](https://journals.plos.org/plosgenetics/article?id=10.1371/journal.pgen.1003993)

## Pitfalls of predicting complex traits from SNPs

[Link to paper](https://www.nature.com/articles/nrg3457)

Paper was published in 2013, on Nature Genetics.  I want to understand the pitfall associated with this method.  

The major findings from the paper were 
* many issues occur in the validation stage when the 

## Genome-Wide Complex Trait Analysis (GCTA): Methods, Data Analyses, and Interpretations

[Link to paper](https://link.springer.com/protocol/10.1007/978-1-62703-447-0_9)

This paper was publihed in 2013 from authors in Australia.  This paper details one of the methods that Matt has been using in his GWE pipelines.  I want to read this paper, understand the rational for creating this method, and learn how to use it.  

Purpose = to estimate the proportion of additive genetic variance that can be captured by considering all the SNPs simultaneously (with out testing for any individual associations of the SNPs with the trait) 

Missing heritability can also be called hiding heritability, because most SNP effets are too small to be pick up by the strigent GWAS significance levels.  

SNPs are set as random effects in a mixed linear model.  

This method is not necessarily meant for calculating SNP heritability.  The h2SNP value that is calculated is described as phenotypic variance explained by fitting all the genome-wide SNPs simultaneously.  (not as the proportion of phenotypic varaince explained by the additive effects of all causal variants).  Unless the method was used on a closely related cohort, then the h2SNP would be similar to the h2 of the trait.  Therefore the h2SNP in a family study can not be described as, varaince explained by all SNPs, because there is a shared environment effect and causal variant effects not tagged by the SNPs.  

There are two steps 
1. Generating the GRM between individuals 
2. Estiamte variance explained by SNPs via REML

## Harnessing genomic information for livestock improvement 

[Link to paper](https://www.nature.com/articles/s41576-018-0082-2) 

18/02/19 

This paper was publised in Natures reviews in December 2018.  The information that I am interested in from this paper, is how genome wide estimation studies and 'breeding values' or risk anaylses can be useful and how they are done.  The paper also has good definitions for QTL, GWAS and genomic selection.  
* Genetic variance for the trait of interest = additive effects of thousands of variants with very small effects that are uniformly distributed in the genome.  
* In humans this method is used to study the genetic architecture of common complex diseases and predict individuas disease risk 
* BLUP and GBLUP assume that all segements of the genome contribute equaly to the trait of interest (we know that this is not true), this can mean that some SNP effects are regressed down, because it tis being assumed that all effects are small 

In Box 2 there is an explaination and breakdown of LUP and GBLUP equations.  GBLUP estimations are more accurate when the populations are nigger and more closely related.  For the NPH data set, this means that accuracy is decreased due to the small size but increased because the coancestry measures are likely higher. 


## How to know when physicians are ready for genomic medicine

[Link to the paper](http://stm.sciencemag.org/content/7/287/287fs19.short) 

14/02/19 

This paper related to the **applicability** of genomics in a clinical setting.  The paper details the struggles associated with clinicians being unprepared for genomic interventions or interpreting results.  

The paper was published in the journal of Science Translation Medicine. The authors are from a range of North Western Universities in the USA.  
1. Potential perils of unprepardness: intorduces the idea of genetic exceptionalism 
1. Defining prepardness: there is no universal definition so we need to create a support system to educate and train the 
current physicians 
1. Another relative challenge includes incorporating genomic information into clinical health records 

The table presented in the paper details how EPA's (entrusted proffensional activities) relate to family history (documentation), genetic testing for patient management and genetic information for treatment decisions.  

Genomics Aotearoa address the lack of capabilities in the area of clinical genomics in NZ.  They present the following outcomes that they intend to address: 
* To apply genomic diagnostics to a group of 50 families with a child (or children) with an undiagnosed developmental disorder
* To link the research sector with the clinical diagnostic sector across NZ to build capability and embed tools and pipelines to improve clinical genomics diagnostics in NZ
* To introduce clinical genomics into disadvantaged communities with a high proportion of Māori and Pacific people
* To develop and expand linkages between the research and diagnostic genomics sectors in NZ

These outcomes address the lack of laboratory services in NZ, they do not however, address the ability or prepardness of NZ physicians for clinical genetics.  The table presented may be a very useful starting point for NZ to then add to, to ensure the practices are relevant to all New Zealanders.  This would require the incorporation of tikanga Maori.  


## The value of genetic risk scores in precision medicine for diabetes

[Link to paper](https://www.tandfonline.com/doi/abs/10.1080/23808993.2018.1510732) 

14/02/19

The paper was published in the Expert review for precision medicine and drug development.  The authors are from Oxford University.  

The paper summaries in a very short paragraph what genetic risks scores are and why they are so hard to use.  The paper then describes the types of genetic variants that have been robustly associated with diabetes (common, uncommon and individual variants).  The complexity of using such genetic information means the prospects for using genetic risk predictors is poor.  Yet the authors maintain they are optimistic. 

Paper describes the use of the C-statistics for predictions, 50% is chance, 80% is usable in clinics.  One of the first T2D analysis gave a C-statistic of 60%.  This is not very good.  The latest C-statistic from the large UKBIO bank analysis raised this to high 60s.  The authors seemed optimistic about this increase however, this is still no where near clinical applicability of 80%.  

Introduction to the 'palette' model which takes into consideration of genetic and non-genetic components, define clusters of T2D-risk loci into similar mechanisms of actions.  These clusters are then given their own process-specific GRS, this describces the genetic contribution to each intermediate step.  These deconstructed risk scores are able to capture diverse aspects of the clinical het- erogeneity within diabetes
