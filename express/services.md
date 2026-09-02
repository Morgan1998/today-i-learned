# Services

To be brief, your router exposes an endpoint and forwards the request to a specific controller action. That controller action then calls a service. The service is a collection of calls of one or more methods of one or multiple of your [models](models.md) with the goal of successfully carrying out a [use case](usecases.md). The collection of model calls coordinated by your service is called a [business transaction](business-transactions.md).

## Some notes

1. The 1:1 Controller-to-Service Rule: A controller action should ideally call exactly **one** Service method to execute a Use Case. If a Use Case is complex and requires combining multiple other services, those services should be called and coordinated inside the SErvice Layer itself (which is called Service Orchestration), never in the Controller. Why? Because then it's no longer atomic in nature, and therefore it's no longer a true [business transaction](business-transactions.md)! If `service A` does a query and it succeeds, and then `service B` comes in and fails... welp... service A is done and permanently changed. So, **don't pass in multiple services to your controllers**!
2. So why can we nest services in one service? How does that keep it atomic? Because at the top of your main service's function, you can open a single database transaction. Every nested service call inside it will share that exact same database connection and transaction block. If anything goes wrong anywhere down the line, the database engine rolls back the ENTIRE master transaction instantly. Still atomic :D
