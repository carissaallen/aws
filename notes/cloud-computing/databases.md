## Databases 
### Relational Databases
- Relational databases: think of a traditional spreadsheet!
- On AWS: it's called RDS
	- multiple Availability Zones for disaster recovery
	- read replicas (copies of your production database) for performance

#### How It Connects
Your EC2 instance points to a DNS, or connection, string (e.g., myexampledb.alb2c3d4wxyz.us-west-2.rds.amazonaws.com) which points to your primary database in AZ 1 and a secondary database in AZ 2.

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
- Differes in terms of the types of queries you will run

OLTP Example:
Query Order No. 2120121
Returns the row of data: Name, Date, Delivery Address, Delivery Status
(Inserts or retrieves a row in the database)

OLAP Example:
Query net profit for EMEA and Pacific for the Digital Radio Product. 
(Pulls in large numbers of records.)

Data Warehousing allows you to do this away from your database. They use a different architecture.
Amazon's Data Warehouse solution is called _Redshift_.
