
# System Design Concepts

System Design was HARD until I Learned these 30 Concepts

## Table of Contents

| [1. Client-Server Architecture]() | [11. SQL vs NoSQL]()         | [21. CAP Theorem]()    |
|----------------------------------|-------------------------------|-------------------------|
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
> This sounds simple, but there’s a big question: 
> How does the client even know where to find the server?

TL;DR:
> The client finds the server via DNS, config, or service discovery, and connects using an IP/port.



