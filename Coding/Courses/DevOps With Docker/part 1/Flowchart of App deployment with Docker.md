### Steps for Using Docker for App Development and Deployment

1. **Develop Your App in a Container**:
    
    - Create a `Dockerfile` describing how to build your app's container image (e.g., base image, dependencies, commands to run your app, etc.).
    - Use `docker-compose.yml` if your app needs multiple services (e.g., app, database).
    - Build and run the container locally using commands like:
        
        `docker build -t my-app . docker run -p 3000:3000 my-app`
        
    - You can directly work inside the container by mounting your code folder:

        `docker run -v $(pwd):/app -p 3000:3000 my-app`
        
2. **Test Locally**:
    
    - Ensure the app works as expected inside the Docker container.
    - If the app interacts with other services (e.g., databases), spin them up with Docker Compose.
3. **Push the Docker Image**:
    
    - Once your app is ready, push the image to a container registry like Docker Hub, AWS ECR, or a private registry:
        
        `docker tag my-app username/my-app:latest docker push username/my-app:latest`
        
4. **Deploy on VPS**:
    
    - SSH into your VPS and pull the Docker image:

        `docker pull username/my-app:latest`
        
    - Run the app in a container on the VPS:
        
        `docker run -d -p 3000:3000 username/my-app:latest`
        
    - If needed, use Docker Compose on the VPS for multi-container setups.
5. **Optional: Automate Deployment**:
    
    - Use CI/CD pipelines to automate building, testing, and deploying your Docker containers.