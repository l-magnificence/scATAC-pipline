# scATAC-pipline
## SRA file to fastq similar to scRNAseq-pipline
cd ~/scATAC/GSE139136
```
~/SRAToolkit/sratoolkit.current-ubuntu64/bin/fastq-dump SRR10315835 --split-files --gzip -O ./GSM4131776/
```

## rename the file similar to scRNAseq-pipline 
Sample1_S1_L001_I1_001.fastq.gz is Sample index (i7)
Sample1_S1_L001_R1_001.fastq.gz is Transposed DNA
Sample1_S1_L001_R2_001.fastq.gz is 10x barcode (i5)
Sample1_S1_L001_R3_001.fastq.gz is Transposed DNA
For cellranger-atac count, the I1 FASTQ is optional but the R1, R2, and R3 FASTQ files are all mandatory for the analysis

## cellranger-atac
```
/Shared_Software/Single_cell/cellranger-atac-1.2.0/cellranger-atac count --id=GSM4131776_G4218 \
  --reference=/Shared_Software/ref_genome/refdata-cellranger-atac-hg19-1.2.0 \
  --fastqs=~/scATAC/GSE139136/GSM4131776 \
  --sample=SRR10315835 \
  --localcores=48 \
  --localmem=64 
```
* **--id**：output filename  
* **--fastqs**：path to fastq file  
* **--sample**：fastq.gz文件名当中_S1之前的字段  
* **--transcriptome**：参考基因组
