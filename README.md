# 📘 MongoDB Practice – BCAB / BCAB1 Database Operations

## 📌 Overview

This project demonstrates basic to intermediate operations in MongoDB using the Mongo Shell (`mongosh`). It includes database creation, collection management, CRUD operations, query operators, indexing, and performance analysis.

---

## ⚙️ Tools Used

* MongoDB Server
* MongoDB Shell (`mongosh`)

---

## 🗂️ Database Operations

### 🔹 Show Existing Databases

```js
show dbs
```

### 🔹 Create & Switch Database

```js
use BCAB
```

### 🔹 Create Collection

```js
db.createCollection("Students")
```

### 🔹 Drop Database

```js
db.dropDatabase()
```

---

## 📁 Collection Operations

### 🔹 Create Multiple Collections

```js
use BCAB1

db.createCollection("Student")
db.createCollection("Employees")
db.createCollection("Branch")
```

### 🔹 View Collections

```js
show collections
```

---

## 📝 Insert Operations

### 🔹 Insert One Document

```js
db.students.insertOne({
  name: "Mike",
  age: 19.2,
  cgpa: 9.2,
  gender: "Male",
  feespaid: true
})
```

### 🔹 Insert Many Documents

```js
db.students.insertMany([
  { name: "Sushma", age: 20, cgpa: 9.9, gender: "Female" },
  { name: "Prem", age: 21, cgpa: 9.2, gender: "Male" }
])
```

---

## 🔍 Read Operations

### 🔹 Fetch All Documents

```js
db.students.find()
```

### 🔹 Sorting

```js
db.students.find().sort({ age: 1, cgpa: 1 })
```

### 🔹 Limit Results

```js
db.students.find().limit(2)
```

### 🔹 Projection

```js
db.students.find({ age: 20 }, { name: true, _id: false })
```

---

## ✏️ Update Operations

### 🔹 Update One

```js
db.students.updateOne(
  { name: "Mike" },
  { $set: { cgpa: 10 } }
)
```

### 🔹 Update Many

```js
db.students.updateMany(
  {},
  { $set: { courses: ["Java", "CN", "DAA", "Web"] } }
)
```

### 🔹 Add Field if Not Exists

```js
db.students.updateMany(
  { feespaid: { $exists: false } },
  { $set: { feespaid: false } }
)
```

---

## ❌ Delete Operations

### 🔹 Delete One

```js
db.students.deleteOne({ name: "Mike" })
```

### 🔹 Delete Many

```js
db.students.deleteMany({ feespaid: { $exists: true } })
```

---

## 🔎 Query Operators

### 🔹 Comparison Operators

```js
db.students.find({ cgpa: { $gt: 8 } })
db.students.find({ cgpa: { $gte: 8 } })
db.students.find({ cgpa: { $lt: 8 } })
db.students.find({ cgpa: { $lte: 8 } })
```

### 🔹 Logical Operators

```js
db.students.find({ $and: [{ age: 24 }, { cgpa: { $gte: 8 } }] })
db.students.find({ $or: [{ age: { $lte: 24 } }, { cgpa: { $gte: 8 } }] })
```

### 🔹 Array Operators

```js
db.students.find({ age: { $in: [20, 22] } })
db.students.find({ age: { $nin: [20, 22] } })
```

### 🔹 Equality Operators

```js
db.students.find({ name: { $eq: "Priya" } })
db.students.find({ name: { $ne: "Priya" } })
```

---

## ⚡ Indexing & Performance

### 🔹 Without Index (Collection Scan)

```js
db.students.find({ name: "Megha" }).explain("executionStats")
```

### 🔹 Create Index

```js
db.students.createIndex({ name: 1 })
```

### 🔹 With Index (Faster Query)

```js
db.students.find({ name: "Megha" }).explain("executionStats")
```

### 🔹 View Indexes

```js
db.students.getIndexes()
```

### 🔹 Drop Index

```js
db.students.dropIndexes("name_1")
```

---

## 🧹 Cleanup

### 🔹 Drop Collection

```js
db.students.drop()
```

### 🔹 Drop Database

```js
db.dropDatabase()
```

---

## ⚠️ Common Errors Faced

* ❌ `db.dropCollection is not a function`
  ✔️ Correct usage: `db.collectionName.drop()`

* ❌ Case-sensitive issues (`students` vs `Student`)

* ❌ Update requires `$set` operator

* ❌ Syntax errors in arrays and objects

---

## 📊 Final Output Example

```js
db.students.find()
```

Result:

```json
[
  { "name": "Priya", "age": 20, "cgpa": 8 },
  { "name": "Megha", "age": 18, "cgpa": 8.9 }
]
```

---

## 🎯 Conclusion

This project covers:

* Database & collection management
* CRUD operations
* Advanced querying
* Indexing for performance optimization

It is a complete hands-on practice for beginners learning MongoDB.

---
