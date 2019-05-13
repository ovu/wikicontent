* How to diagnose a memory leak in the JVM, and then collect a GC dump.

1. Add SSH key, enable agent forwarding.
2. Connect to crawler stream in environment of your choosing
3. Go to the node where the job manager in question is running
   (Akka/Chrome). This can be found in the flink UI.
4. assume YARN user: =su -i yarn=
5. =jps= gives us a list of running java processes, of which we need the
   session-cluster entry point.
5. First, trigger GC so the things we want are actually dumped: =jcmd <pid>
   GC.run=, where PID is the number you got from =jps=.
6. Command for the dump is =jcmd <pid> GC.heap-dump /tmp/dump.hprof=
7. =chown= the dump created to =hadoop= so you can SCP it off the machine
8. Go back to the master node and =scp= the dump from the child node to the master
   node.
9. =scp= the dump from the master to your machine.

* Analyzing the dump
An example for a program to analyse the dump is =VisualVM=, from Oracle,
available for free. [[https://visualvm.github.io/][(Link to site)]]

/(The parts after this are more of a specific account of what happened to debug
this leak than they are meant as general guide)/

1. After this, in VisualVM, first search for "UserCode", which lists the Class
   Loaders from flink responsible for loading our JARs.
2. Class loader amount should equal the amount of "finished jobs" and "running
   jobs" in Flink
3. Click "GC Root" on the held class loaders, which gives you a reference stack
   of where it is held.
