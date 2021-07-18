# Internet Protocol Suite

When talking about network communications, the first thing you need to understand is the `Open Systems Interconnection Model (OSI Model)`

![OSI model](https://img.router-switch.com/media/wysiwyg/Help-Center-FAQ/Router/osi-model.png)

For the system design purpose, we don't need to go lower than layer 4.

The most commonly used protocols are summarized in this table:

![Internet Protocol Suite](http://2.bp.blogspot.com/-8spz6AylxBQ/UWKFo86yYjI/AAAAAAAAANI/XKyMikMWn7c/s1600/tcpip.jpg)

It is definitely not a complete table, and we are particularly interested in the following areas:

- TCP vs UDP:
    - TCP: 
        - connection-oriented protocol
        - connection established between the peer entities prior to transmission
        - transmission flow is controlled such that a fast sender does not overwhelm a slow receiver.
    - UDP:
        - message-oriented protocol 
        - basically broadcasting messages, no connection/sequence guaranteed 

- Other transport layer protocols:
    - QUIC: Based on UDP, initially designed by google.
    - SCTP: Combination of TCP and UDP, used for telephony over the Internet.

- TCP/IP:
    - Sometimes people also talking about TCP/IP, it means a protocol stack which contains different protocols required for the data transfer from sender to receiver
    - Details can be seen [here](https://stackoverflow.com/questions/31473578/tcp-ip-and-tcp-and-ip-difference) and [here](https://www.fortinet.com/resources/cyberglossary/tcp-ip)

- HTTP: How does it work when a client wants to communicate with a server
    - Open a TCP connection
    - Send an HTTP message
    - Read the response sent by the server
    - Close connection (or reuse connection for further communication)

- HTTPS:
    - Extension of HTTP, but more secure
    - Use SSL/TLS to ensure security of data transportation

- socket:
    - A socket is one endpoint of a two-way communication link between two programs running on the network. 
    - A socket is bound to a port number so that the TCP layer can identify the application that data is destined to be sent to.

- websocket:
    - A WebSocket is a persistent connection between a client and server
    - WebSockets provide a bidirectional, full-duplex communications channel that operates over HTTP through a single TCP/IP socket connection

- HTTP vs Long-polling vs websocket:
    - HTTP is a strictly unidirectional protocol
    - Long-polling is an HTTP request with a long timeout period
        - resources on the server are tied up throughout the length of the long-poll, even when no data is available to send.
    - Websocket: allow for sending message-based data, similar to UDP, but with TCP
        - uses HTTP as the initial transport mechanism (i.e. HTTP request headers), but keeps the TCP connection alive after the HTTP response is received
        - Once TCP connection is established, it uses websocket protocol to communicate
            - WebSocket is a framed protocol, meaning that a chunk of data (a message) is divided into a number of discrete chunks, with the size of the chunk encoded in the frame. 
            - The frame includes a frame type, a payload length, and a data portion.
    - More comparison between websocket and http can be seen [here](https://www.geeksforgeeks.org/what-is-web-socket-and-how-it-is-different-from-the-http/)

- REST: 
    - a software architectural style that was created to guide the design and development of the architecture for the World Wide Web
    - Any web service that obeys the REST constraints is informally described as **RESTful**
    - The goal of REST is to increase performance, scalability, simplicity, modifiability, visibility, portability, and reliability.
    - Six guiding constraints define a RESTful system:
        - Client–server architecture
            - client application and server application MUST be able to evolve separately without any dependency on each other
        - Statelessness
            - The server will not store anything about the latest HTTP request the client made. It will treat every request as new. No session, no history.
        - Cacheability
            - caching shall be applied to resources when applicable
            - Caching can be implemented on the server or client-side.
        - Layered system
            - allows you to use a layered system architecture where you deploy the APIs on server A, and store data on server B and authenticate requests in Server C
        - Uniform interface
            - A resource in the system should have only one logical URI, and that should provide a way to fetch related or additional data.
        - Code on demand (optional)
            - you are free to return executable code to support a part of your application

- REST vs SOAP
    - REST is an architectural style, while SOAP is a protocol
    - REST is not a standard in itself, but RESTful implementations make use of standards

- HTTP response status codes
    - For a full list please see [here](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)
    - Some common ones:
        - 200: ok/success
        - 201: created
        - 202: accepted
        - 204: No content
        - 300: more than one possible response
        - 301: permanent redirect
        - 302: temporarily redirect
        - 400: The server could not understand the request due to invalid syntax.
        - 401: unauthenticated
        - 403: Permission denied
        - 404: The server can not find the requested resource (URL not recognized)
        - 500: Unhandled error on server
        - 502: Server got an invalid response


Reference:

- [Network Layers & Network Layer in OSI Model](https://www.router-switch.com/faq/network-layers-in-osi-model-features-of-osi.html)
- [Application Layer (Internet protocol Suite) ~ Networking Space](http://walkwidnetwork.blogspot.com/2013/04/application-layer-internet-protocol.html)
- [The Internet protocol suite (article) \| Khan Academy](https://www.khanacademy.org/computing/computers-and-internet/xcae6f4a7ff015e7d:the-internet/xcae6f4a7ff015e7d:the-internet-protocol-suite/a/the-internet-protocols)
- [QUIC - Wikipedia](https://en.wikipedia.org/wiki/QUIC)
- [An overview of HTTP - HTTP \| MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview)
- [What Is a Socket? (The Java™ Tutorials > Custom Networking > All About Sockets)](https://docs.oracle.com/javase/tutorial/networking/sockets/definition.html)
- [WebSockets - A Conceptual Deep Dive \| Ably Realtime](https://ably.com/topic/websockets)
- [How Do Websockets Work? - Kevin Sookocheff](https://sookocheff.com/post/networking/how-do-websockets-work/)
- [Short Polling vs Long Polling vs WebSockets - System Design](https://www.youtube.com/watch?v=ZBM28ZPlin8&ab_channel=BeABetterDev)
- [Representational state transfer - Wikipedia](https://en.wikipedia.org/wiki/Representational_state_transfer)
- [REST Principles and Architectural Constraints](https://restfulapi.net/rest-architectural-constraints/)
