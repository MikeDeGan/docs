---
title: Node Dev Tools
---

# Node Dev Tools

## Nodemon

Nodemon is mainly used to speed Node development by restarting your app whenever a file changes in the monitored app folder. 

Nodemon can also be used to emulate process.env variables.

##### Installation

```javascript
npm install --save-dev nodemon
```

##### Usage

```
nodemon [your node app]
```

Usually we will use a package.json script:

```
"scripts": {
  "start": "node index.js",
  "server": "nodemon index.js"
}
```

`npm run server` will start the app for development.

