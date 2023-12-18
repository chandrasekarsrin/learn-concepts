# Linux Networking namespaces

Reference: 
https://dev.to/polarbit/how-docker-container-networking-works-mimic-it-using-linux-network-namespaces-9mj
https://linuxhint.com/use-linux-network-namespace/

- Linux namespaces are linux kernel features allowing us to isolate network environments through virtualization.
- Using networking namesapces we can create a separate 
    - networking interface
        - physical network interface
            - a n/w hardware device such as NIC(Network inteface card)
        - virtual network interface
            - does not represent a hardware device but is linked to a network device. 
    - route tables
    - ip tables

veth pair:
- is a kind of network cable which has two vnic's at both ends.
- it connects docker network namespace with to other devices which are also connected to same bridge.

connecting 2 namespaces:
- put one of the veth in one namespace
- and other end of the veth in another namespace to connect them