
# System Design Concepts

System Design was HARD until I Learned these 30 Concepts

## Table of Contents
![table_of_content](https://github.com/nthai-dev/System-Design-Concepts/blob/main/images/table_of_contents_image.png?raw=true)


## 🖥️ Client-Server Architecture
Client-Server Architecture is a foundational concept in system design where two main entities interact:
### 🧩 Components:
#### 1. Client:
- Initiates requests
- Examples: Chrome browser, Postman, mobile app
#### 2. Server:
- Waits for client requests, processes them, and sends back responses
- Can be one machine or a cluster of machines behind load balancers

### ⚙️ How it works (Basic Flow):
![client-server]()
1. Client sends a request (e.g., fetch user profile)
2. Server processes the request (e.g., query DB, apply logic)
3. Server sends a response (e.g., JSON with user details)
   
> This sounds simple, but there’s a big question: 
> How does the client even know where to find the server?

## 🌐 IP Address
On the internet, computers identify each other using IP addresses, which work a lot like phone numbers—unique identifiers that let them connect and communicate.

### 🧾 What is an IP Address?
An IP address is a numerical label (like 192.168.1.1 or 2001:0db8:85a3::8a2e:0370:7334) assigned to each device connected to a network.
It can be:
- IPv4: e.g., 172.217.3.110 (most common, but limited)
- IPv6: e.g., 2606:4700:4700::1111 (newer, much larger address space)

![ip-address]()

> 📌 Every publicly deployed server has a unique IP address. When a client wants to talk to a server—whether it’s an API, a website, or a game server—it must send requests to the correct IP address.

### ⚠️ The Problem:
But here’s the catch:
- We can’t expect users (or systems) to memorize a random string of numbers for every service.
- If we move our service to a different server (say, during scaling or disaster recovery), the IP address might change.
> 🧪 The Solution: DNS
## 3. DNS
Instead of using hard-to-remember IP addresses, we use something much more human-friendly: domain names.
But how does a domain name lead us to the right server?
That’s where DNS (Domain Name System) comes in.

DNS works like the Internet’s phonebook. It maps easy-to-remember domain names (like google.com) to their actual IP addresses, allowing browsers to load the correct websites.

![dns]()

## 4. Proxy/ Reverse Proxy
When a client (like your browser) wants to connect to a server, it can go directly or it can use a proxy in between.

### Forward-Proxy
![forward-proxy]()
A proxy server acts as an intermediary between a client (like your computer) and the Internet.
When you use a proxy:
- Your requests go to the proxy first -> The proxy forwards your request to the destination -> The response comes back through the proxy -> The proxy then sends it to you
#### Why Use a Reverse Proxy?
1. Privacy & Anonymity(hides client identities)
2. Access Control (organizations can block access to specific websites)
3. Bypass Geographical Restrictions (access content blocked in your country/region)
4. Improved Security
5. Bandwidth Savings & Caching
6. Logging & Monitoring
  
### Reverse Proxy
![reverse-proxy]()
A reverse proxy sits in front of web servers and acts as a gateway between clients and servers:

#### Key Characteristics of Reverse Proxies:
- Server-side technology (set up by service providers)
- Hides server identities from clients
- Provides load balancing, SSL termination, caching, and security
- Common uses: high-traffic websites, CDNs, microservices architectures

#### Why Use a Reverse Proxy?
- Load Balancing: Distributes traffic across multiple servers
- SSL Termination: Handles encryption/decryption to reduce server load
- Caching: Stores static content to improve performance
- Security: Protects against DDoS attacks and hides server vulnerabilities
- Compression: Reduces bandwidth by compressing responses
- Unified Access: Provides a single entry point for multiple backend services  

### Main Differences

|Feature	| Forward Proxy	| Reverse Proxy|
---|---|---
Position|	Close to clients|	Close to servers
Hides|	Client identities|	Server infrastructure
Typical User|	End users/organizations|	Website administrators
Primary Uses |	Privacy, access control|	Load balancing, security
