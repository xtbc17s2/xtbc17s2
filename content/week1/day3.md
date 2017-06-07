+++
date = "2017-06-07T11:54:37-04:00"
title = "Day 3: Jeffervescence"
prev="week1/day2"
toc = true
weight = 3

+++

<date>Wednesday, June 7, 2017</date>

## Lecture Videos

Morning:

* [Full Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [Day 3, part 1]() | [2]() | [3]() | [4]() | [5]() | [6]() | [7]()

Afternoon:

* [Full Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [Day 3, part 1]() | [2]() | [3]() | [4]() | [5]() | [6]() | [7]() | [8]() | [9]() | [10]() | [11]() | [12]()

## Topics

### Git
* Forking and cloning repositories

### Markdown

* [Markdown Cheatsheet](http://assemble.io/docs/Cheatsheet-Markdown.html)
* [Mastering Markdown](https://guides.github.com/features/mastering-markdown/)

### Foundation

* The grid system
* Responsive design (adjusting style based on window size)
* [Foundation Docs](http://foundation.zurb.com/sites/docs/)

### Functions as methods

* Methods calling methods (_e.g._ `megaRoster.addChild` calls `this.buildListItem`)
* Binding: Manually setting the value of `this` with `.bind`

### DOM Manipulation

* [parentElement](https://developer.mozilla.org/en-US/docs/Web/API/Node/parentElement)
* [childNodes](https://developer.mozilla.org/en-US/docs/Web/API/Node/childNodes)
* [firstChild](https://developer.mozilla.org/en-US/docs/Web/API/Node/firstChild)
* [firstElementChild](https://developer.mozilla.org/en-US/docs/Web/API/ParentNode/firstElementChild)
* [insertBefore](https://developer.mozilla.org/en-US/docs/Web/API/Node/insertBefore)
* [closest](https://developer.mozilla.org/en-US/docs/Web/API/Element/closest) (experimental)

## Examples

### Git - Forking a Repo

Making your own copy of an existing repo is called [forking](https://guides.github.com/activities/forking/).  Unlike a cloned copy, which retains the permissions set by the original owner, a forked copy now belongs to you (meaning you can make any changes you want to it).

Just hit the 'Fork' button in the upper right of the repo page, and this will add a copy to your personal github.

<div class="img github-fork-repo"><span>Hit the 'Fork' button in the upper right of the repo page, and this will add a copy to your personal github.</span></div>

### Foundation

Foundation is a CSS (and JS) framework that makes it easy to create stylish, responsive web pages.  The foundation (get it?) of it is the [grid system](http://foundation.zurb.com/grid.html).  The grid splits the page into 12 equally-sized columns, making it easy to set the alignment of elements on the page by specifying how many columns they span.

In addition, you can add sizes of 'small', 'medium', 'large', etc, to specify different behavior at different screen sizes.  In the following example, the two child divs will be full screen width at small screen sizes (stacked on top of each other), and half of the screen width at medium and larger screen sizes (appearing next to each other).

{{< code html >}}
&lt;div class=&quot;row&quot;&gt;
  &lt;div class=&quot;small-12 medium-6 columns&quot;&gt;
  &lt;/div&gt;
  &lt;div class=&quot;small-12 medium-6 columns&quot;&gt;
  &lt;/div&gt;
&lt;/div&gt;
{{< /code >}}

### Manually setting `this` with `bind`

In JavaScript, the value of `this` in any function depends on the context in which the method was called.  For example, if a function is an event listener callback, `this` will be set to the target that caused the event to fire.  Sometimes, this is not the `this` we want. Luckily, JavaScript also has the `.bind` method, which allows a function to be 'bound' to a particular value of `this`.

{{< code js >}}
this.x = 9        // here, 'this' is the global window object

const module = {
  x: 81,
  getX: function() {
    return this.x
  }
}

module.getX()     // 81
// getX was called on module, so 'this' is module and this.x is 81

const retrieveX = module.getX
retrieveX()       // 9
// retrieveX is a const declared in the global scope, so 'this' is window

const boundGetX = retrieveX.bind(module)
boundGetX()       // 81
// by binding to module, 'this' will always be set to module for boundGetX
{{< /code >}}

{{% aside info "`this` is Fun!" %}}
JavaScript's `this` is a source of consternation for many a developer, but it doesn't have to be!  Make the effort to learn it early in your career, and it will pay off in the long run.  Here is a great article with lots of code examples that will help you get a grasp on the nuances of `this`.  [Let's Settle 'this' - Part One](https://medium.com/@nashvail/lets-settle-this-part-one-ef36471c7d97) | [Part Two](https://medium.com/@nashvail/lets-settle-this-part-two-2d68e6cb7dba)
{{% /aside %}}

## Presentations

* [Review: Objects and Functions](/03-review-objects-and-functions.pdf)

## Projects
[Jeffervescence (morning)](https://github.com/xtbc17s2/jeffervescence/tree/f55636b0c73de7469f17b659fcde8f4f5416aa8a) | [Dinoplasty (afternoon)](https://github.com/xtbc17s2/dinoplasty/tree/a3e44eaef9a01b840aafb43ce37e64b05eb9a739)

These are links directly to the repo as of the commits where we left off today. Even after we add more commits tomorrow, these links will still point to this point in time.

## Homework (morning class)

* Store the flicks/dinosaurs in an array, as well as in the DOM.

### Mega Bonus Credit

* Add a promote/fav button, just like you did yesterday!
* Add a delete button, just like yesterday!

### Super Mega Bonus Credit

* Add buttons to move a flick/dinosaur up and down the list.

### Super Mega Bonus Credit Hyper Fighting

* Persist the flicks/dinosaurs data using `window.localstorage`.  The flicks/dinosaurs should stay in the list even when the page is refreshed.
