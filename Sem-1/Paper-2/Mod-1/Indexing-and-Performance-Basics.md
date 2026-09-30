#  Indexing and Performance Basics

## 1. What is Indexing?

An **index** is a special data structure that stores a small, sorted portion of the collection's data, making it much faster to search — similar to an index at the back of a book that helps you find a topic without reading every page.

Without an index, MongoDB has to check **every single document** in a collection to find matches — this is called a **collection scan**.

---

## 2. Why Indexing Improves Query Performance

**Without an index:**
```js
db.users.find({ email: "adhul@example.com" });
// MongoDB scans EVERY document to find a match — slow on large collections
```

**With an index on `email`:**
```js
db.users.createIndex({ email: 1 });
```
Now MongoDB can jump almost directly to the matching document instead of scanning everything — much faster, especially as data grows into thousands/millions of documents.

**Trade-off to remember:**
- Indexes make **reads faster**
- But they make **writes (insert/update) slightly slower**, since the index also needs to update
- Indexes also use extra storage space

So indexes are added strategically — usually on fields you search/filter by often, not on every field.

---

## 3. Basic Indexing Techniques

**Create a single-field index:**
```js
db.users.createIndex({ email: 1 });
// 1 = ascending order, -1 = descending order
```

**Create a compound index (multiple fields):**
```js
db.users.createIndex({ city: 1, age: -1 });
```
Useful when you frequently filter/sort by more than one field together.

**View existing indexes:**
```js
db.users.getIndexes();
```

**The default index:**
Every MongoDB collection automatically has an index on `_id` — this is why searching by `_id` is always fast, even without creating anything extra.

**Simple rule of thumb:** add an index to any field you query or sort by frequently — especially in large collections where performance actually matters.