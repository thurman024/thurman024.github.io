---
layout: post
title:      "Patterns in JS"
date:       2018-06-12 18:20:20 -0400
permalink:  patterns_in_js
---


I spent a lot of time trying to think out my fourth project (Rails + JS) with very little results.  Through the first 3 sections,  I felt comfortably proficient in the patterns I would need to put together my portfolio project.  But I realized with Javascript, I had no recognizable pattern imprinted in my brain to follow.  So after the process of working through my project,  here is a pattern that may be useful to someone somewhere.

Let's say the goal is to let a user click a link/button and have more information displayed on the page without a refresh.  This is one of the main practices learned through the JS section and needed for the final project.

1. **Implement the initializer action** - whether you need to add a link to the view or repurpose and existing one, the first step should be writing the JS code to trigger this whole sequence of events.  Giving your button/link a unique CSS identifier, you can use jquery to add an event handler that will execute the rest of the code upon being clicked. You can test functionality this far by adding an alert.

```
$(function( ) {
  $(".my-js-class").on('click', function(event) {
    alert("you clicked the link")
    event.preventDefault() // if using an existing link
		// to be continued ...
 })	
```
 
2) **Call a backend route that will provide the necessary data** - for example, your controller's #show action could be modified to render .json information as done in several lessons.  There may be situations where you create a new route and action.  Either way, you are essentially making an internal API call. There are several methods like ajax, fetch, etc., but jquery provides a nice shorthand.

```
// continuing...
$.get("/my-route/:${mightIncludeID}", response => {
   console.log(response)
	 //  call another function that handles your response (step 3)
})
```

3) **Instantiate a JS model object to handle data** - Odds are, the information you requested from your internal API is all or some of the data associated with one of your Ruby models.  You can recreate that model in your JS file as a tidy, modular way to handle the data the rest of the way. Adding to the previous code snippet...

```
$.get("/my-route/:${mightIncludeID}", response => {
	  let newObject = new MyModel(response) // (step 3)
})
```

Elsewhere in your JS code, you can code your model constructor.

```
function MyModel(attr_hash) {
   this.id = attr_hash.id
	 this.name = attr_hash.name
	 this.desc = attr_hash.desc
}
```

4)  **Format your data how it should be added to the page** - a nice way to do this (as well as check off a project requirement) is through a model prototype method.  The end result should the the exact html that belongs in the view. Wrap your return string in backticks, and interpolate data from the model as needed.  You will want to call this method on the variable `newObject` within the code snippet of step 3.

```
MyModel.prototype.formatModel = function () {
  let html = `<h1>${this.name}</h1>
	<p>${this.desc}</p>`
	return html
}
```

5) **Inject the html into the page** - whether you want to append or replace, use the necessary jquery tools to grab the correct html element from the view and inject your new html.  Combining the code from 3-5, it will flow something like this:

```
let newObject = new MyModel(response) // (step 3)
let newHtml = newObject.formatModel() // (step 4)
$("div.for-new-object).html(newHtml) // (step 5)
```

That's it!  As always, you can refractor this code by breaking it into modular functions.  But hopefully this explanation combines some JS concepts to paint a broad pattern to utilize in your project.

