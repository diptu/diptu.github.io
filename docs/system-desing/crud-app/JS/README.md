# Introduction to Node.js and Express

!!!s info "What is Node.js?"
    Node.js is an **open-source** and **cross-platform** runtime environment for executing JavaScript code outside of a web browser. It is commonly used to build **back-end services**, also known as **APIs**.

    Node.js is particularly well-suited for building:
  
    * Highly **scalable** applications
    * **Data-intensive** applications
    * **Real-time** back-end services that power client applications


!!! success "Why Node?"

    Node.js has become a preferred choice for backend development due to several compelling reasons:

    * **JavaScript Everywhere:** It allows you to use **JavaScript** for both your frontend and backend, simplifying development and enabling easier transitions between roles.
    * **Scalability:** Node.js facilitates the **easy scaling** of applications, making it suitable for large-scale professional projects with growing user bases.
    * **Performance:** Its **fast and non-blocking** nature, driven by its asynchronous event-driven architecture, ensures efficient handling of concurrent requests.
    * **Community and Ecosystem:** Node.js boasts a **vibrant community** of developers and a **rich ecosystem** of readily available packages and libraries (primarily through npm - Node Package Manager).

??? Question "How to Install Node.js"

    Follow these steps to install Node.js on your system:

    1.  **Download the Installer:** Visit the official [Node.js website](https://nodejs.org/) and download the appropriate installer for your operating system (Mac or Windows).
    2.  **Choose the LTS Version:** It is generally recommended to download and install the **Long-Term Support (LTS)** version, which is usually displayed on the left side of the download page.
    3.  **Run the Installer:** Once the download is complete, run the installer and follow the on-screen prompts. You will likely need to click the "NEXT" button multiple times and accept the default installation settings.
    4.  **Verify Installation:** To confirm that Node.js has been installed correctly, open your terminal (or command prompt on Windows) and run the following command:

        ```bash
        node --version
        ```

        If the installation was successful, this command will output the installed version of Node.js. On Windows, you might need to restart your command prompt after installation before running this command.

!!! note "What is Express?" 

    Express is a **fast**, **unopinionated**, and **minimalist** web backend or server-side web framework for Node.js. Essentially, Express simplifies the process of building APIs and web applications with Node.js by providing a set of robust features and tools with less code.

    Key aspects of Express:

    * It is a **framework built on top of Node.js**.
    * It enables you to **create your backend with ease**, providing structure and conventions for handling routing, middleware, and more.
    * It can be used in conjunction with frontend frameworks like **React**, **Angular**, or **Vue** to build complete **full-stack applications**.

??? Success "Why do You Need Express?"

    Express offers significant advantages for Node.js web development:

    * **Simplified Development:** It makes building web applications with Node.js **much easier** by abstracting away low-level details and providing a more intuitive API.
    * **Lightweight and Fast:** Express is **extremely light**, **fast**, and **free**, contributing to the overall performance of your application.
    * **Versatility:** It is suitable for building both **server-rendered applications** (where HTML is generated on the server) as well as **API/Microservices** (for data exchange with frontend applications).
    * **Popularity and Community Support:** Express is the **most popular** Node.js web framework, benefiting from a large and active community that provides extensive documentation, tutorials, and support.
    * **Full Control:** It gives you **full control over requests and responses**, allowing for highly customized application logic.

??? Question "Prerequisites"

    Before you begin working with Node.js and Express, ensure you have the following:

    * **Basic knowledge of JavaScript:** A fundamental understanding of JavaScript syntax, concepts, and asynchronous programming is essential.
    * **Node.js Installed:** You need to have successfully downloaded and installed **Node.js** on your computer as described in the installation section.
    * **Postman (Recommended):** While not strictly required for development, **Postman** is a valuable tool for testing and interacting with your backend APIs. You can download it from the [Postman website](https://www.postman.com/downloads/).
  
## Crud-api

!!! note "projrct structure"    
    create a directory called server aand move into server directory.
    ```bash
    mkdir server
    cd server
    ```
??? info "View npm Version Information"
    * `npm` stands for **Node Package Manager**. It is the default package manager for the Node.js JavaScript runtime environment.
    * `-v` is a common command-line flag that typically stands for "**version**".

    When you execute `npm -v`, the terminal will output the version number of the npm client that is installed on your machine.

    ## Example Output

    The provided output shows the following:
    10.9.2

??? Example "Initialize a new Node.js project"
    Inside server directory run the following command to initialize a Node.js project.
    ```bash
    npm init -y
    ```
    The command `npm init -y` is used within a Node.js project to **initialize a new `package.json` file**. This file is a fundamental part of any Node.js project managed with npm (Node Package Manager).

    ```json title="package.json"
    {
    "name": "server",
    "version": "1.0.0",
    "main": "index.js",
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
    },
    "keywords": [],
    "author": "",
    "license": "ISC",
    "description": ""
    }
    ```
    !!! note "Project Structure:"
    ```plain
     server
        ├── ./package-lock.json
        ├── ./package.json
        ├── .env
        └── ./src
            ├── ./app.js
            ├── ./index.js
            └── ./secret.js
    ```

??? info "Install Express.js"
    ```bash
    `npm i express`
    ```

??? info "Why use express?"

    Installing Express allows us to:

    * **Quickly set up a web server:** Express simplifies the process of creating and configuring HTTP servers in Node.js.
    * **Define routes for your application:** It provides a clear and organized way to handle different HTTP requests (like GET, POST, PUT, DELETE) to specific URLs (routes) in your application.
    * **Implement middleware:** Express allows you to use middleware functions to perform various tasks before or after handling a request, such as logging, authentication, and data parsing.
    * **Build APIs:** It is a popular choice for building RESTful APIs that can be consumed by frontend applications or other services.
    * **Render dynamic web pages:** Express can be used with templating engines to generate HTML content dynamically on the server.

    !!! note "Project Structure:"
    ```plain
    server
        └── ./server/package.json
        └── ./server/node_modules
    ```
    ```json title="package.json"
    "dependencies": {
    "express": "^5.1.0"
    }
    ```

## Setting Up code Directory

### Creating the Source Directory

The first step is to create a directory that will house all your project's source code files. A common convention is to name this directory `src` (short for "source").

```bash
mkdir src
```
Next, we'll typically want to create a main JavaScript file where our application's entry point will reside. A common name for this file is `index.js`

```bash
touch src/index.js
```
### Creating a Basic Express Server

```javascript title="index.js" linenums="1"
const express = require('express');
const app = express()

app.listen(3000, ()=>{
    console.log(`server running on http://localhost:3000`);
})
```
### Running the Node.js Server

```bash
node src/index.js
```
### Package Installation
1. [Nodemon](#nodemon)
2. [morgan](#morgan)
3. [body-parser](#body-parser)
4. [http-errors](#http-errors)
5. [express-rate-limit](#express-rate-limit)
??? info " Why Use Nodemon?"
    * **Automatic Restarts:** The primary benefit of Nodemon is its ability to **automatically restart** your Node.js server upon saving changes to your files. This saves you valuable development time and allows you to focus on coding.
    * **No Code Changes Required:** Nodemon is designed to be a seamless replacement for the `node` command. You **don't need to modify your existing Node.js code** to use it.
    * **Improved Development Experience:** By automating the server restart process, Nodemon provides a smoother and more efficient development experience.


    We can easily install Nodemon as a development dependency for your project using npm (Node Package Manager):

    ```bash
    npm install --save-dev nodemon
    ```

??? info " Why Use Morgan?"

    Morgan is a popular Node.js logging middleware that provides a simple way to log HTTP requests and responses.
    * **HTTP Request and Response Logging:** Morgan logs HTTP requests and responses, making it easier to monitor and debug your application.
  
    ```bash
    npm install --save-dev morgan
    ```

    ```json title="package.json" linenums="14" hl_lines="2-3"
        "devDependencies": {
            "morgan": "^1.10.0",
            "nodemon": "^3.1.9"

    }
    ```
Now, Add the following lines to script section:
```json title="package.json" linenums="5" hl_lines="2-3"
"scripts": {
    "start" : "node ./src/index.js",
    "dev" : "nodemon ./src/index.js",  
    },
