+++
date = "2017-06-06T09:46:51-04:00"
title = "Day 2: Functions and Objects"
prev="week1/day1"
toc = true
weight = 2

+++

<date>Tuesday, June 6, 2017</date>

## Lecture Videos

Morning:

* [Full Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [Day 2, part 1](https://www.youtube.com/watch?v=lpEy_5sNFIs&index=7&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [2](https://www.youtube.com/watch?v=DQtDHjBlE1U&index=8&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [3](https://www.youtube.com/watch?v=Fq6wX8ntapk&index=9&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [4](https://www.youtube.com/watch?v=3VCPCD_cZfA&index=10&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [5](https://www.youtube.com/watch?v=qaguvzM0MkI&index=11&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [6](https://www.youtube.com/watch?v=zvw7yIHZKfY&index=12&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [7](https://www.youtube.com/watch?v=8MOUnB_IZaA&index=13&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [8](https://www.youtube.com/watch?v=lw9iupqUtE8&index=14&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [9](https://www.youtube.com/watch?v=c-BmDlC5gfE&index=15&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [10](https://www.youtube.com/watch?v=dzC5Bh3GHTg&index=16&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [11](https://www.youtube.com/watch?v=Hc-Q8soQBSY&index=17&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [12](https://www.youtube.com/watch?v=4IpnBM9y2m0&index=18&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [13](https://www.youtube.com/watch?v=iqybKJbldRk&index=19&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84)
 
Afternoon:

* [Full Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [Day2, part 1](https://www.youtube.com/watch?v=bqFQy5hmFrY&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa&index=10) | [2](https://www.youtube.com/watch?v=lOVD50uiZo0&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa&index=11) | [3](https://www.youtube.com/watch?v=jW-3hIwbLbM&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa&index=12) | [4](https://www.youtube.com/watch?v=U6suwuSPMAg&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa&index=13) | [5](https://www.youtube.com/watch?v=I5lfMhtHC3w&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa&index=14) | [6](https://www.youtube.com/watch?v=Y7P4dSscHQE&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa&index=15) | [7](https://www.youtube.com/watch?v=_NdxK_0stYw&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa&index=16) | [8](https://www.youtube.com/watch?v=j_KgLgNsbGA&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa&index=17) | [9](https://www.youtube.com/watch?v=zYdC9C8-JH4&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa&index=18) | [10](https://www.youtube.com/watch?v=kvtWoczuzHE&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa&index=19) | [11](https://www.youtube.com/watch?v=Oh2GwnmYFi8&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa&index=20) | [12]() | [13]() | [14]() | [15]()
 
## Topics

### Functions
* Function Expressions
* Function Declarations
* Functions as Object properties (methods)
* Variable Scope (`var`, `const`, `let`)

### Objects
* Object literals
* Property Naming
* Retrieving property values
* Setting property values

### Arrays
* `Array.map` - [Docs on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map?v=control)
* [Understanding JavaScript's `map()`](https://www.discovermeteor.com/blog/understanding-javascript-map/) blog post

### DOM
* Adding HTML content to an existing element with `someElement.innerHTML`
* Creating elements with `document.createElement`
* Setting style properties with `someElement.style.stylePropertyName`
* Appending child elements with `someElement.appendChild`
* [REM vs EM - The Great Debate](https://zellwk.com/blog/rem-vs-em/)

## Examples

### Functions
{{< code js >}}
  // function declaration - use 'function' keyword
  function aMostExcellentFunction() {
    console.log('This function is great!')
  }

  aMostExcellentFunction() // => 'This function is great!'

  // function expression - defines a function as part of a larger expression syntax
  // (usually assignment to a variable)
  const anotherExcellentFunction = () => {
    console.log('This function is also great!')
  }

  anotherExcellentFunction() // => 'This function is also great!'

  // functions as object properties (also known as 'methods')
  const myObject = {
    myMethod() {
      console.log('I am a method!')
    }
  }

  myObject.myMethod() // => 'I am a method!'
{{< /code >}}

### Variable Scope
The biggest difference between `var` and `let` is that `var` variables are scoped to the _function_ in which they are declared, while `let` variables are scoped to the _block_ in which they are declared.  One of the easiest examples to see this behavior is in a simple `for` loop.

{{< code js >}}
function loopStuff() {
  for (var i = 0; i < 5; i++) {
    // do stuff in the loop
  }
  console.log(i)
}

loopStuff() // => 5

function loopMoreStuff() {
  for (let i = 0; i < 5; i++) {
    // do stuff in the loop
  }
  console.log(i)
}

loopMoreStuff() // => Uncaught ReferenceError: i is not defined
{{< /code >}}

In the function `loopStuff`, `var i` is still available outside the `for` loop so it can be logged to the console.  It is scoped to the function itself.

In the function `loopMoreStuff`, `let i` is not available outside the block it is scoped to (the `for` loop).

The main difference between `const` and `var`/`let` is that `const` cannot be reassigned.
{{< code js >}}
let variableOne = 4
variableOne = 5

var variableTwo = 4
variableTwo = 5

const variableThree = 4
variableThree = 5 // => Uncaught TypeError: Assignment to constant variable
{{< /code >}}

{{% aside tip "Default to using const" %}}
Always use `const` as your default way to declare variables, unless you know specifically that you will need to reassign it, in which case use `let`.  You should rarely, if ever, use `var`.  For further reading, check out [this article](https://medium.com/javascript-scene/javascript-es6-var-let-or-const-ba58b8dcde75)
{{% /aside %}}

### Objects
Almost everything in JavaScript is an Object.  The easiest way to create new Objects is with the [object initializer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object_initializer), more commonly known as 'object literal' syntax.  Basically, use curly braces to make an object `{}` and fill in the properties that you want.

Objects contain `key`/`value` pairs that allow you to set and retrieve values from them.

{{< code js >}}
// create a new object and assign some properties
const myObject = {
  prop1: 'Hello there',
  prop2: 42
}

// access the values in several ways, usually 'dot' or 'square bracket' notation
myObject.prop1 // => 'Hello there'
myObject['prop1'] //=> 'Hello there'

// new key/value pairs can also be assigned with these notations
myObject.prop3 = 'New Value!'
myObject['prop4'] = 'Newest Value!'

console.log(myObject)
// { 
//   prop1: 'Hello there',
//   prop2: 42,
//   prop3: 'New Value!',
//   prop4: 'Newest Value!'
// }
{{< /code >}}

### Arrays
Arrays are extremely useful data structures in JavaScript, as they can be easily iterated and transformed through methods like `map`, `filter`, and `reduce`.  Sometimes, you may have an 'array-like' collection (like a `NodeList` or function arguments) that you would need to convert to an actual Array before you could use these methods.  This can be done using `Array.from`

{{< code js >}}
let paragraphs = document.querySelectorAll('p')
paragraphs.map((paragraph) => {
  p.textContent = "This won't work because paragraphs is a NodeList, not Array!"
})
// => Uncaught TypeError: paragraphs.map is not a function

let actualArrayOfParagraphs = Array.from(paragraphs)
actualArrayOfParagraphs.map((paragraph) => {
  p.textContent = "This totally does work because we created an Array from our NodeList!"
})
{{< /code >}}

{{% aside info "Requirements for 'Array.from'" %}}
What objects can you convert to an Array using 'Array.from'?  

* Any array-like object with a 'length' property and indexed elements
* Iterable objects (like Map or Set)

For more info, check out [this article](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from?v=control) on MDN.
{{% /aside %}}

### DOM
If we start with the following markup:
{{< code html >}}
&lt;div id=&quot;my-div&quot;&gt;&lt;/div&gt;
{{< /code >}}
We can add additional markup to it programmatically using JavaScript.  One way is to create new HTMl elements using `document.createElement`, and adding them by using `appendChild`.  Styling of the element can even be changed by manipulating the element's `style` property.

{{< code js >}}
// create an h1 and modify text content and color
const heading = document.createElement('h1')
heading.textContent = "This is the best heading I've ever seen"
heading.style.color = "red"

// get a reference to the existing div and add the heading as a child element
const div = document.querySelector('#my-div')
div.appendChild(heading)
{{< /code >}}

This will produce the following markup:
{{< code html >}}
&lt;div id=&quot;my-div&quot;&gt;
  &lt;h1 style=&quot;color: red;&quot;&gt;This is the best heading I've ever seen&lt;/h1&gt;
&lt;/div&gt;
{{< /code >}}

## Presentations

* [Review: HTML and the DOM](/02-html-dom.pdf)

## Projects

### People Factory
[Morning](https://github.com/xtbc17s2/people-factory/tree/a6ecc8a2621c9d4ae9aaf3ad17a38b4c40855d0c) | [Afternoon](https://github.com/xtbc17s2/people-factory/tree/8056051f609dd9b0a90e5b63014d557e7d6c669b)

## Homework

Create a new project from scratch that meets the following requirements:

### Baseline Goal

* User can enter a thing (_e.g._ dinosaur, Jeff Goldblum movie) to be added to the list.
* Thing will be added to the end of the list.

### Bonus Credit

* Add things to the top of the list instead of the bottom.

### Super Mega Bonus Credit

* Add a _promote_ button to every list item that changes the appearance (_e.g._ changes the background color, adds a border, etc.) of that item when clicked.

### Super Mega Bonus Credit Hyper Fighting

* Add a _delete_ button to every list item that removes the name from the list when clicked.

