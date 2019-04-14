---
layout: post
title: "Conclusion of the ERCC Projects"
author: James Diao
date: 2019-04-07
location: Boston, MA
categories: Research
excerpt: Reflections on my undergraduate research experience at Yale
images:
  - url: /img/0-gerstein-timeline.png
---

### tl;dr 
After wrapping up two of my undergraduate research projects, I've been thinking about how much went into them: how much work I've put in and how much I've learned. Working in Gerstein Lab has taught me a ton about bioinformatics research, but also about the process, pace, and zeitgeist of academia. 

#### Timeline of my two projects in Gerstein Lab
<img src="/img/0-gerstein-timeline.png" alt="Gerstein Lab Timeline" title="Gerstein Lab Timeline" style="width:700px;height:350px;">  

**Acronyms:** *ISEV*, International Society on Extracellular Vesicles (conference); *NESS*, New England Science Symposium; *YURA/YURC*: Yale Undergraduate Research Association/Conference; *HMS M1*, Harvard Medical School, year 1

### Reflection 
In undergrad, I split my time between two labs: clinical genetics with [Zak Lab](research/zak-lab) and bioinformatics with [Gerstein Lab](/research/gerstein-lab). Although I spent at least as much time on and learned just as much from the former (if not more), I'm going to focus on the latter for now. 

Aside from some not-very-productive wet lab work in high school, Gerstein Lab was my first serious exposure to research. I worked there for almost all of undergrad--starting freshman summer, all the way up to my senior thesis in Statistics & Data Science. It's been interesting to reflect on how much has happened throughout the course of this project. Just looking back on our 2017 and 2018 [abstracts in ISEV](/research/isev-abstracts) is enough to show how far the research has come. 

#### Joining the Lab

I first heard about the Gerstein Lab through Jason Liu, a Yale student whom I met at a summer camp before high school. He reached out when I was admitted and talked about some of the things he was involved in. When he showed me some of his bioinformatics work on his laptop, I was so impressed (honestly, a large part from how cool the command-line looked and how fast he could tab-complete through directories). When it came time to decide on a summer internship, research in Gerstein Lab was the only job I considered. Sometimes I think about how my life would have been different if I had never gone to that math camp and met Jason. Would I have ever found my way to bioinformatics, or chosen to major in Statistics & Data Science? Would I have spent that time on bench work or epidemiology instead? Who knows! Either way, it's interesting to think about how my life direction may have pivoted off of this one connection. 

#### Getting started with project work

When I joined the lab, I didn't have much to offer. I had no experience with sequencing analysis, no experience working with computing clusters, and no experience with R, Python, or UNIX. It took quite a while before I was able to do anything useful. But with the help of my very patient mentor and a whole lot of StackOverflow, I was able to make something of my summer. Over those 2 months, I ran a few hundred human and mouse sequence files from the public Sequence Read Archive (SRA) through a preliminary version of the exceRpt pipeline. In the process, I worked on testing and debugging errors to make the pipeline more robust to malformed inputs. When I became more comfortable with this workflow, I also worked on testing and visualizing quality control metrics, including the transcriptome-mapped reads and transcriptome-to-genome mapped reads ratio metrics that ended up in Figure 2D of the exceRpt paper. It was a wonderful learning experience, and I was excited to expand on this work over the school year. 

Around this time, I was also starting to get involved with the exRNA Atlas project. I had done some data visualization work at Harvard, and we had a great opportunity to produce something similar for the exRNA Atlas. Unlike the exceRpt project, which was entirely internal to Gerstein Lab, this project would involve working closely with other ERCC labs. I worked closely with William Thistlthwaite (co-first author on our Atlas paper) on this. It taught me a lot about how to develop a tool for a broad user base with diverse technical backgrounds, how to work closely with long-distance colleagues I've never met. 

#### The long and rocky road to publishing

When the first papers published using our tools started to emerge, my mentor told me that the lab was going to publish a manuscript on the pipeline, and that I could contribute to its writing as a co-author. At that point, I had already set my heart on exploring more clinical informatics research (enter Zak Lab), but it was wonderfully exciting news, and I eagerly kept tabs on the progress of the manuscript and contributed to updates and edits as needed.

Over the next few years, various issues came up. Rob (the original first-author) left the lab to join a biotech startup. His new job kept him busy and the momentum to publish stalled. On our end, other ERCC projects (such as the exRNA Atlas) began to mature and take priority. It wasn't until late 2017 (now 2.5 years into the project) that my mentor wrote up the exceRpt paper, and that our collaborators at Baylor College of Medicine began rallying co-authors for the exRNA Atlas paper. 

But even with the completed manuscripts, the publication date was restricted by another factor. The ERCC intended to be submit its major papers as a "publication package" to the same family of journals. The full package of 18 papers, when finally published, looked like [this](https://www.cell.com/consortium/exRNA):

<img src="/img/ercc-package.png" alt="ERCC Publication Package" title="ERCC Publication Package" style="width:700px;height:375px;">  

Coordinating preparation for so many papers by hundreds of co-authors across the multi-institutional consortium proved to be challenging. Peer review (and the additional work requested by reviewers) added even more time. By the time the papers came out, it had been almost exactly 4 years since I started everything. 

#### Obligatory complaining about Reviewer 3

It's no secret that peer reviewers often disagree on their evaluations. There are countless memes of this on [grad school memes with relatable themes](https://www.facebook.com/groups/GradSchoolMemesWithRelatableThemes/). Here are two of my favorites: 

<img src="/img/reviewer-3-comic-1.png" alt="Reviewer 3 Comic Venn Diagram" title="Reviewer 3 Comic Venn Diagram" style="width:247px;height:250px;">
<img src="/img/reviewer-3-comic-2.jpg" alt="Reviewer 3 Comic Monster" title="Reviewer 3 Comic Monster" style="width:326px;height:250px;">  

> Exhibit A: Reviewer responses to our resubmission of the exRNA Atlas paper

<img src="/img/reviewer-3.png" alt="Reviewer 3 Comments" title="Reviewer 3 Comments" style="width:600px;height:242px;">

*Followed by a page and a half of criticisms

### Concluding thoughts

I've since moved on from molecular bioinformatics work, but this project was an invaluable first step into computational research and data analysis.
Besides technical skills, it taught me the importance of the non-scientific part of science: all of the writing, presenting, defending, and editing that goes into convincing others that your work is good. 

Although this path to publication was rocky and long (and I had definitely given up on it a couple times), I'm grateful that everything ended up working out. I know many friends whose mentors were less supportive or less willing to recognize them for their work, or who happened to encounter more unreasonable reviewers. I'm proud of the work that went into the pipeline and I think it's a really good thing for science and reproducibility that the details of these resources are peer-reviewed and widely distributed. I'm very glad that we were able to bring this work to a clean conclusion.  


