+++
date = "2017-05-15T11:13:46-04:00"
title = "Day 7: Firebase"
prev="/week2/day7/"
toc = true
weight = 4

+++

<date>Thursday, June 15, 2017</date>

## Lecture Videos

Morning:

* [Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [Day 8, part 1]() | [2]() | [3]() | [4]() | [5]() | [6]() [7]() | [8]() | [9]() | [10]() | [11]()

Afternoon:

* [Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [Day 8, part 1]() | [2]() | [3]() | [4]() | [5]() | [6]() | [7]() | [8]() | [9]() | [10]() | [11]()

## Topics

### React

* Methods as props
* Component lifecycle methods ([Docs](https://facebook.github.io/react/docs/react-component.html))
  * [`componentDidMount()`](https://facebook.github.io/react/docs/react-component.html#componentdidmount)

### JavaScript

* Destructuring assignment
* Property initializers (and arrow functions)

### Firebase

* Getting started
* Database rules
* Re-base for syncing React state with Firebase

## Examples

### React

#### Methods as props

Sometimes one component needs to update another component's state. It can't do that directly, but it can call a method from that other component if it's available via a prop.

[**Try this example live on CodePen**](https://codepen.io/dstrus/pen/bWzWew?editors=1010)

{{< code lang="jsx" line="5,23" class="line-numbers" >}}
import React from 'react'
import ReactDOM from 'react-dom'

const PartyButton = ({ celebrate, celebrations }) =&gt; {
  return &lt;button onClick={celebrate}&gt;Party! {celebrations}&lt;/button&gt;
}

class App extends React.Component {
  constructor() {
    super()
    this.state = {
      celebrations: 0,
    }
    this.celebrate = this.celebrate.bind(this)
  }

  celebrate() {
    const celebrations = this.state.celebrations + 1
    this.setState({ celebrations })
  }

  render() {
    return &lt;PartyButton celebrate={this.celebrate} celebrations={this.state.celebrations} /&gt;
  }
}

ReactDOM.render(&lt;App /&gt;, document.querySelector('main'))
{{< /code >}}

#### Component lifecycle methods

**`componentDidMount()`** is invoked immediately after a component is mounted. Initialization that requires DOM nodes should go here.

{{< code jsx >}}
import React, { Component } from 'react'

class MyComponent extends Component {
  componentDidMount() {
    this.nameInput.focus()
  }

  render() {
    return (
      &lt;input 
        ref={(input) =&gt; { this.nameInput = input; }} 
        defaultValue="will focus"
      /&gt;
    )
  }
}
{{< /code >}}

### JavaScript (ES6+)

#### Destructuring assignment

[Destructuring assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment) syntax is a JavaScript expression that makes it possible to unpack values from arrays, or properties from objects, into distinct variables.

{{< code js >}}
const myObj = {
  a: true,
  b: 'Destructuring!'
}

let { a, b } = myObj

console.log(a) // => true
console.log(b) // => 'Destructuring!'
{{< /code >}}

#### Property initializers

From the proposal:

> "Class instance fields" describe properties intended to exist on instances of a class (and may optionally include initializer expressions for said properties).

We can take advantage of this in React.

[**Read more: Using ES7 property initializers in React**](https://babeljs.io/blog/2015/06/07/react-on-es6-plus)

We can use a property initializer to set the initial value of state without writing a constructor:

{{< code jsx >}}
class Song extends React.Component {
  state = {
    versesRemaining: 5,
  }
}
{{< /code >}}

We can even set default props and use those in the initial state:

{{< code jsx >}}
class Song extends React.Component {
  static defaultProps = {
    autoPlay: false,
    verseCount: 10,
  }
  state = {
    versesRemaining: this.props.verseCount,
  }
}
{{< /code >}}

{{% aside danger "Subject to  minor changes" %}}
[Property initializers](https://github.com/tc39/proposal-class-public-fields) are a [Stage 2 proposal](https://tc39.github.io/process-document/) for ECMAScript, meaning that it's still a _draft_ and is subject to minor changes before becoming standardized. Facebook itself is already using these techniques in production, however.
{{% /aside %}}

#### Property initializers + arrow functions

Yesterday, we used property initializers to set a component's initial state without adding a constructor. Combining property initializers and arrow functions also gives us a convenient way to auto-bind `this`:

{{< code jsx >}}
class Something extends React.Component {
  handleButtonClick = (ev) => {
    // `this` is bound correctly!
    this.setState({ buttonWasClicked: true });
  }
}
{{< /code >}}

### Firebase

#### Getting Started

[Firebase](https://firebase.google.com/) is a real-time database hosted by Google.  In addition to the database, it also provides features of authentication, analytics, cloud storage, and hosting.  For _Thing List_, we synced the `state` of our app to our database on Firebase.  This allowed all of our data to be persisted, even after page refreshes.

[Re-base](https://github.com/tylermcginnis/re-base) is an open source package that allows easy syncing of local state with a Firebase database. Add rebase to your project with one of the following commands:

{{< term >}}
yarn add re-base               # add package using yarn
npm install --save re-base     # add package using npm
{{< /term >}}

Once you have re-base installed, setup is easy!  First, create a new project on Firebase, then click on "Add to a web app" to see your JavaScript config object.  Next, initialize a Firebase app and database in your project using the config object, and provide the database to re-base.

{{< code js >}}
import Rebase from 're-base'
import firebase from 'firebase/app'
import database from 'firebase/database'

const app = firebase.initializeApp({
  apiKey: "YOURAPIKEY",
  authDomain: "YOURAUTHDOMAIN",
  databaseURL: "YOURDATABASEURL",
  projectId: "YOURPROJECTID",
  storageBucket: "YOURSTORAGEBUCKET",
  messagingSenderId: "YOURSENDERID"
})

const db = database(app)
const base = Rebase.createClass(db)

export default base
{{< /code >}}

Finally, call `base.syncState` to sync your app's local state with Firebase.  The first argument to `syncState` is the name of the Firebase endpoint you want to sync, and the second is a configuration object.

{{< code js >}}
base.syncState('myFavoriteEndpoint', {
  context: this,
  state: 'items'
})
{{< /code >}}

Now, any time we update the state of our app, the changes will sync with Firebase in real time.

{{% aside info "More Re-base Options" %}}
Re-base can do much more than just syncing state.  There are methods for `fetch`, `push`, `post`, etc.  To find out more about what all you can do with re-base, check out the [README](https://github.com/tylermcginnis/re-base#re-base)
{{% /aside %}}

#### Rules

For your Firebase database, you can set up rules (written in JSON) that specify the conditions under which data is allowed to be read or written.  By default, a newly generated project will require that a user be authenticated to read or write _any_ data.

{{< code js >}}
{
  "rules": {
    ".read": "auth != null",
    ".write": "auth != null"
  }
}
{{< /code >}}

If you do not have authentication set up yet, these values can be set to `true`.  This allows _anyone_ to read or write any data in the database.  This can be convenient, but probably not a good idea long-term (and you _will_ get a warning if you do that).

Additional rules can be applied per endpoint:

{{< code js >}}
{
  "rules": {
    "emails": {
      ".read": true,
      ".write": "auth != null"
    },
    "texts": {
      ".read": true,
      ".write": "auth != null"
    },
    "users": {
      "$userId": {
        ".read": "auth != null && auth.uid == $userId",
        ".write": "auth != null && auth.uid == $userId"
      }
    }
  }
}
{{< /code >}}

The above rules translate to:

* texts and emails can be read by anyone, but only written by authenticated users
* users data can be read and written only by an authenticated user whose `uid` matches the `$userId` of that item

## Projects

* ThingList [morning](https://github.com/xtbc17s1/thing-list/tree/23bd5cd351313500c971d4fbded85a0fbc656c0f) | [afternoon](https://github.com/xtbc17s1/thing-list/tree/899e37a64952ec96d3b8756bd6077499764851b3)

## Homework

* When the checkbox is checked, mark the corresponding Thing as _completed_.
* Be sure this gets synced to Firebase and persists across page refreshes.

### Super Mega Bonus Credit

* Add a due date to each thing.
* Make sure it persists

**Hint**: HTML 5 includes an input type **date**, _i.e._ `<input type="date" />`
