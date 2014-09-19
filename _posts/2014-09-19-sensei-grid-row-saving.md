---
layout: post
title: "Sensei Grid row saving"
category: development
image: /images/blog/sensei-grid-screenshot.png
---

Today [a new feature was released](https://github.com/datazenit/sensei-grid/releases/tag/v0.1.5) for [Sensei Grid](https://github.com/datazenit/sensei-grid), a simple data grid in JS/HTML. Previously I added an always present empty row at the end of table (configurable option), that was meant for adding new data to the grid. I have added a new callback for easier row saving in the backend, especially if you are storing data in a relational database. 

<!-- more -->

An example how to listen to "row:save" callback: 

{% highlight javascript %}
grid.events.on("row:save", function (data, $row) { 
	// save data via ajax 
	// e.g., $.post("/api/save", data);
});
{% endhighlight %}

Saving rows is a bit different from cells, because rows can be saved only as a whole (INSERT query), whereas cells are saved individually (UPDATE query). Hence a separate event for rows. Cells can be still saved separately with the "editor:save" event.
