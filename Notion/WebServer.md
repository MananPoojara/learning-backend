# Web Server

- The server. This is the computer that receives requests.
- The app. This is the application running on the server that listens for requests, retrieves information from the database, and sends a response.
- The database. Databases are used to organize and persist data.

## **What is a Web API, really?**

An API is a collection of clearly defined methods of communication between different software components.

More specifically, a *Web API* is the interface created by the back-end: the collection of endpoints and the resources these endpoints expose.

## **Other principles of the request-response cycle:**

- The server typically cannot initiate responses without requests!
- Every request needs a response, even if it’s just a 404 status code indicating that the content was not found. Otherwise your client will be left *hanging* (indefinitely waiting).
- The server should not send more than one response per request. This will throw errors in your code.

### [**What is Node?**](https://www.theodinproject.com/lessons/nodejs-introduction-what-is-nodejs#what-is-node)

The [**Node.js website**](https://nodejs.org/en/about/) declares:

> As an asynchronous event driven JavaScript runtime, Node is designed to build scalable network applications.

## Web Server

apache

express

tomcat

Are already ready to use server

we can make our own servers with node.js ,python and etc..

use for serving web pages

use http protocols

hosting web pages and APIs

Requesting web page (httpReq)

- The server. This is the computer that receives requests.
- The app. This is the application running on the server that listens for requests, retrieves information from the database, and sends a response.
- The database. Databases are used to organize and persist data.

## **What is a Web API, really?**

An API is a collection of clearly defined methods of communication between different software components.

More specifically, a *Web API* is the interface created by the back-end: the collection of endpoints and the resources these endpoints expose.

## **Other principles of the request-response cycle:**

- The server typically cannot initiate responses without requests!
- Every request needs a response, even if it’s just a 404 status code indicating that the content was not found. Otherwise your client will be left *hanging* (indefinitely waiting).
- The server should not send more than one response per request. This will throw errors in your code.

### [**What is Node?**](https://www.theodinproject.com/lessons/nodejs-introduction-what-is-nodejs#what-is-node)

The [**Node.js website**](https://nodejs.org/en/about/) declares:

> As an asynchronous event driven JavaScript runtime, Node is designed to build scalable network applications.

## Web Server

apache

express

tomcat

Are already ready to use server

we can make our own servers with node.js ,python and etc..

use for serving web pages

use http protocols

hosting web pages and APIs

Requesting web page (httpReq)

![image.png](./images/image.png)

Getting Response with status code and content (httpRes)

![image.png](<./images/image%20(1).png>)

how actually our request and response goes there and server will find the web page that you requested so

basically this transporting web pages ofc works on TCP so when someone requesting something that time in server some space in memory is created as know as TCP Socket

![image.png](<./images/image%20(2).png>)

We can see here now when someone request web page the cache/thread or space is gone busy it’s called blocking single-threaded web server

so when another client requesting what we can do 🤔

Ohh We can create another thread so that req go to that thread and it’s solved but YK server has space maintance and all 🙃

![image.png](<./images/image%20(3).png>)

In Apache Tomcat have parameter called maxiumThread smthing so.. yahh

**Example :**

httpd

IIS

lighttpd

tomcat

http-server

**Write own :**

node

python

tornado

Let’s See How Things work in code Okay :)

install apache in system then run localhost:80

- and your index.html is running the file is in /var/www/httpd …
- so i make one html file and one Js file for seeing the E-Tag That is in req header

![image.png](<./images/image%20(4).png>)

![swappy-20240828-224200.png](./images/swappy-20240828-224200.png)

you can see two files here

now let’s see in broser

![swappy-20240828-224330.png](./images/swappy-20240828-224330.png)

![image.png](<./images/image%20(5).png>)

we can see here status code is 304 Not Modified cause ETag and If-non-match ETag are same

now i chaging content of js then we see changes

look at images we change and status is 200 ok not 304 for not modified

but now i refresh the if-not-match has new ETag and code 304

![image.png](<./images/image%20(6).png>)

Now Let’s start building something in Node

```jsx
const express = require("express");
const app = express();

app.get("/", (req, res) => {
  res.json({
    message: "heloo",
  });
});

app.listen(5000, () => console.log("i am listening 5000"));
```
