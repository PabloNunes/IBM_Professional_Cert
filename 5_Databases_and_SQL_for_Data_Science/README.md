# Databases and SQL for Data Science - Summary

## Made by Pablo Nunes

----

- Introduction to DBs
  - SQL is a language used for relational databases to query data
  - Data is collection of information
  - Database is a repository of data, providing the functionality of adding, modifying and querying data.
- Cloud Databases
  - Has some benefits especially Scalability and Recovery
  - Are logical abstractions
- SQL Statements
  - There are the 5 simple statements for SQL
    - CREATE the table
    - INSERT data
    - SELECT data
    - UPDATE data
    - DELETE data
  - DDL vs. DML
  - The WHERE command help us by selecting the right statements with some condition is met
  - COUNT is a function that retrieves the number of rows that match the criteria
  - DISTINCT is used to remove duplicates from a result set
  - LIMIT is used for restricting the number of rows retrieved

- String Patterns
  - String Patterns are a tool, to help us with finding data in a database 
  - Using "where something like 'some%'"
    - % is a wildcard letter
  - Using "where number between 10 and 20"
  - Using "where country IN ('AU', 'IR')"

- Sort Result Sets
  - Order by clause
  - Can be ordered alphabetically using "order by something"
  - Can be ordered inverse alphabetically using "order by something desc"
  - Can be used numbers to represent columns
  - Can order numbers

- Grouping Result Sets
  - Some SELECT statements can have duplicate values
  - Using the distinct modifier, takes off all the duplicates
  - "SELECT DISTINCT(Country) FROM Author"
  - Can be used the Group by clause to make the count for how many times a key appear
  - We can use conditions to show the results of the Query.

- Built-in Functions
  - Most DBs come with built-in SQL functions
  - It is possible to create functions
  - Can speed up data processing
  - Reduce the amount of data to be retrieved
  - Aggregate or column functions
    - In: The entire column; Out: Single Value
    - Sum, Min, Max, Avg
  - Scalar functions: Perform operations on every input value
  - String functions
  - Most databases have built-in functions for Date and Time
  - We can use these functions with count and where

- Sub-Queries and Nested Selects
  - Sub-Queries: A query inside another query

- Working with Multiple Tables
  - Sub-Queries
  - Implicit JOIN
  - JOIN operators (INNER JOIN, OUTER JOIN)

- Python
  - SQL APIs
  - DB-API
    - Each one have a specific use
    - Connection Objects
    - Cursor Objects (Control the database)
  - IBM API
    - Using SQL
      - *var = ibm_db.exec_immediate(conn, table commands)*
      - *ibm_db.fetch_both(var)*
    - Using Pandas
      - *pconn = ibm_db_dbi.Connection(conn)*
      - *df = pandas.read_sql(table query, pconn)*
