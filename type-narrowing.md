# Type Narrowing in TypeScript: Working Safely with Union Types

## Introduction

A union type allows a variable to hold values of different types. However, an operation may be valid for only some of those values. Type narrowing reduces the possible types through checks, allowing TypeScript to verify operations within each branch.

## Detailed Discussion

TypeScript analyzes conditions and control flow to determine which types remain possible. For primitive values, `typeof` provides a straightforward check. Here, string methods are available only inside the string branch.

```ts
function processValue(value: string | number): string | number {
  if (typeof value === "string") {
    return value.trim().toLowerCase();
  }
  return value * 10;
}
```

Because the string branch returns, the remaining value must be a number. This avoids unnecessary type assertions. Remember that `typeof null` returns `"object"`, so object checks may also require a null check.

The `instanceof` operator checks whether a value belongs to a constructor's prototype chain. It helps distinguish class instances, such as a `Date`, from other values.

```ts
function formatDate(value: Date | string): string {
  if (value instanceof Date) {
    return value.toISOString();
  }
  return value;
}
```

Inside the first branch, TypeScript allows the `toISOString` method. For objects with different properties, the `in` operator can narrow a union by checking whether a property exists.

```ts
type Admin = { name: string; permissions: string[] };
type Student = { name: string; course: string };

function describeUser(user: Admin | Student): string {
  if ("permissions" in user) {
    return user.permissions.join(", ");
  }
  return user.course;
}
```

Here, only `Admin` declares the required `permissions` property, so the check distinguishes the two types. An optional property needs extra care: its declaring type can remain possible in both branches.

## Conclusion

Narrowing makes union types easier to use safely. Choosing an appropriate guard helps the compiler catch invalid operations and reduces the need for `any` or unchecked assertions.
