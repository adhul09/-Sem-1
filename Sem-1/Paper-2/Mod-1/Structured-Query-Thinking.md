# Structured Query Thinking

## What This Means

This is the skill of **breaking a complex question into a step-by-step pipeline** — deciding in what order to filter, group, sort, and reshape data to get the answer you actually want, rather than trying to do everything in one messy query.

---

## How to Approach It

When faced with a data question, break it down like this:

1. **What data do I need to start with?** → decide your `$match` (filter) condition
2. **Do I need to group anything together?** → decide your `$group` stage
3. **Do I need calculations?** → sums, averages, counts within `$group`
4. **Do I need it sorted?** → add `$sort`
5. **Do I only need certain fields in the result?** → add `$project`

---

## Example: Turning a Question Into a Pipeline

**Question:** "Which city has the highest number of active users?"

**Step-by-step thinking:**
1. Filter → only active users (`$match`)
2. Group → by city, counting users in each (`$group`)
3. Sort → highest count first (`$sort`)
4. Limit → just the top result (`$limit`)

**Resulting pipeline:**
```js
db.users.aggregate([
  { $match: { status: "active" } },
  { $group: { _id: "$city", userCount: { $sum: 1 } } },
  { $sort: { userCount: -1 } },
  { $limit: 1 }
]);
```

---

## Practice Approach

Whenever you get a data question, **write out the steps in plain English first**, before writing any code:

> "I need to filter by X, then group by Y, then sort by Z."

Only after that, translate each plain-English step into its matching aggregation stage (`$match`, `$group`, `$sort`, etc.). This habit prevents you from getting stuck trying to write the whole query in one go, and mirrors exactly how real-world data questions are solved.