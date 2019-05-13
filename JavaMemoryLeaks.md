## How to diagnose a memory leak in the JVM, and then collect a GC dump.

It is assuming the leak is in a Yarn server running a flink session.

* Add SSH key, enable agent forwarding.
* assume YARN user: =su -i yarn=
* =jps= gives us a list of running java processes, of which we need the
   session-cluster entry point.
* First, trigger GC so the things we want are actually dumped: =jcmd <pid>
   GC.run=, where PID is the number you got from =jps=.
* Command for the dump is =jcmd <pid> GC.heap-dump /tmp/dump.hprof=
* =chown= the dump created to =hadoop= so you can SCP it off the machine
* Go back to the master node and =scp= the dump from the child node to the master
   node.
* =scp= the dump from the master to your machine.

* Analyzing the dump
An example for a program to analyse the dump is =VisualVM=, from Oracle,
available for free. [[https://visualvm.github.io/][(Link to site)]]

/(The parts after this are more of a specific account of what happened to debug
this leak than they are meant as general guide)/

1. After this, in VisualVM, first search for "UserCode", which lists the Class
   Loaders from flink responsible for loading our JARs.
3. Click "GC Root" on the held class loaders, which gives you a reference stack
   of where it is held.
