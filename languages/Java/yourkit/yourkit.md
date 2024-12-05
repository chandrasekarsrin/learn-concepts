# your kit

# Heap dump
JVM has a built in feature to dumping Java Heap to a file in the Portable Heap Dump(PHD) binary format. The associated file extension is .phd. You can analyze thread dumps by using powerful features that Yourkit Java profiler provides for its own memory snapshots. However, due to phd format limitations not all features will be available.

eclipse mat analyzer was an amazing tool to analyse heap dump 

# Thread dump
Thread dump is a snapshot of the state of all the threads of a Java process. The state of each thread is presented in a stacktrace. Looks like it is a text file and we cant analyse it with your kit and be done manually.

Thread Dump is used to check whether you're stuck in a deadlock condition. Heap Dump is used to detect memory leaks.

There are multiple ways to generate thread and heap dump. Some of them are 
    jstack(used to take thread dump), 
    jmission control, 
    jvisual vm, 
    jcmd(recommended after java8), 
    jconsole, 

jps to get the processid of running java applications.

# Generating heap dump
jcmd <PID> Dump.heap <path>.phd

# Generating thread dump
jcmd 17264 Thread.print

## jstack to get the dump
jstack -l 80661 > sender-receiver-thread-dump.txt
# JFR
Java flight recorder is a tool for collecting diagnostic and profiling data about a running Java application. It is integrated with JVM and causes almost zero performance cost. 

jcmd 5368 JFR.start duration=60s filename=myrecording.jfr

# cpu profiling

## Integrate with IDE
- after integrating with ide.
- go to run configuration. you will see your kit profiler tab.
- select cpu profiling and the yourkit will automatically connect when you start the app.
- we can also take a cpu snapshot