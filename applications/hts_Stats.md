---
title: hts_Stats
order: 3
suborder: 12
---

# hts_Stats: Sequence statistics

The hts_Stats program computes read statistics, such as number of reads and
basepaires, read lengths, quality scores, and base compostion for the input files.

## Usage

```bash
hts_Stats --help
```

## Command Line Parameters

[Common Parameters Plus](common_parameters)

<br>
**Application Specific Options:**

| Parameter | Description | Default |
| :--- |  :--- | :--- |
| None |   |  |

## JSON Output

```
{
"Program_details": {
    "program": "hts_Stats",
    "version": version used,
    "options": {
        Key:value pair list of options provided on the command line
    }
},
"Fragment": {
    "in": numeric value of total fragments input,
    "out": numeric value of total fragment output,
    "basepairs_in": numeric value of total basepairs input,
    "basepairs_out": numeric value of total basepairs output,
    "base_composition": {
        "A": total number of 'A' bases in fragments,
        "C": total number of 'C' bases in fragments,
        "G": total number of 'G' bases in fragments,
        "T": total number of 'T' bases in fragments,
        "N": total number of 'N' bases in fragments
    }
},
"Single_end": {
    "in": numeric value of total single-end reads input,
    "out": numeric value of total single-end reads output,
    "basepairs_in": numeric value of total single-end basepairs input,
    "basepairs_out": numeric value of total single-end basepairs output,
    "total_Q30_basepairs": numeric value of total Q30 basepairs output,
    "readlength_histogram": [ two column matrix, sequence length by counts ],
    "base_by_cycle": {
        "matrix_type": "dense",
        "matrix_element_type": "int",
        "shape": [#row,#column],
        "row_names": [ "A", "C", "G", "T", "N" ],
        "col_names": [ vector of column names: cycles ],
        "data": matrix of counts per cycle x base,
    "qualities_by_cycle": {
        "matrix_type": "dense",
        "matrix_element_type": "int",
        "shape": [#row,#column],
        "row_names": [ "0", "1", ... , "41", "42" ],
        "col_names": [ vector of column names: cycles ],
        "data": [ matrix of counts per cycle x quality score ]
     }
},
"Paired_end": {
    "in": numeric value of total paried-end reads input,
    "out": numeric value of total paired-end reads output,
    "Read1": {
        "total_basepairs": numeric value of total read 1 basepairs input,
        "total_Q30_basepairs": numeric value of total read 1 basepairs input,
        "readlength_histogram": [ two column matrix, sequence length by counts ],
        "base_by_cycle": {
            "matrix_type": "dense",
            "matrix_element_type": "int",
            "shape": [#row,#column],
            "row_names": [ "A", "C", "G", "T", "N" ],
            "col_names": [ vector of column names: cycles ],
            "data": matrix of counts per cycle x base,
        "qualities_by_cycle": {
            "matrix_type": "dense",
            "matrix_element_type": "int",
            "shape": [#row,#column],
            "row_names": [ "0", "1", ... , "41", "42" ],
            "col_names": [ vector of column names: cycles ],
            "data": [ matrix of counts per cycle x quality score ]
        }
    },
    "Read2": {
        "total_basepairs": numeric value of total read 2 basepairs input,
        "total_Q30_basepairs": numeric value of total read 2 basepairs input,
        "readlength_histogram": [ two column matrix, sequence length by counts ],
        "base_by_cycle": {
            "matrix_type": "dense",
            "matrix_element_type": "int",
            "shape": [#row,#column],
            "row_names": [ "A", "C", "G", "T", "N" ],
            "col_names": [ vector of column names: cycles ],
            "data": matrix of counts per cycle x base,
        "qualities_by_cycle": {
            "matrix_type": "dense",
            "matrix_element_type": "int",
            "shape": [#row,#column],
            "row_names": [ "0", "1", ... , "41", "42" ],
            "col_names": [ vector of column names: cycles ],
            "data": [ matrix of counts per cycle x quality score ]
        }
   }
}
}
```

## Algorithm

None

## Comments

hts_Stats is often used as the first and last applications in any preprocessing
workflow to detail the original and final sequence read statistics. hts_Stats can
be run in between each application in order to better understand the detailed effects
of each application on the input data.
