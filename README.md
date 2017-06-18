# Front-end Development with JavaScript

### Introduction to REST APIs

---

# API

API is short for Application Programming Interface.

It's a common way of refering to HOW a program makes some of its functionality available to other programs. 

For instance, a program running on a server can allow a web page to ask it for a list of users.

---

# Web APIs

There are many kinds of APIs, but in this course we are mostly concerned with Web APIs, also known as Web Services. Both terms mean something like "web pages for computers".

Web pages are a visual format, meant to be visually consumed (i.e. read) by humans. However, computers are blind, and cannot easily interpret many of the visual details of web pages, like what font, colour or size some text is in, where it is positioned in the screen, etc... Web APIs commonly provide information in structured formats such as JSON and XML.

---

# API Endpoints

Web APIs commonly consist of a set of URLs, which in this context are often called API "endpoints". For instance, the Zungebot API has the following endpoints for exchanging information about users:

- Collection endpoint, i.e. a URL for dealing with all users:
  https://redi-zungebot.herokuapp.com/api/user/all

- Resource endpoint, i.e. a URL for dealing the "tiago" user:
  https://redi-zungebot.herokuapp.com/api/user/tiago

---

# REST APIs

An increasingly number of Web APIs are called REST APIs. REST stands for "REpresentational State Transfer", and in a way describes the way the web works.

The web can be seen as a network of "Resources" identified by URLs. These resources can be web pages to be read by humans or API endpoints to be processed by programs.

---

# RESTlike vs RESTful APIs

Actually, most APIs that describe themselves as REST APIs do not comply with the REST standard as described by Roy Fielding in his thesis. 

We often use the term "RESTlike API" to describe APIs that implement some aspect of REST, and use the term "RESTful API" for more sophisticated REST APIs. Most APIs nowadays are RESTlike, not RESTful. 

In this course we only cover RESTlike APIs

---

# Nouns and Verbs

We can think of the resources identified by URLs as the "Nouns" in our web language (e.g. https://redi-zungebot.herokuapp.com/api/user/tiago)

Similarly, the ways we interact these "Nouns" can be seen as the "Verbs" in our web language.

One crucial aspect of REST APIs is that the web only uses a very limited number of verbs, which correspond to the "methods" of the HTTP protocol.

---

# Resource Representation

Another important aspect of REST APIs is that the "Resources" (for instance, a specific user) can be "represented" in various ways.

A human opening the URL for a specific user in his browser might be shown a web page with information about that user.

The same URL, when accessed by a computer program, might return information about the user in JSON, XML, CSV or some other format.

---

# Internet vs Web

What's the difference between the Internet and the Web? The Internet is based on IP, while the web is based on HTTP (which runs on top of IP)

The Internet Protocol allows many different types of communication: viewing web pages, making Skype calls, streaming video, sending emails. Each form of communication usually has its own protocol.

The protocol underlying the web is called HTTP, the HyperText Transfer Protocol.

---

# HTTP Requests and Responses

HTTP was designed as a request-response protocol in a client-server model.

The client (i.e. the browser) always initiates communication by sending an HTTP Request to a server.

The server never initiates communication with the browser - it just replies to an HTTP Request by sending an HTTP Response.

---

# HTTP Request

An HTTP Request always has the same format:

1. Request Line, specifying the HTTP method, URL and HTTP version
2. Optional Request Headers, which are key-value pairs
3. A blank line
4. Optional Message Body

---

# HTTP Response

An HTTP Response always has the same format:

1. Status Line, containing the HTTP version, the HTTP status code and status description
2. Optional Response Headers, which are key-value pairs
3. A blank line
4. Optional Message Body

---

# Example of HTTP Request

```http
GET https://redi-zungebot.herokuapp.com/api/user/pete/ HTTP/1.1
Authorization: REDI-school_2017?
Content-Type: application/json
```

---

# Example of HTTP Response

```http
HTTP/1.1 200 OK
(Headers omitted ...)

{
  "_id": "59189b7c6f56bb1d67375a43",
  "username": "pete",
  "firstName": "Peter",
  "lastName": "Wurst",
  "helper": true,
  "seeker": false,
  ...
  "email": "pete@gmail.com"
}
```

---

# HTTP Methods

RESTlike APIs usually use the following 5 out of the 8 HTTP methods ([More info here](http://restfulapi.net/http-methods/)):

- GET - The method used when you click on links or enter a URL into the address bar
- POST - The method used when you click on the submit button after filling in a form
- PUT - Not commonly used in web pages
- PATCH - Not commonly used in web pages
- DELETE - Not commonly used in web pages

---

# CRUD

CRUD stands for "Create, Retrieve, Update, Delete".

Most of the operations we do with data fall into one of these four categories, and we often call them CRUD operations.

---

# CRUD (continued)

For instance, a web API for a user might allow us to do the following:

- CREATE a user, by sending the user's information to an API endpoint
- RETRIEVE information about the user, structured as a JSON object
- UPDATE the user's data, by sending his new phone number
- DELETE a user

---

# Mapping CRUD operations to HTTP methods

- CREATE: send POST HTTP Request with JSON message body
- RETRIEVE: send GET HTTP Request, receive response with JSON message body
- PUT: send PUT HTTP Request with new JSON message body
- PATCH: send PATCH HTTP Request with partial JSON message body
- DELETE: send DELETE HTTP Request

---

# HTTP Status Codes

These are the four most frequent kinds of HTTP status codes:

- 2xx: it worked (e.g. 200 OK)
- 3xx: redirect to another URL (e.g. 304 Not Modified)
- 4xx: client error (e.g. 404 Not Found)
- 5xx: server error (e.g. 500 Internal Server Error)

[More info here](http://restfulapi.net/http-status-codes/)

---

# Further study

- [HTTP Status Codes](http://www.restapitutorial.com/httpstatuscodes.html)
- [Using HTTP Methods for RESTful Services](http://www.restapitutorial.com/lessons/httpmethods.html)
- [Chapter 17 of Eloquent JavaScript](http://eloquentjavascript.net/17_http.html#h_vXdZCu/Tty) (read only the two first sections, "The Protocol" and "Browsers and HTTP")
- [RESTful API Design - Methods](http://restful-api-design.readthedocs.io/en/latest/methods.html)
- [Anatomy of a Web Request](https://robrich.org/slides/anatomy_of_a_web_request/#/6)