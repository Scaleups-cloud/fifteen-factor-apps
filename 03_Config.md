# 3. Config

Configuration data, which varies between deployments (such as database URLs, credentials for external services, etc.), should be stored in the environment rather than in the code. This separation of configuration from code enables greater flexibility and security.

## Best Practices

### 1. Use Environment Variables for Configuration

* **Setting Environment Variables:** In a `Node.js` application, you might use environment variables to store database connection information. 
<br> For instance, instead of hardcoding the database URL in your code, you can set an environment variable named `DATABASE_URL`.
* **Accessing Environment Variables:** In your application, access these variables using the respective language-specific methods. 
<br> For `Node.js`, you can access the `DATABASE_URL` using `process.env.DATABASE_URL`.
* **.env Files:** For local development, use `.env` files to set environment variables. Libraries like `dotenv` in `Node.js` can load variables from `.env` into `process.env`.

### 2. Avoid Storing Configuration in Code or Version Control

* **Ignore Configuration Files:** Use `.gitignore` to exclude configuration files (like `.env`) from version control. This prevents sensitive information from being exposed in your repository.
* **Use Secure Storage for Secrets:** For sensitive configurations like API keys, use secure storage solutions like AWS Secrets Manager, HashiCorp Vault, or Azure Key Vault. Access these secrets at runtime in your application.

### 3. Implement Configuration Management Tools for Complex Configurations

* **Using Config Servers:** In microservices architecture, use a centralized config server (like Spring Cloud Config Server for Java applications) that provides configuration to all services. Each service retrieves its configuration from this server at runtime.
* **Feature Flags:** For managing feature toggles or flags, use tools like LaunchDarkly or Split.io. These allow you to control features in your application dynamically, without deploying new code.
* **Container Orchestration Platforms:** In containerized environments (like Kubernetes), use ConfigMaps and Secrets to manage configurations. `ConfigMaps` can hold non-confidential data, whereas Secrets are for sensitive information. Both can be injected into containers at runtime.

By adhering to these practices, you ensure that your application's configuration is flexible, secure, and environment-specific, reducing the risk of exposing sensitive information and making it easier to manage different deployment environments (development, staging, production).

