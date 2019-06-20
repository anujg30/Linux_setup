This file is a notebook for bioinformatics related help especially for Gatech community which uses pace clusters.

# Get things working on pace

## Blast

Blast binaries could be directly downloaded from [NCBI ftp](https://www.ncbi.nlm.nih.gov/books/NBK52640/) (ftp://ftp.ncbi.nlm.nih.gov/blast/executables/LATEST) and unzipped and added to the binaries.
However, to make it work on pace a bit modifications and modules are required. Latest versions of Python and GCC lead to errors. This setup worked for me.

```
qsub -I -l walltime=15:00,nodes=1:ppn=1 -q iw-shared-6
module load boost/1.53.0
module load gcc/4.7.2
module load python/2.7
module load ncbi_blast/2.2.29
makeblastdb -in test.fsa -parse_seqids -taxid_map test_map.txt -title "Cookbook demo" -dbtype prot
```
