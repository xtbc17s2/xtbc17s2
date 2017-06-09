+++
date = "2017-06-08T09:55:27-04:00"
title = "Day 4: LocalStorage"
prev="week1/day3"
toc = true
weight = 4

+++

<date>Thursday, June 8, 2017</date>

## Lecture Videos

Morning:

* [Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [Day 4, part 1](https://www.youtube.com/watch?v=hx2_dkHtC7A&index=33&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [2](https://www.youtube.com/watch?v=CN_zGBwsgz8&index=34&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [3](https://www.youtube.com/watch?v=knVNVyIK7Oc&index=35&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [4](https://www.youtube.com/watch?v=DMHgX3rFDA4&index=36&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [5](https://www.youtube.com/watch?v=drroTX14F68&index=37&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [6](https://www.youtube.com/watch?v=hetO7LTqJd0&index=38&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [7](https://www.youtube.com/watch?v=xzGnGSuIREs&index=39&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [8](https://www.youtube.com/watch?v=StjjjAkwfs4&index=40&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [9](https://www.youtube.com/watch?v=8WKBjqerA7Y&index=41&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [10](https://www.youtube.com/watch?v=jOF4ejEMRWw&index=42&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84)

Afternoon:

* [Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [Day 4, part 1](https://www.youtube.com/watch?v=WmMoHgsVEb0&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa&index=39) | [2]() | [3]() | [4]() | [5]() | [6]() | [7]() | [8]() | [9]() | [10]() | [11]()

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

### Foundation
* [Button](http://foundation.zurb.com/sites/docs/button.html)
* [Button Group](http://foundation.zurb.com/sites/docs/button-group.html)
* [Un-bulleted List](http://foundation.zurb.com/sites/docs/typography-helpers.html#un-bulleted-list)

### CSS Selectors
* [Attribute selectors](https://css-tricks.com/attribute-selectors/)

### Array methods
* [`Array.prototype` documentation on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/prototype?v=control)
* [`unshift()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift?v=control)
* [`reverse()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse?v=control)

### Chrome Developer Tools
* [Inspecting storage from the _Application_ panel](https://developers.google.com/web/tools/chrome-devtools/manage-data/local-storage)

## Examples

### `this`

The same function can have different values for `this` depending on how the function is called/invoked.

[Try this example live on CodePen.](https://codepen.io/dstrus/pen/XgmLyv)

{{< code js >}}
const app = {
  sayYeah() {
    console.log(`Yeah, ${this}`)
  },
  
  toString() {
    return 'app object'
  }
}

// When invoked as a method
app.sayYeah() // "Yeah, app object"

// When invoked as an event handler
document
  .querySelector('button')
  .addEventListener('click', app.sayYeah)
  // "Yeah, [object HTMLButtonElement]"

// When manually set with bind
app.sayYeah.bind('w00t')() // "Yeah, w00t"
{{< /code >}}

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

## Presentations

* [Review: Objects and Functions](/03-review-objects-and-functions.pdf)

## Projects

[Jeffervescence (morning)](https://github.com/xtbc17s2/jeffervescence/tree/4532fa3776d1d51912aabfa4d3932625e2e64b6d) | [Dinoplasty (afternoon)](https://github.com/xtbc17s2/dinoplasty/tree/fe3c1fd291393f5db7b3fc5ab1d7d3688974b7ca)

## Homework

### Base Requirement

* Fix the issue with flick / dino id values, which sometimes results in removing the wrong item from the array (and thus from local storage).
* Complete any previous homework levels that are not yet done

### Bonus Credit

* Also track the year the flick was released (Jeffervescence), or additional information about the dino (Dinoplasty)
* Make it look nice (CSS!)

### Super Mega Bonus Credit

* Edit the names of flicks / dinos that are already in the list (and make sure the changes persist across page loads).  Gee, it would be nice if we could make that span's _content editable_ somehow...

### Super Mega Bonus Credit Hyper Fighting

* Have a good weekend!
