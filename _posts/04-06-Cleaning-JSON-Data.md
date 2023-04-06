---
layout: post
title: Cleaning JSON data.
---
On Monday I started a new project for Erdös Institute's data visualization minicourse.  For the project I plan to build a dashboard using my Fitbit data for the past year and `d3.js`, a JavaScript library.  It was daunting at first, every time I see JavaScript I get intimidated, even when I watched Matt's `d3.js` videos I had trouble following what was going on.  So I thought by using `d3.js` in my project I could get more comfortable with JavaScript.

Things have moved pretty slowly so far.  The first thing I had to do was pick out what data to use.  Fitbit exports _all_ the data, including features that I didn't even use with my Fitbit subscription.  The files are all there, but not organized in an obvious way.  Some of the files have the data from each month, while others have it for each day.  Some of the files are `.csv` files, and some are `.json` files.  So what I decided to do was create a Jupyter notebook and use python to consolidate the data.  I chose 7 categories:

1. **Exercise.**  Activity (run/walk), activity level minutes (sedentary, lightly, fairly, very), average hr, Calories burned, duration (ms), steps, minutes and Calories burned in hr zones (out of range, fat burn, cardio, peak), total active zone minutes.
2. **Active zone minutes.** Minute-by-minute active zone minutes.  Doubles for cardio and peak.
3. **Weight.** Daily weight and BMI.
4. **Readiness score.** Daily readiness score with subcomponents.
5. **Daily respiratory rate.** Average breaths per minute during deep sleep.
6. **Sleep score.** Overall score with components, minutes in deep sleep, resting hr, percent restlessness.
7. **Sleep stages.** Time spent in light, deep, REM.

I spent a lot of time trying to consolidate all the data in each category and then export it as a `.csv` file.  However, I could never figure out how to export JSON data to `.csv`.  Turn out I didn't have to.  I started rewatching the `d3.js` videos and saw that in my source file I can load JSON data directly.

I relooked at some of Matt's `d3.js` videos to figure out how to load my data onto my webpage.  In Matt's sample html files he always logs the data into the console, so I did that, too.  I loaded the `.json` file for "Active zone minutes" and the `.csv` file for "Weight".  After that I wasn't really sure what to do next.  I went to Matt's office hours yesterday, hoping he could give me some direction, but I think all he said was that I need to clean my data.  
