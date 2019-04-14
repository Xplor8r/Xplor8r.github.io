---
layout: post
title:      "React + Bootstrap = reactstrap"
date:       2019-04-14 14:00:35 -0400
permalink:  react_bootstrap_reactstrap
---

![React + Bootstrap](https://i.ytimg.com/vi/xCGPPimXgJU/maxresdefault.jpg)

As you begin building your React project you might be thinking about a way to integrate a design pattern using Bootstrap. This free and open-source framework for responsive development contains CSS and JavaScript based design templates for a number of different interface components. Using Bootstrap allows you to easily implement navbars, forms, buttons and a variety of other functionality.

On it's own, React contains no method for creating responsive designs so using a framework like Bootstrap is a great way to streamline your front-end build. Combining Bootstrap to a project usually is as simple as including `<link rel="stylesheet" />` to your index.html file. Brace yourself, this won't work with your React project.

![IT Crowd](https://i2.wp.com/gifrific.com/wp-content/uploads/2013/12/Monitor-Throw-Maurice-Moss-The-IT-Crowd.gif?fit=350%2C193&ssl=1)

Bootstrap depends on jQuery for powering specific user interface components. React uses a declarative approach for updating the DOM while jQuery directly manipulates the DOM. This only leaves room for using Bootstrap for the responsive 12 column grid and a couple other components that don't use jQuery.

Inorder to fully connect React and Bootstrap there are several libraries to choose from. The reactstrap library is a very popular choice that is in active development and built for the most recent version of Bootstrap.

Installing the reactstrap library is simply done using npm:

`npm install --save reactstrap@next`

Because reactstrap doesn’t include Bootstrap CSS we need to also intall Bootstrap as well:

`npm install --save bootstrap`

Then make sure that Bootrap CSS is imported to the index.js file:

```
import 'bootstrap/dist/css/bootstrap.css';
```

Importing components can be done by using:

`import { Modal, ModalBody, Col, Row, Button, Form, FormGroup, Label, Input } from "reactstrap";`

All of the current components can be viewed at [reactstrap.github.io](https://reactstrap.github.io/). Each template is shown in action with the corresponding code below. I personally enjoyed working with reactstrap on my previous React project and will be using it on the rest of my upcoming React apps.
