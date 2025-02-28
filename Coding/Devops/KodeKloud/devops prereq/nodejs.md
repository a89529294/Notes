```bash
npm root -g # shows global node_modules

node -e "console.log(require('module').builtinModules)" # a list of all the built-in modules

npm search file_name # or just use npmjs.com
```

## pm2
### PM2's Built-in Load Balancer:

1. **Purpose**: PM2's load balancer is designed to distribute incoming traffic across multiple instances of a Node.js application running on the same machine. This is particularly useful for taking advantage of multi-core CPUs, as Node.js is single-threaded by default.
2. **How it Works**: When you start a Node.js application with PM2, you can specify the number of instances (or "clusters") you want to run. PM2 will then spawn multiple processes (one per CPU core, by default) and distribute incoming requests among these processes. This is done using the Node.js `cluster` module under the hood.
3. **Use Case**: PM2's load balancer is primarily used for scaling a Node.js application vertically (i.e., on a single machine) by utilizing multiple CPU cores. It is not designed to handle horizontal scaling (i.e., across multiple machines) or to manage traffic between different servers.
4. Node.js applications running in separate processes (or clusters) do **not share memory**. Each process has its own isolated memory space.
5. For example, if one instance sets a variable `count = 1`, this variable will only exist in that specific instance. Other instances will have their own separate `count` variables, which might have different values (e.g., `count = 2` in another instance).
    

### Nginx's Load Balancer:

1. **Purpose**: Nginx is a high-performance web server, reverse proxy, and load balancer. Its load balancer is more general-purpose and can distribute traffic across multiple servers (horizontal scaling), not just multiple processes on a single machine.
2. **How it Works**: Nginx can be configured to act as a reverse proxy, distributing incoming requests to a pool of backend servers. It supports various load balancing algorithms (e.g., round-robin, least connections, IP hash) and can handle more complex scenarios like health checks, SSL termination, and caching.
3. **Use Case**: Nginx's load balancer is typically used in scenarios where you have multiple servers running your application, and you need to distribute traffic among them. It is also commonly used to handle high traffic loads, provide fault tolerance, and improve the overall performance and reliability of web applications.

### When to Use Which:

- **PM2**: Use PM2's load balancer when you want to scale a Node.js application *vertically* on a single machine, especially if you want to take advantage of multiple CPU cores.
- **Nginx**: Use Nginx when you need to scale *horizontally* across multiple servers, or when you need advanced load balancing features like SSL termination, health checks, or caching.

### example

- `pm2 start app.js -i max`
	- `-i max`: This tells PM2 to start the application in cluster mode and create as many instances as there are CPU cores on your machine. You can also specify a fixed number of instances, like `-i 4` to start 4 instances.
- `pm2 list`: check the status of your PM2 processes
- `pm2 reload app.js`: If you make changes to your code and want to reload the app without downtime
- `pm2 stop app.js` or `pm2 stop all`
- `pm2 delete app.js` run this otherwise any further command like `pm2 start app.js -i 4` will only restart the previous process. 

### When to Use `-i max`

Using `-i max` is a good idea when:
- Your machine has **sufficient RAM** to handle multiple instances of your application.
- Your application is **CPU-bound** (e.g., performing heavy computations) and can benefit from parallel processing.
- You want to maximize the utilization of your CPU cores.