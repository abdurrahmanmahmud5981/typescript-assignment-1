# Assignment 1: Problem Solving with TypeScript & OOP

This assignment contains eight TypeScript solutions covering typed functions, union types, readonly tuples, interfaces, generics, inheritance, access modifiers, and asynchronous programming. All coding solutions are implemented in [solutions.ts](./solutions.ts).

## Solutions Overview

| Problem | Function or Class | Description |
| --- | --- | --- |
| 1 | `multiplyValue` | Multiplies a value by an optional multiplier, defaulting to `2` when omitted and correctly handling `0`. |
| 2 | `processInput` | Uses type narrowing to trim and lowercase strings, multiply numbers by `10`, or format booleans as `Active` or `Inactive`. |
| 3 | `formatCoordinate` | Formats a readonly coordinate tuple as `Location: [locationName] ([latitude], [longitude])`. |
| 4 | `concatenateArrays` | Combines arrays of the same element type using generics and rest parameters, preserving element order. |
| 5 | `Course`, `getPopularCourses` | Returns a new array of published courses that meet the minimum student count. |
| 6 | `pluckValues` | Extracts property values from objects using generics and a `keyof` constraint. |
| 7 | `Employee`, `Manager` | Demonstrates inheritance and access modifiers through employee details and manager role information. |
| 8 | `validateAgeAsync` | Resolves with `Access Granted` after one second for ages 18 and above; immediately rejects younger ages with an `Error`. |

## Blog Posts

Two blog posts explain selected TypeScript concepts with practical code examples:

1. [Type vs Interface in TypeScript: Differences and Use Cases](./type-vs-interface.md)
2. [Type Narrowing in TypeScript: Working Safely with Union Types](./type-narrowing.md)



