---
layout: post
title: "Bioinformatics with Gerstein Lab"
date: 2017-08-23
author: James Diao
location: New Haven, CT
categories: Research
excerpt: I built tools to visualize, deconvolute, and classify exRNA-Seq samples
image: /img/0-gerstein-lab.png
featured: true
---

<style TYPE="text/css">
code.has-jax {font: inherit; font-size: 100%; background: inherit; border: inherit;}
</style>
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
    tex2jax: {
        inlineMath: [['$','$'], ['\\(','\\)']],
        skipTags: ['script', 'noscript', 'style', 'textarea', 'pre']
    }
});
MathJax.Hub.Queue(function() {
    var all = MathJax.Hub.getAllJax(), i;
    for(i = 0; i < all.length; i += 1) {
        all[i].SourceElement().parentNode.className += ' has-jax';
    }
});
</script>
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>

<img src="/img/gerstein-exrna-long.jpg" alt="exRNA Image" title="exRNA Image" class="img-responsive" style="width:680px;height:auto;">  

<i><small>Extracellular RNAs (exRNAs) circulate through a range of human body fluids. NIH News Releases, 13 Aug. 2013, https://www.nih.gov/news-events/news-releases/nih-funds-research-explore-cell-communication-process.</small></i>

## tl;dr

#### Non-technical
Our tissues and fluids contain molecules called RNAs. In the past decade, it has become very easy to collect RNA samples in a process called sequencing. To better study these molecules, I built a plotting tool to visualize which RNA samples are similar to each other, and another tool to predict which body tissues have RNAs most similar to those found in a studied sample.  


