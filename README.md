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
* Online Analytical Processing (OLAP):
Databases optimized for these workloads allow for complex analytical and ad hoc queries, including aggregations. These type of databases are optimized for reads.

* Online Transactional Processing (OLTP):
Databases optimized for these workloads allow for less complex queries in large volume. The types of queries for these databases are read, insert, update, and delete.

* The key to remember the difference between OLAP and OLTP is analytics (A) vs transactions (T). If you want to get the price of a shoe then you are using OLTP (this has very little or no aggregations). If you want to know the total stock of shoes a particular store sold, then this requires using OLAP (since this will require aggregations).

## Normal Forms:
### Objectives:
1. To free the database from unwanted insertions, updates, & deletion dependencies
2. To reduce the need for refactoring the database as new types of data are introduced
3. To make the relational model more informative to users
4. To make the database neutral to the query statistics

### Types of Normal Forms:

#### First Normal Form (1NF):
* Atomic values: each cell contains unique and single values
* Be able to add data without altering tables
* Separate different relations into different tables
* Keep relationships between tables together with foreign keys

#### Second Normal Form (2NF):
* Have reached 1NF
* All columns in the table must rely on the Primary Key

#### Third Normal Form (3NF):
* Must be in 2nd Normal Form
* No transitive dependencies
* Remember, transitive dependencies you are trying to maintain is that to get from A-> C, you want to avoid going through B.
    When to use 3NF:
    When you want to update data, we want to be able to do in just 1 place.

## Denormalization:
JOINS on the database allow for outstanding flexibility but are extremely slow. If you are dealing with heavy reads on your database, you may want to think about denormalizing your tables. You get your data into normalized form, and then you proceed with denormalization. So, denormalization comes after normalization.

## Normalize vs Denormalize:
Normalization is about trying to increase data integrity by reducing the number of copies of the data. Data that needs to be added or updated will be done in as few places as possible. Denormalization is trying to increase performance by reducing the number of joins between tables (as joins can be slow). Data integrity will take a bit of a potential hit, as there will be more copies of the data (to reduce JOINS).

## Star Schema:
* Simplest style of data mart schema
* Consist of 1 or more fact tables referencing multiple dimension tables

### Benefits:
* Denormalize tables, simplify queries and provide fast aggregations

### Drawbacks:
* Issues that come with denormalization
* Data Integrity
* Decrease Query Flexibility
* Many to many relationship -- simplified

## Snowflake Schema:
* Logical arrangement of tables in a multidimensional database
* Represented by centralized fact tables that are connected to multiple dimensions
* Dimensions of snowflake schema are elaborated, having multiple levels of relationships, child tables having multiple parents
* Star schema is a special, simplified case of snowflake schema
* Star schema does not allow for one to many relationships while snowflake schema does

## Data Modelling using NoSQL Databases
* NoSQL Databases stand for not only SQL databases
* When Not to Use SQL?
    * Need high Availability in the data: Indicates the system is always up and there is no downtime
    * Have Large Amounts of Data
    * Need Linear Scalability: The need to add more nodes to the system so   performance will increase linearly
    * Low Latency: Shorter delay before the data is transferred once the instruction for the transfer has been received.
    * Need fast reads and write

## Distributed Databases
* Data is stored on multiple machines
* Eventual Consistency:
Over time (if no new changes are made) each copy of the data will be the same, but if there are new changes, the data may be different in different locations. The data may be inconsistent for only milliseconds. There are workarounds in place to prevent getting stale data.
* CAP Theorem:
    * It is impossible for a distributed data store to simultaneously provide more than 2 out of 3 guarantees of CAP
    * **Consistency**: Every read from the database gets the latest (and correct) piece of data or an error
    * **Availability**: Every request is received and a response is given -- without a guarantee that the data is the latest update
    * **Partition Tolerance**: The system continues to work regardless of losing network connectivity between nodes
    * Which of these combinations is desirable for a production system - Consistency and Availability, Consistency and Partition Tolerance, or Availability and Partition Tolerance?
        * As the CAP Theorem Wikipedia entry says, "The CAP theorem implies that in the presence of a network partition, one has to choose between consistency and availability." So there is no such thing as Consistency and Availability in a distributed database since it must always tolerate network issues. You can only have Consistency and Partition Tolerance (CP) or Availability and Partition Tolerance (AP). Supporting Availability and Partition Tolerance makes sense, since Availability and Partition Tolerance are the biggest requirements.
* Data Modeling in Apache Cassandra:
    * Denormalization is not just okay -- it's a must, for fast reads
    * Apache Cassandra has been optimized for fast writes
    * ALWAYS think Queries first, one table per query is a great strategy
    * Apache Cassandra does not allow for JOINs between tables
    * Primary Key must be unique
        * The PRIMARY KEY is made up of either just the PARTITION KEY or may also include additional CLUSTERING COLUMNS
        * A Simple PRIMARY KEY is just one column that is also the PARTITION KEY. A Composite PRIMARY KEY is made up of more than one column and will assist in creating a unique value and in your retrieval queries
        * The PARTITION KEY will determine the distribution of data across the system
    * WHERE clause
        * Data Modeling in Apache Cassandra is query focused, and that focus needs to be on the WHERE clause
        * Failure to include a WHERE clause will result in an error
