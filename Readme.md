
##  Docker (Containerization)

### What it is
- Platform for packaging applications in isolated containers  
- Containers include code, runtime, dependencies, and OS  

### Why Docker
- **Consistency**: Runs the same everywhere (dev, staging, production)  
- **Isolation**: No dependency conflicts  
- **Portability**: Easy to move between environments  
- **Efficiency**: Lightweight compared to virtual machines (VMs)  
- **Version Control**: Track container versions  

### Key Concepts

| Concept | Description |
|----------|--------------|
| **Image** | Recipe for an app (includes code, runtime, libraries, OS) |
| **Container** | Running instance of an image |
| **Dockerfile** | Instructions to build an image |
| **Docker Compose** | Tool to run multi-container apps with one command |
| **Volume** | Persistent storage shared between container and host |
| **Network** | Communication channel between containers |

### Dockerfile Example
```dockerfile
FROM node:20-alpine          # Base image
WORKDIR /app                 # Set working directory
COPY package*.json ./        # Copy dependency files
RUN npm install              # Install dependencies
COPY . .                     # Copy app source
EXPOSE 3000                  # Expose port
CMD ["npm", "start"]         # Run app
````

### Docker Commands

```bash
docker build -t app-name .           # Build image
docker run -p 3000:3000 app-name     # Run container with port mapping
docker ps                            # List running containers
docker images                        # List images
docker stop <container-id>           # Stop container
docker compose up --build            # Build and run multi-container app
```

### Docker Compose Example

```yaml
services:
  web:
    build: .
    ports:
      - "3000:3000"
    volumes:
      - .:/app
      - /app/node_modules
    command: npm run dev
```

---


