
# System Design Concepts

System Design was HARD until I Learned these 30 Concepts

## Table of Contents

| [1. Client-Server Architecture]() | [11. SQL vs NoSQL]()         | [21. CAP Theorem]()    |
|:----------------------------------|:-------------------------------|:-------------------------|
| [2. IP Address]()                | [12. Vertical Scaling]()      | [22. Blob Storage]()    |
| [3. DNS]()                       | [13. Horizontal Scaling]()    | [23. CDN]()             |
| [4. Proxy / Reverse Proxy]()     | [14. Load Balancers]()        | [24. WebSockets]()      |
| [5. Latency]()                   | [15. Database Indexing]()     | [25. Webhooks]()        |
| [6. HTTP/HTTPS]()                | [16. Replication]()           | [26. Microservices]()   |
| [7. APIs]()                      | [17. Sharding]()              | [27. Message Queues]()  |
| [8. Rest API]()                  | [18. Vertical Partitioning]() | [28. Rate Limiting]()   |
| [9. GraphQL]()                   | [19. Caching]()               | [29. API Gateways]()    |
| [10. Databases]()                | [20. Denormalization]()       | [30. Idempotency]()     |


## Client-Server Architecture
Almost every web application that you use is built on this simple yet powerful concept called client-server architecture.

![client-server]()

- The client requests to store, retrieve, or modify data.
- The server receives the request, processes it, performs the necessary operations, and sends back a response.
This sounds simple, but there’s a big question: 
How does the client even know where to find the server?

TL;DR:
> The client finds the server via DNS, config, or service discovery, and connects using an IP/port.


## IP Address
On the internet, computers identify each other using IP addresses, which work like phone numbers.

![ip-address]()

Every publicly deployed server has a unique IP address. When a client wants to interact with a service, it must send requests to the correct IP address.

But there’s a problem:
- When we visit a website, we don’t type its IP address—we just enter the website name.
- We can’t expect users (or even systems) to memorize a string of random numbers for every service they connect to.
- If we migrate our service to another server, its IP address may change, breaking all direct connections.

## 3. DNS
Instead of relying on hard-to-remember IP addresses, we use something much more human-friendly: domain names.

But we need a way to map a domain name to its corresponding IP address.

This is where DNS (or Domain Name System) comes in. It maps easy-to-remember domain names (like google.com) to their corresponding IP addresses.

![dns]()

## 4. Proxy/ Reverse Proxy
When you visit a website, your request doesn’t always go directly to the server—sometimes, it passes through a proxy or reverse proxy first.

A proxy server acts as a middleman between your device and the internet.

### Forward-Proxy
![forward-proxy]()
When you request a webpage, the proxy forwards your request to the target server, retrieves the response, and sends it back to you.
A proxy hides your IP address, keeping your location and identity private.
### Reverse Proxy
![reverse-proxy]()
A Reverse Proxy intercepts client requests and forwards them to backend servers based on predefined rules.
A reverse proxy mitigates these risks by acting as a controlled entry point that regulates incoming traffic and hides server IPs.

It can also act as a load balancer, distributing traffic across multiple servers.

