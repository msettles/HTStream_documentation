---
title: Output JSON statistics
order: 3
suborder: 2
---

# Output JSON File of Statistics

HTStream uses a JSON formated file for its output log of sample/read processing
statistics. The following options (within the standard options section), control
the behavior of output of the JSON file:

<br>

| Parameter | Description | Default |
| :--- | :--- | :--- |
|  -L [ --stats-file ] |  Write to stats file name | stats.json |
|  -A [ --append-stats-file ] |    Append to stats file name | |

<br>

The `--stats-file=file` option creates (or overwrites) a file for JSON output. This
parameter is most often used in the first application of the preprocessing stream and will
start a new JSON log. `--append-stats=file` will append the JSON output to the
specified file. This assumes that the specified file already has at least 1 JSON
output present, otherwise a non-valid JSON file will be created. This parameter is most
often used in the second through final applications of the preprocessing stream in order
to generate a single JSON ouput file for the sample/reads.

## JSON file format

The JSON file is an array of ordered objects, where each object value in the
array is a single HTStream application's output statistics log. Each application's
log contains the same following sections: "Program_details", "Fragment", "Single_end",
and "Paired_end"; and then a "Read1" and "Read2" section within "Paired_end".

Each app contains the application name (program), version number (version), and program
options (options) found on the command line in the "Program_details" section.
Also each app has the number of reads input (in) and output (out) for each of
"Fragment", "Single_end", and "Paired_end". Further, each app reports the total basepairs
read in (basepairs_in) and total basepairs read out (basepairs_in) for each of
"Fragment", "Single_end", "Read1", "Read2".

Also all other JSON output is application specific.
