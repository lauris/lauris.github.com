---
layout: post
title: "Firefox table cell position bug"
category: development
permalink: /firefox-table-cell-position-bug
related: ["First public release of Sensei Grid", "Work and open source #2: Sensei Grid", "The Technology Behind Datazenit: Part 1"]
---

Firefox calculates table cell position differently from other browsers. Left and top positions are off by 1px when table has collapsed borders and zero border spacing, because Firefox does not count in the left and top border of each cell. Technically the left and top border are not part of the cell, when borders are collapsed.

<!-- more -->

I have come up with a simple solution for this. First we need to detect if the client has this bug, that can be easily done by checking if first cell's left coordinate is the same as table's most left position. The check implemented as a basic jQuery function can be seen below. 

{% highlight js %}
$.fn.isSillyFirefox = function() {
    var tableLeft = $(this).position().left;
    var cellLeft = $(this).find("td:first").position().left;
    return cellLeft !== tableLeft;
};
{% endhighlight %}

Further we can use this function to determine if we need to adjust cell position by 1px. In my particular use case I created a new function to access the position of cells:

{% highlight js %}
$.fn.getCellPosition = function() {
    var pos = $(this).position();
    if (plugin.isSillyFirefox()) {
        pos.left -= 1; // fix left position
        pos.top -= 1; // fix top position
    }
    return pos;
}
{% endhighlight %}

When a cell position is needed I just use ``$(".some-cell").getCellPosition()`` instead of ``$(".some-cell").position()``. It works flawlessly on all browsers I have at hand (FF, Safari, Chrome). 

