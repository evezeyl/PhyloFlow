# PhyloFlow
Nextflow pipeline for phylogenetic analysis.

## Disclaimer
This pipeline is currently under development. Contact Håkon Kaspersen for more information.

## Tracks
The pipeline consist of three tracks:

### CORE
This track identifies the core genes in the input assemblies by running Prokka [1],
followed by Panaroo QC and Panaroo pan-genome [2]. Then, duplicated genomes are removed with seqkit [3] (optional).
Then, a maximum likelihood (ML) tree is generated with IQTree [4], and SNP distances calculated with snp-dists [5].

### ASSEMBLY
In this track, the core genome is identified using ParSNP [6]. Then, duplicated genomes are removed with seqkit (optional).
Then, recombinant areas are identified with Gubbins [7], and masked with maskrc-svg [8] before the ML tree is generated 
with IQTree, and SNP-distances calculated with snp-dists. 

### READS
In this track, the core genome is generated through Snippy [9], which use reads
as input. Here too, recombinant areas are identified with Gubbins and subsequently masked with maskrc-svg,
and the tree generated by IQTree. SNP-distances are calculated with snp-dists.

## Usage
Copy the main.config file to your workspace and make necessary changes.
Then run the following:
```
module load Java/1.8.0_212

./PhyloFlow.sh /path/to/main.config /path/to/outdir
```

## References
[1] 10.1093/bioinformatics/btu153

[2] 10.1186/s13059-020-02090-4

[3] https://bioinf.shenwei.me/seqkit/

[4] 10.1093/molbev/msu300

[5] https://github.com/tseemann/snp-dists

[6] 10.1186/s13059-014-0524-x

[7] 10.1093/nar/gku1196

[8] https://github.com/kwongj/maskrc-svg

[9] https://github.com/tseemann/snippy






Håkon Kaspersen,
22.09.2020
