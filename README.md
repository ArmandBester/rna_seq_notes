# rna_seq_notes

## Quality control

```bash
fastp -i fastq/Calbicans-10-min-Control-1_S1_L001_R1_001.fastq -I fastq/Calbicans-10-min-Control-1_S1_L001_R2_001.fastq -o fastq_qc/qc-Calbicans-10-min-Control-1_S1_L001_R1_001.fastq -O fastq_qc/qc-Calbicans-10-min-Control-1_S1_L001_R2_001.fastq -h fastq_qc/qc-Calbicans-10-min-Control-1_S1_L001.html -j fastq_qc/qc-Calbicans-10-min-Control-1_S1_L001.json
```

[video](https://www.youtube.com/watch?v=lG11JjovJHE)

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

