# General 

## Passwords

- Passwords should be stored as hash values in a database.
- Salt: A string added to the beginning or end of a password before it is hashed.
- Salt should be unique for every user.
- Salt can be stored in plain text in the db.
- 

# SQL

- Enhanced entity-relationship (EER) models

# NoSql

- Can stand for no SQL or not only SQL
- Are designed for massive scalability, high performance, and to make programming easier by providing maximum flexibility and allowing schema changes at any time because they do not enforce a structure.
- CosmoDB has multiple APIs that work with it. For instance, MongoDB, Cassandra Query Language, Core (sql) API, and Gremlin API
    -  If you are unsure which API to choose, select Core (SQL) as the default.
    - Cassandra uses row.
    - MongoDB uses document.
    - Graph databases like Gremlin use vertex and edge.

- Unlike with a relational database model, it is common to embed related data. That means duplicating data, like the category and supplier information, in many products. This is good practice if the related data is bounded.
- Denormalized data models provide better read performance but worse write performance.
- Normalized data models require more queries, which worsens read performance but provides better write performance.