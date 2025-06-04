# BNL

Viral Analysis End-to-End

Metagenomic dataset from Global Ocean Viromes 

Step 1 - Import files as SRA
Step 2 - Use FastQC to check quality of data
Step 3 - Quality control - use trimmomatic to trim data
Step 4 - Post QC Read assessment using FastQC
Step 5 - Use MetaSPAdes to assemble
Step 6- contigs input_assembly_refs
min_contig_lengthMin Contig Length
output_nameOutput name
Step 6- Use Virsorter to identify viral genomes 
Step 7 - potentially viral Use Virsorter
Step 8 - use vConTACT2 to classify sequences
Step 9 - Use Prokka for predicting genes
Step 10 - vConTACT2 again

PEP 20 - The Zen of Python

PEP 8
- code layout
- imports
- naming conventions
- spacing
- comments
- docstrings
- comparisons
- code should be readable and consistent

RNA-seq Primer

Step 1 - Upload Genome data
Step 2 - Import single end reads from the internet (Parameters
download_typeURL Type
sequencing_techSequencing Technology
fwd_file_urlFASTA/FASTQ File URL
single_genomeSingle Genome
nameReads Object Name)
Step 3 - create a sample set for experimental data using "Library Type", "Domain", "RNA-seq Sample and Condition Labels," and provide the "RNA-seq Sample Set
Step 4 - FastQC (input_file_refRead Library/RNA-seq Sample Set:)
Step 5 - Align Reads using HISAT2 
Step 6- Assemble Transcripts using StringTie
Step 7 - Create Average Expression Matrix (expression_matrix_refExpression Matrix: KBaseFeatureValues.ExpressionMatrix)
output_suffixAverage Expression Matrix Name Suffix
Step 8 - Identify Differential Expression using DESeq2
Step 9 - Create Feature Set and Filtered Differential Expression Matrix
Step 10 -  Functional enrichment of differential expressed featureset


Client-Server Architecture 

common verbs:

get "read"
post "create"
put "update"
delete "delete"

KBase SDK

- when you run an app in a narrative, it runs in a docker container on KBase

User Input - parameters are listed as references, think of these as URL's to download the files, elements can be customized to accept different kinds of data

App Code and Data Management - input is converted to a python dictionary, then algorithms are run

Output and Reporting - KBase report is generated 

Command-line Interface - called kb-sdk and makes it easy to initiliaze, validate, compile, and test your app

Docker - apps run inside docker images and the interface runs within a container

Composing apps - when you install and run another app within yyours the other app runs on it's own  seperate docker container. also tracked seperately from python dependancies 

KBase Types and Parameters - config files use used for parameters and output 

Working with files and data (Scratch and the Workspace) - scrath is ephemeal so any files in this directory are gone when your app stops running. workspace use if you want the user to see in the narrative.  a dataset in the workplace is referred to as an object 

The Catalog - registry of the apps. three catalogs for testing purposes: dev, beta, and release. dev = prototype beta = requires testing, release = visible to normal kbase users

Publishing 

every vector space has a basis

dowloading kbase kb-sdk

mkdir /home/bridgetallen/bin/
# Generate the kb-sdk script and put it in ~/bin/kb-sdk
docker run kbase/kb-sdk genscript > /home/bridgetallen/bin/kb-sdk
chmod +x /home/bridgetallen/bin/kb-sdk
# Add ~/bin to your $PATH if it is not already there
export PATH=$PATH:/home/bridgetallen/bin/kb-sdk
# You might want to put the above command in your ~/.bashrc or ~/.zshrc:
echo "export PATH=\$PATH:/home/bridgetallen/bin/kb-sdk >> ~/.bashrc

kb-sdk init -e -u bridgetallen bridgetallenContigFilterHelloWorld

bridgetallenContigFilterHelloWorld

git init
git add .
git commit -m 'Initial commit'

git config --global user.name "Bridget Allen"
git config --global user.email "ballen@bnl.gov"


 git remote add origin https://github.com/bridgetallen
 git push -u origin master

 git remote remove origin
git remote add origin https://github.com/bridgetallen/bridgetallenContigFilterHelloWorld.git

Arabidopsis RNA-seq Analysis Tutorial Questions 

1. If FastQC says your reads are no good, how is HISAT2 still able to run and align the reads
2. What does a normalized distribution say about the the gene expression?
3. It says that my expression matrix was successful, but I don't see useful information in the details.
4. Since we know that Arabidopsis is normal, if we saw an unusual dot on the PCA plot, would it be of interest or a known outlier?
5. What are the most common and most uncommon apps used in this analysis?
