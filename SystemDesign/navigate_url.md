# What really happens when you enter a url

1. enter url in browser
2. browser looks up IP address for domain name
    - DNS look up process:
        - **Browser cache**: browser caches DNS record
        - **OS cache**: if browser cache doesn't have the desired record, OS has its own cache
        - **Router cache**: request goes to router, has its own DNS cache
        - **ISP DNS cache**: next check step is the cache ISP’s DNS server
        - **Recursive search**: ISP's DNS server makes recursive search
    - DNS search bottleneck solutions:
        - **Round-robin DNS**: DNS lookup returns multiple IP addresses, rather than just one.
        - **Load-balancer**: the piece of hardware that listens on a particular IP address and forwards the requests to other servers
        - **Geographic DNS**: mapping a domain name to different IP addresses, depending on the client’s geographic location.
        - **Anycast**: a routing technique where a single IP address maps to multiple physical servers. However, it doesn't `fit well with TCP`.
3. Browser sends HTTP request to the web server, use `GET`
4. The web server (i.e. facebook) responds with a permanent redirect
    - The redirect may due to search engine
5. Browser follows redirect
6. Server handles the request
7. Server sends back HTML response
8. Browser begins rendering the HTML
9. Browser sends request for HTML embedded objects (i.e. images, styles, etc)
10. Browser sends further asynchronous (AJAX) request

### Reference

- [What really happens when you navigate to a URL](http://igoro.com/archive/what-really-happens-when-you-navigate-to-a-url/comment-page-3/)
