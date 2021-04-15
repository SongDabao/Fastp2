![Fastp2](qc.png)

# Fastp2
A tool designed to provide high-speed scalable quality control for sequencing data which can take full advantage of modern hardware.
It includes a variety of function modules and supports different sequencing technologies (Illumina, Oxford Nanopore, PacBio). Fastp2 achieves speedups between one and two orders-of-magnitude compared to other state-of-the-art tools.

# Simple usage
## For short read
* For single end data (not compressed)
```
rabbit_qc -w nthreads -i in.fq -o out.fq
```
* For paired end data (gzip compressed)
```
rabbit_qc -w nthreads -i in.R1.fq.gz -I in.R2.fq.gz -o out.R1.fq.gz -O out.R2.fq.gz
```
## For long read
```
rabbit_qc -w nthreads -D -i in.fq
```

## For large gz files
A more efficient strategy to process large gzip compressed FASTQ files is to decompress files using pugz and then process them using Fastp2. Pugz has been integrated into Fastp2 project.

```
cd Fastp2/pugz && make asserts=0
./gunzip -t nthreads in.fq.gz
```

# Options
For more help information, please refer to `rabbit_qc -h`.

If `-w` opition is not specified, Fastp2 will set working thread number to total CPU cores - 2.
By default, the HTML report is saved to `Fastp2.html` (can be specified with `-h` option), and the JSON report is saved to `Fastp2.json` (can be specified with `-j` option).

Fastp2 suports all fastp options for short read quality control and all NanoQC optiions for long read quality control. For details please refer to [fastp](https://github.com/OpenGene/fastp) and [NanoQC](https://github.com/wdecoster/nanoQC).

# Examples of report
`Fastp2` creates reports in both HTML and JSON format.

# Build

**For Linux and OSX:**

```bash
cd Fastp2 && make
```

```bash
cd Fastp2 && make
```




<!--

## If you use Fastp2 for short read quality control please cite:

Shifu Chen, Yanqing Zhou, Yaru Chen, Jia Gu; fastp: an ultra-fast all-in-one FASTQ preprocessor, Bioinformatics, Volume 34, Issue 17, 1 September 2018, Pages i884–i890, https://doi.org/10.1093/bioinformatics/bty560

## If you use Fastp2 for long read quality control please cite:

De Coster W, D’Hert S, Schultz D T, et al. NanoPack: visualizing and processing long-read sequencing data[J]. Bioinformatics, 2018, 34(15): 2666-2669.
-->
