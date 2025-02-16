# Drizzle ORM Query Comparison Operators

Drizzle ORM provides a powerful way to filter data using SQL-based conditions. Below are examples of how to use comparison operators in Drizzle ORM.

## Importing Drizzle ORM Operators

You can import operators from `drizzle-orm` or use them inside a callback function.

### Importing Operators
```ts
import { eq } from 'drizzle-orm';

const users = await db.query.users.findMany({
    where: eq(users.id, 1)
});
```

### Using Callback Syntax
```ts
const users = await db.query.users.findMany({
    where: (users, { eq }) => eq(users.id, 1),
});
```

## Available Query Operators

### `$eq` (Equal)
Find users whose **age is exactly 25**:
```ts
const users = await db.query.users.findMany({
  where: eq(users.age, 25),
});
```

### `$ne` (Not Equal)
Find users whose **role is not "Admin"**:
```ts
import { neq } from 'drizzle-orm';

const users = await db.query.users.findMany({
  where: neq(users.role, "Admin"),
});
```

### `$gt` (Greater Than)
Find employees who have **salary greater than 50,000**:
```ts
import { gt } from 'drizzle-orm';

const employees = await db.query.employees.findMany({
  where: gt(employees.salary, 50000),
});
```

### `$gte` (Greater Than or Equal)
Find users who have **5 or more years of experience**:
```ts
import { gte } from 'drizzle-orm';

const users = await db.query.users.findMany({
  where: gte(users.experience, 5),
});
```

### `$lt` (Less Than)
Find products that cost **less than $100**:
```ts
import { lt } from 'drizzle-orm';

const products = await db.query.products.findMany({
  where: lt(products.price, 100),
});
```

### `$lte` (Less Than or Equal)
Find employees whose **working hours are 40 or less**:
```ts
import { lte } from 'drizzle-orm';

const employees = await db.query.employees.findMany({
  where: lte(employees.workingHours, 40),
});
```

### `$in` (Matches Any in Array)
Find users whose **role is "Admin" or "Editor"**:
```ts
import { inArray } from 'drizzle-orm';

const users = await db.query.users.findMany({
  where: inArray(users.role, ["Admin", "Editor"]),
});
```

### `$nin` (Matches None in Array)
Find users whose **role is NOT "Guest" or "Banned"**:
```ts
import { notInArray } from 'drizzle-orm';

const users = await db.query.users.findMany({
  where: notInArray(users.role, ["Guest", "Banned"]),
});
```

These operators allow you to create powerful queries with Drizzle ORM while keeping your code clean and readable.

