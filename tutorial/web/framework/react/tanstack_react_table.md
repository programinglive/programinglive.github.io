---
title: Tanstack React Table
layout: default
parent: ReactJS
grand_parent: Framework
description: "Tanstack React Table"
---

# Tanstack React Table

**Table of Contents**
1. [Introduction](#introduction)
2. [What is Tanstack React Table?](#what-is-tanstack-react-table)
3. [Key Features of Tanstack React Table](#key-features-of-tanstack-react-table)
4. [Implementation Steps](#implementation-steps)
    - [Install the Library](#1-install-the-library)
    - [Define Data and Columns](#2-define-data-and-columns)
    - [Create the Table](#3-create-the-table)
    - [Add Advanced Features](#4-add-advanced-features)
5. [When to Use Tanstack React Table](#when-to-use-tanstack-react-table)
6. [Conclusion](#conclusion)

---

## Introduction
When working with data in web applications, tables are a go-to component for presenting information. However, managing dynamic tables with features like pagination, filtering, and sorting can be challenging. **Tanstack React Table**, formerly known as **React Table**, is a high-performance and flexible library designed to tackle this challenge.

---

## What is Tanstack React Table?
Tanstack React Table is a lightweight and highly customizable table library for React. While it doesn’t provide a user interface (UI) out of the box, it offers a robust API that you can pair with any UI library or framework, such as Material-UI, Bootstrap, or Tailwind CSS.

As a **headless library**, it gives you complete freedom to design and manage your table's appearance without being restricted by built-in styles.

---

## Key Features of Tanstack React Table

1. **Headless and Flexible**  
   Tanstack React Table provides only the logic for tables, leaving the UI implementation entirely up to you.

2. **High Performance**  
   It’s designed to handle large datasets efficiently without compromising application performance.

3. **Deep Customization**  
   It supports complex features like column grouping, data virtualization, and nested sorting.

4. **Client-side and Server-side Rendering**  
   You can choose to process data on the client-side or server-side, depending on your application’s needs.

---

## Implementation Steps

### 1. Install the Library
Use npm or yarn to install Tanstack React Table:
```bash
npm install @tanstack/react-table
```

### 2. Define Data and Columns
You need two main elements to create a table: **data** and **columns**. Here’s an example:

```javascript
import { useTable } from '@tanstack/react-table';

const data = [
  { id: 1, name: 'John Doe', age: 25 },
  { id: 2, name: 'Jane Smith', age: 30 },
  { id: 3, name: 'Sam Brown', age: 22 },
];

const columns = [
  {
    accessorKey: 'id', // key for the data
    header: 'ID',      // column name
  },
  {
    accessorKey: 'name',
    header: 'Name',
  },
  {
    accessorKey: 'age',
    header: 'Age',
  },
];
```

### 3. Create the Table
Use the `useTable` hook to connect the data and columns to the table:

```javascript
import { useTable } from '@tanstack/react-table';

function MyTable() {
  const table = useTable({ data, columns });

  return (
    <table>
      <thead>
        {table.getHeaderGroups().map(headerGroup => (
          <tr key={headerGroup.id}>
            {headerGroup.headers.map(header => (
              <th key={header.id}>{header.renderHeader()}</th>
            ))}
          </tr>
        ))}
      </thead>
      <tbody>
        {table.getRowModel().rows.map(row => (
          <tr key={row.id}>
            {row.getVisibleCells().map(cell => (
              <td key={cell.id}>{cell.renderCell()}</td>
            ))}
          </tr>
        ))}
      </tbody>
    </table>
  );
}
```

### 4. Add Advanced Features
Features like pagination, filtering, or column grouping can be added by customizing the `useTable` configuration.

---

## When to Use Tanstack React Table?
Use this library if you:
- Need full control over your table's design.
- Are working with large datasets requiring optimal performance.
- Need advanced features such as data virtualization or grouping.

However, if you need a simple table with pre-styled components, libraries like Material-UI DataGrid might be more suitable.

---

## Conclusion
Tanstack React Table is a powerful solution for managing data tables in React applications. Its high flexibility lets you create dynamic and optimal user experiences, even though it requires some extra effort to design the UI.

Try Tanstack React Table in your next project and experience the difference!