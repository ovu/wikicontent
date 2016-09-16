Docker containers with network connection
=========================================

A new container is by default not able to share any ports to the outside.

Here we will see how to allow network connection to the containers.

# Open a port from the container

Use the -p option in the docker command line.

docker run -ti -p <LOCAL PORT>:<CONTAINER PORT> <IMAGE NAME> /bin/bash

In order to verify that the port mapping is working run the command:

docker ps

Another alternative for verifying the is looking at the NAT tables:

iptables -L -t nat

What is the ip address that is shown in the iptables?

It is the ip of the container.

Executing the following command will show you all the interfaces in the local computer:

ip address show

In the result list you will see a docker bridge called docker0. It will be used for doing the mapping.
