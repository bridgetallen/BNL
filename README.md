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