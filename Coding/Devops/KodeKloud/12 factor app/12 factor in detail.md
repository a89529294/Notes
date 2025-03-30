### **I. Codebase**

**One codebase tracked in revision control, many deploys**

- **Explanation**: There should be a single codebase for the application, tracked in a version control system (e.g., Git). This codebase can be deployed to multiple environments (e.g., development, staging, production).
    
- **Example**: A web app has one Git repository. Developers work on the same codebase, and the app is deployed to staging for testing and to production for users. Different environments use the same codebase but may have different configurations.
    
---
### **II. Dependencies**

**Explicitly declare and isolate dependencies**

- **Explanation**: All dependencies (libraries, tools, etc.) should be explicitly declared and isolated. This ensures consistency across environments.
    
- **Example**: In a Python app, use a `requirements.txt` file or `Pipfile` to list all dependencies. In Node.js, use `package.json`. Tools like `virtualenv` (Python) or `npm` (Node.js) isolate dependencies to avoid conflicts.
    
---
### **III. Config**

**Store config in the environment**

- **Explanation**: Configuration (e.g., database URLs, API keys) should be stored in environment variables, not hardcoded in the codebase. This keeps sensitive data secure and makes the app more portable.
    
- **Example**: Instead of hardcoding a database URL in the code, use an environment variable like `DATABASE_URL=postgres://user:password@host:port/dbname`. Tools like `.env` files or cloud provider secrets managers can help manage these.
    
---
### **IV. Backing Services**

**Treat backing services as attached resources**

- **Explanation**: Backing services (e.g., databases, message queues, caching systems) should be treated as attached resources that can be swapped without code changes.
    
- **Example**: If your app uses a PostgreSQL database, you should be able to switch to a MySQL database by changing the configuration (e.g., the `DATABASE_URL` environment variable) without modifying the code.
    
---
### **V. Build, Release, Run**

**Strictly separate build and run stages**

- **Explanation**: The build stage compiles the code and dependencies into an executable bundle. The release stage combines the build with the configuration. The run stage executes the app. These stages should be distinct and never mixed.
    
- **Example**: In a CI/CD pipeline, the build stage compiles the app into a Docker image. The release stage tags the image with the appropriate configuration (e.g., environment variables). The run stage deploys the image to a server or cloud platform.
    
---
### **VI. Processes**

**Execute the app as one or more stateless processes**

- **Explanation**: The app should run as stateless processes. Any data that needs to persist should be stored in a backing service (e.g., a database).
    
- **Example**: A web app should not store session data in memory. Instead, use a shared session store like Redis. This allows you to scale horizontally by adding more instances of the app.
    
---
### **VII. Port Binding**

**Export services via port binding**

- **Explanation**: The app should be self-contained and expose its services by binding to a port. It should not rely on external servers (e.g., Apache, Nginx) to serve requests.
    
- **Example**: A Node.js app listens on port 3000. In production, a reverse proxy like Nginx can route traffic to this port, but the app itself is responsible for binding to the port.
    
---
### **VIII. Concurrency**

**Scale out via the process model**

- **Explanation**: The app should scale horizontally by running multiple processes. Each process should handle a specific type of work (e.g., web requests, background jobs).
    
- **Example**: A web app uses separate processes for handling HTTP requests and processing background jobs (e.g., sending emails). You can scale the web process independently of the worker process.
    
---
### **IX. Disposability**

**Maximize robustness with fast startup and graceful shutdown**

- **Explanation**: Processes should start quickly and shut down gracefully. This ensures the app can handle scaling, crashes, and deployments without downtime.
    
- **Example**: A web app should handle SIGTERM signals to gracefully shut down, ensuring all in-progress requests are completed before exiting. It should also start quickly to allow for rapid scaling.
    
---
### **X. Dev/Prod Parity**

**Keep development, staging, and production as similar as possible**

- **Explanation**: The development environment should closely resemble the production environment to avoid bugs and inconsistencies.
    
- **Example**: Use Docker to containerize your app, ensuring the same environment is used in development and production. Avoid using different databases (e.g., SQLite in development, PostgreSQL in production).
    
---
### **XI. Logs**

**Treat logs as event streams**

- **Explanation**: Logs should be treated as streams of events, not files. The app should not manage log files directly; instead, it should write logs to `stdout` and let the environment handle them.
    
- **Example**: A Node.js app writes logs to `console.log`, which outputs to `stdout`. A logging tool like Fluentd or Logstash collects these logs and sends them to a centralized logging system like ELK or CloudWatch.
    
---
### **XII. Admin Processes**

**Run admin/management tasks as one-off processes**

- **Explanation**: Administrative tasks (e.g., database migrations, scripts) should be run as one-off processes in the same environment as the app.
    
- **Example**: To run a database migration, use a command like `rails db:migrate` or `python manage.py migrate`. These tasks should use the same environment and dependencies as the app.