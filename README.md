# web-application-software-architecture-101
web application software architecture educative course 101


## Importance of getting the application architecture right

To successfully create anything, you have to get the base right. Whether it is constructing a building or making a pizza, if we don’t get the base right, we have to start over. Yeah! I know. But there is no other way around.

Building a web application is no different. The architecture is the base and has to be carefully thought through to avoid any major design changes and code refactoring at a later point.

Speaking from experience, you don’t want to delve into re-designing stuff. It sucks up your time like a black hole and has the potential to push your shipping date further down the calendar by months, if not longer. I won’t even bring up the waste of engineering and financial resources caused due to this.

How much we have to refactor largely depends on the stage of the development process we hit an impasse due to hasty decisions made during the initial design phases. So, before we even touch the code and get our hands dirty, we must make the underlying architecture right.

### An overview of the software development process

In the industry, architects, developers and product owners spend a lot of time studying and discussing business requirements. In software engineering jargon, this is known as Requirement Gathering and Analysis.

Once we are done with the business requirements, we sit down and brainstorm the use cases we have to implement. This also involves figuring out the corner cases as early as possible while trying to fit the building blocks together.

Once we understand the business requirements, use cases, including the corner cases, it’s time to start the research on picking the right technology stack to implement our application.

### Proof of concept

After we pick the fitting tech stack, we start writing a POC (Proof of Concept).

Why a POC?

A POC helps us get a closer, more hands-on view of the technology and the primary use case implementation. We get an insight into the pros and cons of the tech, performance, or other technical limitations, if any.

It helps with the learning curve if we’re working with entirely new tech. Additionally, the non-technical people, like the product owners and stakeholders, have something concrete to play with and base their future decisions on.

Now, this is only for an industry scale product. If you are an indie developer or a small group, you can always skip the POC part and start with the main code.

So, we showcase the POC to the stakeholders. If everyone is satisfied, we get a green light to finally get down to creating the main repo and our first dev branch on GitHub or any similar code hosting service the business prefers.

### Course design

## Introduction

I’ll begin the course by discussing the different tiers involved in the software architectural landscape. This is like having a bird’s eye view of the software architecture realm and it is important to be understood well.

### What is a tier?

Think of a tier as both logical and physical separation of components in an application or a service. This separation is at a component level, not the code level.

What do I mean by components?

*  Database
*  Backend application server
*  User interface
*  Messaging
*  Caching etc.

These are the components that make up a web service.

