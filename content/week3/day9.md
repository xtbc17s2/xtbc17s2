+++
date = "2017-06-19T10:12:30-04:00"
title = "Firebase and Authentication"
toc = true
weight = 1
prev = "week3"
+++

<date>Monday, June 19, 2017</date>

## Lecture Videos

Morning:

* [Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84) | [Day 9, Part 1](https://www.youtube.com/watch?v=K8s8KdVNm6o&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=73) | [2](https://www.youtube.com/watch?v=G-RXxnw-pjY&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=74) | [3](https://www.youtube.com/watch?v=ZZuvfDMfc3M&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=75) | [4](https://www.youtube.com/watch?v=RmvxmjultIY&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=76) | [5](https://www.youtube.com/watch?v=Rn0y-SlyY8E&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=77) | [6](https://www.youtube.com/watch?v=u8IBoRL9Zn0&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=78) | [7](https://www.youtube.com/watch?v=-fZHoWAzRiQ&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=79) | [8](https://www.youtube.com/watch?v=EhAWcVaoQVw&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=80) | [9](https://www.youtube.com/watch?v=R2cFvi3WsgM&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=81) | [10](https://www.youtube.com/watch?v=Ldk359ucjDc&list=PLuT2TqJuwaY9SEkynJl1LudbfzWqc4l84&index=82)

Afternoon:

* [Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [1](https://www.youtube.com/watch?v=t0nYK8le1go&index=93&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [2](https://www.youtube.com/watch?v=e1U_coS7eVg&index=94&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [3](https://www.youtube.com/watch?v=snlcp3pFRIY&index=95&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [4](https://www.youtube.com/watch?v=BJxjePQFbCs&index=96&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [5](https://www.youtube.com/watch?v=6-0fcHXNgrc&index=97&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [6](https://www.youtube.com/watch?v=ppbh9VEW_vY&index=98&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [7](https://www.youtube.com/watch?v=mB1i1ICeZAo&index=99&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [8](https://www.youtube.com/watch?v=zwuNbtcSPIk&index=100&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa) | [9](https://www.youtube.com/watch?v=j7VGZZJMa00&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa&index=101) | [10](https://www.youtube.com/watch?v=OCmouiW2fTU&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa&index=102) | [11](https://www.youtube.com/watch?v=fhysbVejjRc&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa&index=103) | [12](https://www.youtube.com/watch?v=6D9pKdke2RE&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa&index=104) | [13](https://www.youtube.com/watch?v=aPuOo_hTl8I&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa&index=105) | [14](https://www.youtube.com/watch?v=nlMfV_PT_pE&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa&index=106) | [15](https://www.youtube.com/watch?v=N103yaEXIHc&list=PLuT2TqJuwaY9uIH9AFDZUyfalE-tY8REa&index=107)

## Topics

### Firebase [↓](#firebase)

* Getting started
* Database rules
* Re-base for syncing React state with Firebase

### Firebase Authentication [↓](#authentication)

* 'firebase/auth'
* `authWithPopup`
* signing in and out
* handling auth state changes

### Deployment

* GitHub Pages [↓](#deployment-github-pages)

## Firebase

### Getting Started

[Firebase](https://firebase.google.com/) is a real-time database hosted by Google.  In addition to the database, it also provides features of authentication, analytics, cloud storage, and hosting.  For _Noteherder_, we synced the `state` of our app to our database on Firebase.  This allowed all of our data to be persisted, even after page refreshes.

[Re-base](https://github.com/tylermcginnis/re-base) is an open source package that allows easy syncing of local state with a Firebase database. Add rebase to your project with one of the following commands:

{{< term >}}
yarn add re-base               # add package using yarn
npm install re-base            # add package using npm
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

### Rules

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

### Authentication

Firebase isn't just a real-time database.  It can also provide authentication services via email/password, phone, or common third-party services like Github, Facebook, and Google. For _Noteherder_, we set up authentication via Github OAuth.

#### Step 1: Get your authorization callback URL from Firebase

Navigate to your project in Firebase console.  Click on the 'Authenticate' tab on the left and then on the Github logo.  Copy the authorization callback URL.

<div class="img firebase-enable-github"><span>The data for the Client ID and Client Secret will be generated in the next step.</span></div>

#### Step 2: Register your app in Github

Log in to Github and click on 'Settings'.  On the left hand side, click on 'OAuth Applications' under the 'Developer settings' menu.  Register a new app and fill out the form.

<div class="img github-oauth-new-registration"><span>Use the Authorization callback URL from step 1</span></div>

After successfully registering the app, you'll be taken to your new app's settings page.

<div class="img github-oauth-secrets"><span>Seeeeecrets...  (Don't worry, this app has been deleted. Never post your app secrets publicly.)</span></div>

#### Step 3: Enable Github authentication in Firebase

Go back to the Github authentication tab in Firebase and fill in the Client ID and Client Secret that you got from registering your app with Github.

<div class="img firebase-github-secrets"><span>More Seeeeecrets...  (But seriously, don't share your secrets)</span></div>

#### Step 4: Add Firebase auth to your app

_Note: This step assumes you already have your Firebase database added to your app._ 

Import `firebase/auth` into your app's firebase setup.  Enable firebase auth and also create an instance of `GithubAuthProvider`.

**base.js**

{{< code lang="js" line="4,17,18" class="line-numbers" >}}
import Rebase from 're-base'
import firebase from 'firebase/app'
import database from 'firebase/database'
import 'firebase/auth'

const app = firebase.initializeApp({
  apiKey: "YOURAPIKEY",
  authDomain: "YOURAUTHDOMAIN",
  databaseURL: "YOURDATABASEURL",
  projectId: "YOURPROJECTID",
  storageBucket: "YOURSTORAGEBUCKET",
  messagingSenderId: "YOURSENDERID"
})

const db = database(app)

export const auth = app.auth()
export const githubProvider = new firebase.auth.GithubAuthProvider()

export default Rebase.createClass(db)
{{< /code >}}

#### Step 5: Set up the SignIn Component

Import `auth` and the `githubProvider` into whatever component handles the sign-in process.  Call `signInWithPopup` on the `auth` object, passing the provider as a parameter.  This will launch a popup screen that will prompt the user to sign in using the provider you have specified.

**SignIn.js**

{{< code jsx >}}
import React from 'react'
import { auth, githubProvider } from './base'

const SignIn = () => {
  const authenticate = (provider) => {
    auth.signInWithPopup(provider)
  }

  return (
    &lt;button className="SignIn" onClick={() => authenticate(githubProvider)}&gt;
      Sign In With GitHub
    &lt;/button&gt;
  )
}

export default SignIn
{{< /code >}}

#### Step 6: Handling auth state changes (and page refreshes)

Once the user has authenticated via the popup, the state of our authorization has changed (we now have an authenticated user).  Other events that can cause auth state changes are signing out, timeouts, and page refreshes.  We should probably set up something to listen for these events.  In the `componentWillMount` lifecycle hook that runs when the Component is first getting loaded, we can call the `onAuthStateChanged` method provided on the global `auth` object to set up such a listener.

**App.js**

{{< code js >}}
// ...

componentWillMount() {
  auth.onAuthStateChanged(
    (user) => {
      if (user) {
        // finish signing in
        this.authHandler(user)
      } else {
        // finished signing out
        this.setState({ uid: null })
      }
    }
  )
}

// ...
{{< /code >}}

#### Step 7: Finishing sign-in

What the `authHandler` callback does is up to you, but for _Noteherder_, we had it do pretty typical things - save the user ID to state, and initialize syncing our local state for 'notes' with the data stored on Firebase.

**App.js**

{{< code js >}}
// ...

authHandler = (user) => {
  this.setState(
    { uid: user.uid },
    this.syncNotes
  )
}

// ...
{{< /code >}}



#### Step 8: Signing out

Signing out when using Firebase for authentication is also simple - just call `auth.signOut()`!  Once the promise returned by `signOut` has resolved, you can handle any additional cleanup.  In _Noteherder_, we stop syncing with Firebase and set `state.notes` back to an empty object.

**App.js**

{{< code js >}}
// ...

signOut = () => {
  auth
    .signOut()
    .then(
      () => {
        // stop syncing with Firebase
        base.removeBinding(this.ref)
        this.setState({ notes: {} })
      }
    )
}

// ...
{{< /code >}}

### Deployment: GitHub Pages

Deploying an app like Noteherder is fairly simple at this stage, as it runs entirely on the client side (the browser). _create-react-app_ makes it even easier.

{{% aside info Note %}}
_create-react-app_ includes detailed instructions for [deploying with GitHub Pages](https://github.com/facebookincubator/create-react-app/blob/master/packages/react-scripts/template/README.md#github-pages) in the README.
{{% /aside %}}

Start by running the included _build_ script.

{{< term >}}
yarn build     # build with yarn
npm run build  # build with npm
{{< /term >}}

This builds the browser-ready version of our app in a `build` directory. (There are several aspects of our `src` directory that make it less than ideal for production use. For example, recall that our app is written using JSX, which browsers don't understand.)

It also prints out these instructions:

{{< term output="1,2,3,4,5" >}}
The project was built assuming it is hosted at the server root.
To override this, specify the homepage in your package.json.
For example, add this to build it for GitHub Pages:

  "homepage" : "http://myname.github.io/myapp",
{{< /term >}}

To host the app on GitHub Pages ([learn more about GitHub Pages](https://pages.github.com/)), add the "homepage" line to `package.json`, just like it says, substituting your GitHub user name and repository name. In my case:

{{< code lang="json" class="line-numbers" line="3" >}}
  "name": "noteherder",
  "version": "0.1.0",
  "homepage": "http://xtbc17s2.github.io/noteherder",
{{< /code >}}

Now run `build` again.

{{< term >}}
yarn build     # build with yarn
npm run build  # build with npm
{{< /term >}}

This time, the output will include some more specific instructions.

{{< term output="1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18" >}}
The build folder is ready to be deployed.
To publish it at http://xtbc17s2.github.io/noteherder, run:

  yarn add --dev gh-pages

Add the following script in your package.json.

    // ...
    "scripts": {
      // ...
      "predeploy": "npm run build",
      "deploy": "gh-pages -d build"
    }

Then run:

  yarn run deploy

{{< /term >}}

Cool! Let's add the `gh-pages` package.

{{< term >}}
yarn add --dev gh-pages          # with yarn, or...
npm install --save-dev gh-pages  # with npm
{{< /term >}}

Now let's add those two scripts to `package.json`.

{{< code lang="json" class="line-numbers" line="6-7" >}}
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test --env=jsdom",
    "eject": "react-scripts eject",
    "predeploy": "npm run build",
    "deploy": "gh-pages -d build"
  }
{{< /code >}}

Now whenever you're ready to deploy, you can just run `yarn deploy`!

{{< term >}}
yarn deploy     # deploy with yarn
npm run deploy  # deploy with npm
{{< /term >}}

And your app will be available at the homepage listed in your `package.json`&mdash;in my case, [http://xtbc17s2.github.io/noteherder](http://xtbc17s2.github.io/noteherder).


## Projects

Noteherder [morning](https://github.com/xtbc17s2/noteherder/tree/77909bea0c93765a9153c9fcb9466e51d5e133e0) | [afternoon](https://github.com/xtbc17s2/noteherder/tree/e40644f3f4ab884609d5450fab3c744622ad448a)

## Homework

* When you click on a note in the list, populate the form with the data from that note.
* Make sure delete works once you do that.
* _Hint:_ Look up how `componentWillReceiveProps` works.
* Run `npm run deploy` or `yarn deploy` to update the version on GitHub Pages.

### Bonus Credit

* Remove the "Save and new" button from `NoteForm`, and assign the same functionality to the "+" button in the sidebar.

### Super Mega Bonus Credit

* Add another authentication method to your app, such as Twitter, Facebook, Google, email/password, etc.
* Remember, the Firebase documentation is your friend.
