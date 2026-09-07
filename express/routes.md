# Routes

A route is a specific combo of an HTTP method (like GET, POST, PUT, DELETE) and a URL path ( like /users or /checkout) that tells your app app how to listen for incoming client requests.

# Some notes

1. **It's the matchmaker**: It acts as the very entry point of your server. It matches what the user typed in their app with the code inside your backend.
2. **It's also the Director**: Once a route matches, it passes the incoming request through your middle ware pipeline and then routes it directly to its final Controller Action.
