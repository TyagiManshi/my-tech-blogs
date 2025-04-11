---
title: "Why Choose Express.js"
datePublished: Fri Apr 11 2025 19:10:11 GMT+0000 (Coordinated Universal Time)
cuid: cm9d5w76k000t09ky5idq9ini
slug: expressjs-simplifying-backend
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1744393491131/1782048f-26be-498d-9209-cdc83597afc9.png
tags: express, backend, developer, chaicode

---

When building web applications, I like to think of **Node.js** as driving a powerful car — you've got the engine, the wheels, and the fuel to get moving. But imagine trying to drive through a new city without a **GPS** — you’d have to figure out every route, every turn, and every stop manually.

That’s exactly what **Express.js** solves. Express is like the **GPS system** for your backend. It doesn’t replace Node.js — it enhances it by giving you clear directions, automatic routing, and helpful utilities to reach your destination faster and with fewer mistakes.

With Express, you don’t have to hard-code how every HTTP request is handled. Instead, you define routes (like destinations), use middleware (like checkpoints or toll booths), and process data smoothly — all while staying in control of the journey.

In this blog, I’ll walk you through everything step by step. By the end, you’ll see how Express turns backend development into a smooth, guided ride — one where you’re always on the right path.

---

## Introduction

Express.js is a lightweight and flexible web application framework built on top of Node.js. It simplifies the process of building web applications and APIs by providing a set of features such as routing, middleware support, and template engines. With Express.js, developers can efficiently handle HTTP requests and responses, define routes for different endpoints, and manage middleware functions that process requests before they reach the final handler. Its minimalistic approach allows for the creation of scalable and maintainable server-side applications, making it a popular choice in the Node.js ecosystem.

It also supports the **MVC (Model-View-Controller)** structure, which means you can organize your code in a clean way:

* **Model**: Handles the data and business logic. It communicates with the database and manages how data is created, stored, and updated.
    
* **View**: Represents the UI (User Interface). It shows data to the user and displays what the user interacts with.
    
* **Controller**: Acts as a link between the Model and the View. It receives user input, processes it (using the model), and returns the appropriate response (via the view).
    

🧠 **Example to Understand:**

Imagine you're building a **To-Do App**:

* The **Model** stores all the tasks (like: `['Buy groceries', 'Finish project']`).
    
* The **View** is the HTML page that shows the list of tasks to the user.
    
* The **Controller** receives the request when a user adds a new task, updates the model, and then refreshes the view to show the updated list.
    

---

## Key Features of ExpressJS

* ***Routing*** — Express uses routes to direct incoming requests to the correct part of your app.  
    For example, `/home` might show the homepage, and `/login` might show a login form.
    
* ***Cookies*** — Cookies are used to store information about the user, such as login details, etc. Express provides various methods to set, get, and delete cookies.
    
* ***HTTP Requests*** — Express includes all the necessary modules for handling HTTP requests and responses (Like — GET, POST, PATCH, DELETE, etc).
    
* ***Middleware*** — Middleware functions run in the middle of a request and response. They are useful for tasks like authentication, logging, or modifying request data before it reaches the final route.
    
* ***REST*** — (Representational State Transfer or REST). Express apps support the idea of REST-ful web service and can be developed by following the prescribed standards.
    
* ***WebSockets*** — Express can work with WebSockets to support real-time, two-way communication between client and server (useful for chat apps, notifications, etc.).
    
* ***Streaming*** — Express apps can use Streaming methods to handle large amounts of data or to transmit data in real time.
    

---

## How to Create a Simple Web Server with Node.js?

Before jumping into Express, it's crucial to understand how Node.js itself creates a server. Node.js has a built-in module called `http` that allows us to spin up a basic web server.

```javascript
const http = require('http');

const server = http.createServer((req, res) => {
  if (req.url === '/' && req.method === 'GET') {
    res.end('Home Page');
  } else if (req.url === '/about' && req.method === 'GET') {
    res.end('About Page');
  } else {
    res.end('Page Not Found');
  }
});

server.listen(3000, () => {
  console.log('Server is running on port 3000');
});
```

**Line-by-line breakdown:**

✅ `const http = require('http');`: This line imports Node.js's built-in `http` module. Think of this as loading the blueprint to create a server.

✅ `http.createServer(...)`: This method creates the actual server. It takes a callback function with `req` (request) and `res` (response) as parameters.

#### ✅ `if (req.url === '/' && req.method === 'GET') { res.end('Home Page'); }`

* This checks: Did the user request the root (`/`) page with a GET method?
    
* If yes, we send back a simple `Home Page` response.
    

#### ✅ `else if (req.url === '/about' && req.method === 'GET') { res.end('About Page'); }`

* This checks: Did the user request the `/about` page with a GET method?
    
* If yes, we respond with `About Page`.
    

#### ✅ `else { res.end('Page Not Found'); }`

* If the user tries any other route or uses the wrong HTTP method (like POST instead of GET), we respond with a default `Page Not Found` message.
    

✅ `res.end();`: Marks the end of the response.

#### ✅ `server.listen(3000, ...)`: Starts the server and makes it listen on port 3000.

#### Imagine the olden days… 🧍🏻‍♂️

There’s a **telephone operator** sitting in a room. Every time someone wants to make a call, the operator has to:

* **Pick up the call** (like receiving an HTTP request)
    
* **Ask who you want to talk to** (figure out the request details)
    
* **Manually connect the wires** to the correct person (send a response)
    
* **Repeat this for every call** that comes in
    

