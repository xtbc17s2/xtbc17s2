+++
date = "2017-05-30T09:40:47-04:00"
title = "Routing and Fetching"
prev = "/week3/day9"
next = "/week3/day11"
toc = true
weight = 2

+++

<date>Tuesday, June 20, 2017</date>

## Lecture Videos

Morning:

* [Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [Day 10, part 1](https://www.youtube.com/watch?v=qCCHiKkg0uk&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=86) | [2](https://www.youtube.com/watch?v=7uVysc7bU9E&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=87) | [3](https://www.youtube.com/watch?v=42upKQetTgw&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=88) | [4](https://www.youtube.com/watch?v=ipyDi0ttczg&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=89) | [5](https://www.youtube.com/watch?v=xUnVgk5QdYA&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=90) | [6](https://www.youtube.com/watch?v=0rV4y726vaM&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=91) | [7](https://www.youtube.com/watch?v=wA3OZjAjSUA&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=92) | [8](https://www.youtube.com/watch?v=ley_aAVA9Y4&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=93) | [9](https://www.youtube.com/watch?v=Ht58BEUY0Ss&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=94) | [10](https://www.youtube.com/watch?v=99a-nx3-Slw&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=95)

Afternoon:

* [Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [Day 10, part 1](https://www.youtube.com/watch?v=KqznaNTJxHs&index=108&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [2](https://www.youtube.com/watch?v=mehwv-WvHBI&index=109&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [3](https://www.youtube.com/watch?v=YidKdB4yOfk&index=110&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [4](https://www.youtube.com/watch?v=xQVgVCGJUow&index=111&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [5](https://www.youtube.com/watch?v=bTaosUkKlro&index=112&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [6](https://www.youtube.com/watch?v=8Tbwu5yg8vs&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa&index=113&t=1806s) | [7](https://www.youtube.com/watch?v=MkmxPJnEzjI&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa&index=114) | [8](https://www.youtube.com/watch?v=m55ZB3eR_uI&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa&index=115)

## Topics

### Routing

* React Router v4
  * `<Router />`
  * Links and NavLinks
  * Routes
  * `history`

### Fetching Data

* The Fetch API
* Promises
* Parsing the response

## Examples

### Routing

[React Router](https://github.com/ReactTraining/react-router) provides a routing solution that allows us to change what UI we render based on the current URL.  The router is a _Higher Order Component_ that wraps a React app and allows us to navigate without additional requests and responses to and from the server.

#### Router Setup

Setting up React Router is easy.  For web projects, install `react-router-dom`

{{< term >}}
yarn add react-router-dom  # install react router with yarn
{{< /term >}}

or

{{< term >}}
npm install --save react-router-dom  # install react router with npm
{{< /term >}}

Then, in your `ReactDOM.render` call, attach the Router as your base element, wrapping the root-level `<App />` component.  The whole app is now contained within the Router component, so we can take advantage of it anywhere.

**index.js**

{{< code jsx >}}
import React from 'react'
import ReactDOM from 'react-dom'
import { BrowserRouter as Router } from 'react-router-dom'
import App from './App'

ReactDOM.render(
  &lt;Router&gt;
    &lt;App /&gt;
  &lt;/Router&gt;,
  document.getElementById('root')
)
{{< /code >}}

#### Routes

The core of React Router is the `<Route />` component.  It allows you to specify what UI to render when a particular URL is matched.  For instance, if we wanted to render a `<Users />` component when we matched a `/users` URL, we could make the following Route:

{{< code jsx >}}
&lt;Route path='/users' component={Users} /&gt;
{{< /code >}}

If you don't want to render a whole component, a Route can alternatively accept a `render` prop, which accepts a function that returns JSX:

{{< code jsx >}}
&lt;Route path='/users' render={() => &lt;h1&gt;Users Path!&lt;/h1&gt;} /&gt;
{{< /code >}}

One important thing to keep in mind is that if we define a Route's path as `/users`, that will match both `/users` _and_ `/users/123`, because both begin with `/users`.  If we want the Route to match only when the path is _exactly_ `/users`, we can add the prop `exact` to our Route component.

{{< code jsx >}}
&lt;Route exact path='/users' component={Users} /&gt;
{{< /code >}}

#### Links

React Router also provides `<Link />` and `<NavLink />` components to make it easy to generate links to Routes. If we want to generate a Link that goes to `/about`, we can do the following:

{{< code jsx >}}
&lt;Link to='/about'&gt;About&lt;/Link&gt;
{{< /code >}}

NavLinks are similar, but provide some additional functionality.  The main difference is that they will add an `activeClassName` to the rendered link if the current URL matches the `to` property of the NavLink.  This allows active links to be styled differently than inactive links.

{{< code jsx >}}
&lt;NavLink to='/'&gt;Home&lt;/NavLink&gt;    // rendered link tag will have '.active' class when URL is '/'
{{< /code >}}

#### History

The `history` object is maintained and updated by the Router to keep track of where the user has navigated within the app.  It is passed to every component contained within the Router as part of the component's `props`.  It has a variety of helpful properties and methods that provide information and navigation. Here are just a few:

{{< code js >}}
history.length             // number of history entries
history.location           // provides the current location
history.push(path)         // navigates to a new path
history.go(n)              // navigates n steps through history stack
history.goBack()           // go back one step (history.go(-1))
history.goForward()        // go forward one step (history.go(1))
history.block(prompt)      // block navigation
{{< /code >}}

### Fetch

> The Fetch API provides a JavaScript interface for accessing and manipulating parts of the HTTP pipeline, such as requests and responses.  It also provides a global `fetch()` method that provides an easy, logical way to fetch resources asynchronously across the network.

[_MDN - Using Fetch_](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)

If we need to get data from a remote server (or send some to one), there are several ways to do it.  In vanilla JS, there is `XMLHttpRequest`, jQuery provides `$.ajax`, and there are a variety of other packages and libraries that provide their own version.  Luckily, there is a new kid in vanilla JS town - the _Fetch API_.

`fetch()` is a globally available, easy to use way to asynchronously send and receive data.  The simplest usage of fetch is to simply provide it with the URL of the request, and it will perform a `GET` request by default.  The `fetch()` function returns a promise that resolves when the data is received.  Once it is received, we can process and use the data with functions provided to the promise's `.then()` callbacks.

{{< code js >}}
fetch('https://api.mywebsite.com/users')    // fetch users data from 'mywebsite' api
  .then(response => response.json())        // parse the response json into JavaScript object(s)
  .then(users => console.log(users))        // log the parsed users to the console
  .catch(error => console.warn(error))      // if any errors occur, log them to the console
{{< /code >}}

{{% aside info "Fetch does more than just fetch" %}}
If no second argument is provided to `fetch()`, it defaults to a standard `GET` request.  However, the second argument can be a configuration object, allowing it to use different HTTP methods, set Headers, include Credentials, etc.  To find out more, check out [the docs](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
{{% /aside %}}

## Projects

* Noteherder [morning](https://github.com/xtbc17s2/noteherder/tree/8a5102f855d6e9b6842f03e47d6e1d4d75b78c17) | [afternoon](https://github.com/xtbc17s2/noteherder/tree/906dfc12f05c803cd5476084fe3cfa87d10ec351)
* API Party [morning](https://github.com/xtbc17s2/api-party/tree/e09677b1c2fc479ac9605cef42f914cb7143c5d3) | [afternoon] (https://github.com/xtbc17s2/api-party/tree/ae41aa2338b7cd002b0320d0bd7f2ea4b658b692)

## Homework

Extend the API-Party app by adding at least one additional route that gets data from a public API.

* A link to the route should appear in the header along with the 'Github' and 'NASA' links
* When the link is clicked, it should be styled to show that it is active
* The new component should fetch data from a public API
* Some interesting data from the API should be presented
* The data should look pretty (style it with CSS)

### Bonus Credit

* Accept user input to refine the data you request from the API

### Super Mega Bonus Credit

* Add additional routes and APIs

### Super Mega Bonus Credit Hyper Fighting

* Figure out something interesting to do with the data on your own.  Make a graph, render a map, add child routes, go nuts!
