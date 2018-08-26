First thing we will do is create a component for the _list_ of movies. It will look like this:

```
import React, { Component } from 'react';

export default class MovieList extends Component {
    constructor() {
        super();
    }
    render() {
        console.log(this.props);
        return (
            <div>
                { this.props.movies.map((movie, key) => {
                    return <p>{ movie.movie_title }</p>
                })}
                <h1>When Harry Met Sally is the best romcom of all time.</h1>
            </div>
        )
    }
}
```