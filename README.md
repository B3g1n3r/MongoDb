# MongoDb

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
db.collectionName.find().forEach((doc) => { print(doc) }) or printjson -- same output
db.employee.findOne({school:'Hogwarts'}).name  -- specific value
```

```
db.employee.findOne({school:'Hogwarts'}).name  -- specific value
 db.employee.findOne({},{name:1}) --- only name is visible
 db.employee.findOne({'wand.wood': 'Ash'}) -- access within the array
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
-  db.stats() - status
-  db.getName() - current collection name
-  db.getCollectionNames() - all Collection in the database
-  db.getCollectionInfos() -- info
-  db.employee.countDocuments() -- no of document in the collection
-  db.employee.distinct('wand.wood') -- distinct values

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

## OPTIONS

## PROJECTIONS
- **example**  db.employee.find({},{_id:0,name:1,wand:1}) `only the name and wand are retrived`

## Validation
-  db.createCollection('Onepiece', {validator:{$jsonSchema:{ bsonType: 'object', required:['name','power','bounty'], properties:{ name:{bsonType:'string', description:'Must be string and required'},bounty:{bsonType:'int', description:'Must be int and required' }, power:{bsonType:'string', description: 'Must be string and not empty'}}}}})
 
## Notes

- **Cursor Object:** `db.collectionName.find()` returns only the first 20 records, then "it" iterates through the remaining.
- **Convert to Array:** `db.collectionName.find().toArray()` returns all records.
- **Print All Records:** `db.collectionName.find().forEach((doc) => { print(doc) })`
```


