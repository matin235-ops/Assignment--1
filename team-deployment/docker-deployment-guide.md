# Team Docker Deployment Guide

## Instructions for Team Members

### Prerequisites
- Docker installed on your workstation
- Access to Docker Hub
- Internet connection

### Step 1: Pull the Docker Image
```bash
# Pull the latest version
docker pull matinkhaled23/assignment1-app:latest

# Or pull a specific build version
docker pull matinkhaled23/assignment1-app:<build-number>
```

### Step 2: Run the Application
```bash
# Run the container
docker run -d -p 5000:5000 --name flask-app matinkhaled23/assignment1-app:latest

# Or run with custom port
docker run -d -p 8080:5000 --name flask-app matinkhaled23/assignment1-app:latest
```

### Step 3: Access the Application
- Open your web browser
- Navigate to: `http://localhost:5000` (or your custom port)
- You should see the "Hello, World!" Flask application

### Step 4: Manage the Container
```bash
# Check if container is running
docker ps

# Stop the container
docker stop flask-app

# Start the container again
docker start flask-app

# Remove the container
docker rm flask-app

# View container logs
docker logs flask-app
```

### Step 5: Update to Latest Version
```bash
# Stop and remove current container
docker stop flask-app
docker rm flask-app

# Pull latest image
docker pull matinkhaled23/assignment1-app:latest

# Run new container
docker run -d -p 5000:5000 --name flask-app matinkhaled23/assignment1-app:latest
```

### Troubleshooting
- **Port already in use**: Use a different port (e.g., `-p 8080:5000`)
- **Image not found**: Check if you have access to the Docker Hub repository
- **Container won't start**: Check logs with `docker logs flask-app`

### Team Member Checklist
- [ ] Docker installed and running
- [ ] Successfully pulled the image
- [ ] Container runs without errors
- [ ] Application accessible via browser
- [ ] Can update to new versions
- [ ] Document any issues encountered
