# Introduction to Docker
This section covers the fundamentals of Docker and containerization. These notes are written in simple language and aligned with the **KodeKloud – Docker for Absolute Beginners** course.
---
## Why do we need Docker?
Before Docker, applications were installed directly on servers or virtual machines. This often caused issues like dependency conflicts and environment mismatches.
Docker solves these problems by packaging the application along with everything it needs to run.
**Problems without Docker:**
* Works on my machine but not on server* Dependency version conflicts* Difficult setup for new developers* Slow deployments
**Why Docker helps:**
* Same environment everywhere (dev, test, prod)* Faster setup and deployment* Lightweight compared to VMs* Easy to scale and rollback
---
## What can Docker do?
Docker can:
* Package applications with dependencies* Run applications in isolated containers* Start and stop applications quickly* Run multiple apps on the same system* Simplify CI/CD pipelines
**Example:**You can run a web server without installing it manually:
```bashdocker run nginx```
This command downloads and runs Nginx in a container.
---
## What are Containers?
A container is a lightweight, isolated environment where an application runs.
It includes:
* Application code* Runtime (e.g., Java, Node.js)* Libraries and dependencies
Containers **do not include a full operating system**.They use the host machine’s kernel.
**Key points:**
* Fast to start* Uses fewer resources* Portable* Isolated from other containers
---
## Types of Containers (LXC)
Before Docker, Linux containers were managed using **LXC (Linux Containers)**.
**LXC:**
* OS-level virtualization* Uses Linux kernel features like namespaces and cgroups* Docker was initially built on top of LXC
Docker later introduced its own container runtime for better usability.
---
## What is OS and Kernel? (Docker shares the kernel)
**Operating System (OS)** has two main parts:
* **Kernel** – Core part that talks to hardware* **User Space** – Applications and tools
Docker containers:
* Share the **host OS kernel*** Do NOT have their own kernel
**Example:**
* Linux host → Linux containers only* Windows containers need Windows kernel
This is why containers are lightweight and fast.
---
## Containers vs Virtual Machines
| Containers             | Virtual Machines       || ---------------------- | ---------------------- || Share host kernel      | Each VM has its own OS || Lightweight            | Heavy                  || Fast startup (seconds) | Slow startup (minutes) || Less resource usage    | More resource usage    |
**Summary:**
* Containers = process-level isolation* VMs = hardware-level isolation
---
## Container vs Image
**Docker Image:**
* Blueprint or template* Read-only* Used to create containers
**Docker Container:**
* Running instance of an image* Can be started, stopped, deleted
**Example:**
```bashdocker pull nginx   # imagedocker run nginx    # container```
One image can create multiple containers.
---
## Docker in DevOps
Docker plays a key role in DevOps practices.
**How Docker is used in DevOps:**
* Consistent environments* Faster CI/CD pipelines* Easy integration with Kubernetes* Microservices architecture
**Typical DevOps flow:**
* Code → Build Docker Image → Test → Deploy
Docker helps teams move faster with fewer environment-related issues.
---

