# MongoDbHere’s a single copyable README file with all the MongoDB commands:

```markdown
# MongoDB Commands and Usage

## Basic Commands

### Show Databases
```bash
show dbs
```

### Use a Specific Database
```bash
use <db_name>
```

## Create Operations

### Insert a Single Document
```javascript
db.collectionName.insertOne({})
```

### Insert Multiple Documents
```javascript
db.collectionName.insertMany([
  {},
  {},
  {}
])
```

## Read Operations

### Find All Documents
```javascript
db.collectionName.find()
```

### Find One Document (Peek)
```javascript
db.collectionName.findOne()
```

### Find Documents with a Filter
```javascript
db.collectionName.find({key: value})
```

### Convert Cursor to Array (Retrieve All Records)
```javascript
db.collectionName.find().toArray()
```

### Iterate Through Records and Print
```javascript
db.collectionName.find().forEach((doc) => { print(doc) })
```

## Update Operations

### Update a Single Document
```javascript
db.collectionName.updateOne(
  { filter },
  { $set: { values } }
)
```

### Update Multiple Documents with a Single Condition
```javascript
db.collectionName.updateMany(
  { job: 'wizard' },
  { $set: { school: 'Hogwarts School of Witchcraft and Wizardry' } }
)
```

### Update Multiple Documents with Multiple Conditions
```javascript
db.collectionName.updateMany(
  { job: { $in: ['wizard', 'witch'] } },
  { $set: { school: 'Hogwarts School of Witchcraft and Wizardry' } }
)
```

### Replace an Entire Document (ID is Immutable)
```javascript
db.collectionName.replaceOne(
  { name: 'Severus Snape' },
  { _id: ObjectId('66d408584edc95f4022710c2'), name: 'Severus Snape', job: 'wizard', mastery: 'Potions' }
)
```

## Delete Operations

### Delete the First Matching Document
```javascript
db.collectionName.deleteOne({})
```

### Delete All Documents
```javascript
db.collectionName.deleteMany({})
```

### Delete Documents with a Filter
```javascript
db.collectionName.deleteMany({ filter })
```

## Drop Operations

### Drop a Collection
```javascript
db.collectionName.drop()
```

### Drop the Entire Database
```bash
db.dropDatabase()
```

## Datatypes

- **NumberInt, NumberLong, Boolean**
- **Document (`{}`)**
- **Array (`[]`)**

## Functions

- **Date:** `new Date()`
- **Timestamp:** `new Timestamp()`

## Notes

- **Cursor Object:** `db.collectionName.find()` returns only the first 20 records, then "it" iterates through the remaining.
- **Convert to Array:** `db.collectionName.find().toArray()` returns all records.
- **Print All Records:** `db.collectionName.find().forEach((doc) => { print(doc) })`
```

You can copy and paste this file as a README file for MongoDB usage.
