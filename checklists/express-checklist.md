# Core Express Project Setup Checklist

## 1. Environment and Infrastructure

- [ ] Initialize the project using npm and configure TypeScript compilation (`tsconfig.json`).
- [ ] Use Node's native `--env-file=.env` flag in your launch scripts to manage environment variables without third-party packages.
- [ ] Create a `.env.example` file to document all required backend keys and database secrets.
- [ ] Install `cors` and configure it explicitly to whitelist only your frontend domain.

## 2. Testing Setup

- [ ] **Choose and setup your backend test runner** (this is the environment that runs your automated assertions via your .test.js/.test.ts test files). Here are you two options:
*   The Native Node Test Runner Route: No dependencies, sick! All you gotta do is add this line to your **package.json** script field: `"test": "node --test --watch"`
*   The Vitest Test Runner: You need to install it via `npm install -D vitest` and then configure your **package.json** script field as such: `"test: "vitest"`
- [ ] **Configure your live testing server**: Since Node doest this, you don't need to install anything. Just add this line to your scripts field so you can easily spin it up: `"dev": "node --watch app.js"` 

Now, when you start developing, you just need to run `npm run dev` and `npm run test` 

## 3. Security and Middlewares

- [ ] Install `helmet` middleware to secure HTTP headers and protect against common vulnerabilities.
- [ ] Implement `express.json()` middleware to parse incoming JSON payloads.
- [ ] Build a centralized, global error-handling middleware to prevent raw error leaks to the client.

## 3. Routing and Token Authentication

- [ ] Structure routes using an isolated router pipeline (e.g., separating `/api/auth` and `/api/resources`).
- [ ] Implement a reusable custom middleware to verify incoming JWT strings in request headers.
- [ ] Secure sensitive endpoints by injecting the JWT verification middleware into those routes.
