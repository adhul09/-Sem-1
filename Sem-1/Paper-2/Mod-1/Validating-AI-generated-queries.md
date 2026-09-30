# Validating AI-Generated Queries
 
Before running any AI-generated query on your actual database, check it against these points:
 
- **Syntax check** — does it run without errors?
- **Schema accuracy** — do the field names actually match your collection's real fields?
- **Safety check** — does it avoid destructive operations like `deleteMany({})` or `drop()` unless that was specifically intended?
- **Logic check** — does the condition actually match what you asked for (double-check operators like `$gt` vs `$gte`)?
- **Performance** — for large collections, check if the query would benefit from an index
**Simple habit:** always test AI-generated queries on a small sample of data first (or in a test/sandbox database), never directly on production or important data.