# Using AI for Query Generation & Schema Suggestions
 
## 1. Using AI for Query Generation
 
Instead of writing every MongoDB query from scratch, AI can help draft one — but you should always give clear context so the output is actually usable.
 
**Good prompt example:**
```
I have a "users" collection with fields: name, age, city, status. 
Write a MongoDB query to find all active users from Kochi who are 
older than 18, and only return their name and age.
```
 
This works better than a vague prompt like "write me a MongoDB query" because it gives the AI the exact field names and condition needed.
 
---
 
## 2. Using AI for Schema Suggestions
 
AI can help you design a schema when you're not sure how to structure your documents — especially useful for deciding between embedding vs referencing.
 
**Good prompt example:**
```
I'm building a blogging app with users and posts. Each user can have 
many posts. Suggest a MongoDB schema, and tell me whether I should 
embed or reference the posts, and why.
```
 