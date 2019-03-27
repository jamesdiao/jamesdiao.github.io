---
layout: post
title: "Estimating Judging Concordance in Competitive Ballroom Dance"
author: James Diao
date: 2019-03-03
location: Cambridge, MA
categories: Projects
excerpt: Judging at dance competitions is subjective but thankfully much better than random
images:
  - url: /img/o2cm_ex2.png
---


### tl;dr 
I scraped competitive results from a few hundred ballroom dance events to estimate the distribution of concordance rates between judges. As expected, judging is quite subjective but significantly better than random. 

### Collegiate Ballroom Dance
A ballroom dance takes place with a number of couples (usually too many for the given floor size) assembled on a dance floor. Around 3-7 judges stand around the periphery and compare all the couples and issue a set number of callbacks (i.e., voting for whom they want to see in the next round). In the very last round, judges will rank all *N* couples from 1 to *N*. The specific rules come from the [Skating System of Judging](http://www.ballroomguide.com/resources/blog/2017_11_01_skating_system.html), which has many more rules for breaking ties. Other than that, judging is a fairly simple process. All results are recorded in a (pretty poorly designed) system called o2cm.


#### Example final round (full rankings)  
*7 judges have each ranked all 8 competitors*
<img src="/img/o2cm_ex2.png" alt="O2CM Example 1" title="O2CM Example 1" style="width:700px;height:316px;">


#### Example semifinal round (callbacks)
*5 judges have each voted for their favorite 8 competitors (X); the top 8 advance to the final*

<img src="/img/o2cm_ex1.png" alt="O2CM Example 2-1" title="O2CM Example 2-1" style="width:500px;height:218px;">


### Judge Concordance
It's easy after a competition to pore over one's callback numbers and final rankings and get caught up in which dances need the most work, or why some events went well and others didn't. My coach was skeptical of the reliability of these conclusions, saying that there was probably a lot of noise from different judge preferences, moods, or levels of paying attention. To test this hypothesis, I decided to take a look at the data. 

### The Data
I used the package `scrapeR` to extract tables from the finals round of [all 239 events I've participated in](
http://results.o2cm.com/individual.asp?szLast=Diao&szFirst=James) (as of March 2, 2019). The extracted raw data looked something like this (from my first event to my most recent): 


<table class="wide">
<tr>
  <td class="left">
    <img src="/img/o2cm_mat1.png" alt="O2CM Placements 1" title="O2CM Placements 1" style="width:300px;height:302px;">
  </td>
  <td class="right">
    <img src="/img/o2cm_mat2.png" alt="O2CM Placements 2" title="O2CM Placements 2" style="width:300px;height:312px;">
  </td>
</tr>
</table>

### Analysis Methods

Once the data was properly collected and cleaned (this took a while), the statistical analysis was quite straightforward. There are many methods of estimating interrater reliability, but I chose Kendall's W. 
Kendall's W is equivalent to the Friedman test normalized to the range 0-1 (0 indicating random rankings and 1 indicating unanimous rankings). It has several properties that make it a good choice for this problem.

1. Ordinal: accounts for magnitude of disagreement with discordant rankings
2. Non-parametric: makes no assumptions about the underlying probability distribution
3. Generalizes and scales naturally to any number of raters

It might be good here to give an intuition of what each Kendall's W actually looks like. Here are some sample tables with Kendall's W = 0.2, 0.5, and 0.8. 

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;border-color:#ccc;}
.tg td{font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:0px;overflow:hidden;word-break:normal;border-color:#ccc;color:#333;background-color:#fff;}
.tg th{font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-style:solid;border-width:0px;overflow:hidden;word-break:normal;border-color:#ccc;color:#333;background-color:#f0f0f0;}
.tg .tg-1wig{font-weight:bold;text-align:left;vertical-align:top}
.tg .tg-kiyi{font-weight:bold;border-color:inherit;text-align:left}
.tg .tg-883b{font-weight:bold;color:#fe0000;border-color:inherit;text-align:left}
.tg .tg-x6vl{font-weight:bold;color:#663234;border-color:inherit;text-align:left;vertical-align:top}
.tg .tg-76pe{font-weight:bold;color:#009901;border-color:inherit;text-align:left;vertical-align:top}
.tg .tg-0lax{text-align:left;vertical-align:top}
.tg .tg-fymr{font-weight:bold;border-color:inherit;text-align:left;vertical-align:top}
.tg .tg-xldj{border-color:inherit;text-align:left}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
</style>
<table class="tg">
  <tr>
    <th class="tg-883b">W = 0.2</th>
    <th class="tg-0lax"></th>
    <th class="tg-kiyi">J1</th>
    <th class="tg-kiyi">J2</th>
    <th class="tg-kiyi">J3</th>
    <th class="tg-kiyi">J4</th>
    <th class="tg-kiyi">J5</th>
    <th class="tg-1wig"></th>
    <th class="tg-x6vl">W = 0.5</th>
    <th class="tg-fymr">J1</th>
    <th class="tg-fymr">J2</th>
    <th class="tg-fymr">J3</th>
    <th class="tg-fymr">J4</th>
    <th class="tg-fymr">J5</th>
    <th class="tg-1wig"></th>
    <th class="tg-76pe">W = 0.8</th>
    <th class="tg-fymr">J1</th>
    <th class="tg-fymr">J2</th>
    <th class="tg-1wig">J3</th>
    <th class="tg-1wig">J4</th>
    <th class="tg-1wig">J5</th>
  </tr>
  <tr>
    <td class="tg-kiyi">Couple_1</td>
    <td class="tg-0lax"></td>
    <td class="tg-xldj">1</td>
    <td class="tg-xldj">2</td>
    <td class="tg-xldj">2</td>
    <td class="tg-xldj">4</td>
    <td class="tg-xldj">2</td>
    <td class="tg-0lax"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky">1</td>
    <td class="tg-0pky">1</td>
    <td class="tg-0pky">1</td>
    <td class="tg-0pky">3</td>
    <td class="tg-0pky">1</td>
    <td class="tg-0lax"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky">1</td>
    <td class="tg-0pky">1</td>
    <td class="tg-0lax">1</td>
    <td class="tg-0lax">2</td>
    <td class="tg-0lax">2</td>
  </tr>
  <tr>
    <td class="tg-kiyi">Couple_2</td>
    <td class="tg-0lax"></td>
    <td class="tg-xldj">3</td>
    <td class="tg-xldj">3</td>
    <td class="tg-xldj">3</td>
    <td class="tg-xldj">2</td>
    <td class="tg-xldj">1</td>
    <td class="tg-0lax"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky">3</td>
    <td class="tg-0pky">2</td>
    <td class="tg-0pky">3</td>
    <td class="tg-0pky">2</td>
    <td class="tg-0pky">2</td>
    <td class="tg-0lax"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky">2</td>
    <td class="tg-0pky">2</td>
    <td class="tg-0lax">2</td>
    <td class="tg-0lax">1</td>
    <td class="tg-0lax">1</td>
  </tr>
  <tr>
    <td class="tg-kiyi">Couple_3</td>
    <td class="tg-0lax"></td>
    <td class="tg-xldj">5</td>
    <td class="tg-xldj">1</td>
    <td class="tg-xldj">1</td>
    <td class="tg-xldj">5</td>
    <td class="tg-xldj">3</td>
    <td class="tg-0lax"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky">4</td>
    <td class="tg-0pky">4</td>
    <td class="tg-0pky">4</td>
    <td class="tg-0pky">1</td>
    <td class="tg-0pky">3</td>
    <td class="tg-0lax"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky">3</td>
    <td class="tg-0pky">3</td>
    <td class="tg-0lax">3</td>
    <td class="tg-0lax">4</td>
    <td class="tg-0lax">4</td>
  </tr>
  <tr>
    <td class="tg-fymr">Couple_4</td>
    <td class="tg-0lax"></td>
    <td class="tg-0pky">2</td>
    <td class="tg-0pky">4</td>
    <td class="tg-0pky">4</td>
    <td class="tg-0pky">3</td>
    <td class="tg-0pky">5</td>
    <td class="tg-0lax"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky">5</td>
    <td class="tg-0pky">3</td>
    <td class="tg-0pky">2</td>
    <td class="tg-0pky">4</td>
    <td class="tg-0pky">5</td>
    <td class="tg-0lax"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky">5</td>
    <td class="tg-0pky">5</td>
    <td class="tg-0lax">5</td>
    <td class="tg-0lax">3</td>
    <td class="tg-0lax">3</td>
  </tr>
  <tr>
    <td class="tg-fymr">Couple_5</td>
    <td class="tg-0lax"></td>
    <td class="tg-0pky">4</td>
    <td class="tg-0pky">5</td>
    <td class="tg-0pky">5</td>
    <td class="tg-0pky">1</td>
    <td class="tg-0pky">4</td>
    <td class="tg-0lax"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky">2</td>
    <td class="tg-0pky">5</td>
    <td class="tg-0pky">5</td>
    <td class="tg-0pky">5</td>
    <td class="tg-0pky">4</td>
    <td class="tg-0lax"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky">4</td>
    <td class="tg-0pky">4</td>
    <td class="tg-0lax">4</td>
    <td class="tg-0lax">5</td>
    <td class="tg-0lax">5</td>
  </tr>
</table>

### Computing Distributions

To estimate the distribution of concordance values, I computed Kendall's W using measured data and randomly simulated data (with the same couple:judge dimensions) for all 239 finals rounds. The two distributions are shown below. 

<img src="/img/o2cm_distr.png" alt="O2CM Distributions" title="O2CM Distributions" style="width:700px;height:383px;">

- The mean **observed** concordance between judges (red curve) was 0.43.
- The mean **simulated** concordance between random rankings (blue curve) was 0.13. 

### Hypothesis Testing

The two curves are obviously quite different, suggesting that judges almost certainly do better than random. However, there's some overlap that indicates that at least some rounds end up being pretty indistinguishable from random. 

Since we've explicitly modeled the null distribution here, we can compute the p-value as the fraction of observed cases greater than the 95th quantile of the null distribution (in this case, 0.283). Using this method, we find that **78.7%** of finals rounds have judge concordances that are better than random (at significance level &alpha; = 0.05). 

Just for kicks, we can also compute p-values based on a chi-squared approximation to the distribution of the Friedman test statistic. The p-values for all finals rounds are shown below. 

<img src="/img/o2cm_pv.png" alt="O2CM P-values" title="O2CM P-values" style="width:605px;height:376px;">

This approximation finds that **69.9%** of finals rounds have judge concordances that are better than random (at significance level &alpha; = 0.05), which is pretty close the estimate derived from our simulated null distribution. 

For the 20-30% of ranked rounds that are indistiguishable from random, we might suspect that this is driven by some lurking variable. The ones that come most readily to mind (and that are most easily accessible from o2cm) are level and dance style. For example, it might be the case that at lower levels, all dancers are making many mistakes and it may hard to distinguish them. It is also possible that the additional styling that happens in Rhythm and Latin dances make it easier to distinguish dancers. I just made up those hypotheses, but let's see what the data has to say. 

<img src="/img/o2cm_bylevel.png" alt="O2CM By Level" title="O2CM By Level" style="width:585px;height:330px;">

<img src="/img/o2cm_bydance.png" alt="O2CM By Dance" title="O2CM By Dance" style="width:700px;height:411px;"><br>

Qualitatively, I'm convinced that there's no significant difference between any category in either level or dance style. Quantitatively, we can turn to an F-test for analysis of variance. 

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;border-color:#ccc;}
.tg td{font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:0px;overflow:hidden;word-break:normal;border-color:#ccc;color:#333;background-color:#fff;}
.tg th{font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-style:solid;border-width:0px;overflow:hidden;word-break:normal;border-color:#ccc;color:#333;background-color:#f0f0f0;}
.tg .tg-s268{text-align:left}
</style>
<table class="tg">
  <tr>
    <th class="tg-s268"></th>
    <th class="tg-s268">df</th>
    <th class="tg-s268">Sum Sq</th>
    <th class="tg-s268">Mean Sq</th>
    <th class="tg-s268">F value</th>
    <th class="tg-s268">Pr(&gt;F)</th>
  </tr>
  <tr>
    <td class="tg-s268">Level</td>
    <td class="tg-s268">4</td>
    <td class="tg-s268">0.696</td>
    <td class="tg-s268">0.174</td>
    <td class="tg-s268">5.515</td>
    <td class="tg-s268">0.000303</td>
  </tr>
  <tr>
    <td class="tg-s268">Dance</td>
    <td class="tg-s268">19</td>
    <td class="tg-s268">0.885</td>
    <td class="tg-s268">0.047</td>
    <td class="tg-s268">1.476</td>
    <td class="tg-s268">0.096040</td>
  </tr>
  <tr>
    <td class="tg-s268">Residuals</td>
    <td class="tg-s268">215</td>
    <td class="tg-s268">6.782</td>
    <td class="tg-s268">0.032</td>
    <td class="tg-s268"></td>
    <td class="tg-s268"></td>
  </tr>
</table>

The F-test shows a significant difference in the means across levels, and a nonsignificant but suggestive difference in means across dances. Given the low sample sizes and potential non-normalities across categories, I am still convinced that there's no significant difference. 


### Conclusion

While my coach was probably just trying to keep me from overthinking each result, it's pretty clear that judging (at least for finals rounds) is significantly better than random. That being said, it's not wildly better; 20-30% of all finals rounds are discordant enough that they are not statistically different from random. 

There are some caveats here. First, I only looked at events that I compete in; this might not generalize to higher levels of competition (e.g., Pre-Champ and Championship). Second, there may still be value in poring over judging results for rounds that are particularly concordant (e.g., everyone ranked you last). But for most rounds, the data confirms what we pretty much already knew: judging results have value, but are certainly not reliable enough to stress over. 


