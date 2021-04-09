# Microservice Design patterns

## Orchestrator
- its almost like orchestra
- get all data for customer '123' requires to get data from multiple microservices.
- add a microservice orchestrator microservice for each use case.
    - we have an owner for this business model.
    - easy to changes
- another aggregator pattern is available which you can see below.


## Aggregator 
- there are 140 microservices.
- a API call that needs data from all of these microservices.
- orchestration may not work for these usecases.
- deploy one new service called aggregator. : this will aggregate all the data.
- everytime there is a change in any of the microservice each service puts a data into the queue. 
- aggregator service will read the data from queue and update the aggregated data.
- cross cutting service. for example to check limits you can use interservice communication to aggregator to get aggregated data and check limits.
- data consistency can be taken care by data gaurantees with help of message broker(atleast once gaurantee). Another way is to use checksum and reconcillation.


## Gateway pattern
- gets client requests in REST and talks to a mainframe system through OTMA protocol.
- for each operation with mainrame system have one microservice.
    - when we convert functionality from cobol to java we have one microservice for this functionality. the gateway will become functional service.
- there will be one interface for the external system.
- apache camel is a embedable broker. build route to do all the transformation.

## API Gateway (all cross cutting concerns)
- security
- request id generation to support traceblity
- service discovery
- auditing
- metrics based on response time.

- if we plan to do orchestration here  then it will have lot of coupling.


## Choreography