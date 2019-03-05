---
layout: post
title: "Estimated Distributions"
author: James Diao
date: 2018-02-01
location: New Haven, CT
excerpt: Estimated distributions by quantile-optimized parameters
images:
  - url: /img/0-estimated-distributions.png
---

Often, my parents or friends will ask me to estimate my beliefs about a probability or a time. For example, they might ask how likely I am to go to an event, or maybe how much longer it will take me to get there. It's easy to take a guess, but it says nothing about my own uncertainty in this guess. As a result, I made a simple app to turn point estimates into probability distributions. It does this by taking point and range values (best, minimum, and maximum) and fitting them to an appropriate family of distributions. I don't actually use this practically of course, but it was fun to implement and play around with.  

The app is hosted at [https://jamesdiao.shinyapps.io/estimateddistributions/](https://jamesdiao.shinyapps.io/estimateddistributions/) and embedded below (may take 5-10 seconds to load). Simply use the sliders to select an estimated value and range. For time estimates, you can also choose your units and toggle the display format. 

<iframe src="https://jamesdiao.shinyapps.io/estimateddistributions/" style="border: none; width: 850px; height: 660px"></iframe>

**Implementation**: App is built in R Shiny. Parameters were optimized to assigned quantiles by gradient descent using `get.gamma.par()` and `get.beta.par()` from the `rriskDistributions` package. The point estimate is weighted to be twice as important as range estimates. 

**Choice of Distributions**: I chose to represent probabilities using a Beta distribution because, as the conjugate prior to the binomial, it has an intuitive explanation in terms of observed successes and failures (alpha and beta). Similarly, I chose to represent times using a Gamma distribution because, as the conjugate prior to the exponential, it gives an intuitive model of wait time as the sum of independent exponentially-distributed events (shape = n, rate is the same). These families work reasonably well because they are smooth, unimodal, and within the correct domains (0-1 for probabilities, 0-&infin; for time). 

**Potential Improvements**: I find that the Gamma distribution is not as flexible as I hoped, and it fails to capture certain shapes (e.g., left-skewed). In fact, I was forced to use a Normal distribution in these kinds of "unexpected" situations, where the gradient algorithm failed to find acceptable parameters. I suspect that the PERT distribution (a domain-transformed Beta) would work better; it is commonly used to modeling completion times for industry projects. I'm hoping to implement it later when I have time.

