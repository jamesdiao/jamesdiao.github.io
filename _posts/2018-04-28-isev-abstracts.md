---
layout: post
title: "Abstracts in the Journal of Extracellular Vesicles"
date: 2018-04-28
author: James Diao
location: New Haven, CT
categories: Research
excerpt: Comprehensive atlas of human exRNAs and the ERCC's exRNA-Seq analysis tools 
image: /img/0-isev-abstracts.png
---


Over the past four years in the <a href="/research/gerstein-lab">Gerstein Lab</a>, I've poured a lot of time into two main projects under the NIH Extracellular RNA Communications Consortium. One of the main groups involved in this effort, the International Society for Extracellular Vesicles, just held their annual meeting in May. In the months before, we briefly wrote up both projects and my mentor traveled to Barcelona to present them. Just before the meeting, I was excited to see that the [two abstracts](https://www.tandfonline.com/doi/full/10.1080/20013078.2018.1461450) were published in *the Journal of Extracellular Vesicles*. Both are currently being drafted as full-length manuscripts; fingers crossed that they go through smoothly!   


<br>
<img src="/img/ISEV-logo.jpg" alt="ISEV Logo" title="ISEV Logo" class="img-responsive" style="width:400px;height:auto;">  

### PT03.10 The extracellular RNA-Seq processing pipeline of the Extracellular RNA Communication Consortium

Joel Rozowsky<sup>1</sup>; Robert R. Kitchen<sup>2</sup>; Jonathan Park<sup>1</sup>; Timur Galeev<sup>1</sup>; James A. Diao<sup>1</sup>; Jonathan Warrell<sup>1</sup>; William Thistlethwaite<sup>3</sup>; Sai L. Subramanian<sup>3</sup>; Aleksandar Milosavljevic<sup>3</sup>; Mark B. Gerstein<sup>1</sup>

*<sup>1</sup>Department of Molecular Biophysics & Biochemistry, Yale University, New Haven, USA*  
*<sup>2</sup>Exosome Diagnostics, Boston, USA*  
*<sup>3</sup>Department of Molecular & Human Genetics, Baylor College of Medicine, Houston, USA*

**Background:** We will present the tools of the Extracellular RNA Communication Consortium that have been developed for the analysis of extracellular RNA-Seq data and have been used in the construction of a comprehensive atlas of exRNAs in human body fluids. Due to the process of extracting, purifying and sequencing of RNA from extracellular biofluids, exRNAs are more vulnerable to contamination than cellular RNA samples. To address this, we have developed the extracellular RNA processing tool (exceRpt), optimized for the analysis of exRNA-seq data.

**Methods:** This involves three steps: (1) pre-processing: support for random-barcoded libraries, spike-in sequences for calibration or titration, and explicit removal of common laboratory contaminants and ribosomal RNAs. (2) Endogenous processing: alignment and quantitation of the full set of annotated, potentially spliced, endogenous RNA transcripts including all known miRNAs, tRNAs, piRNAs, snoRNAs, lincRNAs, mRNAs, retrotransposons and circular RNAs. (3) Exogenous processing: alignment to annotated exogenous miRNAs in miRBase and exogenous rRNA sequences in the RDP and alignments to the full genomes of all sequenced bacteria, viruses, plants, fungi, protists, metazoa and selected vertebrates.

**Results:** We have developed a novel algorithm for characterizing alignments to all available exogenous genomes in terms of the NCBI taxonomy tree. Existing approaches that remove degenerate sequences (i.e. those that co-occur across multiple species) result in a loss of potentially valuable data as the occurrence of reads aligning to multiple species/strains is very frequent. This is done independently for exogenous reads aligning to exogenous rRNA as well as exogenous genome sequences.

**Summary/Conclusion:** The exceRpt pipeline (available at genboree.org and github.gersteinlab.org/exceRpt) generates a variety of sample-level quality control metrics, produces abundance estimates for various RNA biotypes, including detailed reports of this processing. The exceRpt pipeline (including endogenous and exogenous processing steps) has been used to uniformly process all ~2500 exRNA-Seq data sets that are in the ERCC exRNA Atlas (exrna-atlas.org). We will also present the quality control metrics as applied to the current available extracellular RNA-Seq data sets of the ERCC in the exRNA Atlas.


<br>

