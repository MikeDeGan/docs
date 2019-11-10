---
title: Express
---

# Express

## Body Parser

Body Parser is now included with Express.

## Express-Validator

Express Validator is a set of Express middlewares that wraps Validator.js and sanitizes functions.

Basically a great way to validate user input on the server.

```
npm install --save express-validator
```

The Express-Validator documentation page:

https://express-validator.github.io/docs/

The following bit of code shows the validator in use:

Notice the array entered as the second parameter of the router.post function. The third parameter is a function that will return a status of 400 and the array of errors if there are errors.

```javascript
const express = require("express");
const router = express.Router();
const { check, validationResult } = require("express-validator");

// @route  POST api/users
// @desc   Register user
// @access Public
router.post(
  "/",
  [
    check("name", "Name is required")
      .not()
      .isEmpty(),
    check("email", "Please include a valid email").isEmail(),
    check(
      "password",
      "Please enter a password with 6 or more characters"
    ).isLength({ min: 6 })
  ],
  (req, res) => {
    const errors = validationResult(req);
    if (!errors.isEmpty()) {
      return res.status(400).json({ errors: errors.array() });
    }
    res.send("User route");
  }
);

module.exports = router;
```

