In MongoDB, there are various options and operations you can perform across different levels, such as database, collection, and document. Below is a list of common MongoDB options and commands:

### 1. **Database-Level Options:**
   - **Create Database:** MongoDB automatically creates a database when you insert data into it.
   - **List Databases:** `show dbs`
   - **Switch Database:** `use <db_name>`
   - **Drop Database:** `db.dropDatabase()`

### 2. **Collection-Level Options:**
   - **Create Collection:** `db.createCollection('<collection_name>')`
   - **List Collections:** `show collections`
   - **Drop Collection:** `db.<collection_name>.drop()`
   - **Rename Collection:** `db.<collection_name>.renameCollection('<new_name>')`

### 3. **Insert Operations:**
   - **Insert One Document:** `db.<collection_name>.insertOne({})`
   - **Insert Multiple Documents:** `db.<collection_name>.insertMany([ {}, {}, {} ])`

### 4. **Query Operations:**
   - **Find All Documents:** `db.<collection_name>.find()`
   - **Find One Document:** `db.<collection_name>.findOne()`
   - **Find with Filter:** `db.<collection_name>.find({key:value})`
   - **Find with Projection:** `db.<collection_name>.find({}, {key:1})`
   - **Count Documents:** `db.<collection_name>.countDocuments()`

### 5. **Update Operations:**
   - **Update One Document:** `db.<collection_name>.updateOne({filter}, {$set: {key: value}})`
   - **Update Multiple Documents:** `db.<collection_name>.updateMany({filter}, {$set: {key: value}})`
   - **Replace Document:** `db.<collection_name>.replaceOne({filter}, {new_document})`

### 6. **Delete Operations:**
   - **Delete One Document:** `db.<collection_name>.deleteOne({filter})`
   - **Delete Multiple Documents:** `db.<collection_name>.deleteMany({filter})`

### 7. **Aggregation Operations:**
   - **Aggregate Data:** `db.<collection_name>.aggregate([pipeline])`
   - **Group and Count:** Example: `db.<collection_name>.aggregate([{ $group: { _id: "$field", count: { $sum: 1 } } }])`

### 8. **Index Operations:**
   - **Create Index:** `db.<collection_name>.createIndex({field: 1})`
   - **List Indexes:** `db.<collection_name>.getIndexes()`
   - **Drop Index:** `db.<collection_name>.dropIndex({field: 1})`

### 9. **Options for Read/Write Concerns:**
   - **Read Concern:** Control the consistency and isolation properties of read operations (e.g., `"local"`, `"majority"`).
   - **Write Concern:** Control the acknowledgment of write operations (e.g., `{ w: 1 }`, `{ w: "majority" }`).

### 10. **Backup and Restore Options:**
   - **Backup Database:** `mongodump --db <db_name>`
   - **Restore Database:** `mongorestore --db <db_name> <path_to_backup>`

### 11. **Configuration Options:**
   - **Sharding:** Distribute data across multiple servers.
   - **Replication:** Set up replica sets for high availability.

### 12. **Security Options:**
   - **Create User:** `db.createUser({user: "username", pwd: "password", roles: [{role: "readWrite", db: "<db_name>"}]})`
   - **Authenticate User:** `db.auth("username", "password")`

---

These options cover a broad range of MongoDB operations, from basic CRUD to more advanced features like aggregation, indexing, and security. Let me know if you need further details or specific examples!
