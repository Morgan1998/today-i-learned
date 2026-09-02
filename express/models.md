# Models. What the heck are they?

A model is a dedicated module or class that represents a specific database table. That's why it's called a 'model'. Because... it models the table you're working with. BAZINGA!

Some stuff to keep in mind with models:

1. It has individual methods that execute specific database queries for that table (findById, create, update. etc.)
2. It defines the exact schema, data types, validation rules, and relationships for that specific resource.
   **little side note on this (because I was confused about it for a while).**

- First, why does it define the schema in our application layer if the database already has a schema defined? Because if we send invalid data to the database, the database will scream at us and throw errors or crash. By exactly mirroring the schema in our model ahead of time, we can ensure that database only gets valid queries which in turn makes our whole system way more efficient.
- Second, why does it map the relationships we set up in our database? Because by doing so in our application layer, we can make clean, powerful queries that leverage those relationships via foreign keys and joins.

3. It should **never** contain business logic. Your [service](services.md) is what's supposed to handle the business logic. The model should only care about how to store, retrieve, and structure data for your table.
