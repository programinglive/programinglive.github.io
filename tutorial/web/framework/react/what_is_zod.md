---
title: What is Zod
layout: default
parent: ReactJS
grand_parent: Framework
description: "What is Zod"
---

# What is Zod?

**Intro:**
In modern TypeScript projects, validating data structures and ensuring type safety is crucial, especially when handling user inputs, external APIs, or complex application state. Zod is a TypeScript-first schema declaration and validation library that makes defining, parsing, and validating data a seamless experience. In this article, we'll explore what Zod is, why it's beneficial, and how to get started using it in your TypeScript projects.

---

## What is Zod?

Zod is a TypeScript library for data validation and schema declaration. Created to simplify data validation and type safety, Zod allows developers to define data schemas that enforce specific rules for their application's inputs and outputs. It’s particularly popular in TypeScript applications because it provides a strict, statically typed schema without relying on runtime checks.

With Zod, you can define complex nested structures, enforce validation rules, and easily convert schema definitions into TypeScript types. This makes it a valuable tool for any TypeScript project where data reliability is a priority.

---

## Key Features of Zod

1. **Type Inference**: Zod automatically infers TypeScript types from schemas, which reduces the need for redundant typing. This allows for powerful type-checking without cluttering the codebase.
2. **Composable Schemas**: You can create modular, reusable schemas by combining smaller ones. This is especially useful for managing larger projects with multiple data structures.
3. **Custom Error Messages**: With Zod, you can specify custom error messages for each schema, making debugging much easier.
4. **Integration with TypeScript**: Zod integrates seamlessly with TypeScript, offering end-to-end type safety and validation in one place.
5. **Parsing and Transforming Data**: Besides validating, Zod can parse and transform data, which is beneficial when working with inconsistent or unstructured inputs.

---

## Why Use Zod?

### Type Safety and Reduced Errors
Using Zod in TypeScript projects ensures that data structures are validated at compile-time and runtime. This means fewer surprises in production and reduced chances of runtime errors.

### Improved Developer Experience
Since Zod infers types from schemas automatically, it simplifies the developer experience by reducing redundant typing. This lets developers focus more on writing logic than manually creating types.

### Flexible and Powerful Validation
Zod provides a comprehensive set of built-in validators for handling different data types, as well as the ability to create custom validators, enabling developers to enforce specific rules as needed.

---

## Getting Started with Zod

Let’s dive into a basic setup to show how easy it is to start using Zod in a TypeScript project.

### Installation

Install Zod with npm or yarn:

```bash
npm install zod
# or
yarn add zod
```

### Basic Usage

Here's a quick example of how to define and validate a simple schema with Zod:

```typescript
import { z } from "zod";

// Define a schema
const UserSchema = z.object({
  name: z.string(),
  age: z.number().int().positive(),
  email: z.string().email(),
});

// Parse data
const result = UserSchema.safeParse({
  name: "Alice",
  age: 25,
  email: "alice@example.com",
});

if (result.success) {
  console.log("Data is valid:", result.data);
} else {
  console.log("Validation errors:", result.error.errors);
}
```

### Defining Nested Schemas

Zod allows nesting schemas for more complex data structures. For example, if you have a `User` with `Address` data:

```typescript
const AddressSchema = z.object({
  street: z.string(),
  city: z.string(),
  zipCode: z.string().min(5),
});

const UserWithAddressSchema = UserSchema.extend({
  address: AddressSchema,
});

// Parsing user data with an address
const userWithAddress = UserWithAddressSchema.safeParse({
  name: "Alice",
  age: 25,
  email: "alice@example.com",
  address: {
    street: "123 Main St",
    city: "Wonderland",
    zipCode: "12345",
  },
});
```

---

## Advanced Zod Features

### Custom Validation

You can create custom validation rules if your data needs more complex requirements.

```typescript
const AgeSchema = z.number().refine((age) => age > 18, {
  message: "Must be older than 18",
});
```

### Parsing and Transforming Data

Zod also supports data transformation. For example, if you want to transform a string to uppercase:

```typescript
const NameSchema = z.string().transform((str) => str.toUpperCase());
```

### Zod with Async Validation

For asynchronous validation (like checking if an email is already registered), Zod provides `superRefine` for integrating custom async checks:

```typescript
const AsyncSchema = z.string().superRefine(async (data, ctx) => {
  const exists = await checkIfDataExists(data); // Example async check
  if (exists) {
    ctx.addIssue({ code: z.ZodIssueCode.custom, message: "Data already exists" });
  }
});
```

---

## Conclusion

Zod is an essential library for TypeScript developers who want to ensure type safety and data validation in their applications. By leveraging Zod’s schema declaration and validation capabilities, you can simplify type management, avoid redundant code, and minimize runtime errors. If you're working in TypeScript and need reliable data handling, Zod is definitely worth exploring.