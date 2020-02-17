# Docker Quickstart Notes

## Part 1: Orientation and Setup

- "Fundamentally, a container is nothing but a running process with encapsulation features"
- The image is what contains the filesystem and everything else required to operate
- Major difference between a VM and a container is that the container shares the kernel of the host machine with other containers, through the use of Docker, whereas a VM runs the whole guest OS with virtual access to the kernel through the hypervisor
-- This is somewhat unclear: when you create an image, it still has the OS - does it just get what else it needs from the host OS? Is this why it can be lightweight? What is the difference between how Docker and a hypervisor work?
--- Great resource that cleared this up: <https://blog.mikesir87.io/2017/05/docker-is-not-a-hypervisor/>
- In the tutorial, we run `docker run hello-world` which downloads the 'Hello World' image and runs it, we can then see what images we have downloaded with a `docker image ls`
- `docker container ls` will show current running containers, and appending the `--all` flag will show all containers regardless if they're running or not

## Part 2: Build and Run Your Image

- Starts by cloning a repo and then an explaination of the Dockerfile
- Dockerfile
-- Describes how to create the filesystem by defining the 'base' image (the FROM)
-- Describes where all of the actions will be taking place (the WORKDIR)
-- Describes any files being copies to the container (COPY)
-- Describes any ports, etc. that will be exposed (EXPOSE)
-- Describes what commands will be run once the container starts (CMD)
- The image must first be built with the `docker image` command - this will gather everything and perform the actions stored in the Dockerfile
- Then, we use a `docker run` to run the container we just build, while publishing the expose ports, assigning it a name, and also running it in headless (detach) mode

## Part 3: Share Images on Docker Hub

- We will now be publishing the image we just created onto Docker Hub
- Prior to this we have to `tag` our image (using `docker image tag`). Seems like this is for sorting/sharing/indexing.
- Finally, we use `docker image push` to publish the image to our Docker Hub repo we created. 
