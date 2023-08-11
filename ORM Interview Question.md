
---

# ORM Interview Questions: Prisma & Sequelize

## Prisma

### 1. **What is Prisma?**
   - **Answer**: Prisma is an open-source database toolkit that includes an ORM, a query engine, and a migration system.
   - **Example**:
     ```javascript
     const { PrismaClient } = require('@prisma/client');
     const prisma = new PrismaClient();
     ```

### 2. **How does Prisma differ from traditional ORMs?**
   - **Answer**: Prisma uses an auto-generated query builder based on your database schema, ensuring type safety. Traditional ORMs often rely on model definitions within the application code.
   - **Example**: No code example necessary for this conceptual question.

### 3. **How do you define models in Prisma?**
   - **Answer**: Models in Prisma are defined in the Prisma schema file (`schema.prisma`).
   - **Example**:
     ```prisma
     model User {
       id    Int     @id @default(autoincrement())
       name  String
       posts Post[]
     }

     model Post {
       id     Int  @id @default(autoincrement())
       title  String
       author User @relation(fields: [authorId], references: [id])
       authorId Int
     }
     ```

### 4. **How does Prisma handle migrations?**
   - **Answer**: Prisma Migrate, a part of the Prisma toolkit, handles database migrations. It uses the Prisma schema to generate and execute SQL migration scripts.
   - **Example**: 
     ```bash
     npx prisma migrate dev --preview-feature
     ```

## Sequelize

### 5. **What is Sequelize?**
   - **Answer**: Sequelize is a promise-based Node.js ORM that supports multiple database systems, including PostgreSQL, MySQL, SQLite, and MSSQL.
   - **Example**:
     ```javascript
     const { Sequelize } = require('sequelize');
     const sequelize = new Sequelize('database', 'username', 'password', { dialect: 'mysql' });
     ```

### 6. **How do you define models in Sequelize?**
   - **Answer**: Models in Sequelize are defined using the `define` method of the Sequelize instance.
   - **Example**:
     ```javascript
     const User = sequelize.define('User', {
       firstName: { type: Sequelize.STRING },
       lastName: { type: Sequelize.STRING }
     });
     ```

### 7. **How does Sequelize manage relationships between models?**
   - **Answer**: Sequelize provides methods like `hasOne`, `hasMany`, `belongsTo`, and `belongsToMany` to establish relationships between models.
   - **Example**:
     ```javascript
     const User = sequelize.define('user', { /* ... */ });
     const Project = sequelize.define('project', { /* ... */ });

     User.hasMany(Project);
     ```

### 8. **How do you handle migrations in Sequelize?**
   - **Answer**: Sequelize uses a CLI tool for migrations. This tool helps create migration scripts and manage their execution against the database.
   - **Example**:
     ```bash
     sequelize-cli migration:generate --name create-user
     sequelize-cli db:migrate
     ```

---

