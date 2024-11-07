---
layout: post
title: What is an API? 🤷‍♂️
subtitle: How does two networks connect with a medium?
excerpt_image: 
categories: MISC
tags: [MISC]
---

## Motivation
"An API that isn't comprehensible isn't usable - James Gosling"

### table of contents
1. API ???
2. How does it work?
    - Illustrator
    - Comparision and understanding
3. Types of API.
4. Conclusion

<i><b>Note</b> : This blog represents my way of understanding of API</i>

## 1. API ???

What is an API? It is an acronym for Application Programming Interface. API is a medium for communication between client and server. The communication will be happen based upon set of definitions and protocols.
In API appilication refers to the software and Interface is refferred to the contract of service between two softwares 'definition from AWS'. 

## 2. How does it work?

Illustrator: 

<img src="https://tinyurl.com/kcxv5uye" height="300px" width="300px">

Let's think of an example you went to a movie theatre or a multiplex to book a ticket for a movie.
1. You will go to the ticket counter and ask the clerk to book a ticket for 'God Father'at 'top row'.
2. The clerk will check in the booking portol the if the movie you requested is available or not if available they will check the seats are available or not. 
3. if seats are available they will book a seat.
4. After successful completion of booking you will recieve ticket from them if not an appology.

Comparision and understanding:

there are three majaor components in the above example:
- You = client
- Booking portal = server
- Clerk = API

1. Client will request the API for information/data with URI (universal resource indicator = movie name).
2. The API will check the URI is proper or not .
3. If it's proper then it will communicate with the server and put the request you made.
4. After making the request API will bring the response from the server. 

There are several response codes present in the protocols indicating what happened. Each response code represents the info from the server which will be carried by API.
RESPONSE CODES:
      200-299 :- successful requests
      300-399 :- Redirections
      400-499 :- Client side errors (usually triggers when requests are not proper)
      404 :- Not Found
      403 :- Forbidden
      500-599 :- Server side errors

## Types of API

There are many types of APIs like SOAP, REST, WebAPI, RPC , GraphQL, etc... And these API are categorised into 4 categories.
- Private API: These APIs is restricted to only particular orgnizations/people.
- Public API: These APIs are accessble to everyone just like opensource available for public.
- Partner API: These APIs are accesible for external developers who are authorized.
- Composite API: This is the combination of any two APIs.

Coming two architecture level SOAP and REST are two API architectures majorly followed in most of the organizations.

## Conclusion

An **API (Application Programming Interface)** is a set of rules that allows software applications to communicate. It's like a clerk at a movie ticket counter: you (the client) ask the clerk (the API) to book a ticket, and the clerk communicates your request to the booking system (the server). 

APIs use response codes (like 200 for success, 404 for 'Not Found') to indicate the server's response. They come in different types (like SOAP, REST) and can be private, public, partner-specific, or a combination of APIs. They are crucial for enabling different software systems to interact seamlessly.

## In Next
In the next blog we will be learning `REST API`.
<div style="align:center;">
    <img src="https://tinyurl.com/2smskpkt" width="150px" height="150px" alt="">
</div>
