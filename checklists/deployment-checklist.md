# Core Deployment Setup Checklist

## 1. Environment and Configuration Alignment

- [ ] Create separate production environment files or configure config variables directly in your hosting dashboards.
- [ ] Update your backend production CORS configurations to explicitly whitelist only your live frontend URL.
- [ ] Swap out local database connection strings for your live, hosted production database URL.
- [ ] Generate a cryptographically secure, random string to use as your production JWT secret key.

## 2. Build and Verification Steps

- [ ] Run a local production build for both frontend and backend to verify there are no TypeScript or compilation errors.
- [ ] Ensure the frontend build output process correctly handles routing fallbacks (e.g., configuring redirects for single-page apps).
- [ ] Confirm the backend start script uses the compiled JavaScript file (e.g., `node dist/server.js`) rather than development tools like `ts-node`.

## 3. Database Execution

- [ ] Run production database migrations during the deployment pipeline to update the live schema.
- [ ] Execute your database seed script on the production database if your live application requires baseline lookup data to function.
