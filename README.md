# HTStream    


<a href=""><img src="https://github.com/ibest/HTStream/workflows/C++%20CI/badge.svg"></a>&nbsp;
<a href="https://github.com/ibest/HTStream/releases/latest"><img src="https://img.shields.io/github/v/release/ibest/HTStream"></a>

<a href="https://github.com/ibest/HTStream/blob/master/LICENSE"><img src="https://img.shields.io/github/license/ibest/HTStream?label=License"></a>&nbsp;
<a href="https://github.com/ibest/HTStream/code_of_conduct.html"><img src="https://img.shields.io/badge/Contributor%20Covenant-v2.0%20adopted-ff69b4.svg"></a>


HTStream is a suite of preprocessing applications for high throughput sequencing data (ex. Illumina). A Fast C++ implementation, designed with discreet functionality that can be pipelined together using standard unix piping.

Example:
```bash
hts_Stats -L sample1.json -N "initial Stats" \
    -1 sample1_S1_L001_R1_001.fastq.gz \  
    -2 sample1_S1_L001_R1_001.fastq.gz | \  
hts_AdapterTrimmer -A sample1.json -N "trim adapters" | \  
hts_LengthFilter -A sample1.json -N "remove reads < 50bp" \  
    -m 50 | \  
hts_Stats -A sample1.json -N "final Stats" \  
    -f sample1_preprocessed  
```

## Quick Installation

### Install binaries for linux systems:

On Linux systems, the easiest and most straight forward option is to download and unpack the pre-compiled binaries to somewhere on your `$PATH`.

```bash
wget https://github.com/ibest/HTStream/releases/download/v1.2.0-release/HTStream_v1.2.0-release.tar.gz

tar xvf HTStream_v1.2.0-release.tar.gz
```

### Install from Bioconda:

HTStream is available through the Bioconda channel. Visit [Miniconda](https://docs.conda.io/en/latest/miniconda.html).

```bash
conda install -c bioconda htstream
```

If you wish to install from source or the development version, see our more [complete installation]({{ site.baseurl }}/install) instructions.

## Application Descriptions

HTStream includes the following applications:

[hts_AdapterTrimmer]({{ site.baseurl }}/applications/hts_AdapterTrimmer): Identify and remove adapter sequences.  
[hts_CutTrim]({{ site.baseurl }}/applications/hts_CutTrim): Discreet 5' and/or 3' basepair trimming.  
[hts_LengthFilter]({{ site.baseurl }}/applications/hts_LengthFilter): Remove reads outside of min and/or max length.  
[hts_NTrimmer]({{ site.baseurl }}/applications/hts_NTrimmer): Extract the longest subsequence with no Ns.    
[hts_Overlapper]({{ site.baseurl }}/applications/hts_Overlapper): Overlap paired end reads, removing adapters when present.  
[hts_PolyATTrim]({{ site.baseurl }}/applications/hts_PolyATTrim): Identify and remove polyA/T sequence.  
[hts_Primers]({{ site.baseurl }}/applications/hts_Primers) - Identify and optionally remove 5' and/or 3' primer sequence.  
[hts_QWindowTrim]({{ site.baseurl }}/applications/hts_QWindowTrim) - 5' and/or 3' quality score base trimming using windows.  
[hts_SeqScreener]({{ site.baseurl }}/applications/hts_SeqScreener): Identify and remove/keep/count contaminants (default phiX).  
[hts_Stats]({{ site.baseurl }}/applications/hts_Stats) - Compute read stats.  
[hts_SuperDeduper]({{ site.baseurl }}/applications/hts_SuperDeduper): Identify and remove PCR duplicates.  

We hope in the long run to include any and all needed preprocessing routines.

A [detailed description]({{ site.baseurl }}/applications) of the project.

## Example Workflows

You can build your own preprocessing pipeline specific to the experiment and sequencing library, but we've put together a few [example pipelines]({{ site.baseurl }}/workflows) for you.

## Contributing

First please read [code of conduct](https://github.com/ibest/HTStream/blob/master/CODE_OF_CONDUCT.md).

If you encounter any bugs or have suggestions for improvement, please post them to [issues](https://github.com/ibest/HTStream/issues).

We'd love to accept code and/or application additions! If your interested in contributing please read our [contributing guidelines](https://github.com/ibest/HTStream/blob/master/CONTRIBUTING.md).





Thanks for using HTStream!