```
### Running the Production Application

```bash
npm run start
```
will run the commad `node ./src/index.js`
### Running the Development Application with Nodemon

```bash
npm run dev
```
will run the commad `nodemon ./src/index.js`


## Create a HTTP request

```javascript title="index.js" linenums="1" hl_lines="4-10"
const app = require('./app.js');

app.listen(3000, ()=>{
    console.log(`server is running on http://localhost:3000`);
})
```

```javascript title="app.js" linenums="1" hl_lines="4-10"
const express = require('express');
const app = express()

app.get('/api/users', (req, res) => {
    res.status(200).send(
         {
            'success': true,
            'msg':'users is returned'}
        );
  })

app.get('/products', (req, res) => {
    res.status(200).json(
         {
            'success': true,
            'msg':'products is returned'}
        );
  })

module.exports = app
```

Now let's the Development Application with Nodemon

```bash
npm run dev
```
now we can visit [http://localhost:3000/products](http://localhost:3000/products) in our browser to see the response.

```javascript title="app.js" linenums="1" hl_lines="4-6"
const express = require('express');
const app = express()

const morgan = require('morgan')
// setup the logger
app.use(morgan('dev'))
app.get('/products', (req, res) => {
    res.status(200).send(
         {
            'success': true,
            'msg':'products is returned'}
        );
  })
