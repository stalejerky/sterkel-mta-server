SAM THOMPSON'S *SOFTWARE DEVELOPMENT 101*

## CHAPTER 2: SLICING AND DICING DATA FROM THE MTA

In the last chapter we installed and ran the nodejs "Hello World" example.

In this chapter we will modify the example to return data from the MTA in JSON format.

### STEP 1: UPGRADE OUR STACK WITH EXPRESS

Upon reflection, we update our stack a little.  Although a capable webserver, the core 'nodejs' is just a bit lacking in functionality, so we add another layer to help us with some common data process (such as routing and error handling).

We choose to add Express to our stack, as it is popular for small apps: http://expressjs.com/.

Following the install instructions, http://expressjs.com/en/starter/installing.html, we execute the following terminal commands:

```bash
npm init

```

Answer the prompts with the default (press enter).

Now:

```bash
npm install express --save
```

Taking a look at the Guide for Express: http://expressjs.com/en/guide/routing.html, it looks like we need to update our app.js a bit.

Edit app.js and make it look like this:

```node
const hostname = '127.0.0.1';
const port = 3000;
const express = require('express');
const app = express();

app.get('/', (req, res) => res.send('Hello World!'));

app.listen(port, hostname, () => console.log(`Server running at http://${hostname}:${port}/`));
```

Save this file.  Then run 'node app.js' and visit http://127.0.0.1:3000/ in your browser.  You should see 'Hello World' again.

### STEP 2: 

TKTK

## FOOTNOTES

TKTK
