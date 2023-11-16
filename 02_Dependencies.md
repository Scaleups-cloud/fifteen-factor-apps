# 2. Dependencies
Dependencies of an application should be explicitly declared and isolated. This means the application doesn’t rely on the implicit existence of system-wide packages or libraries.

## Best Practices

### 1. Use Dependency Management Tools
* **Node.js (npm):** For a Node.js project, use npm to manage your dependencies. Begin by initializing your project with `npm init`, which creates a `package.json` file. To add a dependency, use `npm install [package-name]`. This command updates `package.json` and `package-lock.json`, ensuring that your dependencies are explicitly listed and locked to specific versions.
* **Java (Maven):** In a Java project using Maven, dependencies are declared in the `pom.xml` file. To add a dependency, you include it in the `<dependencies>`section of `pom.xml`. 
<br> For example:
``` xml
<dependencies>
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-core</artifactId>
        <version>5.2.3.RELEASE</version>
    </dependency>
</dependencies>
```
This ensures that Maven handles the downloading and linking of this specific version of Spring Core.

### 2. Package All Dependencies with the Application
* **Containerization (Docker):** Use containerization to package your application with its dependencies. For instance, create a `Dockerfile` that specifies the base environment, installs required dependencies, and sets up the application. When you build and run a Docker container from this Dockerfile, it contains everything the application needs to run, isolated from the host system.
* **Virtual Environments (Python):** In Python, use virtual environments to isolate dependencies. Tools like `virtualenv` or `conda` allow you to create an isolated environment with its own installation directories, not shared with other virtual environments. Activate a virtual environment and use `pip` to install dependencies, which are then isolated to that environment.

### 3. Regularly Update and Audit Dependencies for Security Vulnerabilities

* **Using npm Audit:** For a `Node.js` project, use npm audit to scan your project for vulnerabilities in dependencies. This tool reports any known vulnerabilities and suggests updates or patches.
* **Dependency Scanners:** Integrate dependency scanning tools into your CI/CD pipeline. Tools like Trivy, Mend.io, or OWASP Dependency-Check can automatically scan your dependencies for known vulnerabilities whenever you commit changes or build your application.

By following these best practices, you ensure that your application is using a set of known, documented, and secure dependencies, reducing the risks associated with unknown or outdated libraries. Explicit dependency management is crucial for maintaining the health and security of your software over time.