module.exports = app
```
now if we send any request to server e,g [http://localhost:3000/products](http://localhost:3000/products) we'll see logs in the terminal.


!!! info "[Express Middleware](https://expressjs.com/en/guide/using-middleware.html)"

    Express middleware are functions that have access to the request object (`req`), the response object (`res`) and the `next` middleware function in the application’s request-response cycle. The `next` middleware function is commonly denoted by a variable named `next`.

    Middleware functions can perform the following tasks:<br>

      - Execute any code.<br>
      -  Make changes to the request and the response objects.<br>
      - End the request-response cycle.<br>
      - Call the next middleware function in the stack.<br>
      - If the current middleware function does not end the request-response cycle, it must call next() to pass control to the next middleware function. Otherwise, the request will be left hanging.<br>

    We already used an application lavel middleware `morgan` in the above example. This middleware logs the request and response in the terminal every time a request is made to the server.

!!! info " Why Use body-parser?"

    A third pary middleware called `body-parser` is used to parse the request body. This middleware is used to pars incoming request bodies in a middleware before your handlers, available under the req.body property.

    ```bash
    npm i body-parser
    ```
```json title="package.json" linenums="14" hl_lines="2"
    "dependencies": {
    "body-parser": "^2.2.0",
    "express": "^5.1.0"
  },
```

!!! info "Error handling middleware"
    At this stage we will use an [error handling middlewere](https://expressjs.com/en/guide/using-middleware.html#middleware.error-handling) to catch any error that may occur in the application. This middleware is used to catch any error that are not handlled anywhere.
    First we will add error handling middleware to the Client side and then we will add error handling middleware to the server side.

??? info " Why Use http-errors"

    - Create HTTP errors for Express

    Install the package using npm:
    ```bash
    npm i http-errors
    ```

```json title="package.json" linenums="14" hl_lines="4"
    "dependencies": {
    "body-parser": "^2.2.0",
    "express": "^5.1.0",
    "http-errors": "^2.0.0"
},
```
### client error handling

```javascript title="index.js" linenums="1" hl_lines="34-44"
const express = require('express');
const bodyParser = require('body-parser')

const morgan = require('morgan')
const app = express()

// setup the logger
app.use(morgan('dev'))

// parse application/json
app.use(bodyParser.json())

app.get('/api/users', (req, res) => {
    res.status(200).send(
         {
            'success': true,
            'msg':'users is returned'}
        );
  })

app.get('/products', (req, res) => {
    res.status(200).json(
         {
            'success': true,
            'msg':'products is returned'}
        );
  })

// client error handling
app.use(( req, res, next) => {  
    res.status(404).json({'msg':'route not found!'});
    next();
  })
// server error handling
app.use(( error, req, res, next) => {  
    console.error(err.stack)
    res.status(500).json({'msg':'Invalid request!'});
  })

  module.exports = app

```
Now if we try to make any invalid request to the client, it will return a 404 status code with a JSON response. for example if we try to make a request to [/product-details](`http://localhost:3000/product-deetail`). will show us client error message but if we made a request to [/product/1](`http://localhost:3000/products/1`) will give us server error message.

First application will look for client error. using
 `next()` function. If client error is not found then it will look for server error. 

### Improve error handling using http-errors:

At this stage we will use `http-errors` package to improve our error handling. This package will help us to create custom error.

### Security:

**API security:**

!!! info "Why use express-rate-limit"

Basic rate-limiting `middleware` for Express. Use to limit repeated requests to public APIs and/or endpoints such as password reset.<br>
    we want to limit the number of requests per minute from a client to prevent abuse of our API.<br>
    using `app.use(limiter)` will limit the number of requests per minute from a client to prevent abuse of our API.

    ```bash
    npm i express-rate-limit
    ```

```json title="package.json" linenums="14" hl_lines="4"
    "dependencies": {
    "body-parser": "^2.2.0",
    "express": "^5.1.0",
    "express-rate-limit": "^7.5.0",
    "http-errors": "^2.0.0"
},
```

```javascript title="index.js" linenums="9" hl_lines="1-8"
const limiter = rateLimit({
    windowMs: 5 * 60 * 1000, // 5 minutes
    limit: 100, // Limit each IP to 100 requests per `window` (here, per 5 minutes).
        message: 'Too many requests',
})

// Apply the rate limiting middleware to all requests.
app.use(limiter)
```

**Environment setup:**<br>
At this stage we will create a `.env` file in our `server` directory to stores environment-specific variables for an application, often including sensitive data like API keys and database credentials. This allows us to manage configurations without hardcoding them directly into the application's code, promoting flexibility and security. 

```bash
npm i dotenv
```

