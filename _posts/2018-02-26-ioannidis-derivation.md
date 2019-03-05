---
layout: post
title: "Why Most Published Research Findings Are False"
author: James Diao
date: 2018-02-26
location: New Haven, CT
categories: Research
excerpt: Discussion and derivation of Ioannidis' theoretical framework
images:
  - url: /img/confusion_matrix_1.png
---

<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.2/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
  tex2jax: {inlineMath: [['$','$'], ['\\(','\\)']]}
});
</script>

One of the first papers that my mentor at HMS assigned to me was entitled: ["Why Most Published Research Findings Are False"](http://journals.plos.org/plosmedicine/article?id=10.1371/journal.pmed.0020124). I was caught by surprise---it sounded like the poorly informed doubting of a conspiracy theorist, rather than the most cited paper in PLoS Medicine, written by the legendary Stanford epidemiologist [John Ioannidis](https://en.wikipedia.org/wiki/John_Ioannidis). 

The paper itself is incredibly to-the-point, almost brash. It begins: 
> Published research findings are sometimes refuted by subsequent evidence, with ensuing confusion and disappointment. Refutation and controversy is seen across the range of research designs, from clinical trials and traditional epidemiological studies [1–3] to the most modern molecular research [4,5]. There is increasing concern that in modern research, false findings may be the majority or even the vast majority of published research claims [6–8]. However, this should not be surprising. It can be *proven* that most claimed research findings are false.

How does one even begin to prove such a claim? The simplest approach would be to actually replicate representative experiments one-by-one, and other scientists actually do this in later papers. But in this article, Ioannidis approaches the issue from a statistical standpoint. Here's where it gets interesting. 

## 1. Overview

Ioannidis explores the reliability of research findings in terms of positive predictive value (PPV)---the probability that a finding is actually true, given that it is claimed to be true. 

\\[ PPV = \frac{P(\textrm{Claimed True and Actually True})}{P(\textrm{Claimed True})} \\]

Using basic probability theory, we can derive an expression for PPV in terms of well-defined and estimable parameters: power (1-*&beta;*), significance level (*&alpha;*), bias (*u*), number of studies (*n*), and pre-study odds (*R*). 

\\[ PPV = \frac{R(1-\beta')}{R(1-\beta') + \alpha'} \\]

where, if you account for bias and multiple studies under a few assumptions:

\begin{align}
\beta' &= (1-u)^n \beta^n  \\\
\alpha' &= 1 - (1-u)^n(1-a)^n
\end{align}

*(The derivation of the above expressions are given in parts 3-4 of this post.)*  
This expression allows you to do two things: estimate PPV for different study designs, and model how it changes as a function of external factors. 

### 1.1 Estimation of PPV for Different Study Designs 

<b>Table 4: PPV of Research Findings for Various Combinations of <br>Power (1 − <i>&beta;</i>), Ratio of True to Not-True Relationships (<i>R</i>), and Bias (<i>u</i>)</b>

<table class="table table-striped">
  <tr>
    <th>Power (1-<i>&beta;)</i><br></th>
    <th>Ratio (<i>R</i>)<br></th>
    <th>Bias (<i>u</i>)<br></th>
    <th>Study Example<br></th>
    <th>PPV</th>
  </tr>
  <tr>
    <td>0.80</td>
    <td>1:1</td>
    <td>0.10</td>
    <td>Well-designed RCT <br></td>
    <td><font color="green">0.85</font></td>
  </tr>
  <tr>
    <td>0.95</td>
    <td>2:1</td>
    <td>0.30</td>
    <td>Confirmatory meta-analysis (well-designed RCTs)<br></td>
    <td><font color="green">0.85</font></td>
  </tr>
  <tr>
    <td>0.80</td>
    <td>1:3</td>
    <td>0.40</td>
    <td>Corrective meta-analysis (small inconclusive studies)<br></td>
    <td><font color="orange">0.41</font></td>
  </tr>
  <tr>
    <td>0.20</td>
    <td>1:5</td>
    <td>0.20</td>
    <td>Phase I/II RCT (underpowered, unbiased)<br></td>
    <td><font color="orangered">0.23</font><br><br></td>
  </tr>
  <tr>
    <td>0.20</td>
    <td>1:5</td>
    <td>0.80</td>
    <td>Phase I/II RCT (underpowered, high bias)<br></td>
    <td><font color="orangered">0.17</font></td>
  </tr>
  <tr>
    <td>0.80</td>
    <td>1:10</td>
    <td>0.30</td>
    <td>Exploratory epidemiological study (well-powered)<br></td>
    <td><font color="orangered">0.20</font></td>
  </tr>
  <tr>
    <td>0.20</td>
    <td>1:10</td>
    <td>0.30</td>
    <td>Exploratory epidemiological study (underpowered)<br></td>
    <td><font color="orangered">0.12</font></td>
  </tr>
  <tr>
    <td>0.20</td>
    <td>1:1000</td>
    <td>0.80</td>
    <td>Discovery research with massive testing<br></td>
    <td><font color="red">0.0010</font></td>
  </tr>
  <tr>
    <td>0.20</td>
    <td>1:1000</td>
    <td>0.20</td>
    <td>Same as above, but standardized (lower bias)<br></td>
    <td><font color="red">0.0015</font></td>
  </tr>
</table>
*Note: significance level is assumed to be &alpha; = 0.05 for any single study; PPV values do not account for study multiplicity.*  

Ioannidis does not describe how he arrived at his estimates for power, bias, and pre-study odds, and one might disagree on these numbers. However, given the popularity of this article, the scientific community seems to agree with these conclusions. Real-world studies might be more or less predictive, but achieving a PPV of over 50% is quite challenging in Ioannidis's model, and would be even more challenging once study multiplicity is accounted for. 

<br> 

### 1.2 Modeling PPV as a Function of External Factors 

Power decreases as you move down the rows (A to B to C). Bias and number of conducted studies are indicated by colors (blue to orange). 

<table class="wide">
<tr>
  <td class="left">
    <b>Figure 1. Different Levels of Bias</b>
    <br>
    <img src="/img/ioannidis_bias.png" alt="PPV as a Function of Bias" title="PPV as a Function of Bias" style="width:350px;">
  </td>
  <td class = "center">
  </td>
  <td class="right">
    <b>Figure 2. Different Numbers of Studies</b>
    <br>
    <img src="/img/ioannidis_multiplicity.png" alt="PPV as a Function of Multiplicity" title="PPV as a Function of Multiplicity" style="width:350px;">
  </td>
</tr>
</table>
<br>

PPV can assume a range of values, but low pre-study odds, low power, heavy bias, or large study multiplicity can dramatically decrease PPV.  

Although Ioannidis's figures are revealing, it's easier to draw insights from an interactive application. Michael Zehetleitner and Felix Schönbrodt have developed an awesome interface for observing how PPV changes based on Ioannidis's model. Check it out [here](http://shinyapps.org/apps/PPV/)!
  
<br>

## 2. Corollaries

Ioannidis describes several corollaries (which I've tabulated below) that describe how real-world factors can affect the reliability of research. 

<table class="table table-striped">
  <tr>
    <th>Corollary</th>
    <th>Study Characteristic</th>
    <th>Effect on Model<br></th>
    <th>Effect on Findings<br></th>
  </tr>
  <tr>
    <td>1</td>
    <td>Confirmatory Testing<br></td>
    <td>↑ Pre-Study Odds</td>
    <td><font color="green">↑ PPV</font></td>
  </tr>
    <tr>
    <td>2</td>
    <td>Discovery Testing<br></td>
    <td>↓ Pre-Study Odds<br></td>
    <td><font color="red">↓ PPV</font></td>
  </tr>
  <tr>
    <td>3</td>
    <td>↓ Sample Sizes</td>
    <td>↓ Power</td>
    <td><font color="red">↓ PPV</font></td>
  </tr>
  <tr>
    <td>4</td>
    <td>↓ Effect Sizes</td>
    <td>↓ Power</td>
    <td><font color="red">↓ PPV</font></td>
  </tr>
  <tr>
    <td>5</td>
    <td>↑ Study Design Flexibility<br></td>
    <td>↑ Bias</td>
    <td><font color="red">↓ PPV</font></td>
  </tr>
  <tr>
    <td>6</td>
    <td>↑ Financial Interests</td>
    <td>↑ Bias</td>
    <td><font color="red">↓ PPV</font></td>
  </tr>
  <tr>
    <td>7</td>
    <td>↑ Conceptual Prejudices</td>
    <td>↑ Bias</td>
    <td><font color="red">↓ PPV</font></td>
  </tr>
  <tr>
    <td>8</td>
    <td>↑ Popularity of Field<br></td>
    <td>↑ Number of Studies<br></td>
    <td><font color="red">↓ PPV</font></td>
  </tr>
</table>
<br>  
  

## 3. Derivation of the Basic PPV Model

Although Ioannidis provides a quick overview of his math, I thought it would be a useful exercise to derive everything more thoroughly. 

### 3.1 Definitions

Let the events A and C indicate the actual and claimed truth value of a given proposition. For example, the probability that the proposition is true is *P(A)*, and the proposition that the proposition is false is *P(A<sup>c</sup>) = 1 - P(A)*. For readability, I'll use the following notation instead: 

- *AT* : actually true (*A*)
- *AF* : actually false (*A<sup>c</sup>* )
- *CT* : claimed true (*C*)
- *CF* : claimed false (*C<sup>c</sup>* )

Recall the definition of type I and II errors: 

- Type I error (false positive): &nbsp;&nbsp; *&alpha; = P(CT \| AF)*
- Type II error (false negative): &nbsp; *&beta; = P(CF \| AT)*
- Specificity: *1-&alpha;*
- Sensitivity/Power: *1-&beta;*

### 3.2 Prevalence of Actually True Propositions

The first step is to look at how often propositions are actually true. Let $R$ denote the odds-ratio: 
\\[R = \frac{P(AT)}{P(AF)} \\]

$R$ also indicates the pre-study odds and the ratio of true to false propositions in a circumscribed field. We can then derive: 

\begin{align}
P(AT) &= \frac{P(AT)}{P(AT)+P(AF)} = \frac{R}{R+1} \\\
P(AF) &= \frac{P(AF)}{P(AT)+P(AF)} = \frac{1}{R+1}
\end{align}

Using these results and the definitions of type I and II errors, we can complete the [confusion matrix](https://en.wikipedia.org/wiki/Confusion_matrix): 

### 3.3 Confusion Matrix

A confusion matrix is a 2x2 table that records the probability of true positives (top left), false positives (top right), false negatives (bottom left), and true negatives (bottom right). Each square is a joint probability, which can be decomposed into a product of known values by Bayes' Rule.

<img src="/img/confusion_matrix_1.png" alt="Confusion Matrix 1" style="width: 700px; "/>

### 3.4 Positive Predictive Value
To determine whether "most published research findings are false," we can evaluate the positive predictive value (PPV) by dividing the value in top left corner by the sum of the top row. 

\begin{align}
PPV &= P(AT \,|\, CT) \\\
&= \frac{P(CT, AT)}{P(CT)} \\\
&= \frac{P(CT, AT)}{P(CT, AT) + P(CT, AF)} \\\
PPV &= \fbox{\\(\frac{R(1-\beta)}{R(1-\beta) + \alpha} \\)}
\end{align}

Thus, PPV is a function of the pre-study odds (*R*), the power (*&beta;*), and the significance level (*&alpha;*).


## 4. Derivation of PPV Model Corrections 

### 4.1 *&alpha;* and *&beta;* Corrections for Bias ($u$)

Ioannidis investigates the impact of bias as it influences *&alpha;* and *&beta;*. Here, he introduces a new term $u$, the fraction of probed analyses that should not have been findings, but end up reported as such. In other words, $u$ is the fraction of propositions in *CF* that become *CT*.  

Let the subscript [ ]<sub>$u$</sub> indicate the value of [ ] after considering bias. 
\\[ u = \frac{CF_{changed}}{CF_{original}} = \frac{P(CF)-P(CF_u)}{P(CF)} = 1 - \frac{P(CF_u)}{P(CF)} \\]

We want to know how *&alpha;* and *&beta;* are affected by bias. First, we derive a few relations: 
\begin{align}
P(CF_u) &= (1-u)P(CF) \\\
P(CT_u) &= 1- P(CF_u) \\\
&= 1 - (1-u)(1-P(CT)) \\\
&= u + (1-u)P(CT)
\end{align}
Using the above relations: 
\begin{align}
\beta_u &= P(CF_u \,|\, AT)  \\\
&= (1-u) P(CF \,|\, AT) \\\
&= \fbox{\\( (1-u) \beta \\)} \\\
\alpha_u &= P(CT_u \,|\, AF)  \\\
&= u + (1-u) P(CT \,|\, AF) \\\
&= \fbox{\\( u + (1-u)\alpha \\)}
\end{align}

### 4.2 *&alpha;* and *&beta;* Correction for Multiple Studies ($n$)

Let $n$ indicate the number of studies, and the subscript [ ]<sub>$n$</sub> indicate the value of [ ] after considering $n$ studies. 

- CT<sub>$n$</sub> is the event that at least one study claims a true relation
- CF<sub>$n$</sub> is the event that every single study claims a false relation

If all studies are independent: 

\\[ P(CF_n) = \prod_{i=1}^n P(CF_i) \\]

If all studies are equally powered: 

\\[ P(CF_n) = P(CF)^n \\]

Using the above relation (under assumptions of independence and equal power): 

\begin{align}
\beta_n &= P(CF_n \,|\, AT)  \\\
&= P(CF \,|\, AT)^n \\\
&= \fbox{\\( \beta^n \\)} \\\
\alpha_u &= P(CT_n \,|\, AF)  \\\
&= 1 - P(CF_n \,|\, AF) \\\
&= 1 - P(CF \,|\, AF)^n \\\
&= \fbox{\\( 1-(1-\alpha)^n \\)}
\end{align}

### 4.3 Joint *&alpha;* and *&beta;* Corrections

Although Ioannidis only considers bias and multiple studies one at a time, it is simple to extend his model to consider both simultaneously.

Let the subscript [ ]<sub>$u$,$n$</sub> indicate the value of [ ] after correcting for bias and multiple studies. Since biases are study specific, they are accounted for before aggregating. 

If power and bias are the same across all studies: 

\begin{align}
\beta_{u,n} &= \left[ (1-u)\beta \right]^n \\\
&= \fbox{\\( (1-u)^n \beta^n \\)} \\\
\alpha_{u,n} &= 1 - \left( 1-[u + (1-u) a] \right)^n \\\
&= \fbox{\\( 1 - (1-u)^n(1-a)^n \\)}
\end{align}

These are the modified *&alpha;* and *&beta;* values that I listed at the beginning. If power and bias differ between studies, we must index them individually: 

\begin{align}
\beta_{u,n} &= \prod_{i=1}^n (1-u_i) \beta_i  \\\
\alpha_{u,n} &= 1 - \prod_{i=1}^n (1-u_i)(1-a_i)
\end{align}

## 5. Citation

All derivations are based the paper Ioannidis, J. P. A. (2005). Why most published research findings are false. PLoS Medicine, 2(8), e124. http://doi.org/10.1371/journal.pmed.0020124


<!--
|      | $AT$                               | $AF$                               |
|------|------------------------------------|------------------------------------|
| $CT$ | $P(CT, AT) = P(AT)P(CT &#124; AT)$ | $P(CT, AF) = P(AF)P(CT &#124; AF)$ |
| $CF$ | $P(CF, AT) = P(AT)P(CF &#124; AT)$ | $P(CF, AF) = P(AF)P(CF &#124; AF)$ |
-->

<!-- dynamically load mathjax for compatibility with self-contained -->
<script>
  (function () {
    var script = document.createElement("script");
    script.type = "text/javascript";
    script.src  = "https://mathjax.rstudio.com/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML";
    document.getElementsByTagName("head")[0].appendChild(script);
  })();
</script>
