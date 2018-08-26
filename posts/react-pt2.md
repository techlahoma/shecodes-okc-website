---
title: Build a dynamic website with React Part 2
tags:
  - react
  - javascript
  - dynamic-website
  - FayePI
date: 2018-08-25
layout: post
---

Now that we are all set up to code, let's build something! Open up your terminal and generate a new React app with:

```
npx create-react-app my-app
cd my-app
npm start
```

This will new up a React app for you. Next you are navigating to that app directory. The last command serves up the app. You'll see a simple starter app running on port 3000.

Let's open up the app and take a look. Open up the app in your IDE of choice.

Notice that within our app there are some files and three folders: `public`, `node_modules`, and `src`. The only folder we'll mess with is the `src` folder. We won't make any changes to any files outside of the `src` folder or within any other folder.

Within the `src` folder, there is an `App.js` file. Within this file there is a `render` function. A core concept of React is that all of our code will be in the JavaScript files and will be rendered through this `render` function. This means we won't have any HTML files.

The app we are building together is going to use [FayePI](link). We'll be building a list of romantic comedies.

Let's hop into the `App.js` file and set some stuff up. Our `App.js` file will look like this:

```
import React, { Component } from 'react';
import './App.css';

class App extends Component {
  constructor(props) {
    super(props);
  }

  render() {
    return (
      <div className="App">
        // our new component will go here
      </div>
    );
  }
}

export default App;
```

We'll define our state within the constructor function. It will look like this:

```
constructor(props) {
    super(props);
    this.state = {
      movies: []
    };
  }
```

State is where we store the app's data. In our case, this is where we will store the list of movies and the information about each movie.

Next let's set up an Action which is where we'll fetch the movies and information from FayePI. React likes to separate view logic (components) from BLANKETY BLANK. You can read up on this more in [the React docs.](link)

Our action will look like this:

```
export default function fetchMovies() {
    return window.fetch('https://fayepi.herokuapp.com/romcoms')
    .then(function(response) {
        return response.json();
    })
}
```

We are using [fetch](link) to call FayePI, which returns a promise. [Read up on promises here](link) if you aren't familiar with them.

First, we make a request to FayePI. This can take an unknown amount of time, so this code picks up once the response is sent back to us with the `.then()` block. Within that we are parsing the response into a useable format with `response.json()`.

Now that we have an action we can use to go fetch our movie data, let's go implement it in the App.js file.

Before we can call the function we wrote, we need to import the file like this:

```
import FetchMovies from './fetchMovies';
```

React has several [lifecycle methods](link) which allow specific functions to be triggered at certain points while the app is loading. The one we will use is `componentDidMount`. This event is trigger immediately after the app has loaded. Our function will look like this:

```
componentDidMount() {
    FetchMovies().then((response) => {
      this.setState({
        movies: response
      });
    })
  }
```

Notice that we are using `this.setState()` instead of just saying `this.state.movies = response`. This is important because in order for our app to update (or re-render) we must use React's built-in function to update state.

Now our app loads and immediately calls out to the API to access the list of movies.

[Read on for part 3, where we will write and implement components!](link)