![image](https://user-images.githubusercontent.com/25869911/155874173-2f7432d2-cc62-420d-93b9-1b3f3388decd.png)


### Single-tier applications

In a single-tier application, the user interface, backend business logic, and the database reside in the same machine.

![image](https://user-images.githubusercontent.com/25869911/155874207-ad55aacc-8807-4809-9cb4-314622b95374.png)

Typical examples of single-tier applications are desktop applications like MS Office, PC Games, image editing software like Gimp, Photoshop, etc.

### Upsides of single-tier applications#

The primary upside of single-tier applications is that they have no network latency since every component is located on the same machine. This adds up to the performance of the software.

Two, three and n-tier apps have to send data requests to the backend server often. This adds network latency to the system making the user experience slow compared to single-tier apps. In single-tier apps, the data is readily available since all the components are located in the same machine.

However, the actual performance of a single-tier app largely depends on the application’s hardware requirements and how powerful the machine it runs on is.

Also, when it comes to data privacy and safety, it is of the highest order in single-tier apps since the user’s data always stays in their machine and doesn’t need to be transmitted over a network for persistence.

### Downsides of single-tier applications

One big downside of single-tier apps is that the application’s publisher has no control over the application. Once the software is shipped, no code or feature updates can be made until the customer manually updates it by connecting to the remote server or downloading and installing a patch.

Due to this, in the 90s, there was nothing that the studios could do if their game was shipped with buggy code. They eventually had to face a lot of heat from the gamers due to the buggy nature of their software. This made product testing vital, responsible for making or breaking a business. Software testing had to be thorough since there was no room for any mistakes.

The code in single-tier applications is also vulnerable to being tweaked and reversed engineered. The product security for the app publisher is minimal. An evil person with some effort can get access to the application’s source code, modifying or copying it for profit. This is unlikely in an architecture where the company controls the application server and implements security to fend off the hackers.

Finally, a single-tier applications’ performance and look and feel can be inconsistent as the app rendering largely depends on the configuration of the user’s machine.

## Two-Tier Applications

A two-tier application involves a client and a server. The client contains the user interface with the business logic in one machine. Meanwhile, the backend server includes the database running on a different machine. The database server is hosted by the business and has control over it.

![image](https://user-images.githubusercontent.com/25869911/155874395-325085bf-fb34-4798-9963-b7e4936e4c3b.png)

Why do we need two-tier applications? Why not host the business logic on a different machine and have control over it too?

Also, again isn’t the application code vulnerable to being accessed by a third person?

### The need for two-tier applications

Well, yes! The code is vulnerable. However, there are use cases where two-tier applications come in handy, for instance, a to-do list app or a similar planner or a productivity app.

In these scenarios, even if the code is accessed by a third person, it won’t cause the business much harm. On the contrary, since the business logic and the user interface reside in the same machine, there are fewer network calls to the backend server. This keeps the latency of the application low, proving to be an upside.

Taking a to-do list app as an example, the application makes a call to the database server only when the user has finished creating their list and wants to persist the data.

Another good example of two-tier apps is the browser and mobile app-based games. The game files are pretty heavy, and they only get downloaded on the client once when the user uses the application for the first time. And they make the network calls to the backend only to persist the game state.

Additionally, fewer server calls mean less money spent to keep the servers running, which is naturally economical. However, picking this tier type for our service largely depends on our business requirements and the use case. When designing our system, we can choose to keep the user interface and business logic on the client or move the business logic to a dedicated backend server, making it a three-tier application that we will learn in the lesson up-next.

## Three-Tier Applications

Three-tier applications are pretty popular and largely used on the web. Almost all simple websites like blogs, news websites, etc., are part of this category.

In a three-tier application, the user interface, business logic, and the database all reside on different machines and, thus, have different tiers. They are physically separated.

![image](https://user-images.githubusercontent.com/25869911/155874562-164e750a-f692-4731-9903-b89b2a734703.png)


Let’s take the example of a simple blog. The user interface will be written using HTML, JavaScript, and CSS, the backend application logic will run on a server like Apache and the database will be MySQL. A three-tier architecture works best for simple use cases.

## N-Tier Applications

An n-tier application is an application that has more than three components (user interface, backend server, database) involved in its architecture.

What are those components?

* Cache
* Message queues for asynchronous behavior
* Load balancers
* Search servers for searching through massive amounts of data
* Components involved in processing massive amounts of data
* Components running heterogeneous tech commonly known as web services, microservices, etc.

All the social applications like Instagram, Facebook, TikTok, large-scale consumer services like Uber, Airbnb, online massive multiplayer games like Pokémon Go, Roblox, etc., are n-tier applications. n-tier applications are more popularly known as distributed systems.

### What’s the need for so many tiers?

Two software design principles that are key to explaining this are the single responsibility principle and the separation of concerns.

#### Single responsibility principle

Single responsibility principle means giving one dedicated responsibility to a component and letting it execute it flawlessly, be it saving data, running the application logic or ensuring the delivery of the messages throughout the system.

This approach gives us a lot of flexibility, making management easy. We can have dedicated teams and code repositories for individual components keeping things cleaner.

With the single responsibility principle, the components are loosely coupled in terms of responsibility and making a change to one doesn’t impact the functionality of other components. For instance, upgrading a database server with a new operating system or a patch won’t affect other service components. Even if something amiss happens during the OS installation, just the database will go down. The application as a whole would still be up and only the features requiring the database would be impacted.

The single responsibility principle is why I was never a fan of stored procedures.

Stored procedures enable us to add business logic to the database, which is always a big no. What if, in the future, we want to plug in a different database? Where do we take the business logic? Do we take it to the new database? Or do we refactor the application code and squeeze in the stored procedure logic somewhere?

A database should not hold business logic. It should only take care of persisting the data. This is what the single responsibility principle is, which is why we have separate tiers for separate components.

#### Separation Of concerns

Separation of concerns loosely means the same thing, be concerned about your work only and stop worrying about the rest of the stuff. These principles act at all the levels of the service, be it the tier level or the code level.

Keeping the components separate makes them reusable. Different services can use the same database, messaging server or any other component as long as they are not tightly coupled with each other.

Having loosely coupled components is the way to go. This approach enables us to scale our service easily when things grow beyond a certain scale in the future.

### Difference between layers & tiers

Note: Don’t confuse tiers with the layers of the application. Some prefer to use them interchangeably. However, in the industry, application layers typically mean the user interface, business, service and the data access layers.


![image](https://user-images.githubusercontent.com/25869911/155874921-baab5870-c259-4bfd-b89a-630d4c78bfb2.png)

These layers are at the code level. The difference between layers and tiers is that layers represent the conceptual/logical organization of the code, whereas tiers represent the physical separation of components.

All these layers together can be used in any tiered application. Be it single, two, three or n-tiered. I’ll discuss these layers in detail in the course ahead.

## What is Web Architecture?

Web architecture involves multiple components like a database, message queue, cache, user interface, etc., all running in conjunction to form an online service.


![image](https://user-images.githubusercontent.com/25869911/155875138-babc25d7-a90c-4e16-9cf2-c9c04698c990.png)


### Client-Server Architecture

You already learned a bit about the client-server architecture when we discussed the two-tier, three-tier and n-tier architecture. Now, we look at it in detail.

![image](https://user-images.githubusercontent.com/25869911/155875171-f02da6d4-d8e6-4bbc-89b0-c25195ead881.png)

Client-server architecture is the fundamental building block of the web.

The architecture works on a request-response model. The client sends the request to the server for information and the server responds with it.

Every website you browse, be it a WordPress blog, an application like Facebook, Twitter, or your banking app, is built on the client-server architecture.

A very small percentage of business websites and applications use the peer-to-peer architecture, which differs from the client-server.

### Client

The client holds our user interface. The user interface is the presentation part of the application. It’s written in HTML, JavaScript, CSS and is responsible for the look and feel of the application

The user interface runs on the client. In very simple terms, a client is a gateway to our application. It can be a mobile app, a desktop or a tablet like an iPad. It can also be a web-based console, running commands to interact with the backend server.

![image](https://user-images.githubusercontent.com/25869911/155875303-772b3486-3910-449e-90f9-97dcac9d79b1.png)

### Technologies used to implement clients in web applications

The open-source technologies popular for writing the web-based user interface in the industry are vanilla JavaScript, jQuery, React, Angular, Vue, Svelte, etc. All these libraries are written in JavaScript.

Different platforms require different frameworks and libraries to write the front-end of our application. For instance, mobile phones running Android need a different set of tools than those running Apple or Windows OS.

### Types of Clients

There are primarily two types of clients:

* Thin client
* Thick client (sometimes also called the Fat client)

A thin client is a client that holds just the user interface of the application. It contains no business logic of any sort. For every action, the client sends a request to the backend server, just like in a three-tier application.

![image](https://user-images.githubusercontent.com/25869911/155875464-090eb1b4-95c2-494b-85d9-942557f42698.png)


### Thick client

On the contrary, the thick client holds all or some part of the business logic. These are the two-tier applications. We’ve already been through them.

The typical examples of fat clients are utility apps, online games, and so on.

### Server

#### What is a web server?

The primary task of a web server is to receive the requests from the client and provide the response after executing the business logic based on the request parameters received from the client.

Every online service needs a server to run. Servers running web applications are commonly known as application servers.

![image](https://user-images.githubusercontent.com/25869911/155875547-e556d461-81f3-44e8-ab47-9063782ff74e.png)

Besides the application servers, there are also other kinds of servers with specific tasks assigned. These include:

* Proxy server
* Mail server
* File server
* Virtual server
* Data storage server
* Batch job server and so on

The server configuration and the type can differ depending on the use case. For instance, if we run a backend application code written in Java, we would pick Apache Tomcat or Jetty. For simple use cases such as hosting websites, we would pick the Apache HTTP Server.

In this lesson, we will stick to the application server.

All the components of a web application need a server to run, be it a database, a message queue, a cache, or any other component. In modern application development, even the user interface is hosted separately on a dedicated server.

#### Server-side rendering

Often the developers use a server to render the user interface on the backend and then send the generated data to the client. This technique is known as server-side rendering. I will discuss the pros and cons of client-side vs. server-side rendering further down the course.

### Communication Between the Client and the Server

#### Request-response model

The client and the server have a request-response model. The client sends the request and the server responds with the data.

If there is no request, there is no response.

#### HTTP protocol

The entire communication happens over the HTTP protocol. It is the protocol for data exchange over the World Wide Web. HTTP protocol is a request-response protocol that defines how information is transmitted across the web.

It’s a stateless protocol, and every process over HTTP is executed independently and has no knowledge of previous processes.


#### REST API and API Endpoints

Speaking from the context of modern n-tier web applications, every client has to hit a REST endpoint to fetch the data from the backend.

The backend application code has a REST-API implemented. This acts as an interface to the outside world requests. Every request, be it from the client written by the business or the third-party developers, those who consume our API data have to hit the REST endpoints to fetch the data.

![image](https://user-images.githubusercontent.com/25869911/155876016-837e8fb4-aac6-4231-97d0-82a006243aad.png)


#### Real world example of using a REST API#

Let’s say we want to write an application to keep track of the birthdays of all our Facebook friends. The app would then send us a reminder a couple of days before the birthday of a certain friend.

To implement this, the first step would be to get the data of the birthdays of all our Facebook friends. We would write a client to hit the Facebook Social Graph API, which is a REST-API, to get the data and then run our business logic on the data.

### What is REST ?

REST stands for Representational State Transfer. It’s a software architectural style for implementing web services. Web services implemented using the REST architectural style are known as the RESTful web services.

A REST API is an API implementation that adheres to the REST architectural constraints. It acts as an interface. The communication between the client and the server happens over HTTP. A REST API takes advantage of the HTTP methodologies to establish communication between the client and the server. REST also enables servers to cache the response that improves the application’s performance.

![image](https://user-images.githubusercontent.com/25869911/155876168-2fd02d83-4fe1-4bf9-abc0-2658475e627b.png)


The communication between the client and the server is a stateless process. By that, I mean every communication between the client and the server is like a new one.

There is no information or memory carried over from the previous communications. So, every time a client interacts with the backend, the client has to send the authentication information to it as well. This enables the backend to figure out whether the client is authorized to access the data or not.

When implementing a REST API, the client communicates with the backend endpoints. This entirely decouples the backend and the client code.

#### REST endpoint

An API/REST/Backend endpoint means the URL of the service that the client could hit. For instance, https://myservice.com/users/{username} is a backend endpoint for fetching the user details of a particular user from the service.

The REST-based service will expose this URL to all its clients to fetch the user details using the above stated URL.

### Decoupling clients and the backend service

With the availability of the endpoints, the backend service does not have to worry about the client implementation. It just calls out to its multiple clients and says, “Hey Folks! Here is the URL address of the resource/information you need. Hit it when you need it. Any client with the required authorization to access a resource can access it”.

With the REST implementation, developers can have different implementations for different clients, leveraging different technologies with separate codebases. Different clients accessing a common REST API could be a mobile browser, a desktop browser, a tablet or an API testing tool. Introducing new types of clients or modifying the client code does not affect the functionality of the backend service.

This means the clients and the backend service are decoupled.

### Application development before the REST API

Before the REST-based API interfaces became mainstream in the industry, we often tightly coupled the backend code with the client. Java Server Pages (JSP) is one example of this.

We would always put business logic in the JSP tags. This made code refactoring and adding new features difficult because the business logic spread across different layers.

Also, on the backend, we had to write separate code/classes for handling requests from different types of clients. We needed a separate servlet for handling requests from a mobile client and a separate one for a web-based client.

After REST APIs implementation backend developers didn’t need to worry about the type of the client. All the devs had to do was provide the service endpoints to the clients and they would receive the response in a standard data transport format like JSON. It was now the responsibility of the clients to parse and render the response data.

This cut down a lot of unnecessary work for the backend developers. Also, adding new clients became a lot easier. Now, with REST, we can introduce any number of new clients without having to worry about the backend implementation.

In today’s application development landscape, there is hardly any online service implemented without a REST API. Want to access the public data of any social network? Just use their REST API.

#### API Gateway

![image](https://user-images.githubusercontent.com/25869911/155876426-1128764e-d758-44da-9d65-3cc60ccc5f8b.png)

The REST-API acts as a gateway or a single-entry point into the system. It encapsulates the business logic and handles all the client requests, taking care of the authorization, authentication, sanitizing the input data, and other necessary tasks before providing access to the application resources.

So, now we are aware of the client-server architecture. We also know what a REST API is. It acts as the interface, and the communication between the client and the server happens over HTTP.

### HTTP Push and Pull - Introduction

There are two modes of data transfer between the client and the server: HTTP PUSH and HTTP PULL.

Let’s find out what they are and what they do.

#### HTTP PULL

As I stated earlier, for every response, there has to be a request first. The client sends the request and the server responds with the data. This is the default mode of HTTP communication, called the HTTP PULL mechanism.

The client pulls the data from the server whenever required. It keeps doing this over and over to fetch the latest data.

An important thing to note here is that every request to the server and the response to it consumes bandwidth. Every hit on the server costs the business money and adds to the load on the server.

What if there is no updated data available on the server every time the client sends a request?

The client doesn’t know that, so naturally, it would keep sending the requests to the server over and over. This is not ideal and a waste of resources. Excessive pulls by the clients have the potential to bring down the server.

#### HTTP PUSH

To tackle this, we have the HTTP PUSH-based mechanism. In this mechanism, the client sends the request for certain information to the server just once. After the first request, the server keeps pushing the new updates to the client whenever they are available.

The client doesn’t have to worry about sending additional requests to the server for data. This saves a lot of network bandwidth and cuts down the load on the server by notches.

This is also known as a callback. The client phones the server for information. The server responds, “Hey!! I don’t have the information right now, but I’ll call you back whenever it is available”.

A very common example of this is user notifications. We have them in almost every web application today. We get notified whenever an event happens on the backend.

Clients use Asynchronous JavaScript & XML (AJAX) to send requests to the server in both the HTTP PULL and the HTTP PUSH mechanism.

There are multiple technologies involved in the HTTP PUSH-based mechanism, such as:

* Ajax Long polling
* Web Sockets
* HTML5 Event Source
* Message Queues
* Streaming over HTTP

### HTTP Pull - Polling With AJAX

The first is sending an HTTP GET request to the server manually by triggering an event on the user interface by clicking a button or interacting with any other element on the web page.

The other is pulling data dynamically at regular intervals using AJAX without any human intervention.

#### AJAX – Asynchronous JavaScript and XML

AJAX stands for Asynchronous JavaScript and XML. The name says it all. AJAX is used for adding asynchronous behavior to the web page.

![image](https://user-images.githubusercontent.com/25869911/155876841-41b941c8-ba91-4022-a3b3-832b524af6e0.png)


As you can see in the illustration above, instead of requesting the data manually every time with the click of a button, AJAX enables us to fetch the updated data from the server by automatically sending the requests over and over at stipulated intervals.

Upon receiving the updates, a particular section of the web page is updated dynamically by the callback method. We see this behavior all the time on news and sports websites, where the updated event information is dynamically displayed on the page without needing to reload it.

AJAX uses an XMLHttpRequest object to send the requests to the server. This object is built in the browser and uses JavaScript to update the HTML DOM (Document Object Model).

AJAX is commonly used with the jQuery framework to implement the asynchronous behavior on the UI.

This dynamic technique of requesting information from the server at regular intervals is known as polling.

It is important to note here that AJAX polling and AJAX Long polling are different techniques. Do not confuse them as one.

AJAX polling is the HTTP Pull mechanism and AJAX Long polling is a hybrid between the HTTP Push and the Pull, based on the BAYEUX protocol. I’ve discussed it in the HTTP Push-based technologies lesson.

### HTTP Push

#### Time to Live (TTL)

Time to Live (TTL)

In the regular client-server communication, which is HTTP PULL, there is a Time to Live (TTL) for every request. It could be 30 secs to 60 secs, varying from browser to browser.

If the client doesn’t receive a response from the server within the TTL, the browser kills the connection and the client has to re-send the request hoping it receives the data from the server before the TTL ends again.

Open connections consume resources, and there is a limit to the number of open connections a server can handle at one point. If the connections don’t close and new ones are introduced regularly over time, the server will run out of memory. Hence, the TTL is used in client-server communication.

But what if we are certain that the response will take more time than the TTL set by the browser?

#### Persistent connection

A persistent connection is a network connection between the client and the server that remains open for future requests and responses, as opposed to being closed after a single communication.

This facilitates HTTP PUSH-based communication between the client and the server.

![image](https://user-images.githubusercontent.com/25869911/155877146-34681780-ea49-4dfb-bf25-a08936e451fd.png)

#### Heartbeat interceptors

Now you might wonder how a persistent connection is possible if the browser kills the open connections to the server every x seconds?

The connection between the client and the server stays open with the help of Heartbeat Interceptors.

These are just blank request responses between the client and the server to prevent the browser from killing the connection.

Isn’t this resource-intensive?

#### Resource intensive

Yes, it is. Persistent connections consume a lot of resources compared to the HTTP PULL behavior. However, there are use cases where establishing a persistent connection is vital to an application’s feature.

For instance, a browser-based multiplayer game has a pretty large amount of request-response activity within a limited time than a regular web application.

It would be apt to establish a persistent connection between the client and the server in this use case from a user experience standpoint.

Long opened connections can be implemented by multiple techniques such as AJAX Long Polling, Web Sockets, Server-Sent Events, etc.

Let’s take a look into each of these methods in the lesson up next.

### HTTP Push-Based Technologies

#### Web Sockets

A Web Socket connection is preferred when we need a persistent bi-directional low latency data flow from the client to the server and back.

Typical use-cases of web sockets are messaging, chat applications, real-time social streams, browser-based massive multiplayer games, etc. These are apps with quite a significant number of read writes compared to a regular web app.

With web sockets, we can keep the client-server connection open as long as we want.

Have bi-directional data? Go ahead with web sockets. One more thing, web sockets don’t work over HTTP. The mechanism runs over TCP. Also, the server and the client should both support web sockets. Else it won’t work.

The WebSocket API and Introducing WebSockets – Bringing Sockets to the Web are good resources for further reading on web sockets.

https://www.html5rocks.com/en/tutorials/websockets/basics/
https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API

#### AJAX – Long polling

Long polling lies somewhere between AJAX and Web Sockets. In this technique, instead of immediately returning the empty response, the server holds the response until it finds an update to be sent to the client.

The connection in long polling stays open a bit longer compared to polling. The server doesn’t return an empty response. If the connection breaks, the client has to re-establish the connection to the server.

The upside of using this technique is that there are fewer requests sent from the client to the server than the regular polling mechanism. This cuts down a lot of network bandwidth consumption.

Long polling can be used in simple asynchronous data fetch use cases when you do not want to poll the server every now and then.

#### HTML5 Event-Source API and Server-Sent Events

The Server-Sent Events (SSE) implementation takes a different approach. Instead of the client polling for data, the server automatically pushes the data to the client whenever the updates are available. The incoming messages from the server are treated as events.

Via this approach, the servers can initiate data transmission towards the client once the client has established the connection with an initial request.

This helps eliminate a considerable number of blank request-response cycles cutting down the bandwidth consumption by notches.

To implement the server-sent events, the backend language should support the technology. On the UI, HTML5 Event-Source API is used to receive the incoming data from the backend.

An important thing to note here is that once the client establishes a connection with the server, the data flow is in one direction only, from the server to the client.

SSE is ideal for scenarios like a real-time Twitter feed, displaying stock quotes on the UI, real-time notifications, etc.

This is a good resource for further reading on SSE.

https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events

#### Streaming over HTTP

Streaming over HTTP is ideal for cases where we need to stream extensive data over HTTP by breaking it into smaller chunks. This is made possible with HTML5 and a JavaScript Stream API.

![image](https://user-images.githubusercontent.com/25869911/155877678-2bf89077-34a3-4d99-ac9c-501f66eea8c2.png)

Both the client and the server must agree to conform to the streaming settings to stream data. This helps them determine when the stream begins and ends over an HTTP request-response model.

The technique is primarily used for streaming multimedia content, like large images, videos, etc., over HTTP. Empowered by this technique, we can watch a partially downloaded video as it downloads by playing the downloaded chunks on the client.

For further reading on Stream API, this is a good resource.

https://developer.mozilla.org/en-US/docs/Web/API/Streams_API/Concepts

#### Summary

So, now we understand what HTTP Pull and Push are. We went through different technologies that help us establish a persistent connection between the client and the server.

Every tech has a specific use case, and AJAX is used to dynamically update the web page by polling the server at regular intervals.

Long polling has a connection open time slightly longer than the polling mechanism.

Web Sockets have bi-directional data flow, whereas server-sent events facilitate data flow from the server to the client.

Streaming over HTTP facilitates the streaming of large objects like multimedia files.

What tech would fit best for our use case depends on the application we intend to build.

In the next lesson, let’s gain an insight into the pros and cons of the client and the server-side rendering.

### Client-Side vs. Server-Side Rendering

#### Client-side rendering - How does a browser render a web page?

When a browser receives a web page from the server in response, it has to render the response on the window in the form of an HTML page.

To pull this off, the browser has several components, such as:

* The browser engine
* Rendering engine
* JavaScript interpreter
* Networking and the UI backend
* Data storage etc.

I won’t go into much detail; the gist is the browser has to do a lot of work to convert the response from the server into an HTML page. The rendering engine constructs the DOM tree and renders and paints the construction and so on.

Naturally, all this activity takes some time before the user can interact with the page.

#### Server-side rendering

To cut down all this rendering time on the client, developers often render the UI on the server, generate HTML there and directly send the HTML page to the UI.

This technique is known as server-side rendering. It ensures faster rendering of the UI, averting the UI loading time in the browser window because the page is already created and the browser doesn’t have to do much assembling and rendering work.

Here are some use cases for both approaches of rendering the UI—on the client and the server.

#### Use cases for server-side & client-side rendering

The server-side rendering approach is perfect for delivering static content, such as WordPress blogs. It’s also good for SEO because the crawlers can easily read the generated content.

However, modern websites are highly dependent on AJAX. On such websites, content for a particular module or a page section has to be fetched and rendered on the fly. In this use case, the server-side rendering doesn’t help much.

If we render the UI on the server for AJAX-based websites, for every AJAX request, the approach will generate the entire page on the server as opposed to just sending the updated content to the client in response.

This process will prove to be resource-intensive and would consume unnecessary bandwidth, failing to provide a smooth user experience.

Also, once the number of concurrent users on the website goes up, server-side rendering will exert an unnecessary load on the server.

So, for modern dynamic AJAX-based websites, the client-side rendering works best.

Moreover, we can leverage a hybrid approach to get the best of both worlds. We can use server-side rendering for the static content of our website and client-side rendering for dynamic content.

Okay, before we move on to the database, message queue and caching components, it’s essential for us to understand concepts such as:

* Scalability
* High availability
* Load balancing
* Monolith and microservices
* Understanding these concepts will help us understand the rest of the web components better.

### What is Scalability?

being in the software development universe, you’ve come across the word scalability numerous times. What is it? Why is it so important? Why is everyone talking about it? What are your plans or contingencies to scale when your app or the platform experiences significant traffic growth?

Scalability means the application’s ability to handle and withstand increased workload without sacrificing performance.

For example, if your app takes x seconds to respond to a user request. It should take the same x seconds to respond to each of your app’s million concurrent user requests.

The app’s back-end infrastructure should not crumble under a load of a million concurrent requests. It should scale well when subjected to a heavy traffic load and maintain the system’s latency.

![image](https://user-images.githubusercontent.com/25869911/155896623-2a2d6e5a-bbba-4e48-9223-4639201f8731.png)


### What is latency?

Latency is the time a system takes to respond to a user request. Let’s say you send a request to an app to fetch an image and the system takes 2 seconds to respond to your request. The latency of the system is 2 seconds.

Minimum latency is what efficient software systems strive for. No matter how much the traffic load on a system builds up, the latency should not go up. This is what scalability is.

If the latency remains the same, we can say that the application scaled well with the increased load and is highly scalable.

Let’s see scalability in terms of Big-O notation. Ideally, the complexity of a system or an algorithm should be O(1) which is constant time like in a map or a key-value database.

A program with the complexity of O(n^2) where n is the size of the data set is not scalable. As the size of the data set increases, the system will need more computational power and other resources to process the tasks.

So, how do we measure latency?

### Measuring latency

Latency is measured as the time difference between the action that a user takes on the website and the system’s response in reaction to that action. The action can be an event like clicking a button, scrolling down a web page, etc.

This latency is generally divided into two parts:

* Network latency
* Application latency

![image](https://user-images.githubusercontent.com/25869911/155896746-75041e8b-6044-4a23-ab22-c47d5d300752.png)

#### Network latency

Network latency is the time that the network takes to send a data packet from point A to point B. The network should be efficient enough to handle the increased traffic load on the website. To cut down the network latency, businesses use a CDN (Content Delivery Network) to deploy their servers across the globe as close to the end-user as possible. These close to the user locations are also known as Edge locations.

After having spent a decade in the industry writing code, I firmly believe that every software engineer should have knowledge of cloud computing. It’s the present and the future of application development and deployment.

#### Application latency

Application latency is the time the application takes to process a user request. There are more than a few ways to cut down the application latency. The first step is to run stress and load tests on the application and scan for the bottlenecks that slow down the system as a whole. I’ll talk more about it in the upcoming lessons.

#### Why is low latency so crucial for online services?

Latency plays a significant role in determining if an online business wins or loses a customer. Nobody likes to wait for a response on a website. There is a well-known saying, “If you want to test a person’s patience, give them a slow internet connection.”

If the visitor gets the response within a stipulated time, great otherwise, they’ll bounce off to another website. There is ample market research that concludes high latency in applications is a big factor in customers bouncing off a website. If there is money involved, zero latency is what businesses want. If only if this was possible.

Think of massive multiplayer online (MMO) games. A slight lag in an in-game event ruins the whole experience. A gamer with a high latency internet connection will have a slow response time despite having the best reaction time of all the players in an arena.

Algorithmic trading services need to process events within milliseconds. Fintech companies have dedicated networks to run low latency trading. The regular network just won’t cut it.

We can realize the importance of low latency by the fact that in 2011 Huawei and Hibernia Atlantic started laying a fiber-optic link cable across the Atlantic Ocean between London and New York. This property was estimated to cost approximately $300M just to save traders six milliseconds of latency.

### Types of Scalability

To scale well, an application needs solid computing power. The servers should be powerful enough to handle increased traffic loads.

There are two ways to scale an application:

* Vertically
* Horizontally

#### What is vertical scaling?

Vertical scaling means adding more power to our server. Let’s say our app is hosted by a server with 16 gigs of RAM. To handle the increased load, we now augment the RAM to 32 gigs. Here, we have vertically scaled the server.

![image](https://user-images.githubusercontent.com/25869911/155896953-0c8a76bd-b4e4-4e96-a220-a142b0f419d6.png)


Ideally, when the traffic starts to build on the app, the first step should be to scale vertically. Vertical scaling is also called scaling up.

In this type of scaling, we augment the power of the hardware running the app. This is the simplest way to scale as it doesn’t require any code refactoring or the need to make any complex configurations and so on. I’ll discuss in the next lesson why code refactoring is needed when we horizontally scale our app.

However, there is only so much we can do when scaling vertically. There is a limit to the compute power we can augment for a single server.

A good analogy would be to think of a multi-story building. We can keep adding floors to it but only up to a certain point. What if the number of people in need of a flat keeps rising? We can’t scale the building up to the moon for obvious reasons.

Now is the time to build more buildings. This is where horizontal scalability comes in.

When the traffic is too large to be handled by a single server, we bring in more servers to work together.

#### What is horizontal scaling?

Horizontal scaling, also known as scaling out, means adding more hardware to the existing hardware resource pool. This increases the computational power of the system as a whole.

![image](https://user-images.githubusercontent.com/25869911/155897034-8a2d44a1-ec3c-4cb5-a08b-b4a641c71252.png)

With this, the increased traffic influx can be efficiently dealt with. And there is no limit to how much we can scale horizontally, assuming we have infinite resources. We can keep adding servers after servers, setting up data centers after data centers.

Horizontal scaling also allows us to scale dynamically in real-time as the traffic on our website climbs and drops over a period of time. Dynamic scaling is not possible when scaling vertically.

#### Cloud elasticity

The most prominent reason cloud computing became mainstream in the industry is the ability of the cloud to scale dynamically. In case of the traffic climb, the cloud adds additional servers to the hardware resource pool and when it drops, the servers added are removed.

The ability to use and pay only for the hardware resources used by the website got popular with businesses for obvious economic reasons.

The process of adding and removing servers, stretching and returning to the original infrastructural computational capacity, on the fly is popularly known as cloud elasticity. It saves businesses truckloads of money every single day.

If you wish to know in detail how cloud platforms scale our apps and make them highly available. I’ve discussed the concept in my cloud computing 101 course how clustering works and how cloud companies deploy our apps across continents.

Having multiple server nodes on the backend also helps the website stay online even if a few server nodes crash. This is known as high availability. We’ll get to that in the upcoming lessons.

### Which Scalability Approach is Right for our App?

#### Pros and cons of vertical and horizontal scaling

Vertical scaling, as we learned before, is simpler in comparison to horizontal scaling because we do not have to touch the code or make any complex system configurations. It takes much less administrative, monitoring, and management efforts than managing a distributed environment when scaling horizontally.

A significant downside of vertical scaling is the availability risk. The servers are powerful but few in number. There is always a risk of them going down and the entire website going offline, which doesn’t happen when the system is scaled horizontally. In this scenario, the system is more highly available.

#### What about the code? Why does the code need to change when it has to run on multiple machines?

If you intend to run the code in a distributed environment, it needs to be stateless. There should be no state in the code. What do I mean by this?

There should be no static instances in the class. Static instances hold application data and when a particular server goes down, all the static data/state is lost. The app is left in an inconsistent state.

In object-oriented programming, the instance variables hold object state in them. Static variables moreover hold state that spans across multiple objects. They generally hold state per classloader. Now, if the server instance running that classloader goes down, all the data is lost.

Also, whatever data static variables hold, it’s not application-wide. For this reason, distributed memory like Redis, Memcache, etc., are used to maintain a consistent state application-wide. When writing applications for distributed systems, it’s a good practice to avoid using static instances in the class. The state is typically persisted in a distributed memory store; this facilitates components to be stateless.

This is why functional programming got popular with distributed systems. The functions don’t retain any state. However, the same behavior can also be achieved with prominent OOP languages.

#### Which scalability approach is right for our app?

Always have a ballpark estimate in mind when designing your app. How much traffic will it have to deal with?

Today, development teams are adopting a distributed microservices architecture right from the start, and workloads (applications) are meant to be deployed on the cloud. So, inherently the workloads are horizontally scaled out on the fly

![image](https://user-images.githubusercontent.com/25869911/155897396-50083607-dc82-4f70-97ea-cd7558a13421.png)


The upsides of horizontal scaling include no limit to augmenting the hardware capacity. Data is replicated across different geographical regions as nodes and data centers are set up across the globe.

If your app is a utility or tool expected to receive minimal predictable traffic. For instance, an internal tool of an organization or something similar that is not mission-critical.

Why bother hosting it in a distributed environment? A single server is enough to manage the traffic, so go ahead with vertical scaling when we know that the traffic load will not spike in the future.

If your app is a public-facing social app like a social network, a fitness app, an online game, or something similar, where the traffic is unpredictable. Both high availability and horizontal scalability are important to you.

Build these apps to deploy them on the cloud, and always have horizontal scalability in mind right from the start.

### Primary Bottlenecks That Hurt the Scalability of our Application

There are several points in a web application that can become a bottleneck and hurt the scalability of our application. Let’s take a look at them.

#### Database

Imagine we have an application that appears to be well architected. Everything looks good. The workload runs on multiple nodes, and it can scale horizontally.

However, the database is a poor single monolith, where just one server has the onus of handling the data requests from all the server nodes of the workload.

This scenario is a bottleneck. The server nodes work well, handle millions of requests at a point in time efficiently, yet, the response time of these requests and the latency of the application are abysmal due to the presence of a single database. There is only so much it can handle.

Just like workload scalability, the database needs to be scaled well.

Make wise use of database partitioning, sharding with multiple database servers to make your system efficient.

#### Application design

A poorly designed application’s architecture can become a major bottleneck as a whole.

A typical architectural mistake is not using asynchronous processes and modules wherever required; rather, all the processes are scheduled sequentially.

For example, if a user uploads a document on the portal, tasks such as sending a confirmation email to the user, sending a notification to all subscribers/listeners to the upload event should be done asynchronously.

Tasks like these should be forwarded to a messaging server or a task queue for asynchronous processing as opposed to being processed sequentially, making the user wait.

#### Not using caching in the application wisely

Caching can be deployed at several layers of the application. It speeds up the response time by notches. A cache cuts down the overall load on the app, intercepting all the requests before they hit the origin servers.

We should use caching exhaustively throughout the application to speed up things significantly.

If the system has a lot of static data, caching can bring down the deployment costs significantly. I’ve written an article on my blog: How PolyHaven manages 5 million page views and 80TB traffic a month for less than 400 USD.

Polyhaven is a 3D asset library with a large amount of static data. The article delineates how it leverages caching to bring down it’s deployment costs.

https://www.scaleyourapp.com/application-hosting-how-polyhaven-manages-5-million-page-views-and-80tb-traffic-a-month-for-400/

#### Inefficient configuration and setup of load balancers

Load balancers are the gateway to our application. Using too many or too few of them impacts the latency of our application.

#### Adding business logic to the database

No matter what justification anyone provides, I’ve never been a fan of adding business logic to the database.

The database is just not the place to put business logic. Business logic in the database makes the application components tightly coupled. Imagine how much code refactoring this would require when migrating to a different database. Also, the testing gets complex.

#### Not picking the right database

Picking the right database technology is vital for businesses. Need transactions and strong consistency? Pick a relational database. If you can do without strong consistency rather than need horizontal scalability, pick a NoSQL database.

Trying to pull things off with a not-so-suitable tech always has a profound impact on the latency of the entire application in negative ways.

#### At the code level

This shouldn’t come as a surprise, but inefficient and poorly written code has the potential to bring down the entire service in production. This typically includes:

* Using unnecessary loops or nested loops
* Writing tightly coupled code
* Not paying attention to the Big-O complexity while writing the code. (be ready to do a lot of firefighting in production)

Ideally, we should always do a DENTTAL (Documentation, Exception Handling, Null pointers, Time complexity, Test coverage, Analysis of code complexity, Logging) check of our code when doing a dry run.

In this lesson, don’t worry if a few things are not clear to you, such as strong consistency, how the message queue facilitates asynchronous behavior, or how to pick the right database

### How to Improve and Test the Scalability of our Application?

Here are some of the standard strategies to fine-tune the performance of our web application. If the application is performance-optimized, it can withstand more traffic load with less resource consumption than an application that is not optimized for performance.

Now you might be wondering, “Why are you talking about performance when you should be talking about scalability? Isn’t it what the lesson title says?”

Well, the application’s performance is directly proportional to scalability. If an application is not performant, it will certainly not scale well.

These performance optimization strategies can be implemented even before the pre-production testing stage of the application.

#### Tuning the performance of the application – Enabling it to scale better

##### Profiling

Profile the hell out of your app. Run application profiler and code profiler. See what processes are taking too long and are eating up too many resources. Find out the bottlenecks. Get rid of them.

Profiling is the dynamic analysis of our code. It helps us measure the space and the time complexity of our code and enables us to figure out issues like concurrency errors, memory errors and robustness and safety of the program. This Wikipedia resource contains a good list of performance analysis tools used in the industry.

https://en.wikipedia.org/wiki/List_of_performance_analysis_tools

##### Caching

Cache wisely, and cache everywhere. Cache all the static content. Hit the database only when it is really required. Try to serve all the read requests from the cache. Use a write-through cache.

##### CDN

Use a Content Delivery Network (CDN). Using a CDN further reduces the application’s latency due to the proximity of the data from the requesting user.

##### Data compression

Compress data. Use apt compression algorithms to compress data and store data in compressed form. Since compressed data consumes less bandwidth, the data download on the client will be faster.

##### Avoid unnecessary requests response cycles

Avoid unnecessary round trips between the client and server. Try to club multiple requests into one.

These are a few of the things we should bear in mind in the context of application performance.

##### Testing the scalability of our application

Once we are done with the essential performance testing of the application, it is time for capacity planning, provisioning the right amount of hardware—compute and storage power.

The right approach for testing the application for scalability largely depends on the design of our system. There is no standard formula for this.

Testing can be performed at both the hardware and the software level. Different services and components need to be tested—individually and collectively.

During the scalability testing, different system parameters are taken into account, such as:

* CPU usage
* Network bandwidth consumption
* Throughput
*  Number of requests processed within a stipulated time
* Latency
* Memory usage of the program
* End-user experience when the system is under heavy load and so on.

In this testing phase, simulated traffic is routed to the system to study how the system behaves and scales under the heavy load. Contingencies are planned for unforeseen situations.

As per the anticipated traffic, the appropriate hardware and computational power are provisioned to handle the traffic smoothly with some buffer.

Several load and stress tests are run on the application. Tools like JMeter are pretty popular for running concurrent user tests on the application; if you are on the Java ecosystem. There are a lot of cloud-based testing tools available that help us simulate test scenarios just with a few mouse clicks.

Businesses test for scalability all the time to get their systems ready to handle a traffic surge. If it’s a sports website, it prepares itself for the sports event day. If it’s an e-commerce website, it makes itself ready for festival season sale.

Here are a couple of good reads on the topic:

https://engineering.fb.com/2018/02/12/production-engineering/how-production-engineers-support-global-events-on-facebook/

https://www.scaleyourapp.com/how-hotstar-scaled-with-10-3-million-concurrent-users-an-architectural-insight/

In the industry, tech like Cadvisor, Prometheus and Grafana are pretty popular for tracking the system profile via web-based dashboards.

![image](https://user-images.githubusercontent.com/25869911/155898161-196e4a0e-94bb-4259-8362-5f7216b0ede3.png)

https://www.scaleyourapp.com/what-is-grafana-why-use-it-everything-you-should-know-about-it/

### What is High Availability?

Highly available computing infrastructure is the norm in the computing industry today. When it comes to cloud platforms, it is their key feature that enables the workloads running on them to be highly available.

This lesson is an insight into high availability. It covers all the frequently asked questions about it, including:

* What is it?
* Why is it so important to businesses?
* What is a highly available cluster?
* How do cloud platforms ensure the high availability of the services running on them?
* What are fault tolerance and redundancy? How are they related to high availability?

High availability, also known as HA, is the ability of the system to stay online despite having failures at the infrastructural level in real-time.

High availability ensures the service’s uptime is much more than usual. It improves the reliability of the system and ensures minimum downtime.

Reliability is defined as the probability that a product, system, or service will perform its intended function adequately for a specified period of time, or will operate in a defined environment without failure.

The sole mission of highly available systems is to stay online and stay connected. A rudimentary real-world example of staying highly available is having backup generators to ensure continuous power supply in case of any power outages in hospitals, air traffic control towers and so on.

In the industry, HA is often expressed as a percentage. For instance, when the system is 99.99999% highly available, it simply means 99.99999% of the total hosting time the service will be up. You might often see this in the Service Level Agreements (SLA) of cloud platforms.

#### How important is high availability to online services?

Social applications going down for a bit and then bouncing back might not impact businesses that much. However, there are mission-critical systems like aircraft systems, spacecrafts, mining machines, hospital servers, and finance stock-market systems that cannot afford to go down at any time. After all, lives depend on it.

The smooth functioning of the mission-critical systems relies on continual connectivity with their network/servers. These are the instances that do not work without super highly available infrastructures.

Besides, no service likes to go down, critical or not. To meet the high availability requirements, systems are designed to be fault-tolerant and their components are made redundant.

What are fault-tolerant and redundancy in distributed systems?

Fault Tolerance simply means a system's ability to continue operating uninterrupted despite the failure of one or more of its components. This is true whether it is a computer system, a cloud cluster, a network, or something else.


### Reasons For System Failures

common reasons why systems fail.

#### Software crashes

I am sure you are pretty familiar with software crashes. Applications crash all the time, be it on a mobile phone or a desktop.

We also have to deal with corrupt software files. Remember the BSOD blue screen of death in Windows? OS crashing, memory-hogging unresponsive processes. Likewise, software running on cloud nodes crashes unpredictably and takes down the entire node.

#### Hardware failures

Another reason for system failure is hardware crashes, including overloaded CPU and RAM, hard disk failures, nodes going down, and network outages.

#### Human errors

This is the biggest reason for system failures. It includes flawed configurations and whatnot. Google made a tiny network configuration error, and it took down almost half of the internet in Japan

https://thenextweb.com/news/google-japan-internet-blackout

#### Planned downtime

Besides the unplanned crashes, there are planned downtimes that involve routine maintenance operations, patching software, hardware upgrades, etc.

These are the primary reasons for system failures. Now, let’s talk about how HA systems are designed to overcome these system downtime scenarios.

### Achieving High Availability - Fault Tolerance

There are several approaches to achieve HA. The most important of them is to make the system fault-tolerant.

#### What is fault tolerance?

Fault tolerance is a system’s ability to stay up despite taking hits.

A fault-tolerant system is equipped to handle faults. Being fault-tolerant is an essential element in designing life-critical systems.

In a fault-tolerant system, out of several instances/nodes running a service, a few go offline and bounce back all the time. In case of these internal failures, the system can work at a reduced level without going down entirely.

An elementary example of a system like this is social networking platforms. In the case of backend node failures, a few services of the app, such as image upload, post likes, etc., may stop working. However, the application as a whole will still be up. This approach technically is also known as fail soft.

#### A highly available fault-tolerant service – Architecture

A fault-tolerant system can be designed at the application and the deployment level. Since apps are typically deployed on the cloud in the modern web landscape, I discuss the deployment infrastructure in detail in my cloud computing course.

So, to achieve high availability at the application level, the entire massive service is architecturally broken down into more granular loosely coupled services called microservices.

![image](https://user-images.githubusercontent.com/25869911/155898838-6afcd9e7-1fd8-411e-93b9-9abe589913c2.png)


There are many upsides of splitting a big monolith into several microservices:

* Easy management and maintenance
* Ease of development
* Ease of adding new features to a service without affecting other services
* Scalability and high availability of the system

Every microservice takes the onus of running different features of an application such as photo upload, comment system, instant messaging, groups, marketplace, etc. In this case, even if a few services go down, the other services of the application are still up.

### Redundancy

#### Redundancy – Active-passive HA mode

Redundancy is duplicating the server instances and keeping them on standby to take over in case any of the active server instances go down. It is the fail-safe backup mechanism in the deployment infrastructure.

![image](https://user-images.githubusercontent.com/25869911/155899006-b51e035b-4c25-4569-b7cd-aaf76d02cf58.png)

The illustration above shows the redundant instances. One of the redundant instances takes over when the active instance goes offline.

This instance setup approach is also known as the Active-passive HA mode. An initial set of nodes are active, and a set of redundant nodes are passive, on standby. Active nodes get replaced by passive nodes in case of failures.

There are systems like GPS, aircraft, communication satellites, etc., that have zero downtime. The availability of these systems is ensured by making the components redundant.

#### Getting rid of single points of failure

Distributed systems became mainstream with large-scale applications solely because, in them, we can eliminate the single points of failure that were a big downside of a monolithic architecture. I discussed this in the previous lesson how microservices facilitate a fault-tolerant architecture.

In a highly available system, a large number of distributed server nodes work in conjunction with each other to achieve a single synchronous application state.

When so many redundant nodes are deployed, there are no single points of failure in the system. In case a node goes down, redundant nodes take its place. The system as a whole remains unimpacted.

Single points of failure at the application component level mean bottlenecks. I discussed this earlier, having just one database instance handling requests from a number of application nodes. We should detect bottlenecks in performance testing and get rid of them as soon as possible.

#### Monitoring and automation

Systems should be well monitored in real-time to detect any bottlenecks or single point of failures. Automation enables the instances to self-recover without any human intervention. It gives the instances the power of self-healing.

Also, the systems become intelligent enough to add or remove instances on the fly as per the requirements. Kubernetes is one good example of this.

Since the most common cause of failures is human error, automation helps cut down failures considerably.

### Replication

Replication – Active-active HA mode

Replication means having a number of similar nodes running the workload together. There are no standby or passive instances. When a single or a few nodes go down, the remaining nodes bear the load of the service.

![image](https://user-images.githubusercontent.com/25869911/155899180-e2cddd5d-0ed7-4e63-a2e6-872aec09c7cd.png)

This approach is also known as the Active-active high availability mode. In this approach, all the server instances are active at any point in time.

#### Geographical distribution of workload#

As a contingency for natural disasters, regional power outages, and other big-scale failures, data center workloads are spread across different data centers across the world in different geographical locations.

This eliminates a single point of failure in the context of data center zones. If a natural disaster wipes out a few data centers in a certain zone, other data centers in different geographical zones are still powering the application. Also, the latency is reduced significantly due to the proximity of data to the user due to the global replication of data centers.

All highly-available fault-tolerant design decisions are subjective to how critical the system is? The odds of components failing and so on.

Businesses often use multi-cloud platforms to deploy their workloads which ensures further availability. If things go south with one cloud provider, they have another to fail back over.

