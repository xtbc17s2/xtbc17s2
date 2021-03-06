+++
date = "2017-05-15T11:13:46-04:00"
title = "Day 7: React"
prev="/week2/day6/"
next="/week2/day8/"
toc = true
weight = 3

+++

<date>Wednesday, June 14, 2017</date>

## Lecture Videos

Morning:

* [Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [Day 7, part 1](https://www.youtube.com/watch?v=Vd5CsyRX91A&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=55) | [2](https://www.youtube.com/watch?v=8opVQik2j2w&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=56) | [3](https://www.youtube.com/watch?v=SzHq8aXcb3M&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=57) | [4](https://www.youtube.com/watch?v=Yhb5zNq5MoU&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=58) | [5](https://www.youtube.com/watch?v=uVO4nLeAplI&index=59&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [6](https://www.youtube.com/watch?v=kXCIQD4inzs&index=60&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) [7](https://www.youtube.com/watch?v=f6f-LSxe2Bw&index=61&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [8](https://www.youtube.com/watch?v=oOLsyokpoGI&index=62&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84)

Afternoon:

* [Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [Day 7, part 1](https://www.youtube.com/watch?v=03H9Wn4j97E&index=71&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [2](https://www.youtube.com/watch?v=0Vs_z1B1l0U&index=72&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [3](https://www.youtube.com/watch?v=pyYEmbhcRAQ&index=73&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [4](https://www.youtube.com/watch?v=TKZ0s9VizIw&index=74&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [5](https://www.youtube.com/watch?v=FeBfAzbgvAw&index=75&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [6](https://www.youtube.com/watch?v=nOtm_sq680Q&index=76&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [7](https://www.youtube.com/watch?v=2NQ1ZyMTuAg&index=77&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [8](https://www.youtube.com/watch?v=PvEyGL5Ol7U&index=78&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [9](https://www.youtube.com/watch?v=ci0ftNKqLbE&index=79&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [10](https://www.youtube.com/watch?v=o_vEij-aMoY&index=80&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [11](https://www.youtube.com/watch?v=yNwDf-YK-i0&index=81&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa)

## Topics

### GitHub Pages

* [Getting Started With GitHub Pages](https://guides.github.com/features/pages/)

### [React](https://facebook.github.io/react/)

* Using `map` with components
* Stateless Functional Components
  * [Functional Stateless Components in React](http://javascriptplayground.com/blog/2017/03/functional-stateless-components-react/)
  * [Functional Components vs. Stateless Functional Components vs. Stateless Components](https://tylermcginnis.com/functional-components-vs-stateless-functional-components-vs-stateless-components/)
  * [Nine Wins You Might Have Overlooked](https://hackernoon.com/react-stateless-functional-components-nine-wins-you-might-have-overlooked-997b0d933dbc)
* Conditional rendering
* [Controlled](https://facebook.github.io/react/docs/forms.html) vs [Uncontrolled](https://facebook.github.io/react/docs/uncontrolled-components.html) Forms
* [Controlled and uncontrolled form inputs in React don't have to be complicated](https://goshakkk.name/controlled-vs-uncontrolled-inputs-react/)

### JavaScript

* Named and default exports
* Named and default imports
* Spread operator

### Package Managers

* [NPM](https://www.npmjs.com/) - Node Package Manager
* [Yarn](https://code.facebook.com/posts/1840075619545360) - Facebook's version of npm

## Examples

### React

#### Using `map` with Components

**[See this example live on CodePen →](https://codepen.io/dstrus/pen/gWZVOQ?editors=0010#0)**

**Person.js**

{{< code jsx >}}
class Person extends React.Component {
  render() {
    return (
      &lt;li&gt;Hello, {this.props.person.name}!&lt;/li&gt;
    )
  }
}

export default Person
{{< /code >}}

**PersonList.js**

{{< code jsx >}}
import Person from './Person'

class PersonList extends React.Component {
  render() {
    const people = [
      { name: 'Seth', hair: 'blonde' },
      { name: 'Nichole', hair: 'long' },
      { name: 'Davey', hair: 'long gone' }
    ]
    return (
      &lt;div&gt;
        &lt;h2&gt;People&lt;/h2&gt;
        {
          people.map((person => &lt;Person person={person} /&gt;))
        }
      &lt;/div&gt;
    )
  }
}

export default PersonList
{{< /code >}}

#### Stateless Functional Components

Not every React Component needs to have state.  Many simply render a bit of `props` and UI.  For such components, we don't need to instantiate a whole class that inherits from `React.Component`, we can simply write a function that accepts `props` as an argument and returns the markup we need.

For instance, in the previous example, the `Person` component can easily be re-written as a Stateless Functional Component.

{{< code jsx >}}
function Person (props) {
  return (
    &lt;li&gt;Hello, {props.person.name}!&lt;/li&gt;
  )
}

// Or...

const Person = (props) => &lt;li&gt;Hello, {props.person.name}!&lt;/li&gt;
{{< /code >}}

#### Conditional Rendering

There are many instances where you may want to render different UI depending on the state of the application.  One example would be a button that shows "Log in" or "Log out", depending on whether there is a currently logged-in user.

Since React is just JavaScript, we can conditionally render using `if`/`else` statements, or we also learned about the [*ternary operator*](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator).

{{< code js >}}
const condition = true

if (condition) {
  console.log('true!')
} else {
  console.log('false!')
}
// => 'true!'

condition ? console.log('true!') : console.log('false!')
// => 'true!'
{{< /code >}}

An example in React:

{{< code jsx >}}
function UserButton (props) {
  return (
    {props.loggedInUser ? &lt;button&gt;Log out&lt;/button&gt; : &lt;button&gt;Log in&lt;/button&gt;}
  )
}
{{< /code >}}

### JavaScript (ES6+)

#### Named and default exports and imports

Prior to ES6, there were many competing ways to export and import JavaScript modules.  The most common were [CommonJS](https://webpack.github.io/docs/commonjs.html) and [AMD](http://requirejs.org/docs/whyamd.html).  Luckily ES6 defined a specification for standardizing module export and import.

There are two types of exports from any JS file - *named* and *default*.  The important thing to remember is that there can only be *one* default export per module, but there can be as many named exports as you want.

**myModule.js**
{{< code js >}}
export const myNumber = 8

export function sayHi () {
  console.log('hello')
}

export default class MyClass {
  add (a, b) {
    return a + b
  }
}
{{< /code >}}

The main difference is how they are imported.  Default exports get the most concise syntax:

{{< code js >}}
import MyClass from 'myModule'

const classInstance = new MyClass()
classInstance.add(1, 2) // => 3
{{< /code >}}

{{% aside info "Default import naming" %}}
Since there can be only one default export per module, the name by which you import the default export is not important - you can name it whatever you want.  For instance, instead of importing as `MyClass`, we could have said `import LuftBallons from 'myModule'`, and it would have worked just fine.  To read more about default and named exports, click [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export).
{{% /aside %}}

Named exports get a slightly more verbose syntax for importing, and the names _are_ important (otherwise it can't determine what you want to import).

{{< code js >}}
import { myNumber, sayHi } from 'myModule'

console.log(myNumber) // => 8

sayHi() // => 'hello'
{{< /code >}}

If you need to import a named export under a different name&mdash;if, for example, you have another import or local variable with the same name&mdash;you can specifiy a different name using _as_.

{{< code js >}}
import { myNumber as num, sayHi as yo } from 'myModule'

console.log(num) // => 8

yo() // => 'hello'
{{< /code >}}

You can also combine default and named imports in the same line.

{{< code js >}}
import MyClass, { myNumber, sayHi } from 'myModule'
{{< /code >}}

#### Spread operator

The [*spread operator*](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_operator) was added in ES6 to allow an expression to be expanded in places where multiple arguments (for function calls) or multiple elements (for array literals) or multiple variables (for destructuring assignment) are expected.

{{< code js >}}
function myFunc (x, y, z) {
  console.log(x)
  console.log(y)
  console.log(z)
}
const args = [1, 2, 3]

myFunc(...args) // the spread '...args' applies the items in args to the three arguments in myFunc
// => 1
// => 2
// => 3
{{< /code >}}

It is also an easy way to make copies of iterable objects

{{< code js >}}
const ary = [1, 2, 3]
const aryCopy = [...ary] // makes a copy of ary
{{< /code >}}

If you are in a project using Babel (like a React project created with `create-react-app`), you can also use the `object-rest-spread-transform` to apply this same method to objects.

{{< code js >}}
this.state = {'a': true, party: 'hard'}
const stateCopy = {...this.state} // makes a copy of this.state
{{< /code >}}

### Package Managers

#### Node Package Manager (npm)

Node Package Manager hosts almost half a million packages of free, reusable JavaScript code and is the largest software registry in the world. It allows you to easily add any module to your project, and it will install the requested package, as well as any required dependencies of that package.

{{< term >}}
npm install react
{{< /term >}}

#### Yarn

[Yarn](https://code.facebook.com/posts/1840075619545360) is Facebook's version of npm, designed to improve performance and resolve several important issues.  The key differences are:

* Deterministic installation - packages will always install in the same order on every machine
* `yarn.lock` - this lockfile locks dependency versions for consistency and security
* Local cache of downloaded packages - faster and can still work with no internet connection after initial installation
* Parallel installation - Dependency installation can happen in parallel, greatly increasing speed

To install yarn (npm was already installed as part of setup instructions), type the following command (Mac):

{{< term >}}
brew install yarn
{{< /term >}}

Or on Windows, [download the installer](https://yarnpkg.com/latest.msi).

Once installed, you can use yarn with following commands:

{{< term >}}
yarn
# installs all packages and dependencies listed in your project's package.json

yarn add {package_name}
# installs a new package and adds it to package.json

yarn start
# starts your local development web server (in project from create-react-app)
{{< /term >}}

## Projects

* [Dwarf Underground](https://github.com/xtbc17s2/dwarf-underground/)
* Noteherder [morning](https://github.com/xtbc17s2/noteherder/tree/08fc517b51ebed3814156603333b2f92ce44d881) | [afternoon](https://github.com/xtbc17s2/noteherder/tree/a7ba41613b241e7578ff18e1f6a98bd341285dea)

## Day 7 Homework

Finish making these components look acceptable.

### Bonus Credit

* Make the form work!

### Super Mega Bonus Credit

* Make a working _delete_ button.

### Super Mega Bonus Credit Hyper Fighting

* When you click on a note in the list, populate the form with the data from that note.
