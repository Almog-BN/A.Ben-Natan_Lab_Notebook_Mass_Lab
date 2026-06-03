--- 
layout: post
title: "Primer Design and Phylogenetic Analysis of Nori (*Pyropia yezoensis*) Using the *rbcL* Gene"
author: "Almog Ben Natan"
---

# Primer Design and Phylogenetic Analysis of Nori (*Pyropia yezoensis*) Using the *rbcL* Gene

## Objective

The objective of this work was to practice a basic bioinformatics workflow for algal species identification. The workflow included collecting DNA sequences from NCBI, performing multiple sequence alignment, identifying conserved and variable regions, designing primers, checking primer specificity, and constructing a phylogenetic tree.

## Target Organism

The selected target organism was nori, *Pyropia yezoensis*, a red alga commonly used as an edible seaweed.

## Gene Region

The selected gene region was the chloroplast *rbcL* gene, which encodes the large subunit of ribulose-1,5-bisphosphate carboxylase/oxygenase.

The *rbcL* gene is commonly used as a barcode marker in algae and plants because it is conserved enough to allow primer design, but it also contains variable sites that can help distinguish between closely related taxa.

## NCBI Accession Numbers

The following *Pyropia yezoensis rbcL* sequences were downloaded from NCBI:

1. MN561425.1
2. MN561424.1
3. MN561423.1

## FASTA Sequence Source Information

1. <https://www.ncbi.nlm.nih.gov/nuccore/MN561425.1?report=fasta>
2. <https://www.ncbi.nlm.nih.gov/nuccore/MN561424.1?report=fasta>
3. <https://www.ncbi.nlm.nih.gov/nuccore/MN561423.1?report=fasta>

## Multiple Sequence Alignment

The sequences were aligned using ClustalW. The sequence type was DNA.

![Multiple sequence alignment output](![alt text](image.png)

## Conserved Regions Identified

Most positions in the aligned *rbcL* sequences were identical among the three samples. These conserved regions indicate high sequence similarity within the selected *Pyropia yezoensis* samples.

![Multiple sequence alignment output](https://github.com/Almog-BN/A.Ben-Natan_Lab_Notebook_Mass_Lab/blob/master/images/HW/%D7%A6%D7%99%D7%9C%D7%95%D7%9D%20%D7%9E%D7%A1%D7%9A%202026-06-02%20105805.png?raw=true)
## Variable Regions Identified

A small number of variable sites were identified in the alignment. These variable positions represent single nucleotide polymorphisms (SNPs) among the analyzed sequences.

![Multiple sequence alignment output](![!\[alt text\](image.png](https://github.com/Almog-BN/A.Ben-Natan_Lab_Notebook_Mass_Lab/blob/master/images/HW/%D7%A6%D7%99%D7%9C%D7%95%D7%9D%20%D7%9E%D7%A1%D7%9A%202026-06-02%20105320.png?raw=true)

Because all three sequences belong to *Pyropia yezoensis*, the level of sequence variation was low. Therefore, the alignment is useful for practicing the method, but it provides limited phylogenetic resolution compared with an analysis that includes several different but related species.

## Primer Design

Primers were designed using Primer3.

### Primer3 Results

- Template masking: not selected
- Mispriming library: not specified
- Sequence size: 1152 bp
- Included region size: 1152 bp
- Coordinate system: 1-based sequence positions

| Primer | Start | Length | Tm (°C) | GC% | Hairpin | Sequence |
|---|---:|---:|---:|---:|---:|---|
| Forward / Left primer | 575 | 20 | 58.90 | 50.00 | 0.00 | `GTATGGCAATTTGGGCTCGT` |
| Reverse / Right primer | 738 | 20 | 58.66 | 50.00 | 0.00 | `ACCTACAACTGTACCTGCGT` |

### Selected Primer Pair

| Parameter | Value |
|---|---|
| Forward primer | `GTATGGCAATTTGGGCTCGT` |
| Reverse primer | `ACCTACAACTGTACCTGCGT` |
| Primer length | 20 bp |
| Forward primer Tm | 58.90°C |
| Reverse primer Tm | 58.66°C |
| GC content | 50% |
| Primer position in sequence | Forward: 575; Reverse: 738 |

## Primer-BLAST Specificity Results

The selected primer pair was checked using NCBI Primer-BLAST. The specificity result showed that the primer pair was specific to the input template, with no additional targets found in the selected database.

Result summary:

> Primer pairs are specific to input template.

## Phylogenetic Tree Construction

A phylogenetic tree was constructed using MEGA.

![MEGA phylogenetic tree](https://github.com/Almog-BN/A.Ben-Natan_Lab_Notebook_Mass_Lab/blob/master/images/HW/%D7%A6%D7%99%D7%9C%D7%95%D7%9D%20%D7%9E%D7%A1%D7%9A%202026-06-02%20114320.png?raw=true)

## Tree-Building Parameters

| Parameter | Setting |
|---|---|
| Software | MEGA |
| Alignment method | ClustalW |
| Tree-building method | Neighbor-Joining |
| Sequence type | DNA / nucleotide sequences |
| Bootstrap analysis | Not performed |

## Interpretation of the Tree

The phylogenetic analysis grouped MN561425.1 and MN561424.1 together, indicating higher sequence similarity between these two samples. MN561423.1 formed a separate branch and appears slightly more divergent within the analyzed *rbcL* region.

Since all analyzed sequences belong to *Pyropia yezoensis*, the tree reflects variation within the same species rather than relationships among different algal species. Therefore, the tree is suitable for practicing the workflow, but a stronger phylogenetic analysis would require additional related species.

## Summary

This workflow demonstrated the main steps of algal molecular identification and phylogenetic analysis: sequence collection from NCBI, multiple sequence alignment, identification of conserved and variable regions, primer design using Primer3, primer specificity testing with Primer-BLAST, and tree construction using MEGA.
