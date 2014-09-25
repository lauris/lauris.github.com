---
layout: post
title: "Sensei Grid Editors"
category: development
permalink: /sensei-grid-editors
related: ["Awesome Scala", "Servers are fun: Ansible", "Sensei Grid Roadmap"]
---

Today a new editor *TextareaEditor* was bundled with [Sensei Grid](https://github.com/datazenit/sensei-grid) - this one features a textarea for large text editing. Currently Sensei Grid ships with three editors: BasicEditor, SelectEditor and TextareaEditor. Previously SelectEditor was implemented just as an example in the demo file, but I moved it together with other editors and it is now a part of Sensei Grid.

<!-- more -->

These changes introduced a new configuration parameter for columns called *editorProps*. It is an easy way to pass column specific parameters to an editor. This was mostly needed for the SelectEditor, because each column would have its own set of predefined values. To see how it is implemented and how to use it in a custom editor, please check the source file **[sensei-editors.js](https://github.com/datazenit/sensei-grid/blob/master/src/sensei-editors.js)**. 

I have planned to add another editor with a datepicker at some point, but after a quick research I didn't found a datepicker plugin that would be suitable for Sensei Grid. jQuery UI is too heavy and redundant dependecy, but others were too buggy, outdated, lacked functionality or were not customizable enough. The only one that stood out was [CLNDR.js](kylestetz.github.io/CLNDR/), but a further investigation is still needed. 