# rna_seq_notes

<iframe width="560" height="315" src="https://www.youtube.com/embed/lG11JjovJHE?si=f1gObtYwbvHz1vDh" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Commands for building hisat2 indexes

```bash
wget https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/000/182/965/GCF_000182965.3_ASM18296v3/GCF_000182965.3_ASM18296v3_genomic.fna.gz
wget https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/000/182/965/GCF_000182965.3_ASM18296v3/GCF_000182965.3_ASM18296v3_genomic.gtf.gz
gunzip *.gz
mv GCF_000182965.3_ASM18296v3_genomic.fna genome.fa
mv GCF_000182965.3_ASM18296v3_genomic.gtf genome.gtf

hisat2_extract_splice_sites.py genome.gtf > genome.ss
hisat2_extract_exons.py genome.gtf > genome.exon
hisat2-build -p 16 --exon genome.exon --ss genome.ss genome.fa genome_tran

```

## Quality control

[https://github.com/reneshbedre/HTSQualC](https://github.com/reneshbedre/HTSQualC)
