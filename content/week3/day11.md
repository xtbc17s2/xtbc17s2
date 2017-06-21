+++
date = "2017-06-21T09:44:15-04:00"
title = "Routing in Noteherder"
toc = true
weight = 3
prev = "week3/day10"

+++

<date>Tuesday, June 20, 2017</date>

## Lecture Videos

Morning:

* [Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [Day 11, part 1](https://www.youtube.com/watch?v=KXgfQCUuxcQ&index=96&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [2](https://www.youtube.com/watch?v=i1aFmAykIP8&index=97&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [3](https://www.youtube.com/watch?v=AuYr_WHwCII&index=98&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [4](https://www.youtube.com/watch?v=hkb16hmwzRM&index=99&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [5](https://www.youtube.com/watch?v=d4AWx4KbdzY&index=100&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [6](https://www.youtube.com/watch?v=iz5McmUmhWk&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=101) | [7](https://www.youtube.com/watch?v=tp-PzHiJZdQ&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=102) | [8](https://www.youtube.com/watch?v=bgIzMJwdtbM&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=103) | [9](https://www.youtube.com/watch?v=j3uC7xO0p3o&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=104) | [10](https://www.youtube.com/watch?v=bHBrl0Xgz1w&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=105) | [11](https://www.youtube.com/watch?v=c3XDrv0Rzqs&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=106)

Afternoon:

* [Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [Day 11, Part 1]() | [2]() | [3]() | [4]() | [5]() | [6]() | [7]() | [8]() | [9]() | [10]()

## Topics

### React Router
* Redirect component
* Passing props to components in `Route`s

### Create React App
* Ejecting the app

## Examples

### React Router

#### Redirect component

The `Redirect` component provided by React Router allows us to cause the user to navigate to a new location.  Just drop in a `Redirect` component and pass it a `to` prop to tell it where to redirect, and you're good to go!

{{< code jsx >}}
&lt;Redirect to='/widgets' /&gt;
{{< /code >}}

A common use case for a `Redirect` is to send a user to different locations based on whether they are logged in or not.

{{< code jsx >}}
import { Route, Redirect } from 'react-router'

&lt;Route exact path="/" render={() => (
  loggedIn ? (
    &lt;Redirect to="/dashboard"/&gt;
  ) : (
    &lt;PublicHomePage/&gt;
  )
)}/&gt;
{{< /code >}}

The code above translates to: "If the path is at the root route ('/'), redirect to '/dashboard' if the user is logged in.  Otherwise, render the PublicHomePage."

#### Passing props to routed components

Here's a basic `Route` that renders a `Stuff` component when the path matches `'/stuff'`:

{{< code jsx >}}
&lt;Route path="/stuff" component={Stuff} /&gt;
{{< /code >}}

When `Stuff` is rendered, it will automatically receive `props` from the router that include `match`, `history`, and `location`.  But what if we want to pass additional props to `Stuff`?  It turns out, we can use the `render` prop for `Route` instead, which allows us to pass additional props when the anonymous function returns some JSX.

{{< code jsx >}}
&lt;Route path="/stuff" render={(props) => (
  &lt;Stuff name="Bob" {...props} /&gt;
)} /&gt;
{{< /code >}}

In this example, the anonymous function in the `render` for the `Route` receives an argument of `props` (which includes `match`, `history`, and `location`).  Our `render` method returns some JSX - specifically, the `<Stuff />` component.  We pass along our existing `props` to `Stuff` via Object spread, as well as an additional `name` prop.

### Create React App - Ejecting

Back in the olden days of React development, it would often take a significant amount of time to get your project up and running.  Webpack configuration, dependency installations, script configuration, polyfills, etc, all had to be set up just to get a simple "Hello world" displaying on the screen.  

Create React App solved this problem by doing all this initial setup for you!  Just type `create-react-app` and your project name into terminal, and you're up and running in minutes.  The standard configuration works for almost any normal use case.

However, maybe you have a specific need that the standard create-react-app build isn't set up for.  In a standard app, all the config files are hidden, so what can you do?

Luckily, the 'create-react-app' team anticipated this as well.  They provide an `eject` script that copies all configuration files and transitive dependencies into your project so you can have full control over them.  

{{< term >}}
npm run eject
{{< /term >}}

Simply run this command, and all of the configuration files will appear in your project folder!

{{% aside info Note %}}
Remember, ejecting is not reversible. Make sure you have a good reason to eject before you do so!
{{% /aside %}}

## Homework

* Make the sign in page prettier

### Super Mega Bonus Credit

* Add a rich text editor to the form.