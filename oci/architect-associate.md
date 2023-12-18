# OCI Architect associate certification

# OCI overview

Cloud regions  (geo locations)
    - availability domains(data centres)
    - fault domains(grouping of hardware to provide high availability, they will not share single point of failure hardware)
        - use data gaurd for database replication
Customer @ cloud 
multicloud (with azure)
hybrid cloud

- core infra (compute(VMs, containers, OS VMWare), storage, networking)
- database services (Oracle databases, distributed and open source databases)
- data and AI 
    - Big data
    - Data flow (spark)
    - Data catalogue
    - Data Integration(ingestion and ETL)
    - Data science and data assistant
    - Messaging(managed kafka)
- analytics
- Governance and administration
    - cloud ops
    - security
    - observability
- developer services
- application services

80 services

Choosing region:
- choose a region closer to user for highest performance.
- data residency requirements
- service availability


# Free tier account
- always free
- 300$ credit

# Identity and access management
- Authn(who) & Authz(what permissions you have)
- role based access control
- domain
    - container for users and groups
    - way to segregate users, groups and dynamic groups
    - you will get a default domain
    - can also be attached to any compartment
    - oracle apps premium
        - saas, paas
        - on perm oracle apps
    - premimum domain type
        - oracle apps
        - on perm oracle apps
        - non oracle apps
    - External user
        - consumer and non employee use case
        - social login
- compartments
    - logically isolate resources and secure them
    - organize your resources
    - available across regions. its a tenancy level resource
    - nested compartments(6 levels deep)
    - set quotas and budgets for compartments
- users
- groups
    - users with same requirements
    - example: administrators
- policies
    - all the child compartments inherits the policies in the parent compartment
    - where you are attaching(compartment) the policy decides who can modify/delete it.
    - when you are writing policies to the nested compartment use : operator to specify the path of the compartment.
    - conditional policies
        - fine grained policies
        - supports =, !=
        - multiple conditions(any and all). any is logical OR. all is logical AND.
        - string values. (single quotation) the comparison also happens with pattern. example: /HR*/
        - request
            - attributes in request itself
            - example: request.user.id
        - target
            - attributes about target of request
            - example: for update user operation,  target.user.id
- Quotas
    - service limits are set by oracle. quota limits are set by tenancy administrator.
    - set, unset, zero

OCID
 - oracle assigned identifier
 - every resource have a unique id.

Principal
    - identity allowed to access OCI resources
    - IAM Users / Resource principals

Authentication
 - username/password
 - API signing keys
 - Auth tokens (every user can create 2 tokens)
 
Tenancy
  - root compartment

Network resources
- specific vpn ip address or public ip address
- write a policy. request.networkSource.name='corpnet'

Tag based compartments
- helps to provide access across compartments, groups, resources.
- Tags on requesting resource:
    - request.principal.group.tagNamespace.tag='value'
- Tags on target resource:
    - target.resource.tagNamespace.tag

- dynamic groups
    - we write matching rules.
    - allows to group below principals.
    - infrastructure principal: example instance principal
    - stacked principal: Oracle database
    - ephemeral principal: oci functions 

Region level access:
    - target.region.name
# Network - VCN
- Region is localized geo graphic area.
- AD is data centre
- FD is grouping of hardware inside AD. Each AD will have 3 FDs.

Virtual cloud network
- virtual representation of a physical n/w.
- regional service
- Oracle recommends RFC1918 when choosing CIDR blocks but customer can choose any CIDR blocks
- CIDR blocks can be modified at later point of time.
- addressing, subnets, routers(we call it as gateways), route tables, firewalls and connectivity

Internet gateway
- public subnet. both ingress and egress

NAT gateway
- private subnets can only have nat and service gateways.
- only egress

Service gateway
- provides connectivity to Oracle Services network

Local peering gateway
- communication between VCNs

Dynamic routing gateway
- communication to on permises

CIDR
- Classless Inter domain routing
- CIDR prefix looks A.B.C.D/x. 
    - 8 bytes each and 32 bits.
    - A.B.C.D : network address
    - /x : network prefix / mask
    - /16 is usually be the number for VCN
- Subnetting allows to divide n/w(CIDR) to smaller networks
    - /24 is usualy the number for subnet

Example CIDR anotation: 192.168.1.0/24
    - First 24 bits are n/w address
    - last 8 bits is for hosts.
    - Network ID: 192.168.1.0 : n/w address
    - First Host: 192.168.1.1 
    - Last Host: 192.168.1.254 : last address
    - Last Host: 192.168.1.255 : broadcast address
    - In OCI n/w address, first host and broadcast address (3 hosts) are reserved.
    - The range will equate to 192.168.1.0 - 192.168.1.255
    - subnet mask for /24: 24 bits 1 and last 8 bits 0. This will be anded with the ip address to find out the subnet address.
    
/24 : 1 subnet  (0 bit is reserved from D for subnets)
/25: 2 subnets (1 bit is reserved from D for subnets)
/26 : 4 subnets (2 bits)
/ 27: 8 subnets (3 bits)

RFC1918:
- these are resrvered address for private network
- RFC recommendation:
    - 10.0.0.0/8
    - 172.16.0.0/12
    - 192.168.0.0/16
- OCI range should be between /16 - /30
    - max of 65,536 IP addresses
- Customers can use ip address outside of rfc recommendation.

Subnets
    - AD specific
    - regional subnet
    - security lists, route table, dhcp options (if not chosen then the default vcn options are taken)

private subnet:
 - all resources will only have private IP.
 
public subnet
 - can optionally have public ip address.
 

Security list
- set of firewall rules associated with subnet
- you can define rules with stateful or stateless
- is enforced at VNIC level
- ingress and egress rules
- stateful (any rule that you write will automatically have both ingress and egres.) ICMP irrespective of stateful or stateless we need rules for both ingess and egress

Network security groups
- virtual firewall for a set of cloud resources all have same security posture
- can be attached directly to vnics.
- not created by default 
- oracle recomments NSGs instead of SL. Because it provides fine grained details. we can use SL along with NSG.


# Network - Connectivity

# Network - Load Balancer


# Database management systems

