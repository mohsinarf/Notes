
docker ps

docker log <name> -f

docker image ls


# Useful Docker Commands

## 1. Basics
```bash
# Check Docker Version
docker --version
docker version

# Display System-Wide Information
docker info
# List Available Images
docker images
docker image ls

# Pull an Image from Docker Hub
docker pull <image_name>:<tag>

# Remove an Image
docker rmi <image_name_or_id>

# Search for Images
docker search <keyword>

# List Running Containers
docker ps

# List All Containers (Including Stopped)
docker ps -a

# Start a Container
docker start <container_id_or_name>

# Stop a Container
docker stop <container_id_or_name>

# Remove a Container
docker rm <container_id_or_name>

# Run a New Container
docker run <image_name>

# Example: Run an Interactive Shell
docker run -it ubuntu
# List Volumes
docker volume ls

# Create a Volume
docker volume create <volume_name>

# Remove a Volume
docker volume rm <volume_name>
# List Docker Networks
docker network ls

# Inspect a Network
docker network inspect <network_name>

# Create a New Network
docker network create <network_name>

# Remove a Network
docker network rm <network_name>

# Inspect a Container
docker inspect <container_id_or_name>

# View Logs of a Container
docker logs <container_id_or_name>

# Attach to a Running Container
docker attach <container_id_or_name>

# Execute a Command in a Running Container
docker exec -it <container_id_or_name> <command>

# Example: Open Bash in a Container
docker exec -it <container_id_or_name> bash

# Remove All Stopped Containers
docker container prune

# Remove Unused Images
docker image prune

# Remove Unused Data (Images, Containers, Volumes, Networks)
docker system prune

# Start Services in a docker-compose.yml File
docker-compose up

# Start Services in Detached Mode
docker-compose up -d

# Stop Services
docker-compose down


