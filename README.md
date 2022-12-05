# Allele similarity cluster Germline set files

The files in this archive describe the germline set of the allele similarity cluster (ASC) method for human IGHV germline set  downloaded from IMGT site on July 2022.

## Germline processing

The downloaded human IGHV IMGT germline set is processed to include only functional alleles, those who start from the first nucleotide of the 5' region, and are at least 318 nucleotide long. The remaining sequences are trimmed to position 318 (IMGT numbering), the levenshtein distance between sequence pairs is computed and the resulting matrix is clustered with complete linkage. The resulting hierarchical clustering tree is then cut under 0.25 and 0.05 to reflect the family and group level clustering.

## ASC naming scheme

The ASC naming scheme is as follows:

IGHVF1-G1*01

- IGHV - is the chain and segment
- F[number] (F1) - is the assigned ASC family number
- G[number] (G1) - is the assigned ASC cluster number
- \*[number] (\*01) - is the allele number

## Reference set amplicon length

Even though, we wish that all repertoires data available will cover the entire V region this is not always the case. Hence, the ASC will be adapted to fit partial V coverage libraries.

| Library amplicon length | Coverage                                | Similar known protocol |
|--------------------|--------------------------------|--------------------|
| S1                      | Full length - 1 to 318 (IMGT numbering) | 5' Race                |
| S2                      | Starting within the framework 1 region  | BIOMED-2               |
| S3                      | End of the V region                     | Adaptive               |

## Files

### asc_hclust_tree.txt

This file includes the IGHV germline set clustering dendrogram.

The file is saved in newick format. In R the file can be read as so:

```
library(ape)
h <- ape::read.tree(file='asc_hclust_tree.txt')
```

### asc_IGHV_dendrogram.pdf

The dendrogram of the IGHV germline set, based on complete linkage. 

### asc_cluster_cut.tsv

This file shows the ASC clusters by the cutting the trees to heights 0.05 for the clusters and 0.25 for the families

The table columns:

- `allele` - the original IUIS/IMGT allele name
- `ASC_Cluster_0.05` - the ASC cluster number
- `ASC_Family_0.25` - the ASC family number


### asc_alleles_table.tsv

This file includes the ASC names for the IUIS/IMGT alleles of the IGHV germline set (July 2022).

The table columns:

- `new_allele` - the ASC given allele name
- `func_group` - the ASC cluster number
- `imgt_allele` - the original IUIS/IMGT allele name
- `thresh` - the allele threshold for ASC-based genotype inference
- `amplicon_length` - is the original length of the reference set.

