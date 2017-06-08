+++
date = "2017-06-08T09:55:27-04:00"
title = "Day 4: LocalStorage and JavaScript Classes"
prev="week1/day3"
toc = true
weight = 4

+++

<date>Thursday, June 8, 2017</date>

## Lecture Videos

Morning:

* [Full Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [Day 4, part 1]() | [2]() | [3]() | [4]() | [5]() | [6]() | [7]()

Afternoon:

* [Full Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [Day 4, part 1]() | [2]() | [3]() | [4]() | [5]() | [6]() | [7]() | [8]() | [9]() | [10]() | [11]()

## Topics

### DOM Manipulation

* [data attributes](https://developer.mozilla.org/en-US/docs/Learn/HTML/Howto/Use_data_attributes)
* [parentElement](https://developer.mozilla.org/en-US/docs/Web/API/Node/parentElement)
* [childNodes](https://developer.mozilla.org/en-US/docs/Web/API/Node/childNodes)
* [firstChild](https://developer.mozilla.org/en-US/docs/Web/API/Node/firstChild)
* [firstElementChild](https://developer.mozilla.org/en-US/docs/Web/API/ParentNode/firstElementChild)
* [insertBefore](https://developer.mozilla.org/en-US/docs/Web/API/Node/insertBefore)
* [closest](https://developer.mozilla.org/en-US/docs/Web/API/Element/closest) (experimental)

### `localStorage` [↓](#localstorage)
* [Using `localStorage`]((https://www.smashingmagazine.com/2010/10/local-storage-and-how-to-use-it/))
* `JSON.stringify`
  * [Using `JSON.stringify`](http://www.dyn-web.com/tutorials/php-js/json/stringify.php)
  * [Live example](http://jsfiddle.net/queryj/hLkUz/)
  * [API reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify), including optional arguments for whitelisting properties and transforming the data as it's stringified
* `JSON.parse`
  * [Using `JSON.parse`](http://www.dyn-web.com/tutorials/php-js/json/parse.php)
  * [API reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse), including optional argument for transforming the data as it's parsed

### Font Awesome [↓](#font-awesome)
* [Docs](http://fontawesome.io/)
* [Examples](http://fontawesome.io/examples/)
* [Icon list](http://fontawesome.io/icons/)
* [Font Awesome intro](http://www.w3schools.com/icons/fontawesome_icons_intro.asp) on w3schools, including a live editor
* [Icon Fonts &amp; Accessibility](http://fontawesome.io/accessibility/)

### Foundation
* [Button](http://foundation.zurb.com/sites/docs/button.html)
* [Button Group](http://foundation.zurb.com/sites/docs/button-group.html)
* [Forms](http://foundation.zurb.com/sites/docs/forms.html)

### CSS Selectors
**[Child and sibling selectors](https://css-tricks.com/child-and-sibling-selectors/)**

* [Descendant selector (_space_)](https://css-tricks.com/almanac/selectors/d/descendant/)
* [`>` combinator - child selector](https://css-tricks.com/almanac/selectors/c/child/)
* [`+` combinator - adjacent sibling selector)](https://css-tricks.com/almanac/selectors/a/adjacent-sibling/)
* [`:first-child` pseudo-class selector](https://css-tricks.com/almanac/selectors/f/first-child/)
* [`:last-child` pseudo-class selector](https://css-tricks.com/almanac/selectors/l/last-child/)

### Array methods
* [`Array.prototype` documentation on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/prototype?v=control)
* [`reverse()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse?v=control)
* `find()` - [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find?v=control) | [w3schools](https://www.w3schools.com/jsref/jsref_find.asp)
* `findIndex()` - [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex?v=control) | [w3schools](https://www.w3schools.com/jsref/jsref_findindex.asp)

### JavaScript Classes [↓](#javascript-classes)
* Class declarations
* The `constructor` function
* Methods
* Instantiating objects from a class

### Chrome Developer Tools
* [Accessing recently inspected elements with `$0`-`$4`](https://willd.me/posts/0-in-chrome-dev-tools) ([official docs](https://developers.google.com/web/tools/chrome-devtools/console/command-line-reference#0_-_4))
* [Inspecting storage from the _Application_ panel](https://developers.google.com/web/tools/chrome-devtools/manage-data/local-storage)

## Examples

### Data Attributes

HTML5 gave us a way to save extra information on a standard HTML Element via the `data-*` attributes. Basically, you can add any arbitrary information you want, prefixing the name of the attribute with `data-`.  This data is then accessible through JavaScript via the `someElement.dataset` object, or through CSS via `attr(data-*)`.

{{< code html >}}
&lt;div
  id="my-div"
  data-name="Awesome div"
  data-id="div-1234"
  data-color="blue"
  data-marshmallows="yummy"&gt;
&lt;/div&gt;
{{< /code >}}

{{< code js >}}
const myDiv = document.querySelector('#my-div')

myDiv.dataset.name            // "Awesome div"
myDiv.dataset.data-id         // "div-1234"
myDiv.dataset.color           // "blue"
myDiv.dataset.marshmallows    // "yummy"
{{< /code >}}

{{< code css >}}
#my-div {
  background-color: attr(data-color);
}

div[data-id='div-1234'] {
  height: 400px;
  width: 400px;
}
{{< /code >}}

### localStorage

`localStorage` is storage in your web browser that conforms to Web Storage API.  It is scoped by domain, meaning other websites cannot access data stored by your website and vice versa.  The data in `localStorage` persists in the browser until removed, even if the browser is closed and re-opened.

To set an item, use `localStorage.setItem`, and retrieve data using `localStorage.getItem`.  It is important to remember that values stored will always be strings, so it may be use necessary to use the `JSON.stringify` and `JSON.parse` methods to set and retrieve non-string data.  JSON stands for **J**ava**S**cript **O**bject **N**otation.  To learn more about JSON, click [here](https://www.w3schools.com/js/js_json_intro.asp).

{{< code js >}}
const myObject = {
  thisIsCool: true
}

localStorage.setItem('myObject', myObject)
localStorage.getItem('myObject') // => "[object Object]"
// localStorage saves the result of the implicit myObject.toString() call

localStorage.setItem('myObject', JSON.stringify(myObject))
// calling JSON.stringify converts the object to a JSON string representation
// so it can be stored in localStorage without loss of data

const retrievedObject = localStorage.getItem('myObject') // => "{"thisIsCool":true}"
JSON.parse(retrievedObject) // => {thisIsCool: true}
// JSON.parse converts the retrieved JSON string back into a JavaScript object
{{< /code >}}

### Font Awesome

Font Awesome provides hundreds of vectorized, professional-looking icons for free.  Once you have the Font Awesome stylesheet downloaded and included in your project, use `<i>` tags with appropriate classes to render the icons you want.

{{< code html >}}
&lt;-- Sample link tag to include Font Awesome in HTML --&gt;
&lt;link rel=&quot;stylesheet&quot; href=&quot;css/font-awesome.min.css&quot;&gt;&lt;i&gt;

&lt;-- Renders a sweet camera icon --&gt;
&lt;i class=&quot;fa fa-camera-retro&quot;&gt;&lt;/i&gt;
{{< /code >}}

### CSS Selectors

{{< code html >}}
&lt;div&gt;
  &lt;p&gt;paragraph one&lt;/p&gt;
  &lt;p&gt;paragraph two&lt;/p&gt;
  &lt;p&gt;paragraph three&lt;/p&gt;
&lt;/div&gt;
&lt;p&gt;paragraph four&lt;/p&gt;
{{< /code >}}

{{< code css >}}
p:first-child {
  /* selects any paragraph that is the first child of its parent (paragraph one) */
}

p:last-child {
  /* selects any paragraph that is the last child of its parent (paragraph three) */
}

div > p {
  /* selects any paragraph that is a direct child of a div (paragraphs one, two, and three) */
}
{{< /code >}}

### JavaScript Classes

JavaScript is not a class-based language like C++, Java, or Ruby.  It uses [prototypal inheritance](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain) instead.  However, as of ES2015, the `class` keyword was added to the language to provide a more concise syntax and similarity to popular class-based languages.

A class is essentially a constructor of Objects.  Methods and properties in the class will be inherited by each object that is constructed by the class.  Object instances are created by using the `new` keyword.  Classes have a `constructor` method, which is called when instances are created and allows for configuration of the object.

{{< code js >}}
class Dog {
  constructor() {
    this.furColor = 'brown'
  }

  bark() {
    console.log('WOOF')
  }
}

const bowser = new Dog();
bowser.furColor // => 'brown'
bowser.bark()   // => 'WOOF'
{{< /code >}}

Classes can also inherit from another class.  Inheritance is specified using the `extends` keyword.  When a class inherits from another, it has access to the methods and properties of *both* classes, although if both classes implement the *same* property or method, the child class will take precedence.

{{< code js >}}
class Animal {
  constructor() {
    this.furColor = 'brown'
  }

  speak() {
    console.log('Some sort of noise')
  }
}

class Dog extends Animal {
  constructor() {
    this.furColor = 'black'
  }

  bark() {
    console.log('WOOF')
  }
}

const bowser = new Dog()
bowser.furColor // => 'black'
bowser.speak()  // => 'Some sort of noise'
bowser.bark()   // => 'WOOF'

const rodent = new Animal()
rodent.furColor // => 'brown'
rodent.speak()  // => 'Some sort of noise'
rodent.bark()   // => Uncaught TypeError: rodent.bark is not a function
{{< /code >}}


## Presentations

* [Review: Objects and Functions](/03-review-objects-and-functions.pdf)
* [Intro to localStorage](/04-local-storage.pdf)

## Projects

[Jeffervescence (morning)](https://github.com/xtbc17s2/jeffervescence/tree/f55636b0c73de7469f17b659fcde8f4f5416aa8a) | [Dinoplasty (afternoon)](https://github.com/xtbc17s2/dinoplasty/tree/a3e44eaef9a01b840aafb43ce37e64b05eb9a739)

## Homework

### Base Requirement

* Fix the issue with flick id values, which sometimes results in removing the wrong flick from the array (and thus from local storage).

### Bonus Credit

* Also track the year the flick was realeased
* Make it look nice (CSS!)

### Super Mega Bonus Credit

* Edit the names of flicks that are already in the list (and make sure the changes persist across page loads).  Gee, it would be nice if we could make that span's _content editable_ somehow...

### Super Mega Bonus Credit Hyper Fighting

* Have a good weekend!
