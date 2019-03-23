## Databases 
### Relational Databases (RDS)
- Relational databases: think of a traditional spreadsheet!
- Multiple Availability Zones for disaster recovery
- Read replicas (copies of your production database) for performance

#### How It Connects
Your EC2 instance points to a DNS string (connection string: e.g., myexampledb.alb2c3d4wxyz.us-west-2.rds.amazonaws.com) which points to your primary database in _AZ 1_ and a secondary database in _AZ 2_.

You can set it up so your EC2 instances do their writes to your primary database, and all their reads from the read replica (up to 5 copies!).

#### Non Relationl Databases
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

Provides flexibility. 
- Can add columns without impacting all rows.

Amazon's Non Relational Database is called **DynamoDB**. 

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