That’s basically how a raw **Node.js** server works — you write all the logic by yourself. For every incoming request, you have to manually:

* Check the URL and HTTP method
    
* Decide what response to send
    
* Handle any data or errors
    
* Repeat this for every type of request
    

It’s a lot of work! 😓

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1744395485802/f0e90e5c-d072-4e30-ac2b-7a0cdf3c05ea.gif align="center")

---

## Here Comes Express.js — The Smart Operator

To use Express in your NodeJS application, you need to install the ***express*** npm package. You can install it by using the following line of code in the terminal of your project location — **npm install express**

Now, in the next step, you need to include express into your node application and allow your application to listen in on a particular port number. The sample code for this is -

```javascript
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Home Page');
});

app.get('/about', (req, res) => {
  res.send('About Page');
});

app.listen(3000, () => {
  console.log('Server is running on port 3000');
});
```

**Explanation:**

* `const express = require('express');`: We import the Express library.
    
* `const app = express();`: This initializes an Express app instance.
    
* `app.get('/', ...)`: Sets up a GET route for the homepage.
    
* `res.send('...')`: Sends back a response.
    
* `app.listen(3000, ...)`: Makes the app listen on port 3000.
    

**Key Benefit:** Express handles routing cleanly and allows easy separation of logic by URL path and HTTP method (GET, POST, etc.).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1744397921086/97aed6d0-28d9-4561-89db-9dcb5596b4dc.gif align="center")

---

## **Methods in Express.js**

In Express.js, methods refer to the functions that handle different HTTP request types for specific routes. These methods correspond to the standard HTTP verbs like GET, POST, PUT, DELETE, and more.

**Here's a breakdown of common Express.js methods and their usage:**

* `app.get(path, callback)`: Handles GET requests to the specified path.
    
* `app.post(path, callback)`: Handles POST requests to the specified path.
    
* `app.put(path, callback)`: Handles PUT requests to the specified path.
    
* `app.delete(path, callback)`: Handles DELETE requests to the specified path.
    
* `app.all(path, callback)`: Handles all HTTP request methods for the specified path.
    
* `app.use(middleware)`: Mounts middleware functions to the app. Middleware functions can access the request and response objects, and can perform tasks like logging, authentication, or data manipulation.
    

---

## What is Middleware in Express and How to Use It?

A **middleware** in Express is a function that sits between the request and response cycle. It can access the request (`req`) and response (`res`) objects, perform actions (like logging, authentication, or modifying data), and then either end the request or pass control to the next middleware or route using `next()`.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1744391686799/3bc795e2-4c8a-4fbc-a9e0-30a37958b97a.png align="center")

Middleware functions in Express are like **checkpoints or pit stops** that every request goes through **before** it reaches the final destination (your route handler).

They run **in the order they’re defined** and can either:

* Modify the request or response
    
* End the response
    
* Or pass it along to the next middleware with `next()`
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1744390837721/92a72455-5da8-4eaa-b664-4c52633e5b80.png align="center")

**Explanation:**

* `app.use(...)`: This applies middleware globally to all incoming requests.
    
* `req.method` and `req.url`: These provide information about the request type and the URL.
    
* `next()`: Passes control to the next middleware or route. If `next()` is not called, the request will hang.
    

**Why it's powerful:**  
It helps you **keep your logic clean, reusable, and separated**. Instead of repeating checks in every route, you write it once as middleware.

---

## URL Parameters & Query Strings

When building routes that accept dynamic input from users, we commonly use **URL parameters** and **query strings**.

#### URL Parameters (Dynamic Routes) :

URL parameters are used to **capture values directly from the URL path**.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1744393460856/f4e64b2b-a335-4f5a-9003-3bf4f116fc06.png align="center")

* The `:id` acts as a placeholder for any dynamic value.
    
* If a request is made to `/users/101`, `req.params.id` will return `101`.
    

#### Query Strings (Optional Filters) :

Query strings are used to **send extra information** in the URL — usually for filtering, sorting, or searching.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1744393207452/a65f2871-3f4f-4d87-918b-e87fd15a7f3b.png align="center")

* A URL like `/search?q=express` will return `req.query.q` as `express`.
    
* You can pass multiple parameters: `/search?q=nodejs&page=2`
    

---

## **Status codes**

In Express.js, status codes are three-digit numbers that indicate the outcome of an HTTP request. They provide information about whether the request was successful, encountered an error, or requires further action.

**Common Status Codes:**

* **200 (OK):** The request was successful.
    
* **201 (Created):** A new resource was created.
    
* **400 (Bad Request):** The server cannot or will not process the request due to an apparent client error.
    
* **401 (Unauthorized):** The client must authenticate itself to get the requested response.
    
* **403 (Forbidden):** The client does not have access rights to the content.
    
* **404 (Not Found):** The server cannot find the requested resource.
    
* **500 (Internal Server Error):** The server encountered an unexpected condition that prevented it from fulfilling the request.
    

You can set status codes in your Express.js responses using the `res.status()` method

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1744392425850/0b7a5234-94df-44f8-80dd-f34f91ecb58a.png align="center")

---

## Conclusion

And that’s a wrap! 🎬

We’ve gone through the basics of Node.js servers, explored the power of Express.js, understood middleware, and cleared up the confusion between URL parameters and query strings. Whether you're building your first backend app or brushing up for interviews, these concepts are essential.

If this blog helped you even a little, please give it a like ❤️, share it with your fellow coders.

Have questions or feedback? Drop them in the comments — I’d love to connect. 💬

Thanks for reading — and as always, **Happy Coding!** 😄