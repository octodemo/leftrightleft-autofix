# Code Scanning Auto Fix UI demo

## How to 

### 1. Fork this repo to your org

### 2. Enable code scanning
1. Navigate to **Settings** the **Code security and analaysis**
2. Choose default setup

### 3. Create the synthetic vulnerability
1. Create a new branch
   
   ![image](https://github.com/octodemo/leftrightleft-autofix/assets/4910518/cc845cda-17f5-4823-b3a1-c894acef566f)

3. In your new branch, create a new file called `package.json` on the root directory.
4. Enter the following content into that file:
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
4. Commit the `package.json` file (make sure it's being committed to the branch you just created!)
5. Create a new file called `xss.js`
6. Enter the following content into `xss.js`
   ```
   const express = require('express');

   const app = express();
   app.get('/', (req, res) => res.send(`Hello, ${req.query.name}!`));
   ```

6. Commit `xss.js` to the branch you just created
7. Create a new Pull request from the branch you just created.
8. Alerts!
