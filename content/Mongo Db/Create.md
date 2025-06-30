``` javascript
// to check current db
db
// to access/create database
use harshdb

// create collection
db.createCollection("users")

// insert single document
db.users.insertOne({
  name: "Harsh",
  age: 22,
  skills: ["Kotlin", "Python"]
})

// insert multiple document
db.users.insertMany([
  { name: "Tom", age: 25, skills: ["C++"] },
  { name: "Jerry", age: 21, skills: ["Java", "SQL"] }
])

```