---
title: "What Happens After Entering an URL on Your Browser?"
date: "2022-09-25"
summary: "An overview of the client-server model, DNS, HTTP, and HTTPS protocols with details about how your browser processes web requests."
description: "This post explains the behind-the-scenes process that occurs when a user enters a website URL, including the role of the client-server model, DNS, HTTP, HTTPS, and how data is securely transmitted."
toc: true
readTime: true
autonumber: true
math: false
tags: ["networking", "tech", "basics"]
showTags: true
hideBackToTop: false
---

# What Happens After Entering `www.google.com` on Your Browser?

Have you ever thought about what happens behind the scenes after you enter `www.google.com` in your browser? How does the browser know you're requesting Google's homepage, and where is google.com located on the internet? To answer these questions, you need to understand how web technology works behind the scenes.

## The Client-Server Model

![Client-Server Model](https://miro.medium.com/v2/resize:fit:720/0*kZuLJa3OA0BqtEjv)

There are two primary entities involved: **CLIENT** and **SERVER**.

- **CLIENT**: This refers to your browser, from where you request a website/resource.
- **SERVER**: This is the computer where the requested website/resource is hosted.

Whenever a client sends a request, either to get data from the server or to post data on the server, the server responds to the request by providing or posting the data with a success or error message.

A connection is established between these two parties to share data. Now, let's explore how your browser knows the address of the server.

## Domain Name System (DNS)

To understand DNS, think of your phone's contact list. You save a contact by a name, which is mapped to a phone number. The name is easier to remember than the number.

DNS works similarly. The domain name of any website is mapped to the server's IP address to find where the server is located. DNS acts as a translator, converting domain names into IP addresses so that browsers can load internet resources.

Learn more about DNS in this video by IBM: [Watch Video](https://www.youtube.com/watch?v=nyH0nYhMW9M&t=1s).

Once the browser retrieves the server's IP address, communication between the client and server begins to retrieve the desired resources.

## HTTP (HyperText Transfer Protocol)

The Hypertext Transfer Protocol is a network protocol that is based on TCP/IP for the communication between client and server. The Basic flow is client sends the request to the server to get the resource and then the server gives the response back to the client. The transfer of data takes place in the form of small segments which are called **packets**.

![TCP Packet](https://miro.medium.com/max/720/0*oXe5go_NVSj441Gd.jpeg)

### HTTP Headers

Whenever you request something from the server or the server is responding to you back, HTTP headers are involved in both cases. HTTP Headers are nothing but the metadata for requests and responses. It carries the information about the request and response. HTTP Headers are of mainly two types:

- **Request Headers**: Carry information about the client’s request.
  ![HTTP Request Headers](https://miro.medium.com/proxy/0*DU0ACcNb9CN35_uW.png)
- **Response Headers**: Carry information about the server’s response.
  ![HTTP Response Headers](https://miro.medium.com/max/640/1*RK8k7_CLo6TqoPYczMvk4w.png)

### HTTP Request Methods

Look at the first line of the above example of a request header, a method is GET defined which means that you are requesting something from the server.

There are mainly four types of HTTP methods:

- **GET**: To retrieve data from the server.
- **POST**: To send data to the server.
- **PUT**: To update data on the server.
- **DELETE**: To delete data from the server.\

There are other methods also but we generally use the above four. You can see the complete list <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods" target="_blank">here</a>

### HTTP Status Codes

HTTP status code shows if the request is fulfilled by the server or not. If it is fulfilled, the server responds with a success status code otherwise it responds with a specific error code.

All the status codes are clubbed together in 5 different subgroups:

1. **Informational**: (100–199)
2. **Successful**: (200–299)
3. **Redirection**: (300–399)
4. **Client Error**: (400–499)
5. **Server Error**: (500–599)

### HTTP Request and Response Body

- **Request Body**: Used to send data from the client to the server, such as submitting a form.
- **Response Body**: Used to receive data from the server.

## HTTPS (HyperText Transfer Protocol Secure)

The main issue of using HTTP is security. Data packets are not encrypted while transmitting and therefore attackers can quickly get access to your data by stealing data packets with a MITM attack. HTTPS is used instead of HTTP to avoid these things.

### What is HTTPS?

![HTTPS Protocol](https://miro.medium.com/max/720/1*ItKgwGP5_8wB6_IAtPQ0iA.png)

**HTTPS** (HyperText Transfer Protocol Secure) is a protocol built over HTTP with security enhancements. Cryptographic principles are introduced in HTTPS so that you can freely transmit data packets without any security issues. The protocol which is used by HTTPS is TLS ( Transport Layer Security ).

To understand what is TLS and how TLS handshake works, we need to know about public-private key encryption.

### Public-Private Key Encryption

Public keys are used to encrypt sensitive data and anyone can use this to encrypt data but Private keys are for the decryption of encrypted data only receivers has access to this only receiver can decrypt the data. So when you visit `https://www.google.com`, google sends you their public key which is signed by a verified certificate authority ( in this case, google itself ), and then your browser encrypts the data packets with google's public key so that only google can decrypt data packets.

So, in short:

- **Public Key**: Used to encrypt sensitive data, and anyone can use it.
- **Private Key**: Used for decryption, and only the intended receiver has access to it.

When you visit `https://www.google.com`, Google sends its public key, which is signed by a verified certificate authority (in this case, Google itself). Your browser encrypts data packets using Google’s public key, ensuring only Google can decrypt them.

### SSL/TLS Certificate

If you see the green lock icon in your browser, it means the connection is secured with HTTPS, ensuring that data is transmitted securely.

![SSL Certificate Example](https://miro.medium.com/max/640/1*WnXhJljZ8QHOTkNkXht3Bw.png)

### Assembling Web Content

After securing the connection and receiving the data packets, your browser assembles an HTML document along with CSS and JavaScript files to render the website's main content.

---
