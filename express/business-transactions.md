# What's a business transaction?

It's simple Morgan. It's just a sequence of multiple database operations (like inserts, updates, deletes, selects) that are grouped together inside a service layer function to fulfill a single real world [use case](usecases.md).

## Some extra notes:

1. All or nothing! It relies on database Atomicity (which is the A in ACID). Every single database change in the sequence has to succeed, or they're all rolled back. This prevents data corruption.
2. To add onto point number 1, all or nothing ensures that our states don't get out of whack. If we allowed one part of the sequence to stay changed but another part not change, then our whole system would be out of sync. Ahhhh!
3. It makes it so one [use case](usecases.md) can be process via one http request on the backend instead of having to send multiple requests just to achieve one goal/use-case. If we did that, it'd be called a chatty API. Chat APIs are no good haha,
