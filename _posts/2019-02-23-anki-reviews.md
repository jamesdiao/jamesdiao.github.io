---
layout: post
title: "Modeling Anki Review Load"
author: James Diao
date: 2019-02-23
location: Boston, MA
categories: [Medical_School, Projects]
excerpt: How much work does it take to keep up with an Anki study schedule?
images:
  - url: /img/0-anki-reviews.png
---

### Update

This load modeling feature has been incorporated as a component of a broader suite of analysis and visualization of Anki data, and the original app has been archived. All links now point to the new app, which is described in its [own post](/medical_school/projects/anki-app).


### tl;dr 
I built an app to model how much work it takes for a medical student to keep up with a popular flashcard study schedule:

> [https://jamesdiao.shinyapps.io/anki-data](https://jamesdiao.shinyapps.io/anki-data/) (see "Simulator" tab)


### Anki as a study tool

Just as a quick intro: Anki is a flashcard app, much like Quizlet. You learn by testing yourself on flashcards; you can either make them yourself or download shared decks from online (see my post on [Anki for Medical School](/medical_school/anki) for more info). 

The core premise of Anki is the spaced repetition system, which schedules the next time you see a card based on how well you know the material. The interval increases every time you get it right (1 day, 3 days, 7 days, etc.) by about 2.5x, but the interval resets if you get it wrong. As you might expect, this system requires a fairly high amount of sustained effort to keep up with reviews. 

To help people better understand what they're signing up for, or to figure out how aggressively they should schedule new cards to finish on time, I've built an app to model how many cards you'll have to review per day, based on a couple basic parameters. 

### Methodology
Review counts are computed by forward propagating the expected future reviews generated on each day. Here's a video demonstrating this generation process (slowed down 200x). Each frame is a snapshot of your review schedule should you decide to stop learning new cards, but want to continue maturing the ones you've already seen. 

<video width="700" height="400" controls preload="none">
    <source src="/vid/ankireviews.mp4" type="video/mp4" />
    <source src="/vid/ankireviews.webm" type="video/webm" />
    <source src="/vid/ankireviews.ogg" type="video/ogg" /><
</video>

To avoid multiple embedded loops, the program only allows a maximum of 2 possible forgetten reviews. Because this constraint underestimates the true number of reviews, each added review count is then scaled up by the expected difference. This estimate shortcut greatly decreases the computational cost, but results in some shape distortions away from key points (peak and stable state). Another approach is direct simulation, which is significantly slower, but can be more accurate. One such approach can be accessed here: [https://repl.it/repls/GlassBiodegradableTriggers](https://repl.it/repls/GlassBiodegradableTriggers). 

### Validation

Comparison with the direct simulator (referenced above) yielded similar results.  
Clockwise from top-left:

1. **LARGE DECK**: approximate parameters for Zanki, the most popular Step 1 deck.  
2. **SMALL DECK**: approximate parameters for a single Zanki subject deck (e.g., cardiology).  
3. **HIGH FORGET RATE**: worsening concordance (up to 25% difference) between computed expectation and direct simulation due to error propagation.  
4. **ZERO FORGET RATE**: essentially 100% concordance (including the isolated spike around day 170) between computed expectation and direct simulation. 

<img src="/img/ankivalidation1.png" alt="Anki Validation 1" title="Anki Validation 1" style="width:315px;height:255px;">
<img src="/img/ankivalidation2.png" alt="Anki Validation 2" title="Anki Validation 2" style="width:385px;height:255px;">
<img src="/img/ankivalidation3.png" alt="Anki Validation 3" title="Anki Validation 3" style="width:315px;height:255px;">
<img src="/img/ankivalidation4.png" alt="Anki Validation 4" title="Anki Validation 4" style="width:385px;height:255px;">

### Source Code
All code is available on Github: [https://github.com/jamesdiao/anki-reviews](https://github.com/jamesdiao/anki-reviews)

### Improvement Areas
Allowing no more than 2 errors may be too strong a constraint- shape deviations become noticable with an error rate >15% error, and significant at >20%. The program is currently fast enough (elapsed time on the order of 0.01-0.10 s) that adding another embedded loop may improve model accuracy with little noticable lag. Currently, accuracy is good enough that I'm not too worried about fixing this. 