## What is a Data Warehouse?
* Data Warehouse is a system (including processes, technologies & data representations that enables support for analytical processing)

* Goals of a Data Warehouse:
    * Simple to understand
    * Performant
    * Quality Assured
    * Handles new business questions well
    * Secure

## Architecture
* Several possible architectures to building a Data Warehouse
1. **Kimball's Bus Architecture**:
![Kimball's Bus Architecture](snapshots/kimball.PNG)
    * Results in common dimension data models shared by different business departments
    * Data is not kept at an aggregated level, rather they are at the atomic level
    * Organized by business processes, used by different departments 
2. **Independent Data Marts**:
![Independent Data Marts](snapshots/datamart.PNG)
    * Independent Data Marts have ETL processes that are designed by specific business departments to meet their analytical needs
    * Different fact tables for the same events, no conformed dimensions
    * Uncoordinated efforts can lead to inconsistent views
    * Generally discouraged
3. **Inmon's Corporate Information Factory**:
![Inmon's Corporate Information Factory](snapshots/cif.PNG)
    * The Enterprise Data Warehouse provides a normalized data architecture before individual departments build on it
    * 2 ETL Process
        * Source systems -> 3NF DB
        * 3NF DB -> Departmental Data Marts
    * The Data Marts use a source 3NF model (single integrated source of truth) and add denormalization based on department needs
    * Data marts dimensionally modelled & unlike Kimball's dimensional models, they are mostly aggregated
4. **Hybrid Kimball Bus & Inmon CIF**:
![Hybrid Kimball Bus & Inmon CIF](snapshots/hybrid.PNG)

## OLAP Cubes
---
* An OLAP Cube is an aggregation of a fact metric on a number of dimensions

* OLAP cubes need to store the finest grain of data in case drill-down is needed

* Operations:
1. Roll-up & Drill-Down
    * Roll-Up: eg, from sales at city level, sum up sales of each city by country
    * Drill-Down: eg, decompose the sales of each city into smaller districts
2. Slice & Dice
    * Slice: Reduce N dimensions to N-1 dimensions by restricting one dimension to a single value
    * Dice: Same dimensions but computing a sub-cube by restricting some of the values of the dimensions
    Eg month in ['Feb', 'Mar'] and movie in ['Avatar', 'Batman']

* Query Optimization
    * Business users typically want to slice, dice, rollup and drill-down
    * Each sub-combination goes through all the facts table
    * Using CUBE operation "GROUP by CUBE" and saving the output is usually enough to answer forthcoming aggregations from business users without having to process the whole facts table again

* Serving OLAP Cubes
    * Approach 1: Pre-aggregate the OLAP cubes and save them on a special purpose non-relational database (MOLAP)
    * Approach 2: Compute the OLAP Cubes on the fly from existing relational databases where the dimensional model resides (ROLAP)

    ## Choices for implementing Data Warehouse:
---
1. On-Premise
    * Need for diverse IT skills & multiple locations
    * Cost of ownership (capital and operational costs)

2. Cloud
    * Lower barriers to entry (time and money)
    * Scalability and elasticity out of the box
    * Within cloud, there are 2 ways to manage infrastructure
        1. Cloud-Managed (Amazon RDS, Amazon DynamoDB, Amazon S3)
           * Reuse of expertise (Infrastructure as Code)
           * Less operational expense
        2. Self-Managed (EC2 + Postgres, EC2 + Cassandra, EC2 + Unix FS)

    ## Amazon Redshift
---
1. Properties
    * Column-oriented storage, internally it is modified Postgresql
    * Best suited for storing OLAP workloads
    * is a Massively Parellel Processing Database
        * Parallelizes one query on multiple CPUS/machines
        * A table is partitioned and partitions are processed in parallel
    2. Architecture
    * Leader Node:
        * Coordinates compute nodes
        * Handles external communication
        * Optimizes query execution
    * Compute Node:
        * Each with CPU, memory, disk and a number of slices
            * A node with n slices can process n partitions of a table simultaneously
        * Scale-up: get more powerful nodes
        * Scale-out: get more nodes
    * Example of setting up a Data Warehouse in Redshift:
    ![Example of Data Warehouse](redshift_dwh.PNG)
    Source: Udacity DE ND Lesson 3: Implementing Data Warehouses on AWS
    3. Ingesting at Scale
    * Use COPY command to transfer from S3 staging area
    * If the file is large, better to break it up into multiple files
        * Either use a common prefix or a manifest file
    * Ingest from the same AWS region
    * Compress all csv files
    4. Optimizing Table Design
    * 2 possible strategies: distribution style and sorting key

    1. Distribution style
        * Even:
            * Round-robin over all slices for load-balancing
            * High cost of joining (Shuffling)
        * All:
            * Small (dimension) tables can be replicated on all slices to speed up joins
        * Auto: 
            * Leave decision with Redshift, "small enough" tables are distributed with an ALL strategy. Large tables distributed with EVEN strategy
        * KEY:
            * Rows with similar values of key column are placed in the same slice
            * Can lead to skewed distribution if some values of dist key are more frequent than others
            * Very useful for large dimension tables