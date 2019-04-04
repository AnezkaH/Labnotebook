# Calculating Linkage Diseqilibrium between variants 

This protocol is done in bash.

You need to know your:
1. Gene name (file name will be called this)
1. Chromosome
1. Start 
1. End 
1. Overlap (this is optional, use 0 for no overlap)

Note: Use the can a single position in the genome for both the 'Start' and 'End' if you want to check just one variant.  

You will need access to the BioChemistry Department server in order to access the script with the calculations. 
Log into server.  Navigate to the folder that you want the results file to be created in. 

The script used is located here:
./Merriman_Documents/Matt/scripts/ldgene.sh 
 
Make sure that the file address is correct so that the command line is able to access the script from where you are located in the server.  

----------------------
**This is an example of how to format the command**
#bash ~/scripts/ldgene.sh ALMS1	2	73612885	73837046

#gene=ALMS1
#chr=2
#start=73612885
#end=73837046
#overlap=50000

overlap=$5
gene=$1
chr=$2
start=$(($3 - $5))
end=$(($4 + $5))

**Creating results file and giving the script the information**
bcftools filter aseq/variant_annotated/Chr$chr.ann_all.vcf.gz  -r $chr:$start-$end -o VCFs_Random/tmp.vcf.gz -O z
**Ensuring the sequencing data for Poly is kept in biallelic format**
bcftools view -S aseq/keeppoly.txt VCFs_Random/tmp.vcf.gz | bcftools view -q 0.0001 --min-alleles 2 --max-alleles 2 | gzip -c > VCFs_Random/$gene.vcf.gz
**Calculating LD** 
vcftools --gzvcf VCFs_Random/$gene.vcf.gz --ld-window-bp 500000 --geno-r2 --chr $chr --out VCFs_Random/$gene --min-r2 0.001 

------------------


