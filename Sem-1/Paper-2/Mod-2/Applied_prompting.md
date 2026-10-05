# Applied Prompting

## 1. Prompt Chaining (Multi-Step Requests)

Instead of asking for everything in one massive prompt, **prompt chaining** means breaking a task into sequential steps, where each step builds on the previous one's output.

**Example — building a feature step by step:**
```
Step 1: "Design a Mongoose schema for a 'Product' with name, price, and stock."
Step 2: "Now write a controller with CRUD functions for this Product model."
Step 3: "Now write the Express routes that connect to these controller functions."
Step 4: "Now add validation to the create function, ensuring price is a positive number."
```

**Why this works better than one giant prompt:**
- Easier to review and catch mistakes at each stage
- AI output stays more focused and accurate
- You can adjust earlier steps before moving forward, instead of redoing everything

---

## 2. Generating APIs with Constraints

Giving the AI specific constraints leads to much more usable output than a vague request.

**Vague prompt (avoid):**
```
Make me an API for users.
```

**Constrained prompt (better):**
```
Create an Express REST API for a "User" resource with fields: name, email, age. 
Include GET, POST, PUT, DELETE routes. Use Mongoose for the model. Follow MVC 
structure with separate model, controller, and route files. Include basic 
validation (name and email required, age must be a positive number).
```

**Common constraints worth specifying:**
- Folder/file structure (MVC or not)
- Which fields and data types
- Validation requirements
- Response format (e.g., `{ success, data, message }`)
- Error handling expectations

---

## 3. Debugging Backend Logic Using AI

When debugging backend issues, give the AI **enough context to actually diagnose the problem** — not just the error, but what you expected to happen.

**Good debugging prompt:**
```
I'm getting "Cannot POST /users" when testing in Postman. Here's my route file 
[paste code] and my app.js [paste code]. I expected it to create a new user. 
What's likely causing this?
```

This kind of error usually means a route isn't properly registered or the HTTP method doesn't match — but the AI needs your actual code to confirm instead of guessing generically.

---

## 4. Understanding Hallucinations in Code

**Hallucination** = when AI confidently generates something that looks correct but is actually wrong — like inventing a method or package feature that doesn't exist.

**Common ways this shows up in backend code:**
- Using a Mongoose/Express method that sounds plausible but isn't real
- Referencing an outdated syntax from an older library version
- Assuming a package is installed when it isn't
- Generating a working-looking solution that doesn't actually match how your specific schema/routes are structured

**How to catch and avoid this:**
- Always test the generated code — don't assume it runs correctly
- Cross-check unfamiliar methods against official documentation
- If something errors out with "is not a function" or similar, it's a strong sign of a hallucinated method
- Give the AI your actual code/schema as context, rather than asking generically — reduces the chance of mismatched assumptions

**Simple habit:** treat AI-generated backend code as a **first draft**, not a final answer — review, test, and verify before trusting it in a real project (same principle as the "Validating AI-Generated Queries" habit from the MongoDB module).
