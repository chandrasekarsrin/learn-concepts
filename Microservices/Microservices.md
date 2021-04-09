# Microservices Principles
## Reference:
https://www.developertoarchitect.com/lessons/
http://www.devopsbookmarks.com/service-discovery

Next watch: https://www.youtube.com/watch?v=CZ3wIuvmHeM
## Agenda:
- Tools
- Microservice topology
- share nothing architecture
- service components
- api layer overview
- hybrid architectures
- migration patterns
- service identification
- service design(templates)
- service communication(REST, Messaging, GRPC)
- Orchestration
- data and caching patterns (distributed vs replicated cache)

## Tools
- cloud stack, kubernetes, docker
- chef and ansible(recommended)
- Service registry: consul or zookeeper
- hystrix
- spring boot or dropwizard
We get struck in having so much technologies. there are too many choices. we can tangled up in the wheels of technologies.

- microservices if not done right its a painful design.

Most common stack:
- spring boot, prometheus, consul, docker, kubernetes


## Microservice Topology:
TOP to BOTTOM
Client requests
|
API layer
|
microservices(every microservices uses its own data. not database)
|
data

- Communication between microservices is majoritly REST or messaging.
    - can i use SOAP? ofcourse, but you dont have enough tools, frameworks to implement the same.
- protocol aware hetrogenous interoperability. Services can be written in any language but communication protocol should be same.
- no middle ware component for communication. There is no ESP, integration hub, enterprise service bus.
- Why microservices?
    - agility
    - testability
    - deployability
    - scalability
    - availability
- tradeoffs of microservices. there are ways to address this.
    - performance issues(latency)
    - complexity
    - cost
    - reliability
    - feasibilty

Service
- fine grained single purpose service and does one thing really really well.
- 100s to 1000s of microservices can be there.
- Containerization
- devops is required(service registry, security and compliance, load balancing, deployment, inter service communication, etc)
- public api services, infra services, adapter services

Bounded context:
- a customer wishlist. 
- well defined APIs. 

Serverless vs microservices:
- microservice without state.

What size should a microservice should be?
- purpose : 
    - what is it doing? fine grained single prupose.
    - Cohession: degree and manner to which operations and service are related to one another.
    - Example: customer service
        - customer demographics
        - customer notification
        - customer comments
    - verbalize your function and identify conjunction to find out cohession.
- transactions
    - acid transaction is not possible.
    - service consolidation should be done to achive acid transactions.
- choreography
    - no conductor. 
    - this is what microservices should be.
    - if there is too much of dependency between services. 
    - try to reduce inter dependency

LATENCY PROBLEM Get All customer data:
- 

Share nothing architecuture:
- not possible. share as little as possible.
- for example: common library is required to be shared(logging, security)
- have small shared jars. determine based on volatility and functionality of the module.

## CQRS: Command query responsiblity seggregation
    - pattern of architecture.
    - reads and writes in different optimized databes
    - syncronizing is really challenge.

write service(cache and database)
- writes in database after commit updates the cache.
- cache replicate the data to read service cache.
read service(cache)


## Challenges Netfix faced and solutions
- Edge Services: zuul (proxy), API gateway service
- Middle tier: product service, platform services(routing, crypto, etc), persistence(cache)

Dependency
    - intra
scale
variance

