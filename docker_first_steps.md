Docker first steps
===================

# Searching images

docker search mysql


# Pulling images 

docker pull centos

It will pull several images because and image can be the composition of several images. They are called layers.

It will always pull the latest version.

It is similar to:

docker pull centos:latest

For getting a version user the tag in the name of the image:

docker pull centos:14.4


# List local images

docker images

# Starting a container from an image

docker run -ti IMAGE-NAME:TAG /bin/bash


It will run the container and open the bash inside it.

# Going back to the hosting machine

When you are inside a container and wants to go back to the hosting machine. Just press the following keyword combination:

CTRL+P+Q

# Exiting a container

CTRL+D

It will stop the container and the changes made on it are lost.

# Attach to a running container

docker attach <CONTAINER ID OR NAME> 

# Show all container even the stopped ones

docker ps -a

# Start an stopped container

docker start <CONTAINER ID OR NAME>

# Display the running processes in a container

docker top <CONTAINER ID OR NAME>

# Stop a running container

docker stop <CONTAINER ID OR NAME>

# Where are the containers stored in my local machine?

They are stored in the following directory:

/var/lib/docker/containers

# Run image deattached

docker run -d -ti --name=myImage <IMAGE NAME> <INITIAL COMMAND>
