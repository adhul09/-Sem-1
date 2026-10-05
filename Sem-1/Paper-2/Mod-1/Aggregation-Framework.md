# Working with Aggregation Framework

## 1. What is Aggregation?

**Aggregation** is how MongoDB processes and transforms data — grouping, filtering, sorting, and reshaping documents to get meaningful results, similar to SQL's `GROUP BY` and `JOIN` combined.

It works using an **aggregation pipeline** — data passes through a series of **stages**, one after another, each transforming it a bit more.

```js
db.orders.aggregate([
  { stage1 },
  { stage2 },
  { stage3 }
]);
```

---

## 2. Common Aggregation Stages

### `$match` — filter documents (like `find()`)
```js
{ $match: { status: "completed" } }
```

### `$group` — group documents and calculate values
```js
{
  $group: {
    _id: "$customerId",
    totalSpent: { $sum: "$amount" }
  }
}
```
`_id` here defines what to group by; `$sum` adds up the `amount` field for each group.

### `$sort` — sort the results
```js
{ $sort: { totalSpent: -1 } } // -1 = descending, 1 = ascending
```

### `$project` — choose/reshape which fields to show
```js
{ $project: { customerId: 1, totalSpent: 1, _id: 0 } }
```

---

## 3. Simple Aggregation Pipeline Example

**Goal:** find the total amount spent by each customer, for completed orders only, sorted highest to lowest.

```js
db.orders.aggregate([
  { $match: { status: "completed" } },
  {
    $group: {
      _id: "$customerId",
      totalSpent: { $sum: "$amount" }
    }
  },
  { $sort: { totalSpent: -1 } }
]);
```

**How to read this pipeline step by step:**
1. `$match` → keep only completed orders
2. `$group` → group them by customer, summing their order amounts
3. `$sort` → arrange results from highest spender to lowest

