# Code Scanning Auto Fix UI demo

## How to 

### 1. Fork this repo to your org

### 2. Enable code scanning
1. Navigate to **Settings** the **Code security and analaysis**
2. Choose default setup

### 3. Create the synthetic vuln pull request
1. Create a new file called `package.json` on the root directory.
2. Enter the following content into that file:
```
{
  "name": "synthetic-xss",
  "version": "1.0.0",
  "description": "A simple example of an XSS vulnerability.",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "dependencies": {
    "express": "^4.17.1"
  },
  "author": "",
  "license": "ISC"
}
```
3. Commit the `package.json` file to a new branch (named whatever you would like).
4. Create a new file called `xss.js`
5. Enter the following content into `xss.js`
   ```
   const express = require('express');

   const app = express();
   app.get('/', (req, res) => res.send(`Hello, ${req.query.name}!`));
   ```

6. Commit `xss.js` to the same branch as `package.json`
7. Create a new Pull request from the branch you just created.
8. Alerts!
