Docker persistent storage
=========================

Every docker container is ephimeral. It means the changes we make in a container are lost when the container is stopped.

In order to solve this issue docker provides the possibility to mount volumes in the containers.

# How to mount a volume in a container

docker run -ti -v /myVolume --name=myNewContainer <IMAGE NAME> <INITIAL COMMAND>

It will create a volume in the container in the location /myVolume

Any change made inside the directory /myVolume will be persisted.

The data stored in the volume by default is saved in /var/lib/docker/volumes

# Mount an specific directory in the container

docker run -ti -v <LOCAL DIR>:/sharedDir --name=<CONTAINER NAME>  <IMAGE NAME> <INITIAL COMMAND>

It will mount your local directory in the directory /sharedDir in the container. 

For fedora and CentOS it is required to use the flag :Z or :z after the volume to give the access rights on the local directory.

For example:

docker run -ti -v <LOCAL DIR>:/sharedDir:Z --name=<CONTAINER NAME>  <IMAGE NAME> <INITIAL COMMAND>
