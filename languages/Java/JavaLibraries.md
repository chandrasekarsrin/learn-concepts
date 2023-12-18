# Different Libraries Available

## General Libraries
### Gauva
- developed by google.
- has new collection types(multiset, multimap, etc)
- has immutable collections.
- graph library
- utilities of concurrency, IO, hashing, caching primitives, strings and more

## Dependency Injection
### Why do we need dependency injection?
- avoids direct compile time dependency to improve testablity.
- dependencies are sometiems hidden. explicitly declaring the dependencies in constructor is always better.
- core principle is to seperate behaviour from dependency resolution.

### Guice
- injection framework developed by google. 

- to
- toInstance
- @Provides
### Spring Dependency injection

### Dagger 2
- developed by google
- fully static and compile time.
- fast and reflection free.


## Why private final instance variables
- avoids state leak since there is no state update, we dont change values.
- avoids null pointer exception among multiple threads. because once value is set it is available to all the threads.