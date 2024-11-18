---
title: What is Zod
layout: default
parent: ReactJS
grand_parent: Framework
description: "What is Zod"
---

# Zod

**Table of Contents**
1. [Introduction](#introduction)
2. [What is Zod?](#what-is-zod)
3. [Why Use Zod?](#why-use-zod)
4. [Basic Zod Example](#basic-zod-example)
5. [Zod Schema Types](#zod-schema-types)
6. [Custom Validation with Zod](#custom-validation-with-zod)
7. [Integration with TypeScript](#integration-with-typescript)
8. [Error Handling in Zod](#error-handling-in-zod)
9. [Comparison with Other Libraries](#comparison-with-other-libraries)
10. [Conclusion](#conclusion)

---

## Introduction
Zod is a TypeScript-first schema validation library designed to make validating and parsing data straightforward and type-safe. Unlike other libraries, Zod directly integrates with TypeScript’s type system, ensuring that both runtime validation and static types stay in sync.

---

## What is Zod?
Zod is a validation library used to validate inputs and ensure they conform to a predefined structure. It allows you to define schemas for your data models and then validates data against these schemas, throwing errors when data doesn’t match. Zod is particularly focused on TypeScript, providing first-class type safety without needing to define separate types.

---

## Why Use Zod?
1. **Type Safety:** Zod integrates seamlessly with TypeScript’s static type system, providing compile-time guarantees.
2. **Minimal and Simple:** The API is clean and easy to use, making it a good choice for TypeScript users.
3. **Immutability:** Zod schemas are immutable, meaning you can reuse and chain them in a safe and predictable way.
4. **Fast and Efficient:** Zod is designed for performance, making it a good choice for both small and large applications.
5. **Built-in Parsing:** Zod automatically parses and validates data without needing a separate schema for parsing.

---

## Basic Zod Example
Let’s start with a simple example of creating a schema for a user object.

```typescript
import { z } from 'zod';

const userSchema = z.object({
  name: z.string(),
  age: z.number().min(18),
  email: z.string().email(),
});

const userData = {
  name: 'Alice',
  age: 25,
  email: 'alice@example.com',
};

userSchema.parse(userData);  // No error if valid
```

If the `userData` object doesn't conform to the schema, an error will be thrown.

---

## Zod Schema Types
Zod offers various schema types for handling different types of validation, such as:

- **z.string():** Validates strings.
- **z.number():** Validates numbers.
- **z.boolean():** Validates boolean values.
- **z.array():** Validates arrays.
- **z.object():** Validates objects with specific properties.
- **z.enum():** Validates enum values.
- **z.union():** Validates against multiple schemas.
- **z.nullable() / z.optional():** Allows for nullable or optional values.

**Example with an array schema:**

```typescript
const numberArraySchema = z.array(z.number().min(0));

const validArray = [1, 2, 3];
const invalidArray = [1, -2, 3];

numberArraySchema.parse(validArray);  // Passes
numberArraySchema.parse(invalidArray);  // Throws error due to negative number
```

---

## Custom Validation with Zod
Zod allows you to define custom validation logic using `.refine()` or `.superRefine()` methods.

**Example with custom validation:**

```typescript
const userSchema = z.object({
  name: z.string().min(3),
  password: z.string().min(6),
}).refine(data => data.password.includes('123'), {
  message: 'Password must contain 123',
  path: ['password'],
});

const invalidData = { name: 'John', password: 'password' };
userSchema.parse(invalidData); // Throws an error because 'password' does not contain '123'
```

---

## Integration with TypeScript
Zod’s power lies in its integration with TypeScript. When you define a schema, Zod automatically infers TypeScript types for you. This means you don't need to manually define types in separate locations.

**Example:**

```typescript
const personSchema = z.object({
  name: z.string(),
  age: z.number(),
});

type Person = z.infer<typeof personSchema>;

const person: Person = {
  name: 'Alice',
  age: 30,
};
```

Zod uses TypeScript's type system to automatically infer the type of `Person` based on the schema, ensuring that the `person` object adheres to the structure defined by the schema.

---

## Error Handling in Zod
When validation fails, Zod throws detailed errors, which you can catch and handle appropriately.

**Example of error handling:**

```typescript
try {
  userSchema.parse({ name: 'Bob', age: 15, email: 'invalid-email' });
} catch (e) {
  if (e instanceof z.ZodError) {
    console.log(e.errors);  // Logs detailed error information
  }
}
```

Zod’s errors are easy to work with, providing clear messages and paths to help you debug data issues.

---

## Comparison with Other Libraries
Zod is often compared to other schema validation libraries, such as **Joi**, **Yup**, and **Runtypes**. While all these libraries serve similar purposes, Zod stands out due to its deep integration with TypeScript, simple API, and speed.

- **Zod vs Joi:** Zod is TypeScript-first, while Joi is more JavaScript-centric. Zod’s integration with TypeScript types is more seamless.
- **Zod vs Yup:** Both are great for validation, but Zod has a simpler API and is known for better TypeScript support.
- **Zod vs Runtypes:** Runtypes is similar but doesn’t offer the same level of schema building and validation flexibility as Zod.

---

## Conclusion
Zod is a powerful schema validation library that offers TypeScript-first integration, simple API usage, and high performance. It ensures data is correctly validated and parsed, helping developers write safer, more predictable code. Whether you’re building APIs, managing form data, or handling complex state, Zod makes validation painless and type-safe.

If you are working with TypeScript and need robust, easy-to-use validation, Zod is an excellent choice!