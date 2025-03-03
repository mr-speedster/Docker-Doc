### What is Docker?

Docker is a platform that allows you to **containerize** applications, making them portable, lightweight, and consistent across different environments. A **container** is a standalone package that includes everything needed to run a piece of software: code, runtime, libraries, and system tools. Containers are isolated from each other and the host system, ensuring consistency and avoiding conflicts.

Think of Docker as a way to ship your application in a "box" that works the same way everywhere, whether it's on your laptop, a colleague's machine, or a production server.

---

### Key Concepts

1. **Image**: A read-only template that contains the application code, libraries, and dependencies. Images are used to create containers.
2. **Container**: A running instance of an image. It’s isolated and has its own filesystem, networking, and processes.
3. **Dockerfile**: A text file that contains instructions to build a Docker image.
4. **Registry**: A place to store and share Docker images (e.g., Docker Hub).

---

### Essential Docker Commands

#### 1. **Working with Images**
- **Pull an image from a registry**:
  ```bash
  docker pull <image_name>:<tag>
  ```
  Example:
  ```bash
  docker pull ubuntu:latest
  ```

- **Build an image from a Dockerfile**:
  ```bash
  docker build -t <image_name>:<tag> <path_to_Dockerfile>
  ```
  Example:
  ```bash
  docker build -t my_app:1.0 .
  ```

- **List all images**:
  ```bash
  docker images
  ```

- **Remove an image**:
  ```bash
  docker rmi <image_name>:<tag>
  ```

---

#### 2. **Working with Containers**
- **Run a container from an image**:
  ```bash
  docker run <image_name>:<tag>
  ```
  Example:
  ```bash
  docker run -it ubuntu:latest
  ```
  - `-i`: Interactive mode (keeps STDIN open).
  - `-t`: Allocates a pseudo-TTY (terminal).

- **Run a container in detached mode (background)**:
  ```bash
  docker run -d <image_name>:<tag>
  ```

- **List running containers**:
  ```bash
  docker ps
  ```

- **List all containers (running and stopped)**:
  ```bash
  docker ps -a
  ```

- **Stop a running container**:
  ```bash
  docker stop <container_id>
  ```

- **Start a stopped container**:
  ```bash
  docker start <container_id>
  ```

- **Remove a container**:
  ```bash
  docker rm <container_id>
  ```

- **Execute a command in a running container**:
  ```bash
  docker exec -it <container_id> <command>
  ```
  Example:
  ```bash
  docker exec -it my_container bash
  ```

- **View container logs**:
  ```bash
  docker logs <container_id>
  ```

---

#### 3. **Networking and Ports**
- **Map a host port to a container port**:
  ```bash
  docker run -p <host_port>:<container_port> <image_name>:<tag>
  ```
  Example:
  ```bash
  docker run -p 8080:80 nginx
  ```

---

#### 4. **Volumes (Persistent Data)**
- **Mount a host directory as a volume**:
  ```bash
  docker run -v <host_path>:<container_path> <image_name>:<tag>
  ```
  Example:
  ```bash
  docker run -v /home/user/data:/app/data my_app:1.0
  ```

---

#### 5. **Docker Compose (Multi-Container Applications)**
Docker Compose is a tool for defining and running multi-container Docker applications using a `docker-compose.yml` file.

- **Start services**:
  ```bash
  docker-compose up
  ```

- **Stop services**:
  ```bash
  docker-compose down
  ```

---

### Example Dockerfile
Here’s a simple Dockerfile for a Python application:
```Dockerfile
# Use an official Python runtime as a parent image
FROM python:3.9-slim

# Set the working directory in the container
WORKDIR /app

# Copy the current directory contents into the container
COPY . .

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Expose port 80
EXPOSE 80

# Run the application
CMD ["python", "app.py"]
```

---

### Why Docker is Useful for Data Engineers
- **Reproducibility**: Ensure your data pipelines run the same way in development, testing, and production.
- **Isolation**: Avoid dependency conflicts between different projects.
- **Portability**: Easily share your environment with teammates or deploy to cloud platforms.
- **Scalability**: Use Docker with orchestration tools like Kubernetes to scale your data workflows.

---

### Next Steps
1. Install Docker: [https://docs.docker.com/get-docker/](https://docs.docker.com/get-docker/)
2. Play around with basic commands.
3. Dockerize a simple application or data pipeline.
4. Explore Docker Compose for multi-container setups.
