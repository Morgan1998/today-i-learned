# Core Express Project Setup Checklist

## 1. Environment and Infrastructure

- [ ] Initialize the project using npm and configure TypeScript compilation (`tsconfig.json`).
- [ ] Use Node's native `--env-file=.env` flag in your launch scripts to manage environment variables without third-party packages.
- [ ] Create a `.env.example` file to document all required backend keys and database secrets.
- [ ] Install `cors` and configure it explicitly to whitelist only your frontend domain.

## 2. Security and Middlewares

- [ ] Install `helmet` middleware to secure HTTP headers and protect against common vulnerabilities.
- [ ] Implement `express.json()` middleware to parse incoming JSON payloads.
- [ ] Build a centralized, global error-handling middleware to prevent raw error leaks to the client.

## 3. Routing and Token Authentication

- [ ] Structure routes using an isolated router pipeline (e.g., separating `/api/auth` and `/api/resources`).
- [ ] Implement a reusable custom middleware to verify incoming JWT strings in request headers.
- [ ] Secure sensitive endpoints by injecting the JWT verification middleware into those routes.
