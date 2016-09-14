Docker on fedora
================

Documentation based on:

https://docs.docker.com/v1.5/installation/fedora/

# Installation 

sudo dnf install docker-io

# Starting the docker daemon 

sudo systemctl start docker

sudo systemctl enable docker

Verify if Docker is running

sudo docker run -i -t fedora /bin/bash


# Avoid using sudo on docker command

sudo groupadd docker

sudo chown root:docker /var/run/docker.sock

sudo usermod -a -G docker $USERNAME


# Permission denied when mounting volume

The solution is explained on: http://www.projectatomic.io/blog/2015/06/using-volumes-with-docker-can-cause-problems-with-selinux/

By default the containers are allowed to read/execute under /usr however when mounting other directories it is necessary to give the proper permissions.

Use the z and Z options for volumen mounts (-v).


For example:

docker run -v /var/db:/var/db:z rhel7 /bin/sh

It will automatically do the chcon -Rt svirt_sandbox_file_t /var/db as described in the man page of docker-run (see man docker-run)

The difference between z and Z is that z will enable sharing between containers and Z for the specific container.

