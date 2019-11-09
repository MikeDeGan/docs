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