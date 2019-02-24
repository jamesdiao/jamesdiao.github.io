---
layout: post
title: "Modeling Anki Review Load"
author: James Diao
date: 2019-02-23
location: Boston, MA
---


### tl;dr 
I built an app to model how much work it takes for a medical student to keep up with a popular flashcard study schedule. 

### Anki as a study tool

Just as a quick intro, Anki is a flashcard app, much like Quizlet- you can make your own cards or download shared decks. The core premise of Anki is the spaced repetition system, which reschedules the next time you see a card based on how many times you've successfully answered it in a row. This system requires a fairly high amount of sustained effort to keep up with reviews, and many students aiming to try out Anki are worried about whether they'll be able to keep up with it.

To help people better understand what they're signing up for, or figure out how intense they want to schedule new cards, I've built an app to model how many cards you'll have to review per day. 
 
> [https://jamesdiao.shinyapps.io/ankireviews](https://jamesdiao.shinyapps.io/ankireviews/)

**Methodology**: Review counts are computed by forward propagating the expected future reviews generated on each day. Here's a video demonstrating this generation process (slowed down 200x; might not work in Chrome): 

<video width="700" height="400" controls preload="none">
    <source src="/vid/ankireviews.mp4" type="video/mp4" />
    <source src="/vid/ankireviews.webm" type="video/webm" />
    <source src="/vid/ankireviews.ogg" type="video/ogg" /><
</video>

To avoid multiple embedded loops, the program only allows a maximum of 2 possible forgetten reviews. Because this constraint underestimates the true number of reviews, each added review count is scaled up by the expected difference. This shortcut greatly decreases the computational cost, but results in some shape distortions away from key points (peak and stable state). A more accurate (but slower and less visual) simulator can be accessed here: [https://repl.it/repls/GlassBiodegradableTriggers](https://repl.it/repls/GlassBiodegradableTriggers). 

**Validation**: Comparison to the direct simulator (referenced above) yields very similar results. Clockwise from top-left:

1. **LARGE DECK**: approximate parameters for Zanki, the most popular Step 1 deck.  
2. **SMALL DECK**: approximate parameters for a single Zanki subject deck (e.g., cardiology).  
3. **HIGH FORGET RATE**: worsening concordance (up to 30% difference) between computed expectation and direct simulation due to error propagation.  
4. **ZERO FORGET RATE**: almost 100% concordance (including the isolated spike around day 170) between computed expectation and direct simulation. 

<img src="/img/ankivalidation1.png" alt="Anki Validation 1" title="Anki Validation 1" style="width:315px;height:255px;">
<img src="/img/ankivalidation2.png" alt="Anki Validation 2" title="Anki Validation 2" style="width:385px;height:255px;">
<img src="/img/ankivalidation3.png" alt="Anki Validation 3" title="Anki Validation 3" style="width:315px;height:255px;">
<img src="/img/ankivalidation4.png" alt="Anki Validation 4" title="Anki Validation 4" style="width:385px;height:255px;">

**Source Code**
All code is available on Github: [https://github.com/jamesdiao/Anki-Reviews](https://github.com/jamesdiao/Anki-Reviews)

**Potential Improvements**: Allowing no more than 2 errors may be too strong a constraint- shape deviations become noticable with an error rate >15% error, and significant at >20%. The program is currently fast enough (elapsed time on the order of 1-10 ms) that adding another embedded loop may improve model accuracy with little noticable lag. Currently, accuracy is good enough that I'm not too worried about fixing this. 


