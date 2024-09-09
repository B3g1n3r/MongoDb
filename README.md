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
- db.createCollection('yonkos', {validator:{$jsonSchema:{bsonType:'object', required:['name', 'power'], properties:{ name:{bsonType:'string', description:'must be string'}}}}, validationLevel:'strict',validationAction:'error'});

- db.runCommand({collMod:'yonkos', validator:{$jsonSchema:{bsonType:'object', required:['name', 'power'], properties:{name:{bsonType:'string', description:'must be string'}, power:{bsonType:'string', description:'enter a valid string'}}}}, validationLevel:'strict',validationAction:'error'}); **Modification of validation  

**Operators**
- **comparison operator**
   -  db.onepiece.find({name:{$eq:'kuma'}}) -- $eq equals
   -  db.onepiece.find({bounty:{$ne:81000000}}) - not equal
   -  db.onepiece.find({bounty:{$lt:100000000}}) - lower than
   -  db.onepiece.find({bounty:{$gt:100000000}}) - greater than
   -  db.onepiece.find({bounty:{$lte:100000000}}) - lower than or equal
   -  db.onepiece.find({bounty:{$gte:100000000}}) - greater than or equal
   

- **Logical operators**
   -  db.onepiece.find({$and:[{name:{$in:['Jinbe', 'Boa Hancock']}}, {bounty:{$gt:43000000}}]})  -- and operator
   -  db.onepiece.find({$or:[{name:{$in:['Jinbe', 'Boa Hancock']}}, {bounty:{$gt:43000000}}]})  -- or operator
   -   db.onepiece.find({$nor:[{name:{$in:['Jinbe', 'Boa Hancock']}}, {bounty:{$gt:43000000}}]}) -- nor
   -   db.onepiece.find({abilities:{$exists:false}})  -- exists check
   -   db.onepiece.find({ $and: [ { abilities: { $exists: true } }, { bounty: { $lt: 300000000 } } ] }, { name: 1, _id: 0 }) -- example
   -   db.onepiece.find({name:{$type:'string'}}) -- string
   -   db.onepiece.find({name:{$nin:['Jinbe','Crocodile']}}) -- not in
     
-  **Array based operators**
   -  db.onepiece.find({abilities:{$size:2}}) -- base on size
   -  db.onepiece.find({abilities:{$all:['Haki']}}) -- all
   -  db.onepiece.find().sort('bounty') -- ascending
   -  db.onepiece.find().sort({bounty:-1}) -- descending
## Notes

- **Cursor Object:** `db.collectionName.find()` returns only the first 20 records, then "it" iterates through the remaining.
- **Convert to Array:** `db.collectionName.find().toArray()` returns all records.
- **Print All Records:** `db.collectionName.find().forEach((doc) => { print(doc) })`
```


