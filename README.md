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


