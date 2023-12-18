# Java 8 - 17 upgrade

- some releases will be long term support.
- every 3 years a new LTS will come
- Java 8,11,17 are LTS

# Record
- immutable with final fields
- it includes constructors, equals, hascode, etc..
record Point(int x, int y) {}

# instanceOf

if(obj instanceOf String s) {
 // use s
} else {
  // obj is not insance of String
}

# Sealed types
- if a class is sealed then only permitted classes can extend it.

class sealed Shape permits Square, Circle {
}

# switch pattern matching
- instance of.
- some 

# Helpful null pointer exception
- exactly point out which field is null.

# java modules
- introduced in jdk 9
- jdk is modularized using modules.
- so jdk can just be built with smaller subsets with the dependencies that we only need.
- it helps containerized applications as it will reduce size massively.
- jlink should be used to do that

# jdeps (java 9)
- java dependency analyzer

# java packager (java 16)
- generate native packages like .dem, .rpm, etcc
- we can use it even if we use reflection since it packages java, jvm and required dependencies together and builds this package.

# Java single file launch
- we can run without compiling if you just have one file.
- we can add shebang and convert it into script

# Flight recorder

# Libraries
## Loom
## Collection factories (jdk 9)
- create unmodifiable collections directly


# String bytes performance
- To read

# Garbage collectors
- there are 2 garbage collectors. G1 and ZGC.
- G1 is ideal and balanced.
- ZGC is aggressive with less pauses but throughput is less

# Loom
- massive rewrite of concurrence model used in jdk.
- Java threads provide us platform independant way to write parallel code.
    - provides nice way of abstraction and converts into os threads 
    - readable stack trace
    - however its heavy weight since it is using os threads.

- if you are work load is very light weight then you can use loom.
    - virtual threads are light weight threads.
    - virtual thread stacks are stored as continuations in heap.
    - there is no change in Java Threads API and in the background JVM will do the scheduling with actual OS threads.