# React Router

## Programmatic Navigation

```javascript
//programmatic navigation back to the root route
// sometimes a little tricky

import history from "../history";

history.push("/");
```

```javascript
// import createHistory from "history/createBrowserHistory";
const createHistory = require("history").createBrowserHistory;

export default createHistory();
```



## Switch

React Router will, by default, route 'greedily' That just means that if multiple routes match it will try to go to both routes. As in this it would go to streams/new and to streams/:id when you just want /streams/new

```javascript
<Route path="/" exact component={StreamList} />
<Route path="/streams/new" exact component={StreamCreate} />
<Route path="/streams/edit/:id" exact component={StreamEdit} />
<Route path="/streams/delete/:id" exact component={StreamDelete} />
<Route path="/streams/:id" exact component={StreamShow} />
```

To stop this behavior and have it stop after the first hit you need to add the Switch component from react router dom as...

```javascript
import { Router, Route, Switch } from "react-router-dom";
```

```javascript
  <Switch>
    <Route path="/" exact component={StreamList} />
    <Route path="/streams/new" exact component={StreamCreate} />
    <Route path="/streams/edit/:id" exact component={StreamEdit} />
    <Route path="/streams/delete/:id" exact component={StreamDelete} />
    <Route path="/streams/:id" exact component={StreamShow} />
  </Switch>
```

## Redirect

Redirect will take any route that falls through and redirect to wherever you send it.

 

```javascript
import React from 'react';
import {
  BrowserRouter as Router,
  Route,
  Redirect,
  Switch
} from 'react-router-dom';

import Users from './user/pages/Users';
import NewPlace from './places/pages/NewPlace';

const App = () => {
  return (
    <Router>
      <Switch>
        <Route path="/" exact>
          <Users />
        </Route>
        <Route path="/places/new" exact>
          <NewPlace />
        </Route>
        <Redirect to="/" />
      </Switch>
    </Router>
  );
};

export default App;
```

## NavLink

NavLink is similar to Link except you can examine the url and set styling depending on if you are currently on that page and that kind of thing. 

```javascript
import React from "react";
import { NavLink } from "react-router-dom";

import "./NavLinks.css";

const NavLinks = props => {
  return (
    <ul className="nav-links">
      <li>
        <NavLink to="/" exact>
          ALL USERS
        </NavLink>
      </li>
      <li>
        <NavLink to="/">MY PLACES</NavLink>
      </li>
      <li>
        <NavLink to="/">ADD PLACE</NavLink>
      </li>
      <li>
        <NavLink to="/">AUTHENTICATE</NavLink>
      </li>
    </ul>
  );
};
```

