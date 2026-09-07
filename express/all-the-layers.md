# The overall journey/chain of the backend

1. So it all starts with our [Use Case](usecases.md).
2. App-level middleware (the main ones we always want are helmet, cors, cookies-parser, json)
3. Public endpoints/route-mounts (not guarded by our authentication middleware)
4. We can then either use an app level middleware that authenticates and therefore makes all routes below it guarded. However, I've
   learned that it's probably better practice to pass in our authentication middleware in as an argument to the app level endpoints/route-mounts that we want to guard.
5. Our protected app level route mounts (which route our request to a dedicated router that has more routes for that prefix). I suppose putting them below our public endpoints/route mounts is best practice for organization if we go with the pass-auth-middleware-in strategy.
6. The Controller Layer: the receptionist that accepts the request, validates the request structure, and hands it off. Zod is what i'll be learning to validate my payloads in my controllers.
7. The Service Layer: The manager that orchestrates the use case, calling smaller services if needed, keeping the [Business Transaction](business-transactions.md) atomic. Gotta keep this 1:1 with the use case.
8. The Model Layer: The workers executing precise database queries while mirroring your schema rules so the database never breaks. Prisma will be taking care of this.
9. And finally, the permanent database update.
