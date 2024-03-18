# Project Name

This project demonstrates data transmission between Docker containers using netcat.

## Instructions

1. Build the client and server images using the provided Dockerfiles.
2. Create a bridge network.
3. Run the client and server containers in this network.
4. Verify data has been transmitted. 

### Example Commands

```bash
# Build the client image
sudo docker build -t nc_client -f Dockerfile_client .

# Build the server image
sudo docker build -t nc_server -f Dockerfile_server .

# Create a bridge network
sudo docker network create mynetwork

# Run the server container
sudo docker run -d --name server --network mynetwork -v $(pwd):/app nc_server

# Run the client container
sudo docker run -d --name client --network mynetwork -v $(pwd):/app nc_client

# Verify data has been transmitted
sudo docker exec  server cat received_data.txt
Hello, this is a test message



