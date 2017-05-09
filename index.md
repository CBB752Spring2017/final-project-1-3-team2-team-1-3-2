---
layout: page
title: CBB752 Spring 2017
tagline: Final Project
---

Project 1.3: Analyzing the Protein Coding Mutations in the Zimmerome
------------------


Table of Contents
-----------------------




**Contributors**
 -Writing: Ramya
 -Coding: Nir
 -Pipeline: Megan

### Introduction: What is Variant Prioritization?
Since the advent of rapid and cheap whole genome sequencing technologies, we have amassed a large diverse collection of human genomes. Interpreting this large amount of data is still challenging, and one such challenge is understanding the function of single nucleotide variations (SNVs) that often arise in individual genomes compared to reference sets which also include many single nucleotide polymorphisms (SNPs). Specifically, identifying pathogenic or deleterious mutations compared to common background mutations is a key challenge. Often, deleterious mutations are non-synonymous, meaning that they result in the change of one amino acid to another. The average individual has over 10 million SNPs in the whole genome, about 20,000 of which are in the exome or the protein-coding portion of the genome. Of course, not all of these are deleterious - the number of potentially deleterious mutations in the exome often amounts to about several hundred (1)(2). This problem of identifying relevant disease-causing mutations or variants compared to common mutations is called variant prioritization.

Here, we aim to prioritize variants in the exome of subjectZ. SubjectZ has 22,981 exome SNVs of which 1,800 are rare SNVs (4). Furthermore, of these rare SNVs, 1,018 were found to be nonsynonymous. Both a denovo approach and existing tools such as SIFT, PolyPhen, and Provean. The methodology used to prioritize SNVs in the denovo tool will be explained and compared to those used in other approaches. The results of our tool and those from the mentioned tools are detailed in the Pipeline and Coding sections of this text.





### Writing:
#### The Inputs Required for Variant Prioritization Tools
   The output of an alignment of one individual’s genome to a reference is often a Variant Call Format file. This file contains not only information about mutations in the nucleotide sequence compared to the reference, but also important metadata regarding the quality of the alignment, and other important properties that can allow for further sub-classification (3). In our analysis, we have a paired down VCF text file containing the following information. 
   
  insert image.
  
Perhaps the only non-self explanatory field is the GERP score which “measures evolutionary conservation of genetic sequence across species” (5). A higher score means that sequence is more conserved and variation is rarer and potentially more adverse. All of this information is parsed for prioritization.
#### Principles for Variant Prioritization
Ideally, variant prioritization employs several orthogonal pieces of data to effectively classify SNVs. I will discuss some commonly used parameters in variant prioritization and their significance. 
   
*Sequence Information:*

Obviously, the nucleotide sequence information is used, namely to assess any mutations in amino acid. Synonymous mutations as mentioned are often harmless as they result in the same amino acid at the position. However, codon frequency can sometimes cause problems if the new codon does not have enough anti-codon charged tRNAs for effective protein synthesis. Non-synonymous mutations become more harmful as the amino acid substituted is more divergent in size and charge.
   
*Conservation and Position:*

Considering the conservation and position of SNVs is also important. Mutations in the hydrophobic core are often rarer as these regions tend to be more well-conserved. A common hypothesis is that mutating conserved regions has a greater risk of deleteriousness. The reason rare SNVs are more likely to be deleterious is because others have been eradicated from the population due to intolerance – probably because the mutation was a well-conserved region. Using structure prediction software such as TMHMM, and Phyre2 to see whether the mutated amino acid is in a conserved internal secondary structure, active site, or membrane could give further insight into the effect size of the mutation (7).
   
   This does not exclude common variants from the search as there are many examples of common variants that influence well-known diseases such as breast cancer. The GERP score can be used to evaluate conservation in the case of SubjectZ.
   
*Phenotypic Information and Prior Knowledge:*

Existing information about the mutation can be accessed such as any existing information regarding the SNVs involvement in characterized diseases. This phenotypic information can be mined using the position of the SNV and/or the provided protein sequences. For example, finding the BRCA SNV alone (which occurs about 3% of the population on average) may not have given it as high a priority as other rare SNVs, but armed with existing information about its critical role in breast cancer would lead to higher prioritization. Gene Ontology terms are good starting points for this type of information as well as SWISS-PROT entries. Considering whether the SNV was previously identified in the 1000 Genome project or in the dsSNPs database and checking these entries might provide further insights into the deleteriousness of the mutation.
  
*Other genetic factors:*

All humans have two alleles of a given gene. Most often, only when both alleles are mutated, i.e. when the individual is homozygous for the mutation, does the disease phenotype arise. In some cases haploinsufficiency may arise, when the individual does have one functioning copy but it is not producing enough gene product for normal function. Checking whether the SNV identified is in only one or both alleles can help prioritize the mutation.
	 
Ideally, gene information, variant information such as GERP scores, and phenotype information if any can be compiled and used with machine learning for optimal results (6).

#### *De novo* Variant Prioritization Tool for SubjectZ
Below is an overview of the Variant Prioritization Tool constructed by Nir.

![alt text][logo]

[logo]: https://github.com/CBB752Spring2017/final-project-1-3-team2-team-1-3-2/blob/master/13flowchart.png =250x


#### Comparison of *de novo* Tool and Common Variant Prioritization Tools like SIFT and PolyPhen








### Coding:


#### Documentation:


#### Results:







### Pipeline:


#### Documentation:


#### Results:









#### Conclusions:








#### References:

 References can be included here or at the end of each relevant section.
 
 
