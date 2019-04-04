# Calculating Polynesian allele frequencies 

This calcualtion is completed in bash.  
You will need access to the BioChemistry Department server.  Log in and navigate to the location you want the file to be produced in. 

This script is located here:  
./Merriman_Documents/Anezka/Scripts/polyfreq.sh   

You need to know the following:   
1. Gene Name (results file will be called this)  
1. Chromosome  
1. Start  
1. End  
1. Overlap (this is optional, use 0 for no overlap)  

-----------------
**This is an example of what you will enter into the command line**  
#bash polyfreq.sh ALMS1 2 73612885 73837046 0  

#ALMS1  2 73612885 73837046 50000    
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

bcftools filter ../../Matt/aseq/variant_annotated/Chr$chr.ann_all.vcf.gz  -r $chr:$start-$end -o tmp.vcf.gz -O z  

bcftools view -S ../../Matt/aseq/keeppoly.txt tmp.vcf.gz | bcftools view -q 0.0001 --min-alleles 2 --max-alleles 2 | gzip -c > $gene.vcf.gz  

vcftools --gzvcf $gene.vcf.gz --freq --out $gene  
  
rm tmp.vcf.gz
----------------------
