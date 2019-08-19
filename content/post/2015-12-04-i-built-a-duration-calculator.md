---
title: I Built a Duration Calculator
author: 'kurtis'
date: '2015-12-04'
slug: i-built-a-duration-calculator
categories:
  - Teaching
tags:
  - web development
  - coding
  - tools
draft: no
summary:
image:
  caption: ''
  focal_point: ''

---

I get very frustrated when I have to add up durations of time to figure out a total amount of time. The basic communication class at [Purdue][Purdue] (COM 114, a presentational speaking class) is being revamped this year. As part of that revamping, the class has gained an "Asynchronous Presentation." I am a big supporter of this presentation, which amounts to a recorded narration over a PowerPoint-style visual aid, because it uses a lot of important skills for types of presentations that are not taught as well as they could be. I needed to add up the amount of time that students used on each slide to get a total duration for the presentation (some students didn't set their presentations to automatically advance, so timing the entire presentation was inconsistent).

I have had several times over the last few years where I have needed to add durations of time together, and I have never found a quick and easy way to do it. Excel is typically my go-to application for quick calculations, but it **will not** handle duration. For no discernible reason, *all* times in Excel are treated as *times of day* and not durations. This comes with a number of additional problems, not the least of which is that Excel always stores all of these times of day as a decimal value representing the proportion of the day which has passed (so 12:00 noon is stored as 0.5, and 9:00 in the morning is stored as 0.375, since by 9:00 am 3/8ths of a day has already elapsed. Because of this, if I enter that a student's introduction lasted 3 minutes and 2 seconds, Excel stores that number as 12:03:02. This has huge implications when you start adding amounts of time together, because Excel keeps trying to add *times of day* and not *amounts of time.*

Long story short, I couldn't find anything online and I got tired of doing it by hand, so I wrote a quick application which can do it. I wrote one version that includes hours, minutes, and seconds and a second version that only includes minutes and seconds (either version can also handle decimal values in the seconds position, should you require more precision.

Here are links to the [HMS Duration Calculator][HMS Duration Calculator] and the [MS Duration Calculator][MS Duration Calculator].



[Purdue]: www.purdue.edu
[HMS Duration Calculator]: http://kurtisdmiller.com/tools/hms-duration-calculator
[MS Duration Calculator]: http://kurtisdmiller.com/tools/ms-duration-calculator 
