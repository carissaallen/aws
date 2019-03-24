## Databases 
### Relational Databases (RDS)
- Relational databases: think of a traditional spreadsheet!
- Multiple Availability Zones for disaster recovery
- Read replicas (copies of your production database) for performance
- Aurora is Amazon's cloud native RDS

#### How It Connects
Your EC2 instance points to a DNS string (connection string: e.g., myexampledb.alb2c3d4wxyz.us-west-2.rds.amazonaws.com) which points to your primary database in _AZ 1_ and a secondary database in _AZ 2_.

You can set it up so your EC2 instances do their writes to your primary database, and all their reads from the read replica (up to 5 copies!).

#### Non Relational Databases (DyanmoDB)
If your application primarily indexes and queries data with no need for joins or complex transactions--consider a NoSQL database. 

- Collection = Table
- Document = Row
- Key Value Pairs:

```
{ 
"_id":#1235353",
"name":"Samson",
"nickname":"Sammy",
"age":"6",
"address":[
{"street":"21 Jump Street",
"suburb":"Pearl"}
  ]
}
```

Provides flexibility and horizontal scalability. 
- Can add columns without impacting all rows.

Amazon's Non Relational Database is called **DynamoDB**. 

#### Data Warehouse (Redshift) 
A specialized type of relational database, which is optimized for analysis and reporting of large amounts of data. _Redshift_ is a managed data warehouse service that is designed to perate at less than a tenth the cost of traditional solutions.

#### OLTP vs. OLAP
- Online Transaction Processing (OLTP)
- Online Analytics Processing (OLAP)
- Differs in terms of the types of queries you will run

OLTP Example:
Query Order No. 2120121
Returns the row of data: Name, Date, Delivery Address, Delivery Status.
(Inserts or retrieves a row in the database.)

OLAP Example:
Query net profit for EMEA and Pacific for the Digital Radio Product. 
(Pulls in large numbers of records.)

Data Warehousing allows you to do this away from your database. They use a different architecture.
Amazon's Data Warehouse solution is called _Redshift_.

#### Scalability 
**Read Replicas** <br>
Separate database instances that are replicated asynchronously. They are subject to replication lag and might be missing some of the latest transactions. Read replicas cannot accept any write queries. 

**Data Partitioning or Sharding** <br>
Data is split across multiple database schemas ecah running in its own autonomous primary DB instance. 

#### High Availability 
_For any production relational database, use the RDS Multi-AZ deployment feature, which creates a synchronously replicated standby instance in a different AZ. In case of failure of the primary node, RDS performans an automatic failover to the standby without the need for manual administrative intervention._