#### Technical
Using public extracellular RNA (exRNA) sequencing data, we demonstrate that small exRNAs cluster tightly by tissue and biofluid of origin. These patterns are demonstrable as visual patterns on dimensionality-reduced plots and are reasonably separable (by deconvolution) using standard supervised techniques. Further, we show that the miRNAs from related tissues and biofluids share similar signatures and allow for meaningful cross-predictions. The plotting tool is now [hosted on the exRNA Atlas](http://exrna-atlas.org/exat/publicAnalyses), and the deconvolution tool has been integrated into the [exceRpt pipeline](http://genboree.org/theCommons/projects/exrna-tools-may2014/wiki/Small_RNA-seq_Pipeline).  

## Background 

#### Non-technical
Our bodily fluids (e.g., blood, cerebrospinal fluid, urine, etc.) contain many different molecules that can be used to diagnose and track disease. Most non-invasive diagnostic tools--from pregnancy tests to cancer biomarkers--look for abnormal levels of specific proteins. More recently, scientists have discovered that another type of molecule, exRNA, can also be measured from fluid samples for diagnostic purposes. However, measuring exRNA is tricky, and we need to better understand how this data can be mismeasured or misinterpreted before we trust them enough to use in the clinic.  

#### Technical
RNA molecules were once thought to exist only as stable molecules inside cells. However, microarray and RNA sequencing experiments have discovered many classes of RNA in extracellular fluids (exRNA). These molecules are stably present in plasma, cerebrospinal fluid, urine, bile, and saliva, despite the presence of RNase. Since their discovery, exRNAs have been implicated in cell-to-cell communication and a wide variety of diseases. Research efforts have since expanded into identifying patterns associated with tissue states and pathologies. However, reliable progress requires a deeper understanding of the biases and convolutions that underlie exRNA sequencing data.  


#### Relevant Papers
1. [Freedman 2016](https://www.nature.com/articles/ncomms11106). Diverse human extracellular RNAs are widely detected in human plasma. *Nature Communications*. 
2. [Patton 2015](https://www.ncbi.nlm.nih.gov/pubmed/26320939). Biogenesis, delivery, and function of extracellular RNA. *Journal of Extracellular Vesicles*. 
3. [Williams 2013](http://www.pnas.org/content/110/11/4255.long). Comprehensive profiling of circulating microRNA via small RNA sequencing of cDNA libraries reveals biomarker potential and limitations. *PNAS*. 
4. [Creemers 2012](https://www.ncbi.nlm.nih.gov/pubmed/22302755). Circulating MicroRNAs: Novel biomarkers and extracellular communicators in cardiovascular disease. *Circulation Research*. 


## Project 1: Plotting Tool

Visualization of structure for RNA-Seq data shows how samples are distributed and whether similar samples cluster together. Here, we aim to identify potential batch effects and correlations between the read values of different samples. I've embedded a small, sad version of the tool below (may take 5-10 seconds to load). Click [here](https://exrna-atlas.org/genboreeKB/projects/extracellular-rna-atlas-v2/exat/publicAnalysis/ERCC_DimensReduc_Tool/allData_EXCEPT_TPATE1_HEALTHYVSCANCER?dependencyPath=allData_EXCEPT_TPATE1_HEALTHYVSCANCER) for a larger view, or [here](http://exrna-atlas.org/exat/publicAnalyses) to see all the different versions of the tool.  

<iframe src="https://exrna-atlas.org/genboreeKB/projects/extracellular-rna-atlas-v2/exat/publicAnalysis/ERCC_DimensReduc_Tool/allData_EXCEPT_TPATE1_HEALTHYVSCANCER?dependencyPath=allData_EXCEPT_TPATE1_HEALTHYVSCANCER" style="border: none; width: 700px; height: 670px"></iframe>

## Project 2: Deconvolution

Tissue convolution is when different tissues of origin bias a combined RNA-Seq signature. A common model of convolution assumes that the observed RNA expression levels (X) are roughly expressed as a noisy linear combination of tissue proportions (A) and tissue signatures (S). 

This can be expressed as: $\textbf{X} = \textbf{AS} + \varepsilon$.  

Alternatively, for each entry: $ x_{jk} = \sum_{i=1}^N a_{ki} s_{ij} + \varepsilon_{jk} $.  

where: 
- **X** = observed RNA expression levels *(samples v. RNAs)*
- **A** = tissue proportions *(samples v. tissues)*
- **S** = tissue signatures *(tissues v. RNAs)*
- $\varepsilon$ = Gaussian noise

**Our goal is to find the A matrix.** The X matrix is simply the RNA-Seq data, but the S matrix is unknown. Our approach estimates the S matrix by measuring RNA expression levels in pure, cellular tissues. It then uses non-negative matrix factorization (NMF) to estimate the tissue breakdown (A matrix) for any exRNA-Seq input (X matrix). Further details are given in the poster below (Yale Undergraduate Research Symposium, Fall 2015).  


<embed src="/PDF/YURA_Poster_8_29_2015.pdf" width="450" height="300" type='application/pdf'>


## Other Contributions: Quality Control Metrics

Part of the Gerstein Lab's work with the Extracellular RNA Communications Consortium is developing rigorous standards for analysis of exRNA data. As an offshoot of the data visualization project, we were able to justify objective standards to exclude samples with DNA contamination and/or low read counts. 

<embed src="/PDF/Rozowsky_Poster_ISEV_2016.pdf" width="450" height="300" type='application/pdf'>


## Data Description
**exRNA Atlas**: Small RNA and RT-qPCR exRNA sequencing profiles from human biofluids were collected from the exRNA Atlas, the central data repository of the Extracellular RNA Communication Consortium (ERCC). The total dataset is 3,290 mapped small RNA reads vs. 2,267 samples. Individual samples are labeled with disease condition and biofluid source.  

**Sequence Read Archive**: Small RNA sequencing profiles from human tissues were collected from the Sequence Read Archive (SRA), the NIH's primary archive for high-throughput sequencing data. The total dataset is 1,804 mapped small RNA reads vs. 201 samples. Individual samples are labeled with healthy/perturbed condition and tissue of origin.  