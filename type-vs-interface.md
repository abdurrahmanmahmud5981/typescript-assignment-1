# Type vs Interface in TypeScript: Differences and Use Cases

## Introduction

TypeScript provides both `type` aliases and `interface` declarations to describe data structures. Although both can define object shapes, their capabilities differ. Understanding these differences helps us choose a suitable tool and keep our code consistent.

## Detailed Discussion

An `interface` describes an object contract, including its properties and methods. A `type` alias can describe objects, unions, tuples, and primitive types. In this example, `Status` restricts values to two specific strings, while `Coordinate` represents a readonly tuple.

```ts
type Status = "active" | "inactive";

interface User {
  name: string;
  status: Status;
}

type Coordinate = readonly [number, number];
```

One important difference is declaration merging. TypeScript combines compatible interface declarations with the same name in the same scope. Repeated properties must have compatible declarations. This is useful when extending existing contracts, such as library interfaces. Type aliases cannot be reopened this way; declaring the same alias twice produces an error.

```ts
interface Profile {
  name: string;
}

interface Profile {
  age: number;
}

const profile: Profile = { name: "Rakib", age: 22 };

interface Admin extends Profile {
  permissions: string[];
}

type Editor = Profile & { canEdit: boolean };
```

Interfaces support inheritance through `extends`. Type aliases can combine object requirements using the intersection operator `&`. Both `Admin` and `Editor` therefore require the properties from `Profile`. However, conflicting properties behave differently: interface extension can report a conflict immediately, while an intersection may produce an impossible property type such as `never`.

## Conclusion

Choose `interface` for object contracts that benefit from extension or declaration merging. Choose `type` for unions, tuples, and other type expressions. Neither is universally better; follow the requirements and conventions of the project.
