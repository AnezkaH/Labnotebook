
# Genome wide estimations 

## Linkage disequilibrium in finite populations

[Link to paper](Linkage disequilibrium in finite populations) 

## Gametic disequilibrium measures: proceed with caution

[Link to paper](https://www.ncbi.nlm.nih.gov/pubmed/3666445/)

This paper compares 5 measures of LD and their properties.  

## Mathematical properties of the r2 measure of linkage disequilibrium

[Link to paper](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2580747/) 

This paper investigates the mathematical properties of r2.  

## Common SNPs explain a large proportion of the heritability for human height

[Link to paper](https://www.nature.com/articles/ng.608)

13/03/19 

The aim of this paper was to understand where the missing heritability is coming from.  Overall they were able to explain 45% of the heritability using all the SNP simultaneously.  The missing heritability can be explained by: 
* incomplete LD between causal variants and the SNPs genotyped 
* minor allele frequencies of the causal variants is low 

Height is a model quantitative trait studied to investigate the genetic contribution to traits.  GWAS studies have identified ~50 variants in the general population that account for only ~5% of the heritability.  The final paragraph in the introduction has a very good explaination of the difference between GWAS and GWE.  

GWAS = testing the SNPs individually for an association with the trait --> must use a very stringent P-value to account for the multiple testing (prevent false positives) --> means you miss out on significant small effects 

GWE = testing all available SNPs at the same time for association with the trait, the effect sizes are treated as random by the model.

**Results**
3,925 individuals were retained after accounting for pairwise relationships (maximum of 0.025).  They fitted a linear model and then used REML to estimate the variance explained by the SNPs.  The 45% is still less than the 80% previously estmated, this is because the SNPs on the chip are not in full LD with all the causal variants.  

They performed REML analysis by fitting the first two, four and ten eigenvectors from the European-only PCA as covariates.

Other things to consider: 
* gene by environment interactions (but shouldn't contribute to heritability) 
* epigenetic effects if they are inherited stabily 

## Quantifying Missing Heritability at Known GWAS Loci

[Link to paper](https://journals.plos.org/plosgenetics/article?id=10.1371/journal.pgen.1003993)

12/03/19 

This paper investigates the use of GWE methods to calculate heritability compared to GWAS type methods.  I want to understand the method that this paper used, and if their methods were reliable for detecting the effects of small effect variants (this is relavent for the NPH dataset).  

* paper introduces the idea of genetic architecture affecting the effect size estimations of disease causing variants 
* they defined local heritability to be the measure of aggregate variance from all causal variants at a locus
* they used variance components analysis from a single effect size over a relatedness matrix 
* this method allows the analysis of loci that have no known association in the trait but have been associated with other related traits, implicating shared disease architecture

The papers aim is to explain as much of the local heritability as possible without upward bias.


## LDAK 

27/02/19 

Doug Speed is the creator of this tool.  The inital purpose of the paper was "to adjust for linkage disequilibrium (LD) by calculating SNP weightings which downweight the contribution of SNPs in highly tagged regions".  The offical LDAK website is [here](http://dougspeed.com/ldak/). 

Generally LDAK allows you to:
* Calculates LDAK SNP weightings (now much quicker than before)
* Computes weighted and unweighted kinship matrices 
* Generalised REML Solver - allows for both kinships and regions
* Super-efficient mixed-model analysis
* Gene-based Association Testing
* MultiBLUP Prediction 

Relavent papers are about [MultiBLUP](https://www.nature.com/articles/s41588-018-0279-5) and [SumHer](https://www.nature.com/articles/s41588-018-0279-5) (method in LDAK that allows you to use summary level statistics instead of individual level data).  

## Pitfalls of predicting complex traits from SNPs

[Link to paper](https://www.nature.com/articles/nrg3457)

19 and 20/02/19 

Paper was published in 2013, on Nature Genetics.  I want to understand the pitfalls associated with this method.  

The major findings from the paper were 
* many issues occur in the validation stage when it is not independent from the discovery phase 
* make sure that the discovery and validation samples are BOTH representative of the population (while this is true, you must also make sure that the validation strategy is practically appropriate)
* genomic prediction is already heavily used in livestock improvement and there are many potential aplications in plants, preventative medicine and clincal decisions 
* genomic predictors need to be fairly evaluated and not over stated 

Figure 1 in the paper is a really nice summary of how SNP-prediction is used, broken down in discovery, validation and application stages.  

Limitation of prediction analyses 
1. **Prediction of phenotypes from genetic markers**
* assuming that heritability h2 is a true reflection of reality, only achiveable if all the causal variants are known and their effect sizes calucated without error 
* environmental risk factors can be incorporated into the risk prediction to increase accuracy, however not all envr factors are known 
* maybe more applicable at a group level rather than an individual level 
2. **Variance explained by markers**
* SNPs used in chip are not usually causal, can be mitigated by imputing based on LD (however this will not pick up on rare or population specific variants 
* again mentions hidden heritability rather than missing 
3. **Errors in the estimated effects of the markers**
* effects are calculated from a finite sample meaning there will be sampling error 
* generally the effect sizes of alleles are small, therefore so are the accuracies, unless using a large sample 
4. **Statistical methods in the discovery sample**
* least squares predicition is common, but calcualtes the SNP effects one at a time
*  ideally, models the distribution of SNP effects and the correltaion between SNPs in the presence single and multiple causal varaints 

Pitfalls of the analysis 
1. Validation and discovery sample overlap 
2. The validation sample: if the validation sample is more closely related to the discovery sample that the targeted population the prediction accuracy will be overestimated = cryptic relatedness 
3. Population stratification similarity - this pitfall depends on the purpose of the analysis and the target population, (in NPH case this should not be an issue but we should be aware of it). The suggested solution to this to fit the ancestry PCA. 
4. Expectation of equality of R2 and h2M 

## Genome-Wide Complex Trait Analysis (GCTA): Methods, Data Analyses, and Interpretations

[Link to paper](https://link.springer.com/protocol/10.1007/978-1-62703-447-0_9)

20/02/19 

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

In Box 2 there is an explaination and breakdown of BLUP and GBLUP equations.  GBLUP estimations are more accurate when the populations are bigger and more closely related.  For the NPH data set, this means that accuracy is decreased due to the small size but increased because the coancestry measures are likely higher. 


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
