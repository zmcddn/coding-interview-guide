# Load Balancer

- A load balancer distributes incoming client requests among a group of servers, in each case returning the response from the selected server to the appropriate client.
- A load balancer can also enhance the user experience by reducing the number of error responses the client sees.
- Session persistence (sending all requests from a particular client to the same server) is also available for some load balancers

## Types of Load Balancers: Layer 4 and Layer 7

Layer 4 load balancing:

- “Layer 4 load balancing” most commonly refers to a deployment where the load balancer’s IP address is the one advertised to clients for a web site or service (via DNS, for example)
- Layer 4 load balancing operates at the intermediate transport layer, which deals with delivery of messages with no regard to the content of the messages.
- When it receives a request and makes the load balancing decision, it also performs Network Address Translation (NAT) on the request packet, changing the recorded destination IP address from its own to that of the content server it has chosen on the internal network
- Before forwarding server responses to clients, the load balancer changes the source address recorded in the packet header from the server’s IP address to its own.
- Layer 4 load balancing was a popular architectural approach to traffic handling when commodity hardware was not as powerful as it is now, and the interaction between clients and application servers was much less complex.

Layer 7 load balancing:

- Layer 7 load balancing operates at the high‑level application layer, which deals with the actual content of each message. 
- HTTP is the predominant Layer 7 protocol for website traffic on the Internet.
- It terminates the network traffic and reads the message within. 
- It can make a load‑balancing decision based on the content of the message (the URL or cookie, for example). 
- It then makes a new TCP connection to the selected upstream server (or reuses an existing one, by means of HTTP keepalives) and writes the request to the server.
- Layer 7 load balancing is more CPU‑intensive than packet‑based Layer 4 load balancing

## Load Balancing Algorithms

- Least connection
    - Selects the server with least active connection
- Weighted Least Connection
    - Similar to least connection but with weight
- Least response time
    - Selects the server with least response time
- Weighted Least response time
    - Similar to least response time but with weight
- Least bandwidth
    -  Selects the server with least bandwidth
- Round robin
    - Checks each server one by one
- Weighted round-robin
    - Checks each server one by one based one the weight that admin assigns on the server
- IP hash
    - combines source and destination IP addresses of the client and server to generate a unique hash key, which is used to allocate the client to a particular server.
    - the client request is directed to the same server it was using previously.

# Reverse Proxy

- A reverse proxy accepts a request from a client, forwards it to a server that can fulfill it, and returns the server’s response to the client.
- Increased security – No information about your backend servers is visible outside your internal network
- Has security features to help protect backend servers from distributed denial-of-service (DDoS) attacks (i.e. IP address blacklisting, etc)
- Increased scalability and flexibility – Because clients see only the reverse proxy’s IP address, you are free to change the configuration of your backend infrastructure.
- Increased performance on response time
    - Compression (of server responses to reduce bandwidth)
    - SSL termination (Encryption)
    - Caching (server response for same requests)

# API Gateway

- An API Gateway is the element that coordinates and orchestrates how all the requests are processed in a Microservices architecture
- An API Gateway includes an HTTP server where routes are associated with a Microservice or with a FaaS function
- When an API Gateway receives a request, it looks up for the Microservice which can serve the request and delivers it to the relevant part.
- Besides this pure routing task, an API gateway can also be the part that performs **authentication**, **input validation**, **load balancing** and **centralized middleware** functionality, among other tasks.
- It often makes sense to deploy a reverse proxy even with just one web server or application server.
- Drawbacks for API gateway are:
    - It creates a tight coupling between the client and the backend.
    - It has limited choice of communication protocols for services.
    - It could becomes a bottleneck for your application

## An example: The Architecture of Uber’s API gateway

Components in a request lifecycle:

1. **Protocol manager**: provides the ability to implement APIs that can ingest any type of relevant protocol payload
2. **Middleware**: implements composable logic before the endpoint handler is invoked
    - Middleware implements cross-cutting concerns, such as authentication, authorization, rate limiting, circuit breaking, etc.
3. **Endpoint handler**: responsible for request validation, payload transformation, and converting the endpoint request object to the client request object.
4. **Client**: performs a request to a back-end service


# Reference:

- [System Design: What is Load Balancing? - YouTube](https://www.youtube.com/watch?v=gMIslJN44P0&ab_channel=BeABetterDev)
- [System Design — Load Balancing. Concepts about load balancers and… \| by Larry | Peng Yang | Computer Science Fundamentals | Medium](https://medium.com/must-know-computer-science/system-design-load-balancing-1c2e7675fc27)
- [What Is Layer 4 Load Balancing? \| NGINX Load Balancer](https://www.nginx.com/resources/glossary/layer-4-load-balancing/)
- [Benefits of Layer 7 Load Balancing \| NGINX Load Balancer](https://www.nginx.com/resources/glossary/layer-7-load-balancing/)
- [Load Balancing Algorithms, Types and Techniques](https://kemptechnologies.com/load-balancer/load-balancing-algorithms-techniques/)
- [What is a Proxy? \| System Design - YouTube](https://www.youtube.com/watch?v=xiUmXVcLdCw&ab_channel=BeABetterDev)
- [What is a Reverse Proxy vs. Load Balancer? - NGINX](https://www.nginx.com/resources/glossary/reverse-proxy-vs-load-balancer/)
- [Stupid question of the day: What is an API Gateway and what it has to do with a Serverless model? \| by Gabry Martinez | Medium](https://gabrymartinez.medium.com/stupid-question-of-the-day-what-is-an-api-gateway-and-what-it-has-to-do-with-a-serverless-model-2acee3e3eeba)
- [What is API Gateway?. In microservices architecture, there… \| by Vivek Kumar Singh | System Design Blog | Medium](https://medium.com/system-design-blog/what-is-api-gateway-68a11d4ab322)
- [The Architecture of Uber's API gateway \| Uber Engineering Blog](https://eng.uber.com/architecture-api-gateway/)
