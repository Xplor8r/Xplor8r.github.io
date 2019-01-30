---
layout: post
title:      "React Refresher: State and Props"
date:       2019-01-30 21:06:05 +0000
permalink:  react_refresher_state_and_props
---


It has come to my attention that, although my understanding of React goes deep enough to create a fully functioning app with multiple features, I have yet to fully absorb the overall concepts of state and props. They are both plain JavaScript objects that are a vital part to any React project. Via the use of state and props, React controls data flow in order to render components, which display the data to the user. I'll attempt to clarify some key points about state and props that any React developer should comprehend.

![](http://cdn.collider.com/wp-content/image-base/TV/S/State_MTVs_The/slice_the_state_complete_series_dvd_box_set_art.jpg)

The **State**(not the 1993 hit MTV sketch comedy series) of each React component is initially ignored, which classifies the component as *stateless*. Once a components state is declared, that component becomes *stateful*. State contains data important to the user and  is mutable, which means it can be updated. This is accomplished using the `setState()` method upon receiving input from the user.

We can see a common usage of state in the following Form component example.
```
class Form extends React.Component {
  constructor(props) {
    super(props);
    this.state = {value: ''};

    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleChange(event) {
    this.setState({value: event.target.value});
  }

  handleSubmit(event) {
    alert('Input: ' + this.state.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Input:
          <input type="text" value={this.state.value} onChange={this.handleChange} />
        </label>
        <input type="submit" value="Submit" />
      </form>
    );
  }
}
```
We can see an initial state default value is declared within the constructor. The `handleChange()` function updates `this.state.value` with the `event.target.value`  input from the user. When the submit button is clicked the `handleSubmit()` function will be called and an alert box will display the users input.




![](https://media.giphy.com/media/od2gZ4KRRX2M0/giphy.gif)

**Props**(not the legendary fitness guru Richard Simmons) or *properties* are inherited from parent components, or controller components, but can also be set with defaults in the case that the controller component does not pass any. They can not, however, be changed and are considered *immutable*. Using props that are passed down is how data is displayed by child components, or view components, to the user. The state of one component will often become the props of a child component. 

Below we can walk through the process of passing down props.

.../containers/restaurantsContainer.js
```
import React, { Component } from 'react';
import Restaurant from '../components/restaurant';

class RestaurantContainer extends Component {
   constructor(props) {
      super(props);
      this.state = { restaurant: "Five Star Restaurant" };
   }
		
   render() {
      return (
         <div>
            <Restaurant restaurant={this.state.restaurant} />
         </div>
      )
   }
}

export default RestaurantContainer
```

.../components/restaurant.js
```
import React, { Component } from 'react';

class Restaurant extends Component {
  render() {
    return <h1>{this.props.restaurant}</h1>;
  }
}

export default Restaurant
```
The `Restaurant` component(child) is rendered by the `RestaurantContainer` component(parent) and is given a custom attribute `restaurant` which is assigned `this.state.restaurant`. In the `Restaurant` component the props are received in React’s class component via the `this` instance of the class and is rendered within the `<h1>` tag.

To summarize, though it is difficult to conceptually differentiate some things about state and props we can see that they have some very separate abilities. State belongs to a single component allowing it to dynamically change output in response to certain events. Props are received from parent components in uni-directional fashion, are read-only, and should never be changed. If something alters data, that data should belong to the component state.
