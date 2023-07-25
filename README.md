## The Data Modelling Process:
1. Gather requirements
2. Conceptual Data Modelling
3. Logical Data Modelling

## Important Feature of RDBMS:
**Atomicity** - Whole transaction or nothing is processed  
**Consistency** - Only transactions abiding by constraints & rules is written into database  
**Isolation** - Transactions proceed independently and securely  
**Durability** - Once transactions are committed, they remain committed  

## When to use Relational Database?
### Advantages of Using a Relational Database
* Flexibility for writing in SQL queries: With SQL being the most common database query language.
* Modeling the data not modeling queries
* Ability to do JOINS
* Ability to do aggregations and analytics
* Secondary Indexes available : You have the advantage of being able to add another index to help with quick searching.
* Smaller data volumes: If you have a smaller data volume (and not big data) you can use a relational database for its simplicity.
* ACID Transactions: Allows you to meet a set of properties of database transactions intended to guarantee validity even in the event of errors, power failures, and thus maintain data integrity.
* Easier to change to business requirements

### Importance of Relational Databases:
* Standardization of data model: Once your data is transformed into the rows and columns format, your data is standardized and you can query it with SQL
* Flexibility in adding and altering tables: Relational databases gives you flexibility to add tables, alter tables, add and remove data.
* Data Integrity: Data Integrity is the backbone of using a relational database.
* Structured Query Language (SQL): A standard language can be used to access the data with a predefined language.
* Simplicity : Data is systematically stored and modeled in tabular format.
* Intuitive Organization: The spreadsheet format is intuitive but intuitive to data modeling in relational databases.

## When to use NoSQL Database?
### Advantages of Using a NoSQL Database
* Need to be able to store different data type formats: NoSQL was also created to handle different data configurations: structured, semi-structured, and unstructured data. JSON, XML documents can all be handled easily with NoSQL.
* Large amounts of data: Relational Databases are not distributed databases and because of this they can only scale vertically by adding more storage in the machine itself. NoSQL databases were created to be able to be horizontally scalable. The more servers/systems you add to the database the more data that can be hosted with high availability and low latency (fast reads and writes).
* Need horizontal scalability: Horizontal scalability is the ability to add more machines or nodes to a system to increase performance and space for data
* Need high throughput: While ACID transactions bring benefits they also slow down the process of reading and writing data. If you need very fast reads and writes using a relational database may not suit your needs.
* Need a flexible schema: Flexible schema can allow for columns to be added that do not have to be used by every row, saving disk space.
* Need high availability: Relational databases have a single point of failure. When that database goes down, a failover to a backup system must happen and takes time.

## OLAP vs OLTP:
---
* Online Analytical Processing (OLAP):
Databases optimized for these workloads allow for complex analytical and ad hoc queries, including aggregations. These type of databases are optimized for reads.

* Online Transactional Processing (OLTP):
Databases optimized for these workloads allow for less complex queries in large volume. The types of queries for these databases are read, insert, update, and delete.

