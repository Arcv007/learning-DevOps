# History and Working of Docker
This section explains how Docker came into existence, how it evolved, and how Docker works internally. The explanation is kept simple and beginner-friendly.
---
## History of Docker
Before Docker, applications were deployed directly on servers or inside virtual machines. This caused multiple problems:
* Environment mismatch between development and production* Heavy virtual machines consuming more resources* Slow provisioning and scaling
To solve these problems, container-based solutions started gaining attention.
---
## How Docker Was Developed
* Docker was introduced in **2013** by **Solomon Hykes*** Initially released as an open-source project by a company called **dotCloud*** Docker was first built on top of **LXC (Linux Containers)*** Later, Docker developed its own container runtime for better performance and ease of use
Docker simplified containers by:
* Providing a developer-friendly CLI* Introducing Docker images and Dockerfiles* Making containers easy to build, share, and run
This made container technology popular worldwide.
---
## Why Docker Became Popular
Docker became popular because it:
* Solved the "works on my machine" problem* Was lightweight compared to virtual machines* Allowed fast application deployment* Made microservices architecture practical* Integrated well with DevOps tools
---
## What Problem Docker Solves (Real Scenario)
**Without Docker:**
* App works on developer laptop* Fails on testing or production server* Different OS versions, libraries, and configurations
**With Docker:**
* App runs inside a container* Same container runs everywhere* No environment mismatch
---
## How Docker Works (High-Level)
Docker works using a **client-server architecture**.
Main components:
* Docker Client* Docker Daemon* Docker Images* Docker Containers* Docker Registry
---
## Docker Architecture Overview
1. **Docker Client**
   * Used by users to run Docker commands   * Commands like `docker run`, `docker build`
2. **Docker Daemon (dockerd)**
   * Runs in the background   * Manages images, containers, networks, and volumes   * Receives commands from Docker Client
3. **Docker Images**
   * Read-only templates   * Used to create containers
4. **Docker Containers**
   * Running instances of images   * Isolated environments for applications
5. **Docker Registry**
   * Stores Docker images   * Example: Docker Hub
---
## How Docker Works (Step-by-Step)
Example command:
```bashdocker run nginx```
What happens internally:
1. Docker client sends command to Docker daemon2. Daemon checks if `nginx` image exists locally3. If not found, image is pulled from Docker Hub4. Docker creates a container from the image5. Container starts and runs Nginx
---
## How Containers Work Internally
Docker uses Linux kernel features:
### Namespaces
* Provide isolation* Separate process IDs, network, filesystem
### Cgroups (Control Groups)
* Limit CPU, memory, and disk usage* Prevent one container from using all resources
Together, namespaces and cgroups make containers isolated and efficient.
---
## Docker vs Traditional Deployment
**Traditional:**
* Install OS → Install runtime → Install app* Hard to manage dependencies
**Docker-based:**
* Build image once* Run anywhere* Easy version control and rollback
---
## Summary
* Docker was created to simplify application deployment* It evolved from LXC to a full container platform* Docker uses client-server architecture* Containers share the host kernel* Docker is a core technology in modern DevOps
---
