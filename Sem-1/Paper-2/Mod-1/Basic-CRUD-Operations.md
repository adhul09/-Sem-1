#  Basic CRUD Operations

## 1. Insert Documents

**Insert one document:**
```js
db.users.insertOne({
  name: "Adhul",
  age: 20,
  skills: ["JavaScript", "React"]
});
```

**Insert multiple documents:**
```js
db.users.insertMany([
  { name: "Riya", age: 22 },
  { name: "Kabir", age: 25 }
]);
```
MongoDB automatically adds a unique `_id` to each document if you don't provide one.

---

## 2. Read / Fetch Documents

**Find all documents:**
```js
db.users.find();
```

**Find with a condition:**
```js
db.users.find({ age: 20 });
```

**Find only one document:**
```js
db.users.findOne({ name: "Adhul" });
```

**Find with specific fields only (projection):**
```js
db.users.find({}, { name: 1, age: 1, _id: 0 });
// returns only name and age, excludes _id
```

---

## 3. Update Documents

**Update one document:**
```js
db.users.updateOne(
  { name: "Adhul" },
  { $set: { age: 21 } }
);
```

**Update multiple documents:**
```js
db.users.updateMany(
  { age: { $lt: 25 } },
  { $set: { status: "young" } }
);
```

**Replace an entire document:**
```js
db.users.replaceOne(
  { name: "Adhul" },
  { name: "Adhul", age: 21, skills: ["Node.js"] }
);
```

Common update operators:
- `$set` — set/update a field's value
- `$inc` — increase/decrease a number field
- `$unset` — remove a field
- `$push` — add an item to an array field

---

## 4. Delete Documents

**Delete one document:**
```js
db.users.deleteOne({ name: "Kabir" });
```

**Delete multiple documents:**
```js
db.users.deleteMany({ age: { $lt: 18 } });
```

**Delete all documents in a collection:**
```js
db.users.deleteMany({});
```

---

**Quick summary table:**

| Operation | Method |
|---|---|
| Create | `insertOne()`, `insertMany()` |
| Read | `find()`, `findOne()` |
| Update | `updateOne()`, `updateMany()`, `replaceOne()` |
| Delete | `deleteOne()`, `deleteMany()` |