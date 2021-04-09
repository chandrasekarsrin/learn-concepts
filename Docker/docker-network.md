# Docker containers

## bridge network
- default docker network.
- created for single host docker environment.
- user can create a bridge network and run many containers on the same bridge network.
- all the containers that are there in the same bridge network can talk to each other with container ip or name of the container.

## Overlay network
- multi host docker network
- if we want to create overlay network there are some pre requisites
    - access to key value store like consul, zookeeper, etcd, etc..
    - a cluster of hosts with connectivity to key value store.
    - properly configured docker daemon on each host in the cluster.
- docker swarm can help in creating such a cluster.
- docker cluster will generally have overlay network.
- all the containers in the cluster running on different docker host can be connected to same overlay network so that they can talk to each other with help of container ip or name of the container