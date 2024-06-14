# **Docker 101 | We Will learn about Docker: Installation, Usage, and Advantages**

Docker is a platform that allows developers to automate the deployment of applications inside lightweight, portable containers. Containers include everything an application needs to run, such as libraries, system tools, and code, ensuring consistency across multiple environments.

## **Why Use Docker?**

### **Advantages of Docker**

1.  **Portability**: Containers run the same regardless of the environment.
2.  **Efficiency**: Containers share the host OS kernel, making them lightweight.
3.  **Scalability**: Easily scale applications across multiple servers.
4.  **Isolation**: Ensures that applications are isolated from each other.

### **Alternatives to Docker**

| Alternative            | Description                                                                                    |
| ---------------------- | ---------------------------------------------------------------------------------------------- |
| Podman                 | A daemonless container engine for developing, managing, and running OCI containers.            |
| LXC (Linux Containers) | Operating-system-level virtualization environment for running multiple isolated Linux systems. |
| rkt (Rocket)           | A security-focused container runtime.                                                          |

### **Why Docker is Better**

- **Ease of Use**: Simplified CLI and setup process.
- **Vast Ecosystem**: Extensive community support and a large number of pre-built images on Docker Hub.
- **Integration**: Seamless integration with CI/CD pipelines and various cloud services.

## **How to Install Docker**

### **On Linux**

```
# Update existing list of packages
sudo apt update

# Install prerequisite packages
sudo apt install apt-transport-https ca-certificates curl software-properties-common

# Add Docker’s official GPG key
curl -fsSL <https://download.docker.com/linux/ubuntu/gpg> | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# Add Docker APT repository
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] <https://download.docker.com/linux/ubuntu> $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Update package database with Docker packages from the new repository
sudo apt update

# Install Docker
sudo apt install docker-ce

# Verify Docker installation
sudo systemctl status docker
```

### **On Windows/Mac**

1.  Download Docker Desktop from Docker's official website. ()
2.  Run the installer and follow the installation steps.
3.  Verify installation by running `**docker --version**` in your command prompt.

## **Basic Docker Usage**

### **CLI Commands to Run a Container**

### **Step 1: Pull a Docker Image**

```
docker pull ubuntu
```

### **Step 2: Run a Container**

```
docker run -it ubuntu --name ubuntu
```

### **Step 3: Access Container Shell**

```
docker exec -it ubuntu bash
```

### **CLI Commands to Run an Application from Scratch**

### **Step 1: Create Project Directory**

```
mkdir fastapi_project
cd fastapi_project
```

### **Step 2: Create the FastAPI Application**

Create a file named `**app.py**` with the following content:

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"Hello": "World"}

@app.get("/items/{item_id}")
def read_item(item_id: int, q: str = None):
    return {"item_id": item_id, "q": q}
```

### **Step 3: Create Requirements File**

Create a file named `**requirements.txt**` with the following content:

```
fastapi
uvicorn
```

### **Step 4: Create a Dockerfile**

Create a file named `**Dockerfile**` with the following content:

```

Copy code
# Use an official Python runtime as a parent image
FROM python:3.9

# Set the working directory in the container
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Make port 80 available to the world outside this container
EXPOSE 80

# Run app.py when the container launches
CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "80"]
```

### **Step 5: Build the Docker Image**

```
docker build -t fastapi-app .
```

### **Step 6: Run the Application**

```
docker run -p 8000:80 fastapi-app
```

### **Step 7: Access the Application**

Open your web browser and navigate to `**http://localhost:8000**`. You should see the JSON response `**{"Hello": "World"}**`.

### **Common Docker Commands**

| Command                                   | Description                            |
| ----------------------------------------- | -------------------------------------- |
| docker --version                          | Check the Docker version installed.    |
| docker pull \<image_name>                 | Pull an image from Docker Hub.         |
| docker run \<image_name>                  | Run a container from an image.         |
| docker ps                                 | List running containers.               |
| docker stop \<container_id>               | Stop a running container.              |
| docker rm \<container_id>                 | Remove a container.                    |
| docker rmi \<image_name>                  | Remove an image.                       |
| docker exec -it \<container_id> /bin/bash | Access a running container.            |
| docker-compose up                         | Start containers using Docker Compose. |
| docker-compose down                       | Stop containers using Docker Compose.  |

## **Conclusion**

Docker revolutionizes the way applications are developed, shipped, and run. Its portability, efficiency, and scalability make it a preferred choice for developers. While there are alternatives like Podman, Docker's ease of use and vast ecosystem make it an excellent choice for both beginners and experienced developers.

## Feel free to reach out if you have any questions or need help getting started!

Github: [https://0xaungkon.github.io/](https://0xaungkon.github.io/)

Linkedin: [https://www.linkedin.com/in/aungkon-malakar/](https://www.linkedin.com/in/aungkon-malakar/)

Facebook: [https://www.facebook.com/0xAungkon/](https://www.facebook.com/0xAungkon/)
