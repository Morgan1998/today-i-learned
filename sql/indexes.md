# Indexing in SQL

### Why not just create an index for all of your columns if it makes everything SOOOO fast?

1. The engine only brings in one index into RAM for each query anyway
2. RAM overhead. Wait what? Didn't I just write that only one index comes into RAM per query? Welp, turns out
   that index you index everything, every time you do a query that changes your database (`INSERT`, `UPDATE`, or `DELETE`), the database has
   to pull each individual page from all those useless indexes in to your buffer pool (a little designated spot in RAM to hold 'hot' stuff) in order to update them ALL so the b trees stay accurate. Oof. To my understanding, this kicks out the real hot data from the buffer pool which in turn makes your system a whole lot less performant.
3. The writing. Lots of writing. So as stated above, each index possibly will have to be updated after the query. I have a basic understanding of the actual structural changes, like with pages, but for now I'll give this topic a break and revisit it later to gain a
   better understanding.
4. Disk bloat. Indexes take up space on the drive. They can get big, super big.
5. So I know that only one index is pulled in per query. Well, if we give the engine 20 options (because we have 20 indexes), the engine has
   to do a whole lot of effort, and therefore CPU overhead, just to decide which one to use. :O

### When to index columns

From what I've read so far, I've come up with this:

1. Columns used often in `WHERE` clauses
2. Columns used often in `JOIN` conditions
3. Columns used often in `ORDER BY` operations

I repeated myself a lot up there just now. I should be ashamed of myself as an engineer that studied The Odin Project. (I'm sleepy and I should sleep... lol)
