# Terminal truncation calculator for long-read sequencing

The truncation_calculator script calculates truncation metric for long-read sequencing techniques based on first exon or cage peak and polyA peak coordinates. The inputs for the script are

The input for the tr
1-A reference tsv file with the full path to the annotated bed files including cell and sequencing type per sample
2-The intersected bed files
3-The number of features per file

Bedtools can be used to splt the bam files into multiple features and intersect them with gene annotations:

```
#!/bin/bash
file=$1
file_name=$2
ref_genome=$4
dir_out_bed=$5
dir_out_annotation=$6

bed_output="$dir_out_bed"/"$file_name".bed
annotation_output="$dir_out_annotation"/"$file_name".bed

bedtools bamtobed -split -i $file > "$bed_output"
bedtools intersect -s -wo -split -bed -a "$bed_output" -b "$ref_genome" > "$annotation_output"
```



