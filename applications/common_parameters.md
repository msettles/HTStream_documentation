---
title: Common Parameters
order: 3
suborder: 1
---

# HTStream common parameters

All HTSteam applications use a common set of parameters for input, output
and standard parameters.

## Parameters
<br>
**Standard Options:**

| Parameter | Description | Default |
| :--- |  :--- | :--- |
|  -v [ --version ] |                       Version print |  |
|  -h [ --help ]     |                       Prints help documentation |  |
|  -N [ --notes ]   |   Notes to be included int the JSON output log | "" |
|  -L [ --stats-file ] |  Write to stats file name (default=stats.log) | stats.json|
|  -A [ --append-stats-file ] |    Append to stats file name |  |

<br>
**Input Options [default: tab6 format on stdin]:**

| Parameter | Description | Default |
| :--- |  :--- | :--- |
|  -1 [ --read1-input ]     |          Read 1 paired end fastq input (space separated for multiple files) | |
|  -2 [ --read2-input ]      |         Read 2 paired end fastq input (space separated for multiple files) | |
|  -U [ --singleend-input ]   |       Single end read fastq input (space separated for multiple files) | |
|  -I [ --interleaved-input ]  |      Interleaved fastq input (space separated for multiple files) | |
| -T [ --tab-input ]          |      Tab-delimited (tab6) input (space separated for multiple files)  | |

<br>
**Output Options [default: tab6 format to stdout]:**

| Parameter | Description | Default |
| :--- |  :--- |  :--- |
|  -F [ --force ]        |                Forces overwrite of files   |   False |
|  -u [ --uncompressed ]  |               Output uncompressed (not gzipped) files   | False |
|  -f [ --fastq-output ]   |         Output to Fastq files (PE AND/OR files)   | |
|  -i [ --interleaved-output ] |      Output to interleaved fastq files (INTERLEAVED PE AND/OR SE files)  | |
|  -t [ --tab-output ]  |            Output to tab-delimited (tab6) file |   |
|  -z [ --unmapped-output ]  |         Output to unmapped sam file  | |
