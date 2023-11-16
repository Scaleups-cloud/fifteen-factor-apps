# 7. Port Binding

Applications should be self-contained and able to bind to allocated ports without relying on an externally injected webserver. This approach makes the application more portable and easier to deploy in various environments.


## Best Practices

### 1. Use Embedded Servers Within the Application

* **Embedded Web Servers in Java Applications:** For Java applications, use embedded server options like `Tomcat`, `Jetty`, or `Undertow`. 
<br> In Spring Boot, for example, you can easily create a self-contained application with an embedded Tomcat by adding the appropriate starter dependency to your `pom.xml` or `build.gradle` file. Spring Boot automatically configures and starts the embedded server when the application is run.

* **Node.js Applications:** Node.js inherently supports creating web servers within the application using its `http` or `express` module. A simple server can be created and bound to a port as follows:

``` javascript
const express = require('express');
const app = express();

app.get('/', (req, res) => res.send('Hello World!'));

const PORT = process.env.PORT || 3000;
app.listen(PORT, () => console.log(`Server running on port ${PORT}`));
```

### 2. Ensure that the Application Can Bind to Allocated Ports

* **Environment Variable for Port Binding:** To allow flexibility in port allocation, particularly in cloud environments or platforms like `Heroku`, use an environment variable to specify the port. 
<br> In the Node.js example above, `process.env.PORT` is used to determine the port, allowing the environment to dictate the port number.

* **Docker Containers:** When containerizing your application with Docker, specify the port binding in the `Dockerfile` or `docker-compose.yml`. 
<br> For example, in a Dockerfile, you might have `EXPOSE 3000` to indicate that the container listens on port 3000. You can then map this port to a port on the host when running the container, 
<br> e.g., `docker run -p 8000:3000 your-image`, which maps port `3000` in the container to port `8000` on the host.

By following these practices, you ensure that your application is fully self-contained and can be deployed easily across different environments, whether it's on a developer's local machine, a traditional server, or a cloud-based platform. This portability is a key aspect of modern application design, facilitating continuous deployment and scaling.