```json title="package.json" linenums="14" hl_lines="3"
 "dependencies": {
    "body-parser": "^2.2.0",
    "dotenv": "^16.5.0",
    "express": "^5.1.0",
    "express-rate-limit": "^7.5.0",
    "http-errors": "^2.0.0"
  },
```
We want to read the port number from the `.env` file. We can do this by adding the following code to our `.env` and `app.js` files.

```env title=".env" linenums="1" hl_lines="1"
    PORT=3000
```

```javascript title="src/secret.js" linenums="1" hl_lines="1-3"
    const dotenv = require('dotenv').config()
    // read from `.env` if not found set 3000 as default port
    PORT = process.env.PORT || 3000

    module.exports = {PORT}
```

```javascript title="index.js" linenums="1" hl_lines="2"
   const app = require('./app.js');
    const {PORT} = require('./secret.js');
    // responible for instantiating the server
    app.listen(PORT, ()=>{
        console.log(`server running on http://localhost:${PORT}`);
    })

```



### Code so far

=== "javascript"

    ```js title="app.js" linenums="1"
    const express = require('express');
    const createError = require('http-errors')
    const bodyParser = require('body-parser')
    const rateLimit = require('express-rate-limit')
    const morgan = require('morgan')
    const app = express()


    const limiter = rateLimit({
        windowMs: 5 * 60 * 1000, // 5 minutes
        limit: 100, // Limit each IP to 100 requests per `window` (here, per 5 minutes).
            message: 'Too many requests',
    })

    // Apply the rate limiting middleware to all requests.
    app.use(limiter)
    // setup the logger
    app.use(morgan('dev'))

    // parse application/json
    app.use(bodyParser.json())


    app.get('/api/users', (req, res) => {
        res.status(200).send(
            {
                'success': true,
                'msg':'users is returned'}
            );
    })

    app.get('/products', (req, res) => {
        res.status(200).json(
            {
                'success': true,
                'msg':'products is returned'}
            );
    })


    // client error handling
    app.use(( req, res, next) => { 
    // http-errors   
    next(createError(404, 'Route Not Found')); // check error
    })

    // server error handling => all errors will be logged here
    app.use((err, req, res, next) => {
    return res.status(err.status || 500).json({
        success : false,
        message : err.message
        })
        
    })

    module.exports = app
    ```


=== "javascript"

    ```js title="index.js" linenums="1"
    const app = require('./app.js');
    const {PORT} = require('./secret.js');
    // responible for instantiating the server
    app.listen(PORT, ()=>{
        console.log(`server running on http://localhost:${PORT}`);
    })
    ```

=== "env"

    ```env title=".env"  linenums="2"
    PORT=3000
    ```
=== "javascript"

    ```js title="secret.js" linenums="1"
    const dotenv = require('dotenv').config()
    // read from `.env` if not found set 3000 as default port
    PORT = process.env.PORT || 3000

    module.exports = {PORT}
    ```

## Connect to MongoDB:


=== "ENV"

    ```env title=".env"
    MONGO_USER = admin
    MONGO_USER_PASS = admin123
    DB_NAME = crud-api
    MONGO_DB_URL= `mongodb+srv://admin:admin123@mern-ecomerce.to66f.mongodb.net/crud-api`


    ```

=== "JavaScript"

    ```js title="src/config/data.js"  linenums="1"
    const mongoose = require('mongoose');
    const {MONGO_DB_URL} = require('../secret');
    const connectionDB = async(options= {}) => {
        try{
            await mongoose.connect(MONGO_DB_URL, options);
            console.log('DB connection established');
            mongoose.connection.on('error', (error)=>{
                console.error('Error connecting to  database : '+error.toString());
            });
        }catch(error){
            console.error('Could not connect to  database : '+error.toString());
        }

    };
    module.exports = connectionDB
    ```

=== "JavaScript"

    ```js title="secret.js"  linenums="1"  hl_lines="4-5"
    const dotenv = require('dotenv').config()
    // read from `.env` if not found set 3000 as default port
    PORT = process.env.PORT || 3000
    const DB_NAME = process.env.DB_NAME || 'crud-api';
    const MONGO_DB_URL = process.env.MONGO_DB_URL || `mongodb://localhost:27017/${DB_NAME}`;
    module.exports = {PORT,
        MONGO_DB_URL,
        DEFAULT_USER_IMAGE
    }

    ```


=== "JavaScript"

    ```js title="index.js"  linenums="1"  hl_lines="7"
    const app = require('./app.js');
    const {PORT} = require('./secret.js');
    const connectDB = require('./config/db.js');
    // responible for instantiating the server
    app.listen(PORT, async()=>{
        console.log(`server running on http://localhost:${PORT}`);
        await connectDB();
    })
    ```