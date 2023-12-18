# Database

- connection pooling(UCP, hikari, c3po, apache DBCP)
    - connecting to a database is a expensive operation hence connection pooling is required.
    - UCP - Universal connection pool is the oracle implementation of connection pool. 

- Connection object should not concurrently used by multiple threads.
- use connection pooling to get and release connection. This is promote reuse of connections and optimize on the performance.