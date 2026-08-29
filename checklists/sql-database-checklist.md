# Core SQL Database Setup Checklist

## 1. Schema Design and Initialization

- [ ] Initialize Prisma in the project using `npx prisma init`.
- [ ] Configure the database provider to `postgresql` and map the connection URL string natively to your `.env` file.
- [ ] Define relational database tables using appropriate primary keys, data types, and unique constraints.
- [ ] Establish explicit relationships (e.g., One-to-Many or Many-to-Many) between tables using foreign keys.

## 2. Migrations and Version Control

- [ ] Create and execute database migrations using `npx prisma migrate dev` to track schema changes in Git.
- [ ] Verify that the auto-generated Prisma Client types regenerate successfully after every migration.
- [ ] Keep raw database credentials out of version control by tracking them only in your local environment.

## 3. Query Optimization and Safety

- [ ] Ensure all input data is parameterized through the Prisma ORM or sanitized raw queries to completely block SQL injection.
- [ ] Set up an automated database seeding script (`prisma/seed.ts`) to easily populate local environments with dummy data.
