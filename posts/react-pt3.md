---
title: Build a dynamic website with React Part 3
tags:
  - react
  - javascript
  - dynamic-website
  - FayePI
date: "2018-08-26T03:44:08.920Z"
layout: post
---
Author: [Carmen Bourlon](https://twitter.com/carmalou)

In our first blog post [we set up our development environment to write React.](link) In the second post, [we called out to an API and added an event listener to automatically fetch data when our app loads.](link) In this third and final blog post, we'll write two components to show the movie data and complete our list of romantic comedies.

First thing we will do is create a component for the _list_ of movies. It will look like this:

```
import React, { Component } from 'react';

export default class MovieList extends Component {
    constructor(props) {
        super(props);
    }

    render() {
        return (
            <div>
                // the second component will go here
            </div>
        )
    }
}
```

Right now this component doesn't have any data. Let's fix that by passing in the data from the `App.js` component into this component.

We'll need to import this component into the `App.js` file:

```
import MovieList from './movielist';
```

Once that's done, we'll pop into the `render()` function and use this component like so:

```
render() {
    return (
      <div className="App">
        <MovieList />
      </div>
    );
  }
```

However the `MovieList` component still isn't accessing any data. In order to pass it data, [we'll utilize props.](link)

```
<MovieList movie={ this.state.movies }/>
```

That's all we really need to do in the `App.js` file, so let's head back to the `MovieList` component.

Back in the `MovieList` component, we'll access the data from `App.js` like this: `this.props.propName`. Let's start out using the data like this:

```
render() {
        return (
            <div>
                { this.props.movie.map((movie, key) => {
                    return <p key={ movie.movie_title }>{ movie.movie_title }</p>
                })}
            </div>
        )
    }
```

Above we are listing out the title of each movie, after accessing the data from `props`. The `key` property is providing React a unique identifier for each paragraph. [You can read more about that here.](link) 

But this isn't quite what we want. Let's write a second component to format each individual movie. That component will look like this:

```
import React, { Component } from 'react';

export default class Movie extends Component {
    constructor(props) {
        super(props)
    }

    render() {
        return (
        <div>
          <div>
            <a href={ this.props.movie.movie_link }>
                <img src={ this.props.movie.movie_pic} />
            </a>
            <div>
              <h4>
                <a href={ this.props.movie.movie_link }>{ this.props.movie.movie_title }</a>
              </h4>
              <p>{ this.props.movie.movie_description }</p>
            </div>
          </div>
        </div>
        )
    }
}
```

Back in the `MovieList` component, we'll need to update it to pass each individual movie to this new component, like so:

```
render() {
    return (
        <div>
            <div>
                { this.props.movies.map((movie, key) => {
                    return <Movie key={ movie.movie_title } movie={ movie } />
                })}
            </div>
        </div>
    )
}
```

Notice `this.props.movies.map`, the function is looping over each object within the movies array and returning an individual `Movie` component. Within this component we are able to pass in a single `movie` object, instead of passing in the entire `movies` array.

And with that ... we're done! Simply run `npm start` and you'll see your finished product! You'll probably want to add some CSS to liven things up a bit. Check out [the finished product](link) to see how we used [Bootstrap](link) to style our app.

-- [Carmen](link)