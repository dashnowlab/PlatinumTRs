# PlatinumTRs
Annotation of tandem repeat loci in the human genome

- ~7.8 million loci: STRs and VNTRs
- Minimum locus size 10 bp
- Maximum locus size 10,000 bp
- Loci within 50 bp are merged to produce compound/complex loci
- CHM13-T2T and GRCh38 genomes
- TRGT locus definitions and bed files
- Generated using Tandem Repeats Finder and tr-solve
 
These catalogs were used to call tandem repeat genotypes using TRGT by the [Platinum Pedigree Consortium](https://github.com/Platinum-Pedigree-Consortium).


## Defining the TR catalogs
The command `trf-mod -s 20 -l 160 {reference.fasta}` was used, resulting in a minimum reference locus size of 10 bp and motif sizes of 1 to 2000 bp, see [TRF-mod](https://github.com/lh3/TRF-mod). Loci within 50 bp were merged, and then any loci >10,000 bp were discarded. The remaining loci were annotated with [tr-solve](https://github.com/trgt-paper/tr-solve) to resolve locus structure in compound loci. Only TRs annotated on chromosomes 1-22, X, and Y were considered.

The catalogs are available on Zenodo [DOI 10.5281/zenodo.13178745](https://zenodo.org/doi/10.5281/zenodo.13178745)

### Example usage:

```
conda activate trgtdist

# VCF
./tr-solve2TRGT.py --trtools tr-solve-v0.2.0-linux_x86_64 example.vcf

# BED + FASTA
./tr-solve2TRGT.py --trtools tr-solve-v0.2.0-linux_x86_64 --fasta human_g1k_v38_decoy_phix.fasta GRCh38.UCSC.SimpleRepeats.sample.bed

```
