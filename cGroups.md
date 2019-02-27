Cgroups
========

Control Groups in linux. Configuration tried in CentOS.

Used to control the resources used by a group of process including their child processes.

#Important config files

##/etc/cgconfig.conf


It contains the definition of the control groups.

A control group can be defined in the following way, adding the following lines to the end of the file.

group browsers {
   memory {
      memory.limit_in_bytes = "1G";
   
}

}

To see more information about the cgconfig.conf look at the man pages.

man cgconfig.conf


##/etc/cgrules.conf

It contains the definition of the processes that belong to a group.

# user:process                 controller  destination
*:/usr/bin/google-chrome-stable    memory   browsers

To see more information about the cgrules.conf look at the man pages.

man cgrules.conf


#Important commands

##cgcreate

Instead of changing the cgconfig.conf manually the command cgcreate can be used instead to create control groups.
sudo cgcreate -g memory:browsers

##cgset
Instead of changing the values inside the cgconfig.conf manually the command cgset can be used instead.
sudo cgset -r memory.limit_in_bytes=5G browsers


#Important services

cgconfig loads the configuration set in the file cgconfig.conf.

cgred loads the rules configured in the file cgrules.conf.

In order to restart the services use the following commands.

sudo service cgconfig restart

sudo service cgred start

NOTE: When restarting the services, the changes made using the commands cgcreate and cgset are lost, because these two comamnds do not write in the cgconfig.conf file.


#Testing configuration

Every cgroup has a new directory containing several files with the current configuration and statistics about the cgroup.

cat /cgroup/memory/browsers/memory.limit_in_bytes



