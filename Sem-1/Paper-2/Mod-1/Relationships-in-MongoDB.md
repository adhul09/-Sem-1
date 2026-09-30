# Relationships in MongoDB

## 1. Embedding vs Referencing

MongoDB offers two ways to represent relationships between data, since it doesn't use JOINs like SQL.

### Embedding (nested documents)
Store related data **inside** the same document.
```js
{
  name: "Adhul",
  address: {
    city: "Kochi",
    pincode: 682001
  }
}
```

### Referencing (separate documents linked by ID)
Store related data in a **different collection**, linked using an `_id`.
```js
// users collection
{ _id: "u1", name: "Adhul" }

// orders collection
{ _id: "o1", userId: "u1", item: "Laptop" }
```

---

## 2. How to Decide: Embedding vs Referencing

| Use Embedding when... | Use Referencing when... |
|---|---|
| Data is always accessed together | Data is large or grows unbounded |
| Related data doesn't change often | Related data is shared across multiple documents |
| One-to-few relationships | One-to-many or many-to-many relationships |
| You want faster reads (no extra lookup) | You want to avoid duplicate data |

**Example — Embedding makes sense:**
A user's address rarely changes and is only needed with that user → embed it.

**Example — Referencing makes sense:**
A single customer can have hundreds of orders, and orders are queried independently → reference them instead of embedding all orders inside the user document.

---

## 3. Modeling Real-World Data — Example

**Scenario:** Users and their blog posts.

**Referencing approach (recommended here, since one user can have many posts):**
```js
// users collection
{ _id: "u1", name: "Adhul" }

// posts collection
{ _id: "p1", userId: "u1", title: "My First Post" }
{ _id: "p2", userId: "u1", title: "Learning MongoDB" }
```
To get a user's posts:
```js
db.posts.find({ userId: "u1" });
```

**Embedding approach (only good for a few, rarely-changing posts):**
```js
{
  _id: "u1",
  name: "Adhul",
  posts: [
    { title: "My First Post" },
    { title: "Learning MongoDB" }
  ]
}
```

**Rule of thumb:** if the related data can grow large or needs to be queried on its own, use referencing. If it's small, tightly bound, and always used together, embedding is simpler and faster.