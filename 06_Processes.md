# 6. Processes

Applications should be executed as one or more stateless processes. This means that each process runs independently and does not retain state between requests. This approach simplifies scalability and reliability in distributed environments.

## Best Practices   

### 1. Design for Statelessness

* **Stateless Web Services:** When designing web services or APIs, ensure that each request can be served by any instance of the application. 
<br> For example, in a `REST API` developed using `Node.js Express`, avoid storing any user data or session-specific information directly in the application's memory.

* **Functional Approach:** Adopt a functional programming style where possible, emphasizing functions that produce the same output given the same input without side effects.

### 2. Store Session State in a Centralized Data Store

* **External Session Stores:** For applications that need to maintain session data (like `user authentication status`), use external stores like `Redis` or a `database`. 
<br> For example, in a `PHP application`, instead of using the default file-based session storage, configure it to use a `Redis server`. This approach allows any instance of the application to access the session data.

* **Token-Based Authentication:** In microservices or distributed architectures, use token-based authentication methods like `JWT` (JSON Web Tokens). JWTs can be validated by any instance of the service without needing to share session data.

### 3. Scale Horizontally by Adding Process Instances

* **Load Balancing:** Deploy multiple instances of your application behind a load balancer which distributes incoming requests across all instances. 
<br> For example, in a cloud environment like `AWS`, you can use `Elastic Load Balancing` to distribute traffic among `EC2 instances` running your application.

* **Container Orchestration:** Use container orchestration tools like `Kubernetes` or `Docker Swarm`. These tools allow you to define how many instances of your containerized application should be running. When demand increases, the orchestration tool automatically starts more instances (`pods` in Kubernetes) to handle the load.

By adhering to these practices, your application becomes more scalable and resilient. Stateless design makes it easier to scale out (by adding more instances) rather than scaling up (by increasing the capacity of a single instance), which is a key principle for building robust, distributed applications, especially in cloud environments.
