---
layout: post
title: "The Exploding Data Requirements of Pure Probabilistic Reasoning"
author: James Diao
date: 2019-03-17
location: Boston, MA
categories: Projects
excerpt: Modeling the Bayesian reasoning's "voracious demand for data."
images:
  - url: /img/0-data-demand.png
---

<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.2/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
  tex2jax: {inlineMath: [['$','$'], ['\\(','\\)']]}
});
</script>

### tl;dr 
Bayesian probabilistic inference is optimal under ideal circumstances, but can (depending on your assumptions) demand a LOT of conditional probability data. 
> [https://manrai.shinyapps.io/PureProbabilisticReasoning/](https://manrai.shinyapps.io/PureProbabilisticReasoning/)

### Background

I built this app as a TA for a data science class at Harvard (BMI 704: Data Science for Medical Decision-Making). The course directors, Chirag Patel and Arjun Manrai, wanted to demonstrate some key points from Szolovits and Pauker's seminal 1978 paper ("Categorical and Probabilistic Reasoning in Medical Diagnosis").  

#### Parameterizing Probabilistic Reasoning
This paper described medical reasoning as lying between two extremes of a continuum: from purely categorical (e.g., a flowchart) to purely probabilistic (e.g., Bayes' rule). The number of parameters required for the latter (a purely probabilistic decision system) can be computed from three parameters: the number of hypotheses to test (n), the number of tests (m), and the number of possible results per test (r). 

\\[ \text{If test order matters:   # parameters = } \; n \sum_{i=1}^m r^i \cdot {}_m P_i \\]

\\[ \text{If test order is ignored:   # parameters = } \; n \sum_{i=1}^m r^i \cdot {}_m C_i \\]

\\[ \text{If conditional dependence is ignored:  # parameters = } \; nmr \\]

By eyeballing the equations and toggling a few parameters, we can see that the result depends most heavily on the number of tests. But to really get a sense of the scale, it helps to explore some numbers from an actual clinical application. 

#### Case Study: Cardiomyopathy Gene Panel

> The LMM (a molecular diagnostic laboratory operated by Harvard Medical School's teaching hospitals) offers a [panel test](https://personalizedmedicine.partners.org/Laboratory-For-Molecular-Medicine/Tests/Cardiomyopathy/PanCardiomyopathy-Panel.aspx) of 62 genes to detect and distinguish between cardiac conditions: hypertrophic cardiomyopathy (HCM), dilated cardiomyopathy (DCM), arrhythmogenic cardiomyopathy, and left ventricular non-compaction (LVNC). Let's say that we discovered an abnormal heart on echocardiogram and want to build a probability distribution over our differential.  
> 
> In this situation, we have 5 hypotheses (1 for each disease condition + 1 for healthy), 62 tests, and 2 possible results per test (positive/pathogenic and negative/benign). This gives us parameter values of n=5, m=62, and r=2. Plugging in these numbers, we find that our model requires >10<sup>105</sup> conditional probability values: more than the number of atoms in the observable universe!  

Luckily, we can make some assumptions to improve the situation. Ignoring test order (a perfectly reasonable assumption for genetics) brings the numbers down to 10<sup>30</sup>: still unimaginably large. Ignoring conditional dependence, on the other hand, pushes it down to just 2 Kb (at the cost of any semblence of clinical utility). 

### Takeaways

This case study only addresses testing 62 genes for 5 cardiac conditions. With the rise of direct-to-consumer genomics and rapidly ballooning panel tests for genetic testing, the values for n, m, and r will continue to increase. The NIH Genetic Testing Registry has catalogued 59,226 tests for 11,508 conditions over 18,602 genes. Explicit probabilistic modeling just doesn't scale well to many of these data-hungry medical applications. 

While this type of probabilistic modeling is unlikely to be useful in real-world practice, there are plenty of statistical learning methods that have achieved phenomenal performance on medical tasks by estimating underlying (and less explosively high-dimensional) representations of data. And beyond its applications in AI, probabilistic inference is crucial for clinicians as well. Important principles of Bayesian reasoning, such as the nature of conditioning and the importance of prior probabilities, likely deserve an increased role in medical education (see [Medicine's Uncomfortable Relationship with Math](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4955674/)). 


### Shoutouts from Twitter!

<img src="/img/ppr-post-1.png" alt="Raj Twitter Post" title="Raj Twitter Post" style="width:350px;">
<img src="/img/ppr-post-2.png" alt="Zak Twitter Post: All" title="Zak Twitter Post" style="width:350px;">
<img src="/img/ppr-post-3.png" alt="Raj Twitter Comments" title="Raj Twitter Comments" style="width:350px;">


<!-- dynamically load mathjax for compatibility with self-contained -->
<script>
  (function () {
    var script = document.createElement("script");
    script.type = "text/javascript";
    script.src  = "https://mathjax.rstudio.com/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML";
    document.getElementsByTagName("head")[0].appendChild(script);
  })();
</script>

