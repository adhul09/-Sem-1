# NoSQL and MongoDB Basics

## 1. What Are Databases and Why Are They Used?

A **database** is an organized collection of data that is stored electronically so it can be easily accessed, managed, and updated. Instead of keeping data in scattered files, a database stores it in a structured way and lets applications read and write it quickly.

**Why databases are used:**
- **Persistent storage**: data stays saved even after the application closes
- **Fast retrieval**: specific data can be searched and fetched quickly
- **Data management**: easy to create, read, update, and delete (CRUD) records
- **Multi-user access**: many users and applications can use the same data at once
- **Security and reliability**: controlled access, backups, and protection against data loss

Example: an e-commerce app uses a database to store users, products, and orders.

---

## 2. SQL vs NoSQL

| Feature | SQL (Relational) | NoSQL (Non-relational) |
|---|---|---|
| Data structure | Tables with rows and columns | Documents, key-value, graph, or column formats |
| Schema | Fixed, predefined schema | Flexible, dynamic schema |
| Relationships | Uses JOINs across tables | Related data is often embedded in one document |
| Scaling | Mostly vertical (bigger server) | Mostly horizontal (more servers) |
| Query language | SQL | Varies by database (MongoDB uses MQL) |
| Best for | Structured data, complex queries, transactions | Large, changing, or unstructured data |
| Examples | MySQL, PostgreSQL, Oracle | MongoDB, Redis, Cassandra |

**In short:** SQL is rigid and structured, while NoSQL is flexible and scalable.


## ACID vs BASE (Database Consistency Models)

**ACID** (traditionally followed by SQL databases):
- **Atomicity**: a transaction either fully completes or fully fails — no partial updates
- **Consistency**: data always moves from one valid state to another, following defined rules
- **Isolation**: transactions running at the same time don't interfere with each other
- **Durability**: once a transaction is committed, it stays saved even after a crash

**BASE** (commonly followed by NoSQL databases like MongoDB):
- **Basically Available**: the system stays operational most of the time, even during failures
- **Soft state**: data may change over time, even without new input, as it syncs across servers
- **Eventual consistency**: data will become consistent across all servers eventually, not instantly

**Why this matters for MongoDB:** SQL databases prioritize strict accuracy (ACID) at the cost of some speed/scalability, while MongoDB and other NoSQL databases favor availability and scalability (BASE), accepting that data might take a moment to sync perfectly across servers. This is a direct trade-off tied to why NoSQL scales more easily than SQL.

---

## 3. How MongoDB Stores Data

MongoDB is a **document-oriented NoSQL database**. It stores data in a JSON-like format called **BSON** (Binary JSON).

- **Database**: a container for collections
- **Collection**: a group of related documents (similar to a table in SQL)
- **Document**: a single record stored as key-value pairs (similar to a row in SQL)

**Example document in a `users` collection:**
```json
{
  "_id": "64f1a2b3c4d5e6f7a8b9c0d1",
  "name": "Adhul",
  "age": 20,
  "skills": ["JavaScript", "React", "Node.js"]
}
```

**Key points:**
- Each document has a unique `_id` field, added automatically
- Documents in the same collection can have different fields
- Documents can hold arrays and nested objects, so related data can live together

**SQL to MongoDB mapping:**
| SQL | MongoDB |
|---|---|
| Database | Database |
| Table | Collection |
| Row | Document |
| Column | Field |

---

## 4. When and Why MongoDB Is Preferred

**Why MongoDB is preferred:**
- **Flexible schema**: fields can be added or changed without restructuring the whole database
- **JSON-like documents**: matches how JavaScript objects look, which makes it a natural fit for the MERN stack
- **Easy horizontal scaling**: handles large amounts of data by spreading it across servers
- **Fast development**: no need to design rigid tables up front
- **Handles varied data**: works well with unstructured or semi-structured data

**When to use MongoDB:**
- Applications where the data structure changes often
- Real-time apps, content management systems, and social media platforms
- Big data and high-traffic applications
- Projects built with the MERN stack

**When SQL may be better:**
- Data with many complex relationships that need JOINs
- Applications needing strict consistency, such as banking and financial systems

**Conclusion:** MongoDB is preferred when flexibility, scalability, and fast development matter more than rigid structure.