# Database

- connection pooling(UCP, hikari, c3po, apache DBCP)
    - connecting to a database is a expensive operation hence connection pooling is required.
    - UCP - Universal connection pool is the oracle implementation of connection pool. 

- Connection object should not concurrently used by multiple threads.
- use connection pooling to get and release connection. This is promote reuse of connections and optimize on the performance.


# Indexes

Reference: https://stackoverflow.com/questions/38552550/create-sql-indexes-for-complex-filtering

## Multiple columns
firstname, lastname, state, age, gender 

### Some key points
- We should not create index for columns with low cardinality. For example, gender is having only male and female. The index in this case will not be useful. 
- There are 2 ways that you can create indexes for multiple columns:
    - composite index with all the columns. 
        - One single index is used and straight away result is returned.
        - It will be slightly faster
    - individual column index
        - In this case each condition in the where clause will be separately queried. The end result will be merged with all of the queries.
        - In this case it will be slightly slower than the compositie index.
    - one of these 2 options should be chosen based on the query pattern:
        - If the only pattern of query is by including all the fields then we can go with that index.
        - But if we need multiple fields to be queried separately then we can go with individual index.

- We can create covering index if required. Covering indexes are created when the table contains 100 columns but only 4 of them are often queried. We can index all the 4 columns to avoid the disk operaiton. Otherwise to get a entry the compiler needs to read all the 100 columns for all the fields. 

- We usually create indexes for the foriegn key and the ones in the where clause.

# Joins

Inner join vs outer join needs to be chosen carefully.

Lets say, Tabe a and table b needs to be joined. If table a is having less number of rows that needs to be matched in table b then left outer join is better as we need to match less number of rows.