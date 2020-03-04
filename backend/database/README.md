# Database Interview questions

Reference:

[Geeksforgeeks](https://www.geeksforgeeks.org/database-management-system-set-1/)

[Database Migration](https://blog.f5.works/best-practices-manage-database-schema-changes-with-database-migration-and-version-control/)

[w3schools](https://www.w3schools.in/dbms/database-normalization/)

* **How relational database work**

Excellent guide can be found at [here](http://coding-geek.com/how-databases-work/?fbclid=IwAR2U672QuDo7pjEH5VQDQa6shoy-ceCjOZK15JAJDGF1yzOg0qpHn9CgyAg)

You should know some important points:

    * Data structure used in database
    * Basic components inside a database
    * How a query is executed
    * What is query optimizer
    * Join Operation
    * Concurrency, Log, ..

For who don't want to dive deep inside database, you can ignore this question

* **What is the maximum throughput ? How to increase it**

In general terms, throughput is the rate of production or the rate at which something is processed

In IT application, “Throughput” is the amount of transactions produced over time during a test or running-time. It’s also expressed as the amount of capacity that a website or application can handle. Also before starting a performance test it is common to have a throughput goal that the application needs to be able to handle a specific number of request per hr

Throughtput is one of criteria of performance. Increase throughput can be achieved by optimize your system, use db cluster, etc

* **How would you migrate an application from a database to another, for example from MySQL to PostgreSQL? If you had to manage that project, which issues would you expect to face?**

Some answers can be found at:

[Quora](https://www.quora.com/How-big-companies-migrate-from-one-database-to-another-without-losing-data-i-e-database-independent)

[Dzone](https://dzone.com/articles/safe-database-migration-pattern-without-downtime)

Summary steps are:

1. Launch New Database
2. Import backup database to new database
3. Launch an application to drain the queue of writes (e.g. all writes after the DB backup) and apply those changes to new one
4. Enable dual write to application, after write to old database continue write in new database
5. Drainer stop since rows number are equal in both Database
6. Disable dual write, enable dual read, now write to new database only
7. Testing and finish

Issue:

1. Zero down time
2. Conversion to new kind of database
3. Validation
4. Maybe stressure

* **ACID is an acronym that refers to Atomicity, Consistency, Isolation and Durability, 4 properties guaranteed by a database transaction in most database engines. What do you know about this topic? Would you like to elaborate?**

A transaction is a single logical unit of work which accesses and possibly modifies the contents of a database. Transactions access data using read and write operations.

In order to maintain consistency in a database, before and after the transaction, certain properties are followed. These are called ACID properties.

![ACID](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20191121102921/ACID-Properties.jpg)

1. Atomicity

By this, we mean that either the entire transaction takes place at once or doesn’t happen at all. There is no midway i.e. transactions do not occur partially. Each transaction is considered as one unit and either runs to completion or is not executed at all. It involves the following two operations:

—Abort: If a transaction aborts, changes made to database are not visible.

—Commit: If a transaction commits, changes made are visible.
Atomicity is also known as the ‘All or nothing rule’.

Consider the following transaction T consisting of T1 and T2: Transfer of 100 from account X to account Y.

![AtomicityExample](https://media.geeksforgeeks.org/wp-content/uploads/11-6.jpg)

If the transaction fails after completion of T1 but before completion of T2.( say, after write(X) but before write(Y)), then amount has been deducted from X but not added to Y. This results in an inconsistent database state. Therefore, the transaction must be executed in entirety in order to ensure correctness of database state.

2. Consistency

This means that integrity constraints must be maintained so that the database is consistent before and after the transaction. It refers to the correctness of a database.

Referring to the example above, The total amount before and after the transaction must be maintained.

Total before T occurs = 500 + 200 = 700.

Total after T occurs = 400 + 300 = 700.

Therefore, database is consistent. Inconsistency occurs in case T1 completes but T2 fails. As a result T is incomplete

3. Isolation

This property ensures that multiple transactions can occur concurrently without leading to the inconsistency of database state. Transactions occur independently without interference. Changes occurring in a particular transaction will not be visible to any other transaction until that particular change in that transaction is written to memory or has been committed. 

This property ensures that the execution of transactions concurrently will result in a state that is equivalent to a state achieved these were executed serially in some order.

Let X= 500, Y = 500.
Consider two transactions T and T”.

![IsolationExample](https://media.geeksforgeeks.org/wp-content/uploads/22-1.jpg)

Suppose T has been executed till Read (Y) and then T’’ starts. As a result , interleaving of operations takes place due to which T’’ reads correct value of X but incorrect value of Y and sum computed by

T’’: (X+Y = 50, 000+500=50, 500)
is thus not consistent with the sum at end of transaction:

T: (X+Y = 50, 000 + 450 = 50, 450).

This results in database inconsistency, due to a loss of 50 units. Hence, transactions must take place in isolation and changes should be visible only after they have been made to the main memory.

4. Durability

This property ensures that once the transaction has completed execution, the updates and modifications to the database are stored in and written to disk and they persist even if a system failure occurs. These updates now become permanent and are stored in non-volatile memory. The effects of the transaction, thus, are never lost.

* **How would you manage database schema migrations? That is, how would you automate changes to database schema, as the application evolves, version after version?**

When you develop software with a SQL database, there are code changes that requires database changes as well. It could be database schema changes (e.g. adding a new column) or data fixes (e.g. changing all existing user phone number format). While it is common to use version control to manage code changes, there still many development teams not managing the database changes.

1. Every database changes will be documented incrementally, as small as possible.

When there is a code change that requires several database table schema to be updated, database change script should be split into
multiple scripts.

For example, when there is code change that requires changing 2 database tables plus patching existing data, there should be at least 3 scripts:

    - add_discounted_amount_to_products.sql
    - add_total_amount_to_orders.sql
    - patch_products_default_discounted_amount.sql

2. Database change script should include unique sequence number or timestamp

For example, files could be named using sequence number:

    001_add_discounted_amount_to_products.sql
    002_add_total_amount_to_orders.sql
    003_patch_products_default_discounted_amount.sql

or using timestamp:

    20170517080001_add_discounted_amount_to_products.sql
    20170517081501_add_total_amount_to_orders.sql
    20170517083601_patch_products_default_discounted_amount.sql

With these in place, the time dependency of database changes can be illustrated. It also enables change conflict induced by different conflicting changes from different developers.

3. All database changes are tracked in version control

With all database changes script in version control, you can keep every development database, staging database and production database in sync. It also allow flexibility to have different versions of schema in different development environment.

4. Store current schema version number in database

Each database instance should store their own version number (and also "migrated" database change versions, but let's do go too depth for now).

How would that be useful ? Take previous file naming as an example. In the version control, there are 3 database change scripts:

    20170517080001_add_discounted_amount_to_products.sql
    20170517081501_add_total_amount_to_orders.sql
    20170517083601_patch_products_default_discounted_amount.sql

When one of the developer machines get the latest source code and found out it's current schema version is only **20170517081501**, then it knows there are database changes haven't been applied yet and apply those to catch up the latest schema version.

**Use Migration Tools**:

Now there're alot of available tools to help developer with migration.

* **How is lazy loading achieved? When is it useful? What are its pitfalls?**

Lazy loading is a concept where we delay the loading of object until the point where we need it.

    - Lazy loading is just a fancy name given to the process of initializing a class when it’s actually needed.

    - In simple words, Lazy loading is a software design pattern where the initialization of an object occurs only when it is actually needed and not before to preserve simplicity of usage and improve performance.
    
    - Lazy loading is essential when the cost of object creation is very high and the use of the object is very rare. So this is the scenario where it’s worth implementing lazy loading.The fundamental idea of lazy loading is to load object/data when needed.

For Example, Suppose You are creating an application in which there is a Company object and this object contains a list of employees of the company in a ContactList object. There could be thousands of employees in a company. Loading the Company object from the database along with the list of all its employees in the ContactList object could be very time consuming. In some cases you don’t even require the list of the employees, but you are forced to wait until the company and its list of employees loaded into the memory.

One way to save time and memory is to avoid loading of the employee objects 
until required and this is done using the Lazy Loading Design Pattern.

There are four common implementations of Lazy Loading pattern :

1. Virtual proxy
2. Lazy initialization
3. Ghost
4. Value holder

**When note use lazy loading**

    - You have images above the fold. (it delays your header/banner load)
    - You have a store. (shoppers can’t fast-scroll as quickly through your site)
    - Doing it only to fool pagespeed scores. (while hurting UX for actual human users)
    - You’ve got a CDN. (their servers do the work, and not yours)
    - Have only a few images on each page. (static assets are easily cached and load quickly anyways)
    - You have a fast-loading website and strong server. (no point in delayed asset loads if your current site and server handle them well)

* **How would you find the most expensive queries in an application?**

Make a query, for [example](https://dbtut.com/index.php/2019/04/19/how-to-find-most-expensive-queries-in-sql-server/)

1. Top 50 CPU Consuming Queries in SQL Server

```
Select 
     st.[text] AS [Query Text],          
     wt.last_execution_time AS [Last Execution Time],
     wt.execution_count AS [Execution Count],
     wt.total_worker_time/1000000 AS [Total CPU Time(second)],
     wt.total_worker_time/wt.execution_count/1000 AS [Average CPU Time(milisecond)],
     qp.query_plan,
     DB_NAME(st.dbid) AS [Database Name]
from 
    (select top 50 
          qs.last_execution_time,
          qs.execution_count,
	  qs.plan_handle, 
          qs.total_worker_time
    from sys.dm_exec_query_stats qs
    order by qs.total_worker_time desc) wt
cross apply sys.dm_exec_sql_text(plan_handle) st
cross apply sys.dm_exec_query_plan(plan_handle) qp
order by wt.total_worker_time desc
```

2. Top 50 Disk IO Consuming Queries in SQL Server

```
select 
     st.[text] AS [Query Text],      
     qs.last_execution_time AS [Last Execution Time],
     qs.execution_count AS [Execution Count],
     qs.total_logical_reads AS [Total Logical Read],
     qs.total_logical_reads/execution_count AS [Average Logical Read],
     qs.total_worker_time/1000000 AS [Total CPU Time(second)],
     qs.total_worker_time/qs.execution_count/1000 AS [Average CPU Time(milisecond)],
     qp.query_plan AS [Execution Plan],
     DB_NAME(st.dbid) AS [Database Name]
from 
    (select top 50 
          qs.last_execution_time,
          qs.execution_count,
	  qs.plan_handle, 
          qs.total_worker_time,
          qs.total_logical_reads
    from sys.dm_exec_query_stats qs
    order by qs.total_worker_time desc) qs
cross apply sys.dm_exec_sql_text(plan_handle) st
cross apply sys.dm_exec_query_plan(plan_handle) qp
order by qs.total_logical_reads desc
```

* **In your opinion, is it always needed to use database normalization? When is it advisable to use denormalized databases?**

Database normalization is a database schema design technique, by which an existing schema is modified to minimize redundancy and dependency of data.

Normalization split a large table into smaller tables and define relationships between them to increases the clarity in organizing data.

Normalization of a Database is achieved by following a set of rules called 'forms' in creating the database:

    First Normal Form (1NF)
    Second Normal Form (2NF)
    Third Normal Form (3NF)
    Boyce-Codd Normal Form (BCNF)
    Fourth Normal Form (4NF)
    Fifth Normal Form (5NF)

* **What is Blue-Green Deployment?**

[Blue-green](https://docs.cloudfoundry.org/devguide/deploy-apps/blue-green.html) deployment is a technique that reduces downtime and risk by running two identical production environments called Blue and Green.

Blue-green deployment is a technique that reduces downtime and risk by running two identical production environments called Blue and Green.

At any time, only one of the environments is live, with the live environment serving all production traffic. For this example, Blue is currently live and Green is idle.

As you prepare a new version of your software, deployment and the final stage of testing takes place in the environment that is not live: in this example, Green. Once you have deployed and fully tested the software in Green, you switch the router so all incoming requests now go to Green instead of Blue. Green is now live, and Blue is idle.

This technique can eliminate downtime due to app deployment. In addition, blue-green deployment reduces risk: if something unexpected happens with your new version on Green, you can immediately roll back to the last version by switching back to Blue.

**Note**: If your app uses a relational database, blue-green deployment can lead to discrepancies between your Green and Blue databases during an update. To maximize data integrity, configure a single database for backward and forward compatibility.

**Note**: You can adjust the route mapping pattern to display a static maintenance page during a maintenance window for time-consuming tasks, such as migrating a database. In this scenario, the router switches all incoming requests from Blue to Maintenance to Green.

* **[How would you explain the recent rise in interest in NoSQL?](https://www.simplilearn.com/rise-of-nosql-and-why-it-should-matter-to-you-article)**

The advantages of NoSQL include:

    High scalability
    Distributed Computing
    Lower cost
    Schema flexibility
    Un/semi-structured data
    No complex relationships

There are four types of NoSQL:

    Key Value Databases: Amazon DynamoDB, Apache Cassandra, Redis
    Document Databases: MongoDB
    Column family stores: Bigtable, Cassandra
    Graph databases: GraphDB Lite

* **How does NoSQL tackle scalability challenges?**

`Scalability is the capability of a system, network, or process to handle a growing amount of work, or its potential to be enlarged to accommodate that growth.
— Wikipedia`

Scaling can be classified into Vertical and Horizontal Scaling.

![Scaling](https://hackernoon.com/hn-images/0*zQDy30a97Fwa0C_q.png)

Vertical Scaling was adopted when the database couldn’t handle the large amount of data.

Suppose you have a database server with 10GB memory and it has exhausted. Now, to handle more data, you buy an expensive server with memory of 2TB. Your server can now handle large amounts of data. Relational databases mostly use vertical scaling.

Instead of buying a single 2 TB server, you are buying two hundred 10 GB servers. Vertical scaling focuses on increasing the power and memory, whereas horizontal scaling increases the number of machines. NoSQL databases mostly use horizontal scaling

|Type of Scaling|Advantages|Disadvantages|
|--|--|--|
|Vertical|- **Simple**, since everything exists in a single server. No need to manage multiple instances. <br> - **Performance Gain**, because you have faster RAM and memory power on each update. <br> - Same Code. **No change** — You need not change your implementation or your code at all.|- Dfficult to perform multiple queries simultaneously. <br> - Chances of downtime are high, when the server exceeds maximum load. <br> - Expensive. Hardware resources are costly, after all.|
|Horizontal|- It is cheap compared to vertical scaling. <br> - Lesser Load, Better performance. <br> - Chances of downtime are less. <br> - Resilience and Fault Tolerance.| - Making joins is difficult, as it may involve cross-server communication. <br> - Eventual consistency is only possible. <br> - It may not be best suited for bank transactions, which happens simultaneously. <br> - We can’t easily categorize each feature to each server. <br> - Sometimes, images may take up more space than a single server can handle.| 

* **When would you use a document database like MongoDB instead of a relational database like MySQL or PostgreSQL?**

|Factor|SQL|NoSQL|
|--|--|--|
|Data Structure|data is very structured and ACID compliance is a must: customer relationships, accounting software, and e-commerce platforms|data is unstructured, need flexibility: article content, social media posts, sensor data
|Ability to query data|efficient queries, retrieves and edits data quickly|perform extra processing on the data|
|Scaling|scale vertically|horizontal scale|

* **Make a simple comparison between MySQL, PostgresSQL MongoDB, Cassandra**

|MySQL|PostgresSL|MongoDB|Cassandra|
|--|--|--|--|--|
|- Free and open-source <br> - Maturity, huge community <br> - Extensive testing, stability <br> - Compatibility with major platforms <br> - Replicable, Sharding <br> - Transaction| - Free and open-source, Cost-effective <br> - Compatibility with major platforms <br> - High ACID Compliance <br> - Object  Oriented Database Management System | - Free to use <br> - Dynamic schema <br> - Scalability, Flexibility <br> - Speed <br> - MongoDB Atlas | - Free and Open-Source <br> - Highly scalable <br> - Fast writes and reads <br> - excellent data protection <br> - Poor with updating and deleting data