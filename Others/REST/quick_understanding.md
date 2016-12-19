# 快速理解 REST

> 原文链接：[A quick understanding of rest]()

## 什么是 REST

- REST 是 REpresentational State Transfer  的缩写，翻译过来就是「表述性状态转移」。
- REST 是一种建立在多种约束之上的架构风格，比较核心的一个关键词是「资源」(Resource)。

在 REST 的论文中，Roy Thomas Fielding 博士有一个从「空风格」推导的过程 -- 在架构中逐渐添加约束，包含了以下：

- 客户-服务端，也就是常说的 Client-Server，即 CS 架构；
- 无状态，每个请求包含了理解该请求的所有信息，会话状态（Session）完全保存在客户端；
- 缓存，请求的返回数据需要隐式或显式的标记为是否可以缓存；
- 统一接口，这是 REST 的核心特征；

### 参考与相关阅读

- Architectural Styles and the Design of Network-based Softwares Architecture, Roy Thomas Fielding, http://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm
- Representational State Transfer, Wikipedia, https://en.wikipedia.org/wiki/Representational_state_transfer
- A Quick Understanding of REST, Brian Mosigisi, https://scotch.io/bar-talk/a-quick-understanding-of-rest

## 什么是 REST

When you hear phrases like "that API is not RESTful" being thrown around, if you are like me, you end up questioning:

- What really is REST, anyway?
- How does something end up being RESTful?

So you do some research and this is the gist of what you end up with:

REST refers to Representational State Transfer. It is an architectural style for designing distributed systems using a set of constraints. The central abstraction in REST is a resource. The set of constraints defined by REST include:

- A client-server model.
- Stateless interaction.
- Uniform interface.

The Internet strikes again! You still have no idea what this means. All you want to do is make your API RESTful. I've been there. In order to understand what this means, let us first remind ourselves of the basic concepts of the world wide web.

## Client-Server

What happens when you type https://scotch.io in the address bar of your browser?

The short answer is your browser (acting as a client), using HTTP, sends out a GET request to some server (in this case Scotch servers residing on Digital Ocean). The Scotch servers respond and your browser receives the response, which is in turn rendered into what you see.

In the client-server model, servers are the providers of a service or resource, with clients acting as the requesters of the resources. Clients can come in a wide variety of forms: as android applications, a browser running on a PC or an ATM machine.

The advantage of having the client-server style as a constraint is that it supports separation of concerns. As long as you have a separate machine (a server) providing the data, the clients can take any form, and may change independently.

## 无状态交互

In RESTful design, the server should not store any communication state. Sessions should be stored entirely by the client. This means that if the server receives two separate requests from the same client, it should not remember anything about the first request, by the time the second one comes through. Due to this, every request coming from the client should carry all the information necessary for an action to be performed by the server.

The rationale for this is that as the number of clients grows, the server will not have to keep track of all the clients it is talking to which would take a lot of time and space. This ensures that our overall system scales well.

This constraint basically says that your RESTful API should not have a login and logout function, which would involve the use of sessions, and isn't allowed. In order to authenticate and authorize clients, the server will look for authentication information within each request. Hence the client is in charge of storing authentication credentials, and sending them in each subsequent request. One such example is the use of JSON web tokens for authentication, and more information on this can be found here.

## 什么是资源？

A resource is a representation of either a virtual object such as an image, a real life thing such as a customer or a collection of objects such as a crowd. In essence, a resource can be anything. It is up to the API designer to decide which parts of his system should be mapped to resources.

Let's say you were providing a RESTful web API for a system running a chain of music stores which only sell banjos. Possible candidates for resources include banjos, stores, customers, employees, sales, users, visits and so on. The entities in the store (people and objects) and events (such as tour bookings) can all be mapped to resources.

In REST, every single resource should be unique. As such, it is only logical to assign IDs to our resources. For our chain of music stores, /store/1 and /store/2 would be two unique resources, with IDs 1 and 2. In practice, resources may also be nested. For instance, there may be an employee 2 in store 1, whose URI is /store/1/employee/2.

## 一致性接口

The GET we mentioned is not the only HTTP verb. The common ones are POST, PUT, PATCH and DELETE. A major part of having a uniform interface in our RESTful APIs is using HTTP to provide CRUD (create, read, update and delete) actions for our resources. This table illustrates how a certain operation would intuitively map to an SQL operation and a HTTP verb.

As such, these HTTP verbs would be used as follows:

In order to retrieve store 1, you would send a GET request to /store/1
To create a new store, you would send a POST request to /store
To replace store 1 with an entirely new store, you PUT to /store/1
To partially modify store 1, you would PATCH to /store/1
To delete store 1, you would send a DELETE request to /store/1

## 最后，一点备忘

In the beginning, the wonderful world of theoretical computer science, degrees and specialization brought us a guy called Roy Fielding whose work has helped in shaping the world wide web as we know it. He is known for contributing to the HTTP protocol, Apache Web Server, REST, among others. His intention, in his REST dissertation wasn't for REST to be interpreted as a web service, tied directly to HTTP.

However, HTTP is a RESTful protocol and it has ended up being used for almost all REST implementations. This article is about REST as you would use it to build a Web API over HTTP, as there is more than a high chance this is the context in which you shall be using REST.

## 接下来？

Now that we understand what REST is, we can go out and build an actual RESTful API, to get these concepts infused.

A fantastic place to start is building a RESTful API in Node.js and express.

Also, check out REST best practices which builds upon these concepts.
