---
layout: post
title: "exRNA Atlas: Publication in Cell"
author: James Diao
date: 2019-04-04
location: New Haven, CT
categories: Research
excerpt: Publication of my work in Gerstein Lab on the exRNA Atlas (dimensionality reduction, visualization, and deconvolution)
images:
  - url: /img/0-exrna-deconvolution.png
---


### tl;dr 
As part of the [Gerstein Lab](/research/gerstein-lab) at Yale, I contributed to a large multi-institutional effort to document and catalog the variety of exRNA molecules found in human biofluids. My main contribution was a dimensionality reduction and visualization tool that the consortium used for quality control and hypothesis generation. Our work was published just today, more than 5 years after the consortium was founded, and more than 3 years after I started working on it. 

> Murillo OD, Thistlethwaite W, Rozowsky, J, Subramanian SL, Lucero R, Shah N, Jackson AR, Srinivasan S, Chung A, Laurent CD, Kitchen RR, Galeev T, Warrell J, **Diao JA**, Welsch JA, Hanspers K, Riutta A, Burgstaller-Muehlbacher S, Shah R, Yeri A, Jenkins L, Ahsen ME, Cordon-Cardo C, Dogra N, Gifford SM, Smith JT, Stolovitzky G, Tewari AK, Wunsch BH, Yadav KK, Danielson KM, Filant J, Moeller C, Nejad P, Paul A, Simonson B, Wong DK, Zhang X, Balaj L, Gandhi R, Sood AK, Alexander RP, Wang L, Wu C, Wong D, Galas DJ, Van Keuren-Jensen K, Patel T, Jones JC, Das S, Cheung K, Pico AR, Su AI, Raffai RL, Laurent LC, Roth ME, Gerstein MB, Milosavljevic A. "ExRNA Atlas analysis reveals distinct extracellular RNA types and their carriers present across human biofluids." *Cell*. 4 Apr 2019. [https://doi.org/10.1016/j.cell.2019.02.018](https://www.cell.com/cell/fulltext/S0092-8674(19)30167-9).

<img src="/img/exrna-atlas-title.png" alt="exRNA Atlas Header" title="exRNA Atlas Header" style="width:700px;height:267px;">  


### Non-technical summary

Our bodily fluids (e.g., blood, urine, etc.) contain many different molecules that can be used to diagnose and track disease. Most non-invasive diagnostic tests--from pregnancy tests to cancer biomarkers--look for abnormal levels of specific proteins. More recently, scientists have discovered that another type of molecule, exRNA, can also be measured from fluid samples for diagnostic purposes. To help standardize the study of exRNA, the NIH put together a consortium--the Extracellular RNA Communication Consortium (ERCC). 

A primary goal for the ERCC was to create a catalog of exRNA molecules found in human biofluids, like blood, saliva, and urine. The resulting data, consisting of >50,000 samples from >2,000 donors across 13 different biofluids, was uniformly processed through a pipeline that our lab developed (our [paper](/research/excerpt) on this came out today too!) and compiled into the exRNA Atlas. 

This paper aims to describe the suite of data resources and analysis tools available in the exRNA Atlas, and to demonstrate how they can be used to better understand exRNA sequencing data. To accomplish the second aim, the Atlas resource was used to develop a model for explaining variability between exRNA profiles in terms of the cargo types found in each sample (i.e., which carriers are helping to shuttle the exRNAs around). The hope is that modeling these sources of variation can help us better understand our data, and that correcting for them can improve statistical power and decrease false positives for studies that aim to demonstrate clinical correlations. 

