+++
date = "2017-05-15T11:13:46-04:00"
title = "Day 8: Props and Destructuring"
prev="/week2/day7/"
toc = true
weight = 4

+++

<date>Thursday, June 15, 2017</date>

## Lecture Videos

Morning:

* [Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [Day 8, part 1](https://www.youtube.com/watch?v=sONty6TCQQI&index=63&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [2](https://www.youtube.com/watch?v=b_FlbuzvNVc&index=64&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [3](https://www.youtube.com/watch?v=wqUC6_5HWpo&index=65&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [4](https://www.youtube.com/watch?v=nc14iaOPgGg&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=66) | [5](https://www.youtube.com/watch?v=B-MB7vTKMJo&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=67) | [6](https://www.youtube.com/watch?v=vnNYG00P2G4&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=68) [7](https://www.youtube.com/watch?v=4_uPb5ETF48&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=69) | [8](https://www.youtube.com/watch?v=YuqSI0BupbQ&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=70) | [9](https://www.youtube.com/watch?v=w4VaKGQOTqk&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=71) | [10](https://www.youtube.com/watch?v=D1XSqnNbNBE&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=72)

Afternoon:

* [Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [Day 8, part 1](https://www.youtube.com/watch?v=3WU51t1U8F0&index=82&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [2](https://www.youtube.com/watch?v=K6VQsvhOeCo&index=83&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [3](https://www.youtube.com/watch?v=_Qm6fMaljtg&index=84&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [4](https://www.youtube.com/watch?v=TtfqQFsFxbc&index=85&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [5](https://www.youtube.com/watch?v=UFw3hMsdCxc&index=86&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [6](https://www.youtube.com/watch?v=-0Hz3StubvQ&index=87&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [7](https://www.youtube.com/watch?v=74LnKRKU7e8&index=88&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [8](https://www.youtube.com/watch?v=jdJR9WOU1vs&index=89&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [9](https://www.youtube.com/watch?v=h3J-oZawyq8&index=90&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [10](https://www.youtube.com/watch?v=d6DbNn41sIU&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa&index=91) | [11](https://www.youtube.com/watch?v=FZD4vcLW8EI&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa&index=92)

## Topics

### React

* Methods as props
* Component lifecycle methods ([Docs](https://facebook.github.io/react/docs/react-component.html))
  * [`componentDidMount()`](https://facebook.github.io/react/docs/react-component.html#componentdidmount)

### JavaScript

* Destructuring assignment
* Property initializers (and arrow functions)

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

Combining property initializers and arrow functions gives us a convenient way to auto-bind `this`, since arrow functions inherit `this` from the scope in which they are declared (lexical scoping):

{{< code jsx >}}
class Something extends React.Component {
  handleButtonClick = (ev) => {
    // `this` is bound correctly!
    this.setState({ buttonWasClicked: true });
  }
}
{{< /code >}}

## Projects

* Noteherder [morning](https://github.com/xtbc17s2/noteherder/tree/a87cefc6d20c718be2f42405b20d3d340b136e72) | [afternoon](https://github.com/xtbc17s2/noteherder/tree/436da21e0b53cff727f1af6be78dded4a31cc966)

## Homework

Finish all the bonus work from yesterday.

* Make a working _delete_ button.
* When you click on a note in the list, populate the form with the data from that note.

### Super Mega Bonus Credit

* Make the _new note_ button in `Sidebar` clear out the form with a blank note. (Then you can get rid of the _save and new_ button in `NoteForm`).

### Super Mega Bonus Credit Hyper Fighting

* Have a nice weekend!
