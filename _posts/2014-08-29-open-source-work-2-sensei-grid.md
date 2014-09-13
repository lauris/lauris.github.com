---
layout: post
title: "Work and open source #2: Sensei Grid"
category: datazenit
image: /images/blog/sensei-grid-screenshot.png
---

Previously I [wrote about an issue](http://lauris.github.io/development/2014/08/25/work-and-open-source/) I had regarding an open source library. A short summary – an update that was supposed to fix several blocker issues broke everything else and I was left with a dilemma to either fix the lib or to find a new one. Initially I tried to fix the library, but when enough time was wasted and new bugs started popping up randomly I decided it was time to ditch that dependency entirely. The package provided an Excel-like data grid, which is one of the core elements of Datazenit's interface. I couldn't wait for another update, because Datazenit needs to be moving forward.

<!-- more -->

A decent and simple enough alternative couldn't be found, therefore a decision was made to build our own library. After several hours of determined coding I was happy to have a working prototype. I tried to avoid hacks and workarounds as much as I could, which is not always easy when programming in JavaScript. The code base ended up clean and simple, at least for now. The project will probably get a bit more complex as soon as additional functionality is introduced.

The name of my library is "Sensei Grid", because the official character of Datazenit is our own version of [Sensei](http://en.wikipedia.org/wiki/Sensei) and he is even displayed in our [logo](http://datazenit.com/static/img/datazenit-logo.png). The library will be definitely open sourced when the work is done. Right now I can only show you a small demo. Instructions can be found below the demo data grid.

**[Sensei Grid Demo](http://datazenit.com/static/sensei-grid/)**

A side note: While building the prototype I found a nasty Firefox bug regarding table rendering and border-collapse property. Google Chrome and all other WebKit browsers rendered everything nice and smooth, but Firefox was inconsistently calculating widths of table cells and randomly glitching table borders. It appears that the only way to avoid the bug is to use ``border-collapse: separate``, that would introduce new complexity in other parts of the library. This is also a well known and quite old bug/series of bugs. 



