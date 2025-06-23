
## Basic

| Operator | Meaning               | Example                 |
| -------- | --------------------- | ----------------------- |
| `$eq`    | Equals                | `{ age: { $eq: 22 } }`  |
| `$ne`    | Not equals            | `{ age: { $ne: 22 } }`  |
| `$gt`    | Greater than          | `{ age: { $gt: 22 } }`  |
| `$gte`   | Greater than or equal | `{ age: { $gte: 22 } }` |
| `$lt`    | Less than             | `{ age: { $lt: 22 } }`  |
| `$lte`   | Less than or equal    | `{ age: { $lte: 22 } }` |

## Relational 

| Operator | Meaning                | Example                                                  |
| -------- | ---------------------- | -------------------------------------------------------- |
| `$and`   | Both conditions true   | `{ $and: [{ age: { $gt: 20 } }, { status: "junior" }] }` |
| `$or`    | Any one condition true | `{ $or: [{ age: 22 }, { status: "junior" }] }`           |
| `$not`   | Negates condition      | `{ age: { $not: { $gt: 25 } } }`                         |
| `$nor`   | Neither condition true | `{ $nor: [{ age: 22 }, { status: "junior" }] }`          |
