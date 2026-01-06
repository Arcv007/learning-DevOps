# Docker Basic Commands
This section covers the most commonly used Docker commands. These are the foundation commands you will use daily while working with Docker.
---
## docker run
Used to **create and start a container** from an image.
```bashdocker run nginx```
What happens:
* Checks if the image exists locally* Pulls the image if not available* Creates a container* Starts the container
---
## docker ps
Lists **running containers only**.
```bashdocker ps```
Useful to check:
* Container ID* Image name* Status* Port mapping
---
## docker ps -a
Lists **all containers**, including stopped ones.
```bashdocker ps -a```
Use this when:
* Container is stopped* You want to remove old containers
---
## docker stop
Stops a running container gracefully.
```bashdocker stop <container_id>```
Example:
```bashdocker stop 3f2a9c1b2d```
---
## docker rm
Removes a **stopped container**.
```bashdocker rm <container_id>```
To remove multiple containers:
```bashdocker rm id1 id2 id3```
Note: Container must be stopped before removal.
---
## docker images
Lists all Docker images available locally.
```bashdocker images```
Shows:
* Repository* Tag* Image ID* Size
---
## docker rmi
Removes a Docker image.
```bashdocker rmi <image_id>```
Example:
```bashdocker rmi nginx```
Note:
* Image cannot be removed if it is used by a container
---
## docker pull
Downloads an image from Docker Hub **without running it**.
```bashdocker pull nginx```
Used when:
* You only want the image* You want to control when containers start
---
## docker pull vs docker run
| docker pull          | docker run                  ||
 --------------------- | ---------------------------- ||
 Downloads image only  | Downloads + starts container ||
 No container created  | Container created            ||
 Manual start required | Auto start                   |
---
## docker exec
Used to **run a command inside a running container**.
```bashdocker exec <container_id> <command>```
Example:
```bashdocker exec -it mycontainer bash```
Common use cases:
* Debugging* Checking files inside container
---
## docker run – Attach and Detach Mode
### Attached Mode (default)
```bashdocker run nginx```
* Terminal is attached to container* Logs are shown* Ctrl+C stops the container
---
### Detached Mode
Runs container in background.
```bashdocker run -d nginx```
Benefits:
* Container runs in background* Terminal remains free
---
## Summary
* `run` → create and start container* <br> `ps` → list running containers* <br> `ps -a` → list all containers*  <br> `stop` → stop container* <br> `rm` → remove container* <br> `images` → list images* <br> `rmi` → remove image* <br> `pull` → download image* <br> `exec` → execute inside container
---