---
layout: post
title: "Discussion: AI in Medicine"
date: 2017-07-21
author: James Diao
location: Boston, MA
categories: Events
excerpt: Summary of the departmental discussion at Harvard Biomedical Informatics
image: /img/0-ai-discussion.png
featured: true
---

Summary and reflections on the "AI in Medicine" discussion at the Department of Biomedical Informatics, Harvard Medical School. 

<img src="/img/robodoc.jpg" alt="Medical Robot" title="Medical Robot" class="img-responsive" style="width:200px;height:auto;">

### Background, Definitions, and People:  

1. [AI Winter](https://en.wikipedia.org/wiki/AI_winter): when research and investment interest in AI wanes due to unmet expectations.  
2. [ROC](https://en.wikipedia.org/wiki/Receiver_operating_characteristic): <u>R</u>eceiver <u>O</u>perating <u>C</u>haracteristic- a curve that shows the diagnostic ability of a binary classifier as its threshold is varied.  
3. [EPIC](https://en.wikipedia.org/wiki/Epic_Systems): private implementation of EHR holding >50% of US patient records. Closed platform makes it hard and costly for outsiders to interface with clinical or billing software.  
4. [DBMI](http://dbmi.hms.harvard.edu/): <u>D</u>epartment of <u>B</u>io<u>M</u>edical <u>I</u>nformatics, Harvard Medical School  
5. [Zak](http://dbmi.hms.harvard.edu/person/faculty/zak-kohane): Isaac S. Kohane, MD/PhD, Chair of DBMI (and my PI)  
6. [Maha](http://dbmi.hms.harvard.edu/person/faculty/maha-farhat): Maha Farhat, MD/MSc, Assistant Professor at DBMI  
7. [Gabe](https://www.linkedin.com/in/gbrat/): Gabriel Brat, MD, MPH, Instructor in Surgery, HMS, co-founded Tissue Analytics, a smartphone imaging platform for wound documentation.  
8. [Andy](https://scholar.harvard.edu/beam): Andrew Beam, PhD, Instructor at DBMI, specializes in deep learning.  


### Part I: Beware the Hype

Zak begins by describing his own PhD work, which revolved around AI and computational solutions to medical problems. There was a big hype cycle at that time (around 30 years ago), when his advisors told him things like:  
1. Doctors will soon be obsolete  
2. Computers will solve medical problems  
3. We'll get much better care.  

Similarly, even the New England Journal of Medicine published the paper ([Medicine and the Computer](http://www.nejm.org/doi/full/10.1056/NEJM197012032832305)) predicting massive changes. The abstract reads: 
> Rapid advances in the information sciences, coupled with the political commitment to broad extensions of health care, promise to bring about **basic changes in the structure of medical practice.** Computing science will probably exert its major effects by augmenting and, in some cases, **largely replacing the intellectual functions of the physician.**  

None of these things have come to fruition, of course, and Zak predicts that there WILL be another AI winter, at least in biomedicine. People will fund things they don't understand, and business plans will go up in smoke when the technology is not mature enough to deliver. The biggest question is: how should we handle it? 


### Part II: Money and Incentives

The potential of health care AI is well-known. AI has achieved incredible successes in other fields, but not yet in health care. In fact, the health sector receives heavy investment precisely for that reason: because it is seen as untransformed, i.e. low-hanging fruit. For example, reducing medical errors alone would tap into the $20-30 billion USD lost every year. 

However, the problems with health care AI are huge, largely due to the complex and nonsensical incentive structure. The hospital business model does NOT directly benefit from better quality care. Moreover, patients are barely considered compared to the 3 P's of funding: payers, providers, and pharmaceuticals. 

Zak left us with four questions to consider:  
1. What role will AI information have in billing warfare?  
> For context, the "billing war" is fought between hospitals and insurance companies over what can be billed for, and how much. If hospitals have control over AI, they can suggest settings that increase medicalization and procedures. If insurance companies have it, they can set more restrictions on when patients can receive certain treatments.

2. Does AI mean game over for medical imaging? How will the money be distributed?  
3. Will AI bypass existing health care processes?  
4. Will AI lead to better outcomes for patients?  


### Part III: Current State of AI in Medicine

One prominent failure was IBM's Watson, which was [dropped by MD Anderson Cancer Center in early 2017](https://www.technologyreview.com/s/607965/a-reality-check-for-ibms-ai-ambitions/). Dozens of explanations have been offered for this event, but everyone would agree that this was quite the reality check for the field.  

<img src="/img/mda-watson.jpg" alt="IBM Watson Failure" title="IBM Watson Failure" class="img-responsive" style="width:500px;height:auto;">  

However, recent news has been much more optimistic. [Google has developed a system to detect diabetic retinopathy using retinal images](http://jamanetwork.com/journals/jama/fullarticle/2588763), which it has already begun to deploy in India.  

Maha argued that this technology will not replace ophthalmologists, since a sliver of their work and incomes depend on diagnosis. In fact, most of their money comes from operating. Maha then claims that AI would actually free doctors from the less lucrative parts of their work (e.g. image analysis). Another prominent success is [Stanford's landmark paper that classifies skin cancers](http://www.nature.com/nature/journal/v542/n7639/full/nature21056.html).  

Maha extends the same line of argument, claiming that this leads to more referrals for biopsies. She also warns against doctors' incentives to push the ROC decision point towards more sensitive and less specific settings, which increases biopsies. 


### Part IV: Implementation Problems

It seems that there are two main ways AI is being implemented. 
The first path is: Data => AI => EHR, essentially helping doctors making decisions. EHR companies love this, because it keeps them in the loop and gives them control over patient data.  
The second path is: Data => AI => Patient, which circumvents both physicians and EHR. One example is Atul Butte's company, Personalis.  

Discussion was scattered here, so I'm going to present the next part as a list.  
1. Gabe: The FDA will never approve a predictive system right now. The best AI can do in the near future is provide providers with augmented information about a patient's disease state. This leads to a preference for systems that return assessment scores and enhanced features.  
2. Gabe: AI might be used for utilization review criteria (to assess doctors). FDA approval is not needed, and this can still influence care.  
3. Andy: There is a risk that insurance companies can force results by adjusting weights imperceptibly e.g. with adversarial networks (doesn't sound like an important concern to me).  
4. Zak: Insurance companies are incentivized to set profit-driven assessment score cutoffs. Moreover, this would push the point of responsibility from physicians to systemic (insurance/hospital) decisions.  
> Maha's reply: This can be resolved by a patient-centered view. Options can be presented, and the patient could have the latitude to choose AI vs. MD. 


### Part V: Role of Physicians

Maha led the discussion here. She presented a rare optimism about AI in medicine, describing a kind of mutual support. On the one hand, AI can help physicians get rid of repetitive and draining tasks. Most cases are common and easy cases, and doctors don't want to see the screen if everything is normal. Computers can help with this. Doctors will still be needed as general decision-makers, even if they are outperformed on some specifics, like image analysis. On the other hand, physicians are also critical for helping AI earn usage and acceptance.  

Zak is more skeptical of physician domain knowledge. He brings up a story: if you ask doctors about the proper drug dosages, they'll debate forever. If you just set the default and give them options, they almost never deviate from the default. This is an example of what he calls "health system dynamics," where data is strongly biased by system effects. On the flip side, he also acknowledges that we may need physicians to parse and understand these effects. 

One large problem is that industry and VC often frame startups in terms of replacing physicians. Besides cutting doctors out of the picture, this is also, in Zak's opinion, too ambitious for the current state of technology. Overambitious business plans lead to failures which will only hasten the AI winter. 


### Concluding Thoughts
I was impressed by the complexity of the implementation and incentive structures in health care. I was also surprised to find optimism on AI's projected effect on physicians. Or, another way to think of it, pessimism about AI's ability to live up to its hype. Learning the history of boom-bust cycles and AI winters is also very important, although I think that the sheer scale of success in other fields does bode well for health care. It may be a long and circuitous road, but this talk left me some faith that AI in medicine will get there. 


