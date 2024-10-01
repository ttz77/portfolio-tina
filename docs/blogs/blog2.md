---
title: Blog 2
layout: doc
---

# The DNS

In today's lecture we went over how HTTP requests worked. I thought it would be interesting to dive a bit deeper in how the DNS functions. 

### So what is the DNS?

The Domain Name System (DNS) is often compared to the internet’s phonebook. While we use domain names like www.docs.google.com to access websites, the internet relies on IP addresses to route information. The DNS acts as the translator, converting these domain names into machine-readable IP addresses.

### Types of DNS Services: 
There are two primary types of DNS services: Authoritative DNS and Recursive DNS.

#### Authoritative DNS:

An authoritative DNS service is responsible for managing and updating DNS records for a specific domain. It holds the definitive information about a domain’s IP addresses and other related records. When a DNS query reaches an authoritative DNS server, it provides the accurate IP address associated with the requested domain name.

Key Functions:

Update Mechanism: Developers use authoritative DNS services to manage their public DNS names, ensuring that any changes to IP addresses or other DNS records are accurately reflected.

Final Authority: Authoritative DNS servers have the ultimate authority over their respective domains, providing reliable responses to DNS queries.
For example, if example.com uses an authoritative DNS service, that service maintains the records that map www.example.com to its IP address.

#### Recursive DNS
Most users do not interact directly with authoritative DNS services. Instead, their DNS queries are handled by recursive DNS services, often referred to as resolvers. Think of a recursive DNS service as a knowledgeable intermediary that fetches DNS information on your behalf.

Key Functions:

Caching: Recursive DNS services store DNS query results temporarily. If a requested domain’s IP address is already cached, the resolver can provide the information immediately, speeding up the resolution process.

Query Handling: If the resolver does not have the necessary information cached, it forwards the query to authoritative DNS servers to obtain the required IP address.
In essence, recursive DNS services streamline the DNS resolution process by reducing the need for repeated queries to authoritative servers, thereby enhancing efficiency and reducing latency.

### How Does DNS Route Traffic to Your Web Application?
User Initiates a Request:
A user opens their web browser, types www.docs.google.com into the address bar, and presses Enter.

DNS Resolver Query:
The browser sends a DNS query to a DNS resolver, typically managed by the user’s Internet Service Provider (ISP) or a third-party DNS provider.

Root Name Server Interaction:
If the resolver does not have the IP address cached, it queries one of the root name servers. These servers respond with the address of a Top-Level Domain (TLD) name server responsible for the .com domain.

TLD Name Server Response:
The resolver then queries the TLD name server, which provides the address of the authoritative DNS server for example.com.

Authoritative DNS Server Response:
The resolver contacts the authoritative DNS server for example.com, which returns the IP address associated with www.example.com (e.g., 192.0.2.44).

Caching the IP Address:
The resolver caches the IP address for a specified Time-To-Live (TTL) duration. This caching allows future requests for www.example.com to be resolved more quickly without repeating the entire query process.

Connecting to the Web Server:
The resolver sends the IP address back to the user’s web browser. The browser then uses this IP address to establish a connection to the web server hosting www.example.com and requests the web page.

Displaying the Web Page:
The web server responds by sending the requested web page to the browser, which then displays it to the user.

The entire DNS resolution process typically occurs within milliseconds.

