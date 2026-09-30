#  Data Types and Document Structure

## 1. Data Types in MongoDB

MongoDB documents can store many data types, similar to JSON but a bit richer (BSON):

```js
{
  name: "Adhul",                  // String
  age: 20,                        // Number
  isStudent: true,                // Boolean
  skills: ["JS", "React", "Node"],// Array
  address: {                      // Nested Object
    city: "Kochi",
    pincode: 682001
  },
  joinedAt: new Date(),           // Date
  profilePic: null                // Null
}
```

**Common types:**
- **String** — text data (`"Adhul"`)
- **Number** — integers or decimals (`20`, `3.14`)
- **Boolean** — `true` / `false`
- **Array** — a list of values (`["JS", "React"]`)
- **Object (nested/embedded document)** — data inside data
- **Date** — timestamps
- **Null** — empty/no value
- **ObjectId** — MongoDB's special unique ID type, used for `_id`

---

## 2. Flexible Schema in MongoDB

Unlike SQL, MongoDB doesn't force every document in a collection to have the same fields.

```js
// Both of these can exist in the same "users" collection:
{ name: "Adhul", age: 20 }
{ name: "Riya", age: 22, city: "Kochi", isPremium: true }
```

**Why this matters:**
- You can add new fields later without changing every existing document
- Different documents can have different structures based on need
- Useful when your data naturally varies (e.g., some users have a phone number, some don't)

This flexibility is called a **dynamic** or **schema-less** structure — though in real projects, tools like **Mongoose** (in Node.js) are often used to *enforce* a consistent structure when needed, even though MongoDB itself doesn't require it.

---

## 3. Structured vs Unstructured Documents

**Structured document** (consistent, predictable fields):
```js
{
  name: "Adhul",
  age: 20,
  email: "adhul@example.com"
}
```

**Unstructured / varied document** (fields differ per document):
```js
{
  name: "Riya",
  hobbies: ["reading", "coding"],
  socialLinks: {
    instagram: "@riya",
    github: "riya-dev"
  }
}
```

**Practice idea:**
Try creating one document with only basic fields (name, age), and another in the same collection with nested objects and arrays (address, hobbies) — both are valid in MongoDB, which is the core idea behind its flexible schema.