### OS27.06 ExRNA Atlas analysis provides an exRNA census and reveals six types of vesicular and non-vesicular exRNA carrier profiles detectable across human body fluids

Oscar D. Murillo<sup>1</sup>; William Thistlethwaite<sup>1</sup>; Rocco Lucero<sup>1</sup>; Sai Lakshmi Subramanian<sup>1</sup>; Neethu Shah<sup>1</sup>; Andrew R. Jackson<sup>1</sup>; Joel Rozowsky<sup>2</sup>; Robert R. Kitchen<sup>3</sup>; James Diao<sup>2</sup>; Timur Galeev<sup>2</sup>; Jonathan Warrell<sup>2</sup>; Kristina Hanspers<sup>4</sup>; Anders Riutta<sup>4</sup>; Alexander Pico<sup>5</sup>; Roger P. Alexander<sup>5</sup>; David Galas<sup>5</sup>; Andrew I. Su<sup>6</sup>; Louise C. Laurent<sup>7</sup>; Kendall Jensen<sup>8</sup>; Matthew Roth<sup>1</sup>; Mark B. Gerstein<sup>2</sup>; Aleksandar Milosavljevic<sup>1</sup>

*<sup>1</sup>Department of Molecular & Human Genetics, Baylor College of Medicine, Houston, USA*  
*<sup>2</sup>Department of Molecular Biophysics & Biochemistry, Yale University, New Haven, USA*  
*<sup>3</sup>Exosome Diagnostics, Boston, USA*  
*<sup>4</sup>Gladstone Institutes, San Francisco, USA*  
*<sup>5</sup>Pacific Northwest Research Institute, Seattle, USA*  
*<sup>6</sup>Department of Integrative, Structural and Computational Biology, The Scripps Research Institute, La Jolla, USA*  
*<sup>7</sup>University of California, San Diego, San Diego, USA*  
*<sup>8</sup>Neurogenomics, Translational Genomics Research Institute, Phoenix, USA*

**Background:** To gain insights into exRNA communication, the NIH Extracellular RNA Communication Consortium created the Extracellular RNA Atlas including 5309 exRNA-seq and qPCR profiles, most obtained from five body fluids (cerebrospinal fluid, saliva, serum, plasma, urine).

**Methods:** Extensive metadata, uniform processing and standardized data quality assessments facilitated integrative analysis of miRNA, tRNA, Y RNA, piRNA, snRNA, snoRNA and lincRNA abundance across 21 data sets represented in the Atlas. A computational deconvolution method was applied to infer ncRNA profiles of specific exRNA carriers (vesicular or not) and to estimate relative amounts of exRNA contributed to each Atlas sample by the carriers.

**Results:** We obtain a census of ncRNAs that includes, among others, 96 miRNAs abundantly detected (>10 RPM) in CSF, saliva, serum, and plasma, of those, 46 are detected in all five fluids, including urine. Deconvolution of ncRNA profiles reveals six major carrier types and a striking amount of their sample-to-sample abundance variability. In contrast, highly concordant exRNA profiles of all six carrier types can be detected across different studies and biofluids. Three (LD and HD exosomes and HDL particles) of the six were previously purified and profiled. We define three new carrier profiles, ABF, CP and XSA, that are yet to be profiled in isolation and carry miRNAs in higher abundance than the LD, HD and HDL. All six carrier profiles are detected across body fluids, with ABF and HD exosome profiles detected in all five body fluids; XSA and LD exosome profiles in all except saliva; CP in CSF and plasma; and HDL particle profiles in plasma and saliva. We demonstrate the potential of this knowledge and methodology to improve interpretation of individual case–control studies by reducing variance due to sample-to-sample variation in carrier abundance and by assigning differential (cases vs. controls) abundance of specific small ncRNAs to specific carrier types.

**Summary/Conclusion:** ExRNA Atlas analysis yields global insights into vesicular and non-vesicular exRNA communication by combining and deconvoluting data across multiple studies.  

> For context, last year's analysis count be found in [ISEV's 2017 Abstract Book](https://www.tandfonline.com/doi/full/10.1080/20013078.2017.1310414). The exRNA Atlas went from 12 studies to 21, and from 1567 exRNA profiles up to 5309! As of June (1 month later), the number increased again to 5750. Progress :)

