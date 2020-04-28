---
title: Applications
order: 3
suborder: 0
---

# Streamed preprocessing of sequence data

HTStream is a suite of preprocessing applications for high throughput sequencing data (ex. Illumina). A Fast C++ implementation, designed with discreet functionality that can be pipelined together using standard unix piping.

Benefits Include:
  * No intermediate files, reducing storage footprint.
  * Reduced I/O, files are only read in and written out once to disk.
  * Handles both single end and paired end reads at the same time.
  * Applications process reads at the same time allowing for process parallelization.
  * Built on top of mature C++ Boost libraries to reduce bugs and memory leaks.
  * Designed following the philosophy of [Program Design in the UNIX Environment](https://onlinelibrary.wiley.com/doi/abs/10.1002/j.1538-7305.1984.tb00055.x).
  * Works with native Unix/Linux applications such as grep/sed/awk etc.
  * Can build a custom preprocessing pipeline to fit the specific expectation of the data.
  * A single JSON output per sample detailing the preprocessing statistics from each application.

HTStream achieves these benefits by using a tab delimited intermediate format that allows for streaming from application to application. This streaming creates some awesome efficiencies when preprocessing HTS data and makes it fully interoperable with other standard Linux tools.

## Why preprocess reads

We have found that aggressively “cleaning” and preprocessing of reads can make a large difference to the speed and quality of mapping and assembly results. Preprocessing your reads means:

  * Removing bases of unwanted sequence (Ex. vectors, adapter, primer sequence, polyA tails).
  * Merge/join short overlapping paired-end reads.
  * Remove low quality bases or N characters.
  * Remove reads originating from PCR duplication.
  * Remove reads that are not of primary interest (contamination).
  * Remove too short reads.

Preprocessing also produces a number of statistics that are technical in nature that should be used to evaluate “experimental consistency”.

## Preprocessing statistics as QA/QC.

Beyond generating "better" data for downstream analysis, preprocessing statistics also give you an idea as to the original quality and complexity of the sample, library generation features, and sequencing quality.

This can help inform you of how you might change your procedures in the future, either sample preparation, or in library preparation.

We’ve found it best to perform __QA/QC__ on both the run as a whole (poor samples can negatively affect other samples) and on the samples themselves as they compare to other samples (**BE CONSISTENT**).

Reports such as Basespace for Illumina, are great ways to evaluate the run as a whole, the sequencing provider usually does this for you.  

PCA/MDS plots of the preprocessing summary are a great way to look for technical bias across your experiment. Poor quality samples often appear as outliers on the MDS plot and can ethically be removed due to identified technical issues. You should **NOT** see a trend on the MDS plot associated with any experimental factors. That scenario should raise concerns about technical sample processing bias.

## HTStream applications

HTStream includes the following applications:

[hts_AdapterTrimmer](./hts_AdapterTrimmer): Identify and remove adapter sequences.  
[hts_CutTrim](hts_CutTrim): Discreet 5' and/or 3' basepair trimming.  
[hts_LengthFilter](./hts_LengthFilter): Remove reads outside of min and/or max length.  
[hts_NTrimmer](./hts_NTrimmer): Extract the longest subsequence with no Ns.    
[hts_Overlapper](hts_Overlapper): Overlap paired end reads, removing adapters when present.  
[hts_PolyATTrim](./hts_PolyATTrim): Identify and remove polyA/T sequence.  
[hts_Primers](hts_Primers) - Identify and optionally remove 5' and/or 3' primer sequence.  
[hts_QWindowTrim](hts_QWindowTrim) - 5' and/or 3' quality score base trimming using windows.  
[hts_SeqScreener](./hts_SeqScreener): Identify and remove/keep/count contaminants (default phiX).  
[hts_Stats](hts_Stats) - Compute read stats.  
[hts_SuperDeduper](./hts_SuperDeduper): Identify and remove PCR duplicates.  

We hope in the long run to include any and all needed preprocessing routines.

## Contributing

First please read [code of conduct](https://github.com/ibest/HTStream/blob/master/CODE_OF_CONDUCT.md).

If you encounter any bugs or have suggestions for improvement, please post them to [issues](https://github.com/ibest/HTStream/issues).

We'd love to accept code and/or application additions! If your interested in contributing please read our [contributing guidelines](https://github.com/ibest/HTStream/blob/master/CONTRIBUTING.md).
