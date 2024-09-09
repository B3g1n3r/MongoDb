Elemental operators in MongoDB allow you to interact with individual elements of an array or fields within a document. These operators enable you to perform operations on specific elements or evaluate conditions that apply to individual items. Below are some commonly used elemental operators in MongoDB:

### 1. `$elemMatch`
- **Usage:** Matches documents that contain an array field with at least one element that matches all the specified query criteria.
- **Example:**
  ```javascript
  db.inventory.find({ items: { $elemMatch: { qty: { $gt: 10, $lt: 20 } } } })
  ```
  This query matches documents where the `items` array contains at least one element with a `qty` field greater than 10 and less than 20.

### 2. `$all`
- **Usage:** Matches arrays that contain all the specified elements.
- **Example:**
  ```javascript
  db.inventory.find({ tags: { $all: ["red", "blue"] } })
  ```
  This query matches documents where the `tags` array contains both `"red"` and `"blue"`.

### 3. `$size`
- **Usage:** Matches arrays with the specified number of elements.
- **Example:**
  ```javascript
  db.inventory.find({ tags: { $size: 3 } })
  ```
  This query matches documents where the `tags` array has exactly 3 elements.

### 4. `$slice`
- **Usage:** Limits the number of elements returned in an array field.
- **Example:**
  ```javascript
  db.inventory.find({}, { items: { $slice: 2 } })
  ```
  This query returns only the first 2 elements of the `items` array.

### 5. `$arrayElemAt`
- **Usage:** Returns the element at the specified array index.
- **Example:**
  ```javascript
  db.inventory.aggregate([
    { $project: { itemAtSecondIndex: { $arrayElemAt: ["$items", 2] } } }
  ])
  ```
  This query retrieves the element at the second index of the `items` array.

### 6. `$first` and `$last`
- **Usage:** Returns the first or last element in an array.
- **Example:**
  ```javascript
  db.inventory.aggregate([
    { $project: { firstItem: { $first: "$items" }, lastItem: { $last: "$items" } } }
  ])
  ```
  This query retrieves the first and last elements of the `items` array.

### 7. `$push`
- **Usage:** Adds an element to an array.
- **Example:**
  ```javascript
  db.inventory.updateOne({ _id: 1 }, { $push: { items: "newItem" } })
  ```
  This operation adds `"newItem"` to the `items` array.

### 8. `$pop`
- **Usage:** Removes the first or last element from an array.
- **Example:**
  ```javascript
  db.inventory.updateOne({ _id: 1 }, { $pop: { items: 1 } })
  ```
  This operation removes the last element from the `items` array. Use `-1` to remove the first element.

### 9. `$pull`
- **Usage:** Removes all array elements that match a specified condition.
- **Example:**
  ```javascript
  db.inventory.updateMany({}, { $pull: { items: { qty: { $lt: 5 } } } })
  ```
  This operation removes all elements from the `items` array where `qty` is less than 5.

### 10. `$addToSet`
- **Usage:** Adds elements to an array only if they do not already exist.
- **Example:**
  ```javascript
  db.inventory.updateOne({ _id: 1 }, { $addToSet: { items: "uniqueItem" } })
  ```
  This operation adds `"uniqueItem"` to the `items` array if it doesn't already exist.

These elemental operators are powerful tools for working with arrays and individual fields within documents, enabling more complex and granular queries in MongoDB.
