# Query and Filter Data Effectively

## 1. Filtering Data Using Conditions

Basic filtering is done by passing a condition object to `find()`:
```js
db.users.find({ age: 20 });          // exact match
db.users.find({ city: "Kochi" });    // exact match on a string field
```

---

## 2. Common Query Operators

| Operator | Meaning | Example |
|---|---|---|
| `$eq` | Equal to | `{ age: { $eq: 20 } }` |
| `$gt` | Greater than | `{ age: { $gt: 18 } }` |
| `$lt` | Less than | `{ age: { $lt: 30 } }` |
| `$gte` | Greater than or equal | `{ age: { $gte: 18 } }` |
| `$lte` | Less than or equal | `{ age: { $lte: 30 } }` |
| `$in` | Matches any value in a list | `{ city: { $in: ["Kochi", "Delhi"] } }` |
| `$ne` | Not equal to | `{ status: { $ne: "inactive" } }` |

**Examples:**
```js
// Users older than 18
db.users.find({ age: { $gt: 18 } });

// Users from Kochi or Delhi
db.users.find({ city: { $in: ["Kochi", "Delhi"] } });
```

---

## 3. Logical Operators: $and, $or

**$and** — all conditions must be true:
```js
db.users.find({
  $and: [
    { age: { $gte: 18 } },
    { city: "Kochi" }
  ]
});
```

**$or** — at least one condition must be true:
```js
db.users.find({
  $or: [
    { city: "Kochi" },
    { city: "Delhi" }
  ]
});
```

Note: for simple cases, you can skip `$and` since multiple fields in one object are already treated as AND:
```js
db.users.find({ age: { $gte: 18 }, city: "Kochi" }); // same as $and above
```

---

## 4. Retrieving Specific Fields (Projection)

The second argument to `find()` controls which fields to show:
```js
db.users.find(
  { city: "Kochi" },        // filter condition
  { name: 1, age: 1, _id: 0 } // only show name and age
);
```
- `1` = include the field
- `0` = exclude the field
- `_id` is included by default unless explicitly excluded

**Combined example:**
```js
// Find users aged 18+ from Kochi, show only their name and email
db.users.find(
  { age: { $gte: 18 }, city: "Kochi" },
  { name: 1, email: 1, _id: 0 }
);
```