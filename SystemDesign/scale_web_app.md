# Web app scale from monolithic to distributed 

## 1. Single Server + Database

![01-initial-700.png](https://arcentry.com/blog/scaling-webapps-for-newbs-and-non-techies/01-initial-700.png)

MVC Design:
- Advantage:
    - Easy to debug
    - Easy to deploy

- Disadvantage:
    - very difficult to scale. Each request is handled by the server and one page can have many requests which will consume lots of server resources
    - whenever there is a server issue, entire site goes down
    - deployment goes with both front end or backend end

## 2. Adding a Reverse Proxy

![02-reverse-proxy-700.png](https://arcentry.com/blog/scaling-webapps-for-newbs-and-non-techies/02-reverse-proxy-700.png)

- **Health Checks** make sure that our actual server is still up and running
- **Routing** forwards a request to the right endpoint
- **Authentication** makes sure that a user is actually permitted to access the server
- **Firewalling** ensure that users only have access to the parts of our network they are allowed to use ... and more

## 3. Add a Load Balancer with multiple servers

![03-load-balancer-700.png](https://arcentry.com/blog/scaling-webapps-for-newbs-and-non-techies/03-load-balancer-700.png)

- Reverse Proxy can act as load balancer

## 4. Add more database to each server

![04-database-scale-700.png](https://arcentry.com/blog/scaling-webapps-for-newbs-and-non-techies/04-database-scale-700.png)

How to ensure data consistency:
- **Master/Slave setup or Write with Read-replicas**: split into multiple parts where each part does its own thing

## 5. Microservices

![05-microservices-700.png](https://arcentry.com/blog/scaling-webapps-for-newbs-and-non-techies/05-microservices-700.png)

- each service can be scaled individually, enabling us to better adjust to demand
- development teams can work independently, each being responsible for their own microservice's lifecycle (creation, deployment, updating etc.)
- each microservice can use its own resources

## 6. Caching & CDN(Content Delivery Networks)

![06-cdn-700.png](https://arcentry.com/blog/scaling-webapps-for-newbs-and-non-techies/06-cdn-700.png)

- cache the static content

## 7. Message Queues

![07-message-queue-700.png](https://arcentry.com/blog/scaling-webapps-for-newbs-and-non-techies/07-message-queue-700.png)

Advantages:
- it decouples tasks and processors. Sometimes a lot of images need to be processed, sometimes only a few. Sometimes a lot of processors are available, sometimes its just a couple. By simply adding tasks to a backlog rather than processing them directly we ensure that our system stays responsive and no tasks get lost.
- it allows us to scale on demand. Starting up more processors takes time - so by the time a lot of users tries to upload images, it's already too late. By adding our tasks to a queue we can defer the need to provision additional capacities to process them

## 8. Sharding

![08-sharding-700.png](https://arcentry.com/blog/scaling-webapps-for-newbs-and-non-techies/08-sharding-700.png)

- Sharding can be based on any number of factors, e.g. letters, location, usage frequency (power-users are routed to the good hardware) and so on. 
- You can shard servers, databases or almost any aspect of your stack this way, depending on your needs.

## 9. Load-balancing the load-balancer

![09-dns-700.png](https://arcentry.com/blog/scaling-webapps-for-newbs-and-non-techies/09-dns-700.png)

- DNS (Domain Name System): allows us to specify multiple IPs per domain name, each leading to a different load balancer.

## Reference:

- [Scaling webapps for newbs & non-techies](https://arcentry.com/blog/scaling-webapps-for-newbs-and-non-techies/)

## More resources

- [Scaling Up to Your First 10 Million Users](https://www.youtube.com/watch?v=Ma3xWDXTxRg&ab_channel=AmazonWebServices)
- [Web Scalability for Startup Engineers](https://www.amazon.ca/Scalability-Startup-Engineers-Artur-Ejsmont/dp/0071843655)
- [A Beginner's Guide to Scaling to 11 Million+ Users on Amazon's AWS - High Scalability -](http://highscalability.com/blog/2016/1/11/a-beginners-guide-to-scaling-to-11-million-users-on-amazons.html